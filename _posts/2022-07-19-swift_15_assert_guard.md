---
layout: post
title: (swift) 15. assert, guard
description: "(swift) assert, guard"
tags: [swift, 공부]
comments: true
---

> # [swift] 15. assert와 guard

<br>

## assert
 - 특정 조건을 체크하고, 조건이 성립되지 않으면 메세지를 출력 하게 할 수 있는 함수
 - assert 함수는 디버깅 모드에서만 동작하고 주로 디버깅 중 조건의 검증을 위하여 사용한다.

## guard 문
 - 뭔가를 검사하여 그 다음에 오는 코드를 실행할지 말지 결정 하는 것이다.
 - guard 문에 주어진 **조건문이 거짓일 때 구문이 실행**된다.

<br>
<br>
<br>

# 예제

## assert
``` swift
var value = 0
assert(value == 0)

value = 2
assert(value == 0, "값이 0이 아닙니다.")
```
이와 같이 실행하게 되면 다음과 같이 RunTime ERROR가 발생한다.  
```
Assertion failed: 값이 0이 아닙니다.
```

<br>
<br>
<br>

## guard
``` swift
guard 조건 else {
    // 조건이 false 이면 else 구문이 실행되고, return, throw, break를 통해 이 후 코드를 실행하지 않도록 한다.
}
```

<br>

## guard 예제 1
``` swift
func guardTest(value: Int) {
    guard value == 0 else { return }
    print("안녕하세요")
}

guardTest(value: 2) // value가 0이 아니기 때문에 guard문에 막혀 return되어 아무 것도 출력이 되지 않는다.
guardTest(value: 0) // value가 0이기에 "안녕하세요"가 출력된다.
```

출력 결과  
```
안녕하세요
```

<br>

## guard 예제 2
``` swift
func guardTest(value: Int?) { // 매개변수를 옵셔널 타입으로 선언
    guard let value = value else { return } // 값이 nil이라면 return
    print("value: \(value)")
}

guardTest(value: 2)
guardTest(value: nil)
```

출력 결과  
```
2
```