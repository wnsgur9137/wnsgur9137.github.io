---
layout: post
title: (swift) 20. try - catch 문
description: "(swift) try - catch 문"
tags: [swift, 공부]
comments: true
---

> # [swift] 20. try - catch 문

<br>

에러 처리란 프로그램 내에서 에러가 발생한 상황에 대해 대응하고 이를 복구하는 과정을 말한다.  
런타임 오류와 함께 프로그램이 종료되지 않는다.  

swift는 RunTime 에러를 처리하기 위한 다음과 같은 1급 클래스를 제공한다.
 - 발생(throwing)
 - 감지(catching)
 - 전파(propagating)
 - 조작(manipulating)

<br>

swift에서는 오류를 처리하는 네 가지 방법이 존재한다.
 1. 함수에서 발생한 오류를 해당 함수를 호출한 코드에 전파하는 방법
 2. do - catch 구문을 이용해서 오류를 처리 하는 방법
 3. optional 값으로 오류를 처리하는 방법
 4. 오류가 발생하지 않을 것이라고 확신하는 방법


<br>
<br>
<br>

# 예제

<br>

스위프트에서 에러는 에러 프로토콜을 따르는 타입의 값으로 표현된다.  
에러 프로토콜은 요구사항이 없는 빈 프로토콜이지만, 오류를 표현하기 위해서는 에러 프로토콜을 채택해야 한다.  

<br>

## 에러 프로토콜을 채택한 열거형
``` swift
enum PhoneError: Error { // 오류 처리를 위해 Error 프로토콜을 채택한 PhoneError 열거형
    case unknown
    case batteryLow(batteryLevel: Int) // 배터리 잔량을 알려주기 위한 Int값
}

throw PhoneError.batteryLow(batteryLevel: 20) // throw 구문을 이요해서 에러가 발생할 것 같은 지점에 에러를 던져준다.
```

출력 결과
```
Playground execution terminated: An error was thrown and was not caught:
   PhoneError
      batteryLow : 1 element
      - batteryLevel : 20
```

<br>
<br>

## 1. do - catch 문으로 오류를 처리하는 방법
``` swift
do {
    try 오류 발생 가능한 코드
} catch 오류 패턴 {
    처리 코드
}
```

예제
``` swift
enum PhoneError: Error {
    case unknown
    case batteryLow(batteryLevel: Int)
}

func checkPhoneBatteryStatus(batteryLevel: Int) throws -> String {
    guard batteryLevel != -1 else { throw PhoneError.unknown } // betteryLevel이 1이 아니면 else 구문 실행 (guard문은 false 일 때 실행)

    guard batteryLevel >= 20 else { throw PhoneError.batteryLow(batteryLevel: 20)}

    return "배터리 상태가 정상입니다."
}

do {
    try checkPhoneBatteryStatus(batteryLevel: -1)
} catch PhoneError.unknown {
    print("알 수 없는 에러입니다.")
} catch PhoneError.batteryLow(let batteryLevel) {
    print("배터리 전원 부족, 남은 배터리 : \(batteryLevel)%")
} catch { // 위 catch 문이 모두 해당하지 않는 경우
    print("그 외 오류 발생 : \(error)")
}

do {
    try checkPhoneBatteryStatus(batteryLevel: 20)
} catch PhoneError.unknown {
    print("알 수 없는 에러입니다.")
} catch PhoneError.batteryLow(let batteryLevel) {
    print("배터리 전원 부족, 남은 배터리 : \(batteryLevel)%")
} catch { // 위 catch 문이 모두 해당하지 않는 경우
    print("그 외 오류 발생 : \(error)")
}
```

출력 결과  
```
알 수 없는 에러입니다.
배터리 전원 부족, 남은 배터리 : 20%
```

<br>
<br>
<br>

## 2. try - ? 를 사용 (옵셔널 값으로 변환하여 오류를 처리)
(코드의 반환값은 nil이 된다.)
``` swift
enum PhoneError: Error {
    case unknown
    case batteryLow(batteryLevel: Int)
}

func checkPhoneBatteryStatus(batteryLevel: Int) throws -> String {
    guard batteryLevel != -1 else { throw PhoneError.unknown } // betteryLevel이 1이 아니면 else 구문 실행 (guard문은 false 일 때 실행)

    guard batteryLevel >= 20 else { throw PhoneError.batteryLow(batteryLevel: 20)}

    return "배터리 상태가 정상입니다."
}

let status1 = try? checkPhoneBatteryStatus(batteryLevel: -1)
print(status1)  // 오류일 경우 nil 반환

let status2 = try? checkPhoneBatteryStatus(batteryLevel: 30)
print(status2)  // 오류가 아닐 경우 Optional 값으로 반환
```

출력 결과  
```
nil
Optional("배터리 상태가 정상입니다.")
```

<br>
<br>
<br>

## 3. try - ! 를 사용 (오류가 발생하지 않을 것으로 확신)

``` swift
enum PhoneError: Error {
    case unknown
    case batteryLow(batteryLevel: Int)
}

func checkPhoneBatteryStatus(batteryLevel: Int) throws -> String {
    guard batteryLevel != -1 else { throw PhoneError.unknown } // betteryLevel이 1이 아니면 else 구문 실행 (guard문은 false 일 때 실행)

    guard batteryLevel >= 20 else { throw PhoneError.batteryLow(batteryLevel: 20)}

    return "배터리 상태가 정상입니다."
}

/*
오류일 경우 프로그램 강제 종료
즉, 조심해서 사용해야 함.
let status1 = try! checkPhoneBatteryStatus(batteryLevel: -1)
print(status1)  
*/
let status2 = try! checkPhoneBatteryStatus(batteryLevel: 30)
print(status2)
```

출력 결과  
```
배터리 상태가 정상입니다.
```