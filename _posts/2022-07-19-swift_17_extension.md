---
layout: post
title: (swift) 17. Extension (익스텐션)
description: "(swift) 익스텐션"
tags: [swift, 공부]
comments: true
---

> # [swift] 17. Extension (익스텐션)

<br>

## 익스텐션이 타입에 추가할 수 있는 기능
 - 연산 타입 프로퍼티 / 연산 인스턴스 프로퍼티
 - 타입 메서드 / 인스턴스 메서드
 - 이니셜라이저
 - 서브스크립트
 - 중첩 타입
 - 특정 프로토콜을 준수할 수 있도록 기능 추가

``` swift
extension SomeType {
    // 추가 기능
}
```

<br>
<br>
<br>

# extension 예제

<br>

## Int extension
``` swift
extension Int { // Int형 타입의 값이 짝수인지 홀수인지 판별할 수 있는 기능 추가.
    // Int 타입의 어떠한 인스턴스에도 사용이 가능하다.
    var isEven: Bool {
        return self % 2 == 0
    }

    var isOdd: Bool {
        return self % 2 == 1
    }
}

var number = 3
var isOdd = number.isOdd
var isEven = number.isEven

print("number(\(number)) - isOdd: \(isOdd), isEven: \(isEven))
```

출력 결과  
```
number(3) - isOdd: true, isEven: false
```

<br>
<br>

## String extension
``` swift
extension String { // String to Int extension
    func convertToInt() -> Int? {
        return Int(self)
    }
}

var string = "0"
print(string)
print(string.convertToInt())
```

출력 결과  
```
"0"
0
```