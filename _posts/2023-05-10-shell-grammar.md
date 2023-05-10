---
title: Shell Grammar
author: icyou
date: 2023-05-10 00:00:00 +0900
categories: [Computer Science, Programming Language]
tags: [Programming Language, Leetcode]
pin: false
math: true
---

## Shell Grammar

### Shell Script
Linux shell이나 command line interpreter에서 구동되도록 작성된 언어입니다.

### 변수
* 변수 사용  

```
#!/bin/bash

name="icyou" # 변수 선언 및 대입
pass=123123  # 따옴표로 감싸든 말든 문자열로 저장됩니다

echo $name # 
echo "my name is ${name}" # 문자열과 함께 사용할 경우 "" 안에 ${}를 사용합니다.
echo 'my name is ${name}' # '' 안이므로 my name is ${name} 그대로 출력합니다.
printf "%s" $pass
```

* 지역 변수  
local을 변수명 앞에 붙여줘야만 합니다.

* 매개 변수

```
echo "script name: ${0}"
echo "매개변수 갯수: ${#}"
echo "전체 매개변수 값: ${*}"
echo "전체 매개변수 값2: ${@}"
echo "매개변수 1: ${1}"
echo "매개변수 2: ${2}"
```

* 변수 연산
Bash 변수는 문자열이기 때문에 특수한 문법을 통해 연산을 해야합니다.
1. expr
2. let
3. $(())

```
#!/bin/bash

number1=10
number2=20

mul=`expr $number1 \* $number2` # 곱셈에는 \* 를 이용합니다.
echo "mul:      ${mul}"

let re=num1*num2 #Mul
echo "mul:$re"

echo mul:$((num1*num2))
```

### 주석
1. \#
2. << "END" ~ >>

### if

```
if [ 값1 비교식 값2 ]  # 반드시 if 와 [] 사이, [] 안에 공백이 존재해야 합니다.
~
fi
```
```
if (( ${num1} < ${num2} )); then # (( ))를 사용하면 비교식을 기호로 표현 가능합니다.
    echo "yes"
fi
```

* file 검사

```
if [ -d ${변수} ]; then     # ${변수}의 디렉토리가 존재하면 참
if [ ! -d ${변수} ]; then	  # ${변수}의 디렉토리가 존재하지 않으면 참

if [ -e ${변수} ]; then     # ${변수}라는 file이 존재하면 참

if [ -r ${변수} ]; then     # file을 읽을 수 있으면 참
if [ -w ${변수} ]; then     # file을 쓸 수 있으면 참
if [ -x ${변수} ]; then     # file을 실행할 수 있으면 참

if [ -s ${변수} ]; then     # file의 크기가 0보다 크면 참

if [ ${변수1} -nt ${변수2}]; then # 변수1이 변수2보다 최신이면 참
if [ ${변수1} -ot ${변수2}]; then # 변수1이 변수2보다 최신이 아니면 참
if [ ${변수1} -ef ${변수2}]; then # 변수1과 변수2이 동일하면 참
```
```
then
if [ ${string1} == ${string2} ] || [ ${string3} == ${string4} ];
then 

elif [[ ${string1} == ${string2} || ${string3} == ${string4} ]] && [ ${string5} == ${string6} ];
then
# [[ ]]를 활용하면 &&, ||, =~와 * 같은 정규식과 다중 조건까지 사용할 수 있습니다.
```

### for

```
for ((i=1; i<=4; i++)); do # 비교식을 쓰므로 (( ))를 활용합니다.
    echo $i
done
```

<br/><br/><br/><br/>
참고 
- [https://inpa.tistory.com/entry/LINUX-%EC%89%98-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%95%B5%EC%8B%AC-%EB%AC%B8%EB%B2%95-%EC%B4%9D%EC%A0%95%EB%A6%AC](https://inpa.tistory.com/entry/LINUX-%EC%89%98-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%95%B5%EC%8B%AC-%EB%AC%B8%EB%B2%95-%EC%B4%9D%EC%A0%95%EB%A6%AC)
- [https://80000coding.oopy.io/7c84ede6-2741-4491-8fa4-d6f216944c13](https://80000coding.oopy.io/7c84ede6-2741-4491-8fa4-d6f216944c13)