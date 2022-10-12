---
layout: post
title: (swift) Generic(제네릭)
description: "(swift) Generic"
tags: [swift, 공부]
comments: true
---

> # [swift] Generic(제네릭)

<br>

# Generic

* '포괄적인'이라는 뜻을 가지고 있다.
* 타입에 유연하게 대처할 수 있다.
* 제네릭으로 구현한 기능과 타입은 **재사용**에 용이하다.
* 코드의 중복을 줄일 수 있어 **가독성**이 좋다.


<br>
<br>
<br>

# Generic을 사용하지 않았을 때

``` swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let tempA = a
    a = b
    b = tempA
}
```

<br>

위 경우에서는 **파라미터 모두 Int형일 경우 문제가 없지만 타입이 다른 경우 사용할 수 없다**  

그렇기에 다른 타입(예시로 Double, String)일 경우에도 사용하려면 다음과 같이 코드를 작성해야 한다.  

<br>

``` swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let tempA = a
    a = b
    b = tempA
}

func swapTwoInts(_ a: inout Double, _ b: inout Double) {
    let tempA = a
    a = b
    b = tempA
}

func swapTwoInts(_ a: inout String, _ b: inout String) {
    let tempA = a
    a = b
    b = tempA
}
```

<br>

이렇게 코드가 굉장히 길어질 수 있기 때문에 **Generic**을 사용하는 것이다.

<br>
<br>
<br>

# Generic Function

``` swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let tempA = a
    a = b
    b = tempA
}
```

<br>

이런식으로 코드를 작성할 경우 '<', '>'를 사용하여 안에 **타입처럼 사용할 이름**(T)을 선언해 주면 그 뒤로 해당 이름을 타입처럼 사용할 수 있다.  

여기서 이 T를 **Type Parameter**라 하는데, T라는 새로운 형식이 생성되는 것이 아닌, **실제 함수가 호출될 때 해당 매개변수의 타입으로 대체**되는 Placeholder이다.

<br>
<br>
<br>

# Generic Type

제네릭은 함수에서만 사용 가능한 것이 아니라 **구조체, 클래스, 열거형** 타입에서도 선언할 수 있다.

<br>

``` swift
struct Stack<T> {
    let items: [T] = []

    mutating func push(_ item: T) { ... }
    mutating func pop() -> T { ... }
}
```

<br>

이렇게 제네릭 타입으로 Stack을 선언할 수 있다.

<br>
<br>
<br>

# Type Constraints

제네릭 함수와 타입을 사용할 때 특정 클래스의 하위 클래스나, 특정 프로토콜을 준수하는 타입만 받을 수 있게 **제약**을 둘 수 있다.

<br>
<br>

## Protocol Constraints

``` swift
func isSameValues<T>(_ a: T, _ b: T) -> Bool {
    return a == b
}
```

<br>

이렇게 선언하면 에러가 난다.
== 이란 a와 b의 타입이 Equatable이란 프로토콜을 준수할 때만 사용할 수 있기 때문이다.  
따라서 이 때는 **T: Equatable** 이라는 제약을 줄 수 있다.

<br>

``` swift
func isSameValues<T: Equatable>(_ a: T, _ b: T) -> Bool {
    return a == b
}
```

<br>
<br>

## Class Constraints

프로토콜 제약과 똑같지만, 해당 자리에 프로토콜이 아닌 클래스 이름이 오는 것이다.

<br>

``` swift
class Bird { }
class Human { }
class Teacher: Human { }

func printName<T: Human>(_ a: T) { }
```

<br>

이렇게 **T: Human** 클래스 이름을 작성하면

<br>

``` swift
let bird = Bird.init()
let human = Human.init()
let teacher = Teacher.init()

printName(bird) // Global function 'printName' requires that 'Bird' inherit from 'Human'
printName(human)
printName(teacher)
```

<br>

Human 클래스 인스터인스인 Human, Human 클래스를 상속 받은(Subclass) teacher은 printName이란 제네릭 함수를 싱핼시킬 수 있지만, **Human 클래스의 Subclass가 아닌 bird 인스턴스는 실행할 수 없다**.