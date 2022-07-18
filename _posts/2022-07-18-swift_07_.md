---
layout: post
title: (swift) 07. 옵셔널과 옵셔널 바인딩
description: "(swift) 옵셔널, 옵셔널 바인딩"
tags: [swift, 공부]
comments: true
---

> # [swift] 07. 옵셔널

옵셔널이란 값이 있을 수도 있고 없을 수도 있다 라는 의미이다.  

<br>
<br>

다음과 같이 옵셔널 변수를 생성할 수 있다.
``` swift
var name: String?
```

옵셔널 변수는 nil(다른 언어에서는 Null)과 같다.
``` swift
var name: String? = nil
```

<br>
<br>
<br>

옵셔널 예제 코드  
``` swift
var name: String?

var optionalName: String? = "Gunter" // 값을 선언할 수도 있다.
print("optionalName: \(optionalName)")

// var requiredName: String = optionalName -> error
// 에러가 나는 이유는 옵셔널로 선언된 변수는 코드가 실행되기 전까지 값이 있는지 없는지 알 수가 없기 때문에 대입할 수 없다.
```

출력 결과  
```
optionalName: Optional("Gunter")
```

<br>
<br>
<hr>
<br>
<br>

> # 옵셔널 바인딩  

## 옵셔널 해제 방법

<br>

 - ### 명시적 해제
   - 강제 해제
   - 비강제 해제(옵셔널 바인딩)

<br>

 - ### 묵시적 해제
   - 컴파일러에 의한 자동 해제
   - 옵셔널의 묵시적 해제

<br>
<br>
<br>

# 명시적 해제


## 옵셔널 강제 해제

옵셔널 선언된 변수 뒤에 !를 붙이면 강제로 해제하게 된다.  
하지만 강제로 해제하는 것은 에러가 발생해 프로그램이 강제 종료될 수 있는 위험이 따른다.  

<br>

코드  
``` swift
var number: Int? = 3
print(number)
print(number!)
```

출력 결과
```
Optional(3)
3
```

<br>

좀 더 안전하게 해제하려면 비강제 해제(옵셔널 바인딩)을 사용하면 된다.  

<br>
<br>
<br>

## 비강제 해제(옵셔널 바인딩)

if를 사용하여 옵셔널 바인딩(추출 방법이다.)

<br>

### if문을 사용한 옵셔널 바인딩
``` swift
var number: Int? = 3
if let result = number { // result는 if문 내에서만 사용 가능하다.
    print(result)
}
```

출력 결과  
```
3
```

<br>
<br>

## guard를 사용한 옵셔널 바인딩

if만을 사용한 옵셔널 바인딩은 if문 내에서만 바인딩한 변수를 사용할 수 있기 때문에 guard를 사용한다.  

``` swift
func test() {
    let number: Int? = 5
    guard let result = number else { return }
    print(result)
}
test()
```

출력 결과  
```
5
```

<br>
<br>
<br>

# 묵시적 해제

## 비교 연산자를 사용한 옵셔널 바인딩

비교 연산자를 사용하면 컴파일러가 자동으로 바인딩해 준다.

``` swift
leet value: Int? = 6
if value == 6 {
    print("value가 6입니다.")
} else {
    print("value 6이 아닙니다.")
}
```

출력 결과
```
value가 6입니다.
```

<br>
<br>

## 묵시적 해제

``` swift
let string = "12"
var stringToInt1: Int? = Int(string) // 문자열이 숫자 외의 문자가 들어가게 되면 nil을 반환하게 된다. 그렇기 때문에 옵셔널 타입으로 선언하기 위해 아래와 같이 !를 써야한다.
var stringToInt2: Int! = Int(string)
print(stringToInt)
```

출력 결과  
```
13
```