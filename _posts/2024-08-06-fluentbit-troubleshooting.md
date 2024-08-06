---
title:  Fluentbit OOM Trouble shooting
author: icyou
date: 2024-08-06 00:00:00 +0900
categories: [Infra, Logging]
tags: [Logging, Fluentbit, OOM]
pin: true
math: true
---

### Fluentbit OOM Trouble shooting
##### OOM 원인 분석
Fluentbit에서 OOM이 발생하여 이에 대한 원인을 찾고 문제를 해결하는 과정을 기록했습니다.

먼저, OOM 발생 원인을 찾기 위해 fluentbit log를 확인했을 때, OOM의 원인에 대한 이유는 나와있지 않아 있어서 원인을 유추하는 수밖에 없다고 생각했습니다.  
다른 project의 fluentbit config, 동일 project에서 여러 region에서 발생하는 OOM의 pod 수 및 빈도 수를 확인하며 원인을 다음과 같이 유추했습니다.

1. application log 설정이 debug level로 설정되어 있어 너무 많은 log가 쌓이고 있는 상황
2. 이 상황에서, fluentbit에서 elasticsearch(es) 뿐만 아니라, s3에도 log를 쌓고 있어 log 쌓이는 속도가 가중되는 상황
3. 하루에 s3에 쌓이는 log가 100GB 이상
4. 

이 두 가설이 맞는지를 검증하기 위해서 DEV, QA 환경의 fluentbit config 설정을 변경하려고 했습니다. 두 번째 가설의 경우, s3로 log를 보내는 output 설정을 삭제하니 OOM이 발생하지 않는 것을 확인했지만 s3로 log를 보내는 것 또한 필수적이므로 삭제가 불가능한 상황이었고, 첫 번째 가설의 경우 PRD 환경의 application log가 많이 쌓이는 상황에서 debug level을 수정해야하는데, PRD 설정값을 수정하는 것은 불가능한 상황이라 가설 검증도 할 수 없었습니다.  

어차피 두 설정값을 변경할 수 없는 상황에서 이 문제를 해결하기 위해서는 다른 설정값을 조금 더 최적화하는 방식으로 문제를 개선하는 수밖에는 없었습니다.  

##### OOM 해결 과정
1. fluentbit의 memory limit을 넉넉히 설정해서 OOM이 발생하지 않는지 확인  
-> 100MB -> 1G까지 memory를 늘리고 pod를 재기동했어도 OOM이 발생하는 시간이 느려질 뿐, OOM이 발생하는 현상이 지속됨  
2. memory buffer, backpressure의 가능성  
-> INPUT, OUTPUT memory buffer를 늘리거나 storage를 virtual memory로 활용하도록 설정해보기도 했으나, 동일하게 OOM 발생 (storage를 사용할 경우, 오히려 OOM이 발생하는 시간이 빨라짐)  
-> backpressure 해결방안은 batch 같이 특정 시간에 log가 많이 발생하는 경우에 대한 처리방법으로 보임
3. 위 방법을 다시 검증하기 위해 fluentbit config의 설정값들 중, performance에 영향을 줄만한 요소들을 전부 삭제하고 fluentbit 설정값 초기화 수준으로 설정  
-> buffer 초기화, pipeline 삭제
4. fluentbit의 OUTPUT에 맞춰 tail INPUT을 es용, s3용으로 두 개로 분리함   
-> OOM이 발생하는 pod의 개수가 감소함 (INPUT의 index가 따로 존재하므로 서로의 upload로 인한 지연을 방지함)
5. s3 OUTPUT의 upload 방식을 multipart upload 방식으로 변경  
-> s3 putobject api 방식은 일반적인 방식, multipart 방식은 file을 여러개로 쪼갠 후, 각 조각들을 동시에 upload하는 방식
6. 마지막으로 aws-for-fluentbit 이미지를 fluentbit 최신 이미지로 교체하면서 OOM이 발생하는 pod가 사라진 것을 확인


<br/><br/><br/><br/>
참고  
- [https://docs.fluentbit.io/manual/administration/buffering-and-storage](https://docs.fluentbit.io/manual/administration/buffering-and-storage)
- [https://docs.fluentbit.io/manual/administration/backpressure](https://docs.fluentbit.io/manual/administration/backpressure)
- [https://github.com/fluent/fluent-bit/issues/4609](https://github.com/fluent/fluent-bit/issues/4609)
- [https://github.com/fluent/fluent-bit/issues/2671](https://github.com/fluent/fluent-bit/issues/2671)
- [https://github.com/aws/aws-for-fluent-bit/issues/278](https://github.com/aws/aws-for-fluent-bit/issues/278)
- [https://github.com/fluent/fluent-bit/issues/3204](https://github.com/fluent/fluent-bit/issues/3204)
- [https://github.com/aws/aws-for-fluent-bit/blob/mainline/troubleshooting/debugging.md#common-network-errors](https://github.com/aws/aws-for-fluent-bit/blob/mainline/troubleshooting/debugging.md#common-network-errors)