---
layout: post
title: (swift) 04. Function (함수)
description: "(swift) 함수"
tags: [swift, 공부]
comments: true
---

> # [swift] 04. Function (함수)

<br>

함수는 **작업의 가장 작은 단위이자 코드의 집합**이다.  
함수를 사용하는 가장 큰 이유는 반복적인 프로그래밍을 피할 수 있기 때문이다.  

함수의 크기에 대해 명시된 규칙은 없으나, 대략 하나의 기능을 하나의 함수로 만드는 것이 가장 바람직하다.

<br>
<hr>
<br>

## 함수 생성 방법  
``` swift
func 함수명(파라미터 이름: 데이터 타입) -> 반환 타입 {

}
```

<br>
<br>

## 매개변수가 존재하는 함수  
``` swift
func sum(a: Int, b: Int) -> Int {
    return a + b
}
sum(a: 5, b: 3)
```

## 출력 결과
```
8
```

<br>
<br>

## 매개변수가 없는 함수
``` swift
func hello() -> String {
    return "hello"
}
hello()
```

## 출력 결과  
```
hello
```

<br>
<br>

## 반환 값이 없는 함수 
``` swift
func printName1() {

}

func printName2() -> Void {

}

func greeting(friend: String, me: String = "gunter") { // me에 기본 매개변수 값 "gunter"를 지정한다.
    print("Hello, \(friend)! I'm \(me)")
}
greeting(friend: "Albert")
```

## 출력 결과  
```
Hello, Albert! I'm gunter
```

<br>
<br>
<br>

# 전달인자

전달인자 레이블을 사용할 경우 사용자 입장에서 매개변수의 역할을 좀 더 명확하게 표현할 수 있다.  
즉 코드의 가독성이 좋아진다.  
전달인자를 사용하지 않을 경우 _ 를 사용하면 된다.

## 전달인자 레이블

``` swift
func sendMessage(from myName: String, to name: String) -> String {
    return "Hello \(name)! I'm \(myName)"
}

func sendMessage(_ name: String) -> String {
    return "Hello \(name)"
}

sendMessage(from: "Gunter", to: "Json")
sendMessage("권태완")
```

## 출력 결과  
``` 
Hello, Json! I'm Gunter
Hello 권태완
```

<br>
<br>
<br>

# 가변 매개변수

가변매개변수로 들어온 인자는 **배열**처럼 사용할 수 있다.

가변 매개변수 코드  
``` swift
func sendMessage(me: String, friends: String...) -> String { // 가변 매개변수는 맨 뒤, 하나를 지정할 수 있다.
    return "Hello \(friends)! I'm \(me)"
}

sendMessage(me: "Gunter", friends: "Json", "Albert", "Stella")
```

출력 결과
```
Hello, ["Josn", "Albert", "Stella"]! I'm Gunter
```
