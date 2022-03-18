---
layout: post
title: (MAC) OracleDB, SQLDeveloper 설치
description: "OracleDB 설치, SQLDeveloper 설치"
tags: [MAC, 공부]
comments: true
---

<style>
    span.code {
        background-color : #dcffe4;
        font-weight : 600;
    }
</style>

>## **1. Oracle 11g 이미지 다운로드 및 컨테이너 생성**

<br>

<span class='code'>docker search oracle-xe-11g</span> 명령어를 이용하여 다운로드할 이미지를 검색한다.  

검색한 이미지 목록 중 jaspeen/oracle-xe-11g를 사용한다.  

<span class='code'>docker pull jaspeen/oracle-xe-11g</span> 명령어를 이용하여 이미지를 다운로드한다.  

<span class='code'>#docker images</span> 명령어를 이용하여 다운로드한 이미지 목록을 확인할 수 있다.

![oracle_01](/images/docker/oracle_setup_1.png)

<br>

다운로드 완료 후 컨테이너를 생성해준다.  

<span class='code'>docker run --name my_oracle -d -p 8080:8080 -p 1521:1521 jaspeen/oracle-xe-11g</span> 명령어를 입력하여 컨테이너 생성과 실행을 해 준다.  

<span class='code'>docker ps</span> 명령어를 이용해 실행 중인 컨테이너 목록을 확인할 수 있다.

![oracle_02](/images/docker/oracle_setup_2.png)

<br>

<br>
<br>

>## **2. Oracle DB SQLPlus 실행**

<br>

<span class='code'>docker exec -it my_oracle sqlplus</span> 명령어를 이용하여 Oracle DB SQLPlus를 실행한다.  

<span class='code'>user-name : system, password : oracle</span>

![oracle_03](/images/docker/oracle_setup_3.png)

<br>

<br>
<br>

>## **3. SQLDeveloper 설치 및 접속**

<br>

SQLDeveloper 설치파일 다운로드 및 설치  

[https://www.oracle.com/tools/downloads/sqldev-downloads.html](https://www.oracle.com/tools/downloads/sqldev-downloads.html)  

![sqldeveloper_01](/images/docker/sqldeveloper_1.png)
