---
layout: post
title: (Eclipse) 이클립스 설치 및 JDK 설치
description: "(Eclipse) 이클립스 설치 및 JDK 설치"
tags: [eclipse, 공부]
comments: true
---

<style>
    span.code{
        background-color : #dcffe4;
        font-weight : 600;
    }
</style>

> ## **1. JDK 설치**

<br>

**JDK**란 Java Development Kit으로 JRE(Java Runtime Environment)와 JAVA 바이트코드 컴파일러, JAVA 디버거 등을 포함하는 개발 도구로 이루어져 있다.  

[https://www.oracle.com/java/technologies/downloads/](https://www.oracle.com/java/technologies/downloads/)에 서 설치를 진행한다.  

![jdk](/images/eclipseSetup/jdk.png)  

<br>

운영체제, 버전을 확인하고 설치한다.  

<br>
<br>

> ## **2. 환경변수 설정**

<br>

<span class="code">제어판 > 시스템 및 보안 > 시스템 > 고급시스템 설정 > 환경변수</span>로 들어간다.

![jdksetup1](/images/eclipseSetup/jdksetup1.png)  

<br>

새로 만들기를 클릭한다.

![jdksetup2](/images/eclipseSetup/jdksetup2.png)  

<br>

* 변수 이름 : JAVA_HOME
* 변수 값 : C:\Program Files\Java\jdk1.8.0_### (디렉터리 찾아보기로 경로 지정하는게 편하다.)

![jdksetup3](/images/eclipseSetup/jdksetup3.png)  

<br>

시스템 변수에서 Path를 선택하고 편집을 누른다.

![jdksetup4](/images/eclipseSetup/jdksetup4.png)  

<br>

새로 만들기 버튼을 클릭해 <span class="code">%JAVA_HOME%\bin</span>을 입력한다.  

%JAVA_HOME%\bin을 '위로 이동' 버튼을 눌러 맨 위로 이동시킨다.

![jdksetup5](/images/eclipseSetup/jdksetup5.png)  

<br>

**새 시스템 변수 추가** 하여
 * 변수 이름 : CLASSPATH 
 * 변수 값 : %JAVA_HOME%\lib

을 입력한다.

<br>


cmd에서 <span class="code">java -version</span> 를 입력하여 자바 버전을 확인한다.  

![cmd](/images/eclipseSetup/cmd.png)  

<br>
<br>

> ## **3. Eclipse 설치**

<br>

**Eclipse**란 JAVA를 기반으로 한 통합 개발 환경(IDE)로 이클립스 재단에서 만들었다.

[https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)에서 설치를 진행한다.  

![eclipse](/images/eclipseSetup/eclipse.png)  

<br>
