---
title:  "[프로젝트] Jsoup을 이용한 크롤링 (코로나(Covid19) 사이트)"
excerpt: 2020-04-24 18:26:24
last_modified_at:   2020-04-24 18:26:24 +0900
categories: Project
tags:
- 크롤링
- Jsoup
---
>## 시작  

토이 프로젝트 해야지 해야지 하면서 미루고 미루고 노답 :woman_facepalming:  
레인보우 지숙씨 인스타그램 보고 또 반성;.  
참 열심히 공부하고 즐기고 있구나! 하면서..  

나도 다시 초심으로!  
요즘엔 재택근무에 시간도 여유로우니 하나하나 다시 시작하는 마음으로! 아자아자! :ok_woman:  

코로나 때문에 전세계적으로 하나의 테마로 엄청난 데이터가 쏟아지고 있는 상황이니 데이터를 이용해 프로젝트를 시작!  
이미 다양한 사이트들이 시중에 많이 나와있으니 참고 모델로 삼으며 볼 수 있다는 장점, 공부하기에 딱 좋은 상황이라고 생각하면서 선택했다.  

크롤링은 학원 다닐 때 잠깐 맛만 봤었는데 기존 데이터를 가져와서 다양하게 재편집하는 것이 꽤 재미있게 느껴졌었다.  

Jsoup을 이용해서 만들어보자! :+1:  


>## 크롤링 라이브러리(Jsoup)  

- Java로 만들어진 HTML Parser.  
- DOM 구조를 추적하거나 CSS 선택자를 사용하여 데이터를 찾아 추출하는 것 가능.  
  

- Jsoup 라이브러리를 추가 : [https://jsoup.org/download](https://jsoup.org/download) 에서 .jar 파일 다운로드   

- Maven 추가   

```

  <dependency>
  <!-- jsoup HTML parser library @ https://jsoup.org/ -->
    <groupId>org.jsoup</groupId>
    <artifactId>jsoup</artifactId>
    <version>1.13.1</version>
  </dependency>
```
