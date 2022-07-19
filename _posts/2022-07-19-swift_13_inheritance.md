---
layout: post
title: (swift) 13. Inheritance (상속)
description: "(swift) 상속"
tags: [swift, 공부]
comments: true
---

> # [swift] 13. Inheritance (상속)

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

# 클래스 상속

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
train.makeNoise: speaker on
choo choo
```

<br>
<br>

## 프로퍼티 상속

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

class Car: Vehicle {
    var gear = 1
    override var description: String {
        return super.description + " in gear \(gear)"
    }
}

let car = Car()
car.currentSpeed = 30.0
car.gear = 2
print("car.description: \(car.description)")
```

출력 결과  
```
car.description: traveling at 30.0 miles per hour in gear 2
```

<br>
<br>

## 상속된 프로퍼티 override를 사용해서 프로퍼티 옵저버를 추가
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

class AutomaticCar: Car {
    override var currentSpeed: Double {
        didSet{
            gear = Int(currentSpeed / 10) + 1
        }
    }
}

let automatic = AutomaticCar()
automatic.currentSpeed = 35.0
print("AutomaticCar: \(automatic.description)")
```

출력 함수  
```
AutomaticCar: traveling at 35.0 miles per hour in gear 4
```

<br>
<br>

## final
``` swift
class Vehicle {
    final var currentSpeed = 0.0 // final이므로 재정의할 수 없다.
    var description: String {
        return "traveling at \(currentSpeed) miles per hour"
    }
    func makeNoise() {
        print("speaker on")
    }
}

class AutomaticCar: Car {
    override var currentSpeed: Double { // ERROR (final로 인한 재정의 불가)
        didSet{
            gear = Int(currentSpeed / 10) + 1   // ERROR (final로 인한 재정의 불가)
        }
    }
}
```