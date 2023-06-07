---
title: Carousel with React
author: icyou
date: 2023-06-07 00:00:00 +0900
categories: [Frontend]
tags: [Carousel, React]
pin: true
math: true
---

### Carousel with React
React(Preact)로 Carousel component를 만들어봅니다.  

carousel을 표현하기 위한 trick은 여러 화면을 순서대로 횡으로 나열해놓고 하나의 화면씩만 노출될 수 있도록 나머지 화면은 `overflow:hidden`을 사용하여 숨깁니다. 또한 화면을 중앙배치하도록 `position:relative`와 `left:50%`, `transform:translate(-50%)`를 활용합니다. 높이와 너비를 비율로 맞추기 위해 width는 %로 설정하고 height는 0으로 설정한 후에 padding-bottom을 %로 맞춰 비율을 조절합니다. 이를 바탕으로 한 껍데기의 css는 다음과 같습니다.  
```
container: {
  position: 'relative',
  left: '50%',
  transform: 'translate(-50%)',
  overflow: 'hidden',
  
  display: 'flex',
  justifyContent: 'center',
      
  width: '70%',
  height: 0,
  paddingBottom : "45%",
},
```  

relative element의 자식들은 absolute 속성을 통해 위치를 조정할 수 있습니다. 이후 carousel 화면이 하나씩 넘어갈 수 있도록 translateX 속성으로 적절한 계산식을 만들어줍니다.  
```
carousel: {
  position: 'absolute',
  top: '0%',
  display: 'flex',
  flexDirection: 'row',
  height: '100%',
  
  transform: `translateX(${ 100 * (carousels.length - 2 * currentIndex - 1) / (2 * carousels.length) }%)`,
  transition: '0.5s ease-out',
  webkitTransition:"0.5s ease-out",
},
```  

일정 시간마다 화면이 넘어가도록 하기 위해 useEffect를 index를 증가시키고 전체 carousel의 길이보다 길어지면 index를 0으로 초기화합니다. index를 증가시키는 함수는 index가 바뀔 때마다 한 번씩 실행되어야 하므로 return을 통해 clear해주고 index가 바뀔 때마다 새로 실행할 수 있도록 useEffect []에 index를 추가합니다.  
```
useEffect(() => {
  const timer = setInterval(() => {
    if (currentIndex < carousels.length - 1) {
      setCurrentIndex(currentIndex + 1)
    } else {
      setCurrentIndex(0)
    }
  }, interval)
  return () => clearInterval(timer)
}, [currentIndex])
```


props에서 carousel data를 가져왔으면 map을 통해 data를 하나씩 가져와 맞는 화면을 개발해줍니다.  
```
{carousels.map((item, index) =>
  <div key={index} style={{ ...styles.item, ...carouselStyle, backgroundColor: item }}>
    {item}
  </div>
)}
```