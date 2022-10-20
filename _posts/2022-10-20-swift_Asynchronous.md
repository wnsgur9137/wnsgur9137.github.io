---
layout: post
title: (swift) Asynchronous(비동기 처리)
description: "(swift) Asynchronous"
tags: [swift, 공부]
comments: true
---

> # [swift] Asynchronous(비동기 처리)

<br>

# Synchronous(동기식 처리)

* 동기식 처리
* 직렬로 일(UI 변경, 네트워크 통신)을 수행
* (순차적으로 진행)

<br>
<br>
<br>

# Asynchronous(비동기식 처리)

* 비동기식 처리
* 병렬로 일(UI 변경, 네트워크 통신)을 수행
* (동시에 진행)

<br>
<br>
<br>

# 비동기 처리가 가장 많이 행해지는 경우

Server와 네트워크 통신이 있을 경우이다.  
서버에 데이터를 요청하게 되면 서버로부터 결과를 받게 되는데, 이 결과를 기다리는 동안 시간이 낭비되고,  
유저에게 인디케이터를 보여주는 등의 다양한 동작이 추가로 더 필요하게 된다.  

즉, Synchronous는 성공/실패의 네트워크 통신 결과를 서버로부터 받으면, IOS App 내부에서 처리해 주어야 한다.  
하지만 Asynchronous는 타이밍 구분 없이 코드를 작성하면 **서버로부터 통신결과가 올 때까지, 코드는 기다려주지 않는다. 적절한 타이밍에 원하는 코드를 구동시키기 위해**서는 비동기 처리를 구현해야 한다.

<br>
<br>
<br>

# 비동기 처리의 구현 방법

1. Notification Center
2. Delegate Pattern
3. Closure
    - [지하철 도착정보 앱](https://github.com/wnsgur9137/Swift_UpperItermediate_Projects/tree/master/SubwayStation)
4. RxSwift
5. Combine IOS 14~