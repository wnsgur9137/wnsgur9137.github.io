---
layout: post
title: (swift) 22. High order function (고차 함수)
description: "(swift) 고차 함수"
tags: [swift, 공부]
comments: true
---

> # [swift] 22. High order function (고차 함수)

<br>

## 고차함수
다른 함수를 전달 인자로 받거나 함수 실행의 결과를 함수로 반환하는 함수  

## swift에서 제공하는 고차 함수 (모두 컬렉션 타입에 정의됨)
 - map
 - filter
 - reduce

<br>
<br>
<br>

# 예제

<br>

## map
``` swift
let numbers = [0, 1, 2, 3]
let mapArray = numbers.map { (number) -> Int in
    return number * 2
}
print("map \(mapArray)")
```

출력 결과  
```
map [0, 2, 4, 6]
```

<br>

## filter
필터는 컨테이너 내부의 값을 걸러서 새로운 컨테이너를 생성한다.  
``` swift
let intArray = [10, 5, 20, 13, 4]
let filterArray = intArray.filter { $0 > 5 }    // 클로저 간소화
print("filter \(filterArray)")
```

출력 결과  
```
filter [10, 20, 13]
```

<br>

## reduce
reduce는 컨테이너 내부의 값들을 하나로 통합시켜준다.
``` swift
let someArray = [1, 2, 3, 4, 5]
let reduceResult = someArray.reduce(0) {    // 초기 값 0
    (result: Int, element: Int) -> Int in   // 매개변수 result(누적 값), element(배열의 요소 값)
    print("\(result) + \(element)")
    return result + element
}
print("reduce \(reduceResult)")
```

출력 결과
```
0 + 1
1 + 2
3 + 3
6 + 4
10 + 5
reduce 15
```