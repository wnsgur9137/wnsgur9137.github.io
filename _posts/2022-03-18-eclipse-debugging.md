---
layout: post
title: (Eclipse) 이클립스 디버깅 방법
description: "OracleDB 설치, SQLDeveloper 설치"
tags: [eclipse, 공부]
comments: true
---

<style>
    .icon {

    }
</style>

> ## **디버깅**

<br>

디버깅(Debugging)이란 프로그램 개발 혹은 코드 작성 시 발견되는 각종 오류를 수정하는 과정이다. 또한, 작성된 프로그램의 정확도를 확인하기 위해 필요한 과정이기도 하다.  

**디버깅 중요한 이유**  
소프트웨어에서 종종 발생하는 버그는 프로그램 실행 목표를 서서히 저하시키거나 프로그램 자체를 중단 시킬 위험이 있다. 디버깅을 완료하면, 개발자의 의도에 따라 소프트웨어가 더 완벽하게 작동할 확률인 높아진다는 점에서 디버깅이 중요하다.  

또한 개발자는 디버깅 과정을 거치며 다음 개발 과정에서 더 훌륭한 프로그램을 제작할 방법을 알 수 있다. 프로그램 개발 과정에서 논리적, 문법적 실수를 깨닫는데 도움이 된다.  

다음은 Eclipse에서의 디버깅 방법이다.

<br>
<br>


> ## **1. 브레이크 포인트를 지정한다.**

<br>

에러가 발생하는 라인이나 의심이 가는 변수를 추적할 라인 위치에 브레이크 포인트를 지정한다.  

**브레이크 포인트 설정 방법**  
다음 빨간 박스 안에서 브레이크 포인트를 설정할 곳에 더블 클릭 혹은 마우스 우클릭한다.  

![breakPoint](/images/debugging/breakPoint.png)  

<br>

**브레이크 포인트 해제 방법**  
마우스로 다시 더블 클릭 혹은 마우스 우클릭한다.  

<br>
<br>

> ## **2. Debug**

<br>

run이 아닌 벌레 모양을 클릭한다.  
(디버깅)

![debugIcon](/images/debugging/debugIcon.png)  

<br>

| 아이콘 | 설명 | 단축키 |
|:---:|:----:|:----:|
| ![icon1](/images/debugging/icon1.png) | 멈추어 있던 스레드를 다시 진행, 다음 브레이크 포인트까지 이동 | F8 |
| ![icon2](/images/debugging/icon2.png) | 브레이크 포인트부터 시작해서 한 라인씩 진행하되, 함수 안이면 함수 안으로 들어감. | F5 |
| ![icon3](/images/debugging/icon3.png) | 브레이크 포인트부터 시작해서 한 라인씩 진행하되, 함수 호출은 건너뜀. | F6 |
| ![icon4](/images/debugging/icon4.png) | 현재 함수 끝까지 바로 가서 리턴 후 함수 호출부로 되돌아감. | F7 |

<br>
<br>

> ## **3. Variables 탭**

<br>

Variables 탭에서 다음과 같이 변수에 어떤 정보들이 있는지 확인이 가능.

![variablesTab](/images/debugging/variablesTab.png)  

<br>

마우스 커서를 올려서 확인도 가능하다.

<br>

> ## **5. Expression 탭**

<br>

Expression 탭에서는 찾고자 하는 변수를 입력하면 그 변수에 대한 값을 확인할 수 있다.  
![Expression](/images/debugging/expressionTab.png)  

<br>
<br>

> ## **6. Breakpoints 탭**

<br>

Breakpoints 탭에서는 현재 설정되어 있는 브레이크 포인트를 확인할 수 있다.  
더블클릭하여 해당 브레이크 포인트로 이동할 수도 있고, 체크박스를 해제하여 비활성화 할 수도 있다.  
![BreakpointsTab](/images/debugging/breakpointsTab.png)  

<br>
<br>

> ## **Debugging 탭들이 안보이는 경우**

<br>

상단 [windows - show view] 에서 보이게 할 탭들을 선택한다.  
![showview](/images/debugging/showview.png)  
