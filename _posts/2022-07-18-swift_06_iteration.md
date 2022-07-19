---
layout: post
title: (swift) 06. Iteration (반복문)
description: "(swift) 반복문"
tags: [swift, 공부]
comments: true
---

> # [swift] 06. Iteration (반복문)

<br>

반복적으로 코드가 실행되게 만드는 구문을 말한다.

**for-in**, **while**, **repeat-while** 문이 존재한다.

<br>
<br>
<br>

# for-in 문

``` swift
// for 루프상수 in 순회대상 {}

for i in 1...4 { // 1 ~ 4 까지 4번 반복
    print(i)
}

let array = [1, 2, 3, 4, 5]
print("\narray: ")
for i in array {
    print(i)
}
```

출력 결과  
```
1
2
3
4

array: 
1
2
3
4
5
```

<br>
<br>
<br>

# while 문

``` swift
var number = 5
while number < 10 {
    number += 1
}

print("number: \(number)")
```

출력 결과  
```
number: 10
```

<br>
<br>
<br>

# repeat while 문

``` swift
var x = 6
repeat {
    x += 2
} while x < 5

print("x: \(x)")
```

출력 결과  
```
x: 8
```