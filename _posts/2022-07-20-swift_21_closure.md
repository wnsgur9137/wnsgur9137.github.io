---
layout: post
title: (swift) 21. Closure (클로저)
description: "(swift) 클로저"
tags: [swift, 공부]
comments: true
---

> # [swift] 21. Closure (클로저)

<br>

### 클로저
 - 코드에서 전달 및 사용할 수 있는 독립 기능 블록이며, 일급 객체의 역할을 할 수 있다.  

### 일급 객체
 - 전달 인자로 보낼 수 있고, 변수/상수 등으로 저장하거나 전달할 수 있으며, 함수의 반환 값이 될 수도 있다.

### Named Closure
 - 이름이 있는 함수
### Unnamed Closure
 - 이름이 없는 함수(보통 클로저를 지칭할 때 이를 말함)

<br>
<br>

## 클로저 표현 식
``` swift
{ (매개 변수) -> 리턴 타입 in)
    실행 구문
}
```

<br>
<br>
<br>

## 예제

``` swift
let hello = { () -> () in
    print("hello")
}

hello()
```

출력 결과
```
hello
```

<br>

## 파라미터와 리턴 타입이 있는 클로저
``` swift
let hello2 = { (name: String) -> String in 
    return "Hello, \(name)" // 함수에서 배운대로 파라미터의 네임은 단독으로 쓰였으니, 전달인자 레이블이자 파라미터 네임으로 생각할 수도 있지만, 클로저에서는 전달인자 레이블을 사용용하지 않기 때문에, 파라미터 네임으로만 사용한다.
}

// hello2(name: "Junhyeok") // 즉, 전달인자를 적고 파라미터 값을 넘겨주면 에러가 나게 된다.
hello2("Junhyeok")
```

출력 결과  
``` 
Junhyeok
```

<br>

## 클로저는 함수의 파라미터 타입으로 클로저를 전달할 수 있다.  
### 클로저가 1급 객체이기 때문에 가능하다.  
``` swift
func doSomething(closure: () -> ()) { // 파라미터 이름은 closure
    closure
}

doSomething(closure: { () -> () in
    print("hello")
})
```

출력 결과
```
hello
```

<br>

## 함수의 반환 타입으로 클로저를 사용할 수 있다.
``` swift
func doSomething2() -> () -> () {
    return { () -> () in
        print("hello4")
    }
}

doSomething2()()
```

출력 결과  
```
hello4
```

<br>

클로저가 길어지거나, 가독성이 떨어진다면 후엔클로저 기능을 사용한다.
(맨 마지막 매개변수에만 사용할 수 있다.)
## 후엔클로저
``` swift
func doSomething(closure: () -> ()) {
    closure()
}

doSomething() {
    print("hello2")
}

doSomething {
    print("hello3")
}
```

출력 결과
```
hello2
hello3
```

<br>

## 다중 후엔 클로저 문법을 이용해 여러 개의 클로저를 사용한다.
``` swift
func doSomething2(success: () -> (), fail: () -> ()) {

}

doSomething2 {
    print("success")
} fail: {
    print("fail")
}
```

<br>

## 클로저 간소화
파라미터 형식과 리턴 형식의 타입을 생략할 수 있다.
약식인수 이름를 사용하여 매개변수 이름 또한 생략이 가능하다.  
약식인수 이름 : 매개변수를 대신하여 사용

단일 구문(return이 하나라면) 타입 유추를 통해 return 타입도 생략 가능하며, 
``` swift
// 모두 같은 의미를 가진 클로저

func doSomething3(closure: (Int, Int, Int) -> Int) {
    closure(1, 2, 3)
}

doSomething3(closure: { (a, b, c) in // 파라미터 값의 타입을 생략
    return a+b+c
})

doSomething3(closure; { // 약식인수 이름을 사용하여 매개변수 이름 생략 가능
    return $0 + $1 + $2
})

doSomething3(closure: {
    $0 + $1 + $2 // 단일 구문이므로 return 생략 가능
})

doSomething3() { // 후엔클로저 방식으로 작성
    $0 + $1 + $2
}

doSomething3 {  // 단 하나의 클로저만 매개변수로 전달하는 경우에는 소괄호까지 생략 가능
    $0 + $1 + $2
}
```