---
layout: post
title: (swift) 05. 조건문
description: "(swift) 조건문"
tags: [swift, 공부]
comments: true
---

> # [swift] 05. 조건문

<br>

주어진 조건에 따라서 에플리케이션을 다르게 동작하도록 하는 것.

**if**, **switch**, **guard** 문이 존재한다.

<br>
<br>
<br>

# if 문

``` swift
let animal = "cat"
if animal == "dog" {   // 조건식이 만족하면 해당 구문 실행
    print("강아지 사료 주기")
} else if animal == "cat" { // 조건식 2를 만족하면 해당 구문 실행
    print("고양이 사료 주기")
} else {    // 아무 조건식도 만족하지 않으면 해당 구문 실행
    print("해당하는 동물 사료가 없움")
}
```

출력 결과
```
고양이 사료 주기
```

<br>
<br>
<br>

# switch 문

### 기본 switch 문

``` swift
let color = "white"

switch color {
    case "red":
        print("파란색 입니다.")
    case "green":
        print("초록색 입니다.")
    case "blue":
        print("파란색 입니다.")
    case "yellow":
        print("노란색 입니다.")
    default:
        print("찾는 색상이 없습니다.")
}
```

출력 결과  
```
찾는 색상이 없습니다.
```

<br>

### switch문 범위로 사용

``` swift
let temperature = 30

switch temperature {
    case -20...9:
        print("겨울 입니다.")
    case 10...14:
        print("가을 입니다.")
    case 15...25:
        print("봄 입니다.")
    case 26...35:
        print("여름 입니다.")
    default:
        print("이상 기후입니다.")
}
```

출력 결과  
```
여름 입니다.
```
