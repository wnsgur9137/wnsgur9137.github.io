---
layout: post
title: MAC OS 메뉴바 색상 변경하기
description: "MAC OS Change Menu Bar Color"
tags: [MAC, 공부]
comments: true
---

## 맥OS 메뉴바 색상 변경하기
<br>

맥 OS Bigsur, monterey에서 매뉴바 색상은 바탕화면 색상에 의해 변경된다.  
<br><br>

![menuBar](/images/MenuBarColor/menuBar.png)  

바탕화면은 파란색인데, 다크모드를 활성화해놨기 때문에 색상이 다르다.  
<br>

결국 메뉴바의 색상을 변경하기 위해서는 메뉴바 위치의 바탕화면을 색상을 변경해야하는데 이는 [ChangeMenuBarColor](https://github.com/igorkulman/ChangeMenuBarColor)을 통해 변경할 수 있다.  
<br><br>

![ChangeMenuBarColor](/images/MenuBarColor/CMBC.png)  

터미널에서 ChangeMenuBarColor 실행파일 경로로 들어간다.  

./ChangeMenuBarColor <방법> <색상>  
으로 실행한다.  

<방법>에는 두 가지 방법이 존재한다.  
* SolidColor
* Gradient

<br>  

```
./Change MenuBarColor SolidColor "#000000"  

./ChangeMenuBarColor Gradient "#FF0000" "#0000FF"
```  

<br>

색상표는 [ColorBank](https://colorbank.net)에서 확인할 수 있다.
