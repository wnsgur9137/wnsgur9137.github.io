---
layout: post
title: (Visual Studio Code) 비주얼 스튜디오 코드 디버깅 방법
description: "(Visual Studio Code) 비주얼 스튜디오 코드 디버깅 방법"
tags: [공부]
comments: true
---

> ## **1. Debugger for Chrome 설치**

<br>

좌측 인스텐션 아이콘을 클릭하고, 'debugger' 검색  
Debugger for Chrome 설치.  

![DebuggerForChrome](/images/vscodeDebug/debuggerForChrome.png)  

<br>
<br>

> ## **2. launch.json 파일 생성**

<br>

좌측 디버그 아이콘을 클릭하고 launch.json 파일 생성  

![launchJson](/images/vscodeDebug/launchJson.png)  

<br>

VSCode 선택  

![vscode](/images/vscodeDebug/vscode.png)  

<br>

자동으로 생성된 코드  

![code1](/images/vscodeDebug/code1.png)  

<br>

만약 자동으로 생성되지 않았다면 우측 하단 구성 추가 버튼 클릭 후 Chrome: Launch (legacy)  

![plus](/images/vscodeDebug/plus.png)  

<br>

![chormeLaunch](/images/vscodeDebug/chromeLaunch.png)  

<br>

launch.json 파일 코드 수정  

![codeUpdate](/images/vscodeDebug/codeUpdate.png)  

<br>
<br>

> ## **3. 디버깅**

<br>

브레이크 포인트 추가 (빨간 점이 위치한 곳을 더블클릭하여 추가 및 삭제)  

![breakpoint](/images/vscodeDebug/breakpoint.png)  

<br>

F5를 누르거나 실행 - 디버깅 시작 클릭하면 다음과 같이 표시된다.  

![debugging](/images/vscodeDebug/debugging.png)  

<br>

다음과 컨트롤러 아이콘들을 클릭하여 현재라인 실행, 종료 등을 수행할 수 있다.  

![control](/images/vscodeDebug/control.png)  

<br>
<br>

> ## **단축키**

<br>

* f5 : 디버그 시작/정지
* shift + f5 : 디버그 중지
* f9 : breakpoint 설정/해제
* f10 : 디버그 현재 라인 실행
* f11 : 디버그, 함수의 경우 함수 내부로 들어가서 실행