---
layout: post
title: (swift) 19. Optional chaining (옵셔널 체이닝)
description: "(swift) 옵셔널 체이닝"
tags: [swift, 공부]
comments: true
---

> # [swift] 19. Optional chaining (옵셔널 체이닝)

<br>

옵셔널 체이닝이란 옵셔널에 속해 있는 nil 일지도 모르는 프로퍼티, 메서드, 서브스크립션 등을 가져오거나 호출할 때 사용할 수 있는 일련의 과정  

<br>
<br>
<br>

# 예제

<br>

``` swift
struct Developer {
    let name: String
}

struct Company {
    let name: String
    var developer: Developer?
}

var company: Company(name: "Gunter", developer: nil)
print(company.developer)

var developer = Developer(name: "jun")
var company2: Company(name: "CompanyJun", developer: developer)
print(company2.developer)
// print(company.developer.name) // ERROR company.developer.name에 접근하기 전에 developer의 옵셔널을 벗겨내라는 에러
print(company2.developer?.name) // ?로 Optional 체니잉을 하면 프로퍼티의 값은 항상 Optional로 감싸 있다. (값이 nil일 수도 있기 때문)
print(company2.developer!.name) // !로 Optional 체이닝을 하면 옵셔널 프로퍼티를 강제 언래핑하기 때문에 값이 옵셔널로 감싸져 있지 않다.
```

출력 결과  
```
nil
Optional(__lldb_expr_595.Developer(name: "jun"))
Optional("jun")
jun
```