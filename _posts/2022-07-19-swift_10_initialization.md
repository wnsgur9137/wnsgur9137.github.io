---
layout: post
title: (swift) 10. Initialize (초기화)
description: "(swift) 초기화"
tags: [swift, 공부]
comments: true
---

> # [swift] 10. Initialize (초기화)

<br>

초기화란 클래스 구조체 또는 열거형의 인스턴스를 사용하기 위한 준비 과정을 말한다.  

<br>

사용 방법이다.
``` swift
init(매개변수: 타입, ...) {
    // 프로퍼티 초기화
    // 인스턴스 생성시 필요한 설정들 해주는 코드 작성
}
```

<br>

[(swift) 09. 클래스](https://wnsgur9137.github.io/swift_09_class/)에서 코드이다.  
``` swift
struct User {
    var nickname: String = "이준혁"
    var age: Int = 0

    init() {
        // 인스턴스가 생성되면 호출
        // 프로퍼티의 초기 값, 필요한 설정 등을 여기서 진행한다.
    }
}

let user = User()
```

<br>
<br>
<br>

## 예제

``` swift
class User {
    var nickname: String
    var age: Int

    // 기본 생성자
    init(nickname: String, age: Int) {
        self.nickname = nickname
        self.age = age
    }

    // 사용자 정의 생성자
    init(age: Int) {
        self.nickname = "김철수"
        self.age = age
    }

    // 인스턴스가 메모리에 해제되기 직전에 호출된다.
    // 종료 전 정리작업을 사용할 경우 사용
    // 클래스에서만 사용 가능
    deinit {
        print("deinit user")
    }
}

var user = User(nickname: "이준혁", age: 22)
print("user.nickname: \(user.nickname)")
print("user.age: \(user.age) \n")

var user2 = User(age: 22)
print("user.nickname: \(user.nickname)")
print("user.age: \(user.age) \n")

var user3 = User(age: 23)
user3 = nil // swift는 인스턴스가 더 이상 필요없다고 판단하면 자동으로 메모리에서 소멸시킨다.
```

실행 결과  
```
user.nickname: 이준혁
user.age: 22

user.nickname: 김철수
user.age: 22

deinit user
```