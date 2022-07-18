---
layout: post
title: (swift) 02. 기본 데이터 타입
description: "(swift) 기본 데이터 타입"
tags: [swift, 공부]
comments: true
---

> # [swift] 02. 기본 데이터 타입

- Int: 64bit 정수형
- UInt: 부호가 없는 64bit 정수형
- Float: 32bit 부동 소수점
- Double: 64bit 부동 소수점
- Bool: true, false 값
- Character: 문자
- String: 문자열
- Any: 모든 타입을 지칭하는 키워드

<br>

코드
``` swift
// Int
var someInt: Int = -100
someInt = 100

// UInt
var someUInt: UInt = 200
// someUInt = -200 // error

// Float
var someFloat: Float = 1.1
someFloat = 1

// Double
var someDouble: Double = 1.1
someDouble = 1

// Bool
var someBool: Bool = true
someBool = false

// Character
var someCharacter: Character = "가"
someCharacter = "A"
someCharacter = "😀"
// someCharacter = "abcdefg" // error

// String
var someString: String = "안녕하세요 😀"

// 타입 추론
var number = 10 // 데이터 타입을 명시하지 않아도 컴파일러가 자동적으로 number는 Int형 변수라는 것을 판단한다.
```