---
layout: post
title: (swift) 12. 클래스와 구조체의 차이
description: "(swift) 클래스와 구조체의 차이"
tags: [swift, 공부]
comments: true
---

> # [swift] 12. 클래스와 구조체의 차이

<br>

## 클래스와 구조체의 공통점
 - 값을 저장할 프로퍼티를 선언할 수 있다.
 - 함수적 기능을 하는 메서드를 선언 할 수 있다.
 - 내부 값에 . 을 사용하여 접근할 수 있다.
 - 생성자를 사용해 초기 상태를 설정할 수 있다.
 - extension을 사용하여 기능을 확장할 수 있다.
 - Protocol을 채택하여 기능을 설정할 수 있다.


<br>
<br>

## 클래스와 구조체의 차이점

<br>

### 클래스
 - 참조 타입
 - ARC로 메모리를 관리한다.
 - 상속이 가능하다.
 - 타입 캐스팅을 통해 런타임에서 클래스 인스턴스의 타입을 확인할 수 있다.
 - deinit을 사용하여 클래스 인스턴스의 메모리 할당을 해제할 수 있다.
 - 같은 클래스 인스턴스를 여러 개의 변수에 할당한 뒤 값을 변경시키면 모든 변수에 영향을 준다.(메모리가 복사 된다.)

### 구조체
 - 값 타입
 - 구조체 변수를 새로운 변수에 할당할 때마다 새로운 구조체가 할당된다.
 - 같은 구조체를 여러 개의 변수에 할당한 뒤 값을 변경시키더라도 다른 변수에 영향을 주지 않는다.(값 자체를 복사)

<br>
<br>
<br>

# 예제

<br>

## 클래스
``` swift
class SomeClass {
    var count: Int = 0
}

var class1 = SomeClass()
var class2 = class1
var class3 = class1

class3.count = 2
print("class1.count: \(class1.count)")
```

출력 결과  
```
class1.count: 2
```

<br>

## 구조체
``` swift
struct SomeStruct {
    var count: Int = 0
}

var struct1 = SomeStruct()
var struct2 = struct1
var struct3 = struct1

struct2. count = 3
struct3. count = 4

print("struct1.count: \(struct1.count)")
print("struct2.count: \(struct2.count)")
print("struct3.count: \(struct3.count)")
```

출력 결과  
```
struct1.count: 0
struct2.count: 3
struct3.count: 4
```