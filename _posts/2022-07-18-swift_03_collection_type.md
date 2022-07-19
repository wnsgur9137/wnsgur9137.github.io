---
layout: post
title: (swift) 03. 컬렉션 타입
description: "(swift) 컬렉션 타입"
tags: [swift, 공부]
comments: true
---

> # [swift] 03. 컬렉션 타입

<br>

컬렉션 타입은 **데이터들의 집합 묶음**

<br>

### **Array**  
데이터 타입의 값들을 **순서대로** 지정하는 리스트 (배열)  

### **Dictionary**  
순서없이 **키(key)와 값(Value)** 한 쌍으로 데이터를 저장하는 컬렉션 타입  

### **Set**  
같은 데이터 타입의 값을 **순서없이** 저장하는 리스트(중복 없음)

<br>
<hr>
<br>

배열 생성 방법  
``` swift
var arrayName: Array<DataType> = Array<DataType>()
var arrayName2: [DataType] = []
```

배열 코드
``` swift
var numbers: Array<Int> = Array<Int>() // 기본적인 배열 선언
numbers.append(1) // numbers에 값 1을 추가
numbers.append(2)
numbers.append(3)

numbers[0]
numbers[1]

numbers.insert(4, at: 2) // 2번 index에 4의 값을 추가

numbers.remove(at: 0) // 0번 index의 값을 삭제
numbers
```

출력
```
[2, 4, 3]
```

<br>
<hr>
<br>

딕셔너리 생성 방법  
``` swift
var dic: Dictionary<KeyDataType, ValueDataType> = Dictionary<KeyDataType, ValueDataType>()
var dic2: [KeyDataType, ValueDataType] = [KeyDataType, ValueDataType]
```

딕셔너리 코드  
``` swift
var dic: [String: Int] = ["권태완": 1]
dic["김철수"] = 3
dic["김민지"] = 5
dic.removeValue(forKey: "김철수") // Key가 "김철수"인 값을 제거
```

출력  
``` swift
["김민지":5, "권태완":1]
```

<br>
<hr>
<br>

set 생성 방법  
``` swift
var set: Set = Set<DataType>()
// set은 축약형 선언이 없다.
```

코드  
``` swift
var set: Set = Set<Int>()
set.insert(5)
set.insert(10)
set.insert(20)
set.insert(30)
set.insert(30)
set.insert(30)

set.remove(5) // 5 삭제
```

출력 결과  
``` swift
{10, 20< 30}
```