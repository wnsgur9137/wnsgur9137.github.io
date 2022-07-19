---
layout: post
title: (swift) 16. Protocol (프로토콜)
description: "(swift) 프로토콜"
tags: [swift, 공부]
comments: true
---

> # [swift] 16. Protocol (프로토콜)

<br>

프로토콜이란 특정 역할을 하기 위한 메서드, 프로퍼티, 기타 요구사항 등의 청사진을 의미한다.  

``` swift
protocol 이름 {

}
```

<br>
<br>
<br>

## protocol 사용 방법

``` swift
protocol SomeProtocol {

}

protocol SomeProtocol2 {

}

struct SomeStructure: SomeProtocol, SomeProtocol2 { // 프로토콜 채택

}

struct SomeStructure2: SuperClass, SomeProtocol, SomeProtocol2 { // 상속받을 클래스가 있다면 클래스를 맨 앞에 적는다.

}

protocol FirestProtocl {
    var name: Int { get set } // 읽기, 쓰기가 가능한 property
    var age: Int { get }    // 읽기만 가능한 property
}

protocol AnotherProtocol {
    static var someTypeProperty: Int { get set }    // 프로토콜에서 타입 프로퍼티를 요구하려면 맨 앞에 static을 작성.
}

protocol SomeProtocol3 {
    func someTypeMethod()   // 메소드 요구사항 정의
    // 메서드에 필요한 매개변수를 정의해 주어야 한다.(default 값은 지정할 수 없다.)
}

protocol SomeProtocol4 {
    init(someParameter: Int)
}

protocol SomeProtocol5 {
    init()
}

class SomeClass: SomeProtocol5 {
    required init() {   // 클래스에서는 생성자 요구사항을 만족시키기 위해서는 required가 필요하다. (만약 클래스 자체가 상속받을 수 없는 final 클래스라면 required를 붙일 필요가 없다.)

    }
}
```

<br>
<br>
<br>

# 예제

``` swift
protocol FullyNames {
    var fullName: String { get set }
    func printFullName()
}

struct Person: FullyNames {
    var fullName: String 
    fullName = "이준혁"
    func printFullName() {
        print(fullName)
    }

    // 위 변수와 메서드를 정의하지 않으면 프로퍼티의 요구사항을 충족시키지 않아 에러가 발생한다.
}
```

출력 결과  
```
이준혁
```