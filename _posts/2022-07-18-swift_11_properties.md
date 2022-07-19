---
layout: post
title: (swift) 11. 프로퍼티
description: "(swift) 프로퍼티"
tags: [swift, 공부]
comments: true
---

> # [swift] 11. 프로퍼티

<br>

프로퍼티란 클래스, 구조체 또는 열거형 등에 관련된 값을 뜻한다.  

프로퍼티는 **저장 프로퍼티**, **연산 프로퍼티**, **타입 프로퍼티**가 존재한다.  
저장 프로퍼티는 인스턴스의 변수 또는 상수를 의미한다.  
연산 프로퍼티는 값을 저장하는 것이 아닌, 특정 연산을 실행하는 결과 값을 저장한다.  
타입 프로퍼티는 특정 타입에서 사용하는 프로퍼티이다.  

<br>
<br>
<br>

## 저장 프로퍼티  
``` swift
// 저장 프로퍼티
struct Dog {
    var name: String
    let gender: String
}

var dog = Dog(name: "이준혁", gender: "Male")
print(dog)

dog.name = "김철수"
// dog.gender = "Female" -> Error (let이므로)

let dog2 = Dog(name: "김철수", gender: "Male")
// dog2.name = "김철수" -> Error (구조체 인스턴스가 상수이기 때문에.)

//클래스는 상수로 선언해도 인스턴스에서 변경이 가능하지만, 구조체는 상수로 선언할 경우 인스턴스에서 변경이 불가하다.

class Cat {
    var name: String
    let gender: String

    init(name: String, gender: String) {
        self.name = name
        self.gender = gender
    }
}

let cat = Cat(name: "json", gender: "Male")
cat.name = "gunter"
print("cat.name: \(cat.name)")
```

출력 결과  
```
Dog(name: "이준혁", gender: "Male")
cat.name: gunter
```

<br>
<br>
<br>

## 연산 프로퍼티

``` swift
struct Stock {
    var averagePrice: Int
    var quantity: Int
    var purchasePrice: Int {    // 게터 세터를 사용한 연산형 프로퍼티
        get {
            return averagePrice * quantity
        }
        set(newPrice) {
            averagePrice = newPrice / quantity
        }
    }
}

var stock = Stock(averagePrice: 2300, quantity: 3)
print("stock: \(stock)")
print("stock.purchasePrice: \(stock.purchasePrice)")
stock.purchasePrice = 3000
print("stock.averagePrice: \(stock.averagePrice)")
```

출력 결과  
```
Stock(averagePrice: 2300, quantity: 3)
stock.purchasePrice: 6900
stock.averagePrice: 1000
```

<br>
<br>
<br>

## 프로퍼티 옵저버

프로퍼티의 값의 변화를 관찰하고 반영한다.  
새로운 값이 기존 값과 같더라도 프로퍼티 옵저버가 호출이 된다.(set 될 경우 호출)  
**저장 프로퍼티, override된 저장 계산 프로퍼티에서만 사용 가능하다.**  

``` swift
class Account {
    var credit: Int = 0 {
        // 소괄호 이름 지정
        willSet {   // 값이 저장되기 직전에 호출
            print("잔액이 \(credit)원에서 \(newValue)원으로 변경될 예정입니다.")
        }
        didSet {    // 값이 저장된 직후에 호출
            print("잔액이 \(oldValue)원에서 \(credit)원으로 변경되었습니다.")
        }
    }
}

var account = Account()
account.credit = 1000
```

출력 결과  
```
잔액이 0원에서 1000원으로 변경될 예정입니다.
잔액이 0원에서 1000원으로 변경되었습니다.
```

<br>
<br>
<br>

## 타입 프로퍼티

타입 프로퍼티란 인스턴스 생성 없이 객체 내 프로퍼티 접근을 가능하게 하는 것을 말한다.  
타입 프로퍼티는 **저장 프로퍼티와 연산 프로퍼티에서만** 사용 가능하다.

``` swift
struct SomeStructure {
    static var storedTypeProperty = "Some value."
    static var computedTypeProperty: Int {
        return 1
    }
}

print("SomeStructure.computedTypeProperty: \(SomeStructure.computedTypeProperty)")
print("SomeStructure.storedTypeProperty: \(SomeStructure.storedTypeProperty)")
SomeStructure.storedTypeProperty = "Hello"
print("SomeStructure.storedTypeProperty: \(SomeStructure.storedTypeProperty)")
```

출력 결과  
```
SomeStructure.computedTypeProperty: 1
SomeStructure.storedTypeProperty: Some value
SomeStructure.storedTypeProperty: Hello
```