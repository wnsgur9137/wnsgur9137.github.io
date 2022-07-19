---
layout: post
title: (swift) 08. Struct (구조체)
description: "(swift) 구조체"
tags: [swift, 공부]
comments: true
---

> # [swift] 08. Struct (구조체)

<br>

스위프트에는 클래스와 구조체가 있다.

구조체와 클래스는 데이터를 용도에 맞게 프로그래밍 할 때 편리하다.
즉, 사용자 정의 데이터 타입을 만들 수 있다.

구조체는 값 타입이며, 클래스는 참조 타입이라는 차이점을 가지고 있다.

구조체는 다음과 같이 작성할 수 있다.
``` swift
struct 구조체 이름 {
    프로퍼티와 메서드
}
```

<br>
<br>
<br>

## 예제

``` swift
struct User {
    var nickname: String
    var age: Int

    func information() {
        print("\(nickname) \(age)")
    }
}

var user = User(nickname: "이준혁", age: 22)

print("user.nickname: \(user.nickname)")
print("user.age: \(user.age)")

user.nickname = "김철수"
print("\nuser.nickname: \(user.nickname)")

user.information()
```

출력 결과  
```
user.nickname: 이준혁
user.age: 22

user.nickname: 김철수
김철수 22
```
