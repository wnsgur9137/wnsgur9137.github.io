---
layout: post
title: (swift) 13. 상속
description: "(swift) 상속"
tags: [swift, 공부]
comments: true
---

> # [swift] 13. 상속

<br>

상속이란 부모가 자식에게 재산을 몰려주는 행위  
상속을 사용할 땐 다음과 같이 한다.  

``` swift
class 클래스 이름: 부모 클래스 이름 {
    // 하위 클래스 정의
}
```

<br>
<br>
<br>

# 예제

<br>

## 상속

``` swift
class Vehicle {
    var currentSpeed = 0.0
    var description: String {
        return "traveling at \(currentSpeed) miles per hour"
    }
    func makeNoise() {

    }
}

class Bicycle: Vehicle {
    var hasBasket = false
}

var bicycle = Bicycle()
bicycle.currentSpeed = 15.0
print("bicycle.currentSpeed: \(bicycle.currentSpeed)")
```

출력 결과  
```
bicycle.currentSpeed: 15.0
```

<br>
<br>

## Override

``` swift
class Vehicle {
    var currentSpeed = 0.0
    var description: String {
        return "traveling at \(currentSpeed) miles per hour"
    }
    func makeNoise() {
        print("speaker on")
    }
}

class Train: Vehicle {
    override func makeNoise() {
        super.makeNoise()
        print("choo choo")
    }
}

let train = Train()
print("train.makeNoise: \(train.makeNoise)")
```

출력 결과  
```
train.makeNoise: choo choo