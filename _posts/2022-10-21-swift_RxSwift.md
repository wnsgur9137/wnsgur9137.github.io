---
layout: post
title: (swift) RxSwift
description: "(swift) RxSwift"
tags: [swift, 공부]
comments: true
---

> # [swift] RxSwift

<br>

코드의 대부분은 외부 이벤트에 대한 응답과 관련이 된다.  
사용자가 컨트롤러를 조작할 때 응답할 IBAHander, 키보드 감지를 위해 Notification을 감지해야 한다.  
이런 코드들은 불필요하게, 복잡하게 만든다.  
모든 호출 코드를 일관되게 하나로 만들어주기 위해 RxSwift를 사용한다.

<br>
<br>
<br>

# 기본 개념

## Observable
> 'Every Observable instance is just a sequence'

Swift에서 제공하는 Sequence와 동일하다.  
Sequence 개개인의 요소들을 하나씩 순회할 수 있는 타입을 말한다.  

<br>
<br>
<br>

# 구성 요소
* [Observable](#Observable)  
    - Sequecne
* [Operator](#Operator)
    - Observable의 이벤트를 입력받아 결과를 출력해내는 연산자.
* [Scheduler](#Scheduler)
    - 직접적으로 Scheduler를 생성하고 커스텀할 일은 거의 없다.

<br>
<br>
<br>

# Observable

``` swift
Observable<T>
```
- Rx 코드 기반
- T 형태의 데이터 snapshort을 '전달'할 수 있는 일련의 이벤트를 '비동기적'으로 생성하는 기능
- 하나 이상의 Observers가 실시간으로 어떤 이벤트에 반응
- 세 가지 유형의 이벤트만 방출

<br>

``` swift
enum Event<Element> {
    case next(Element)      // next element of a sequence
    case error(Swift.Error) // sequence failed with error
    case completed          // sequence terminated successfully
}
```

<br>

![Observable_1](/images/RxSwift/Observable_1.png)

<br>
<br>

## Finite Observable

<br>

![FiniteObservable](/images/RxSwift//FiniteObservable.png)

<br>

``` swift
Network.download(file: "https://www...")
    .subscribe(onNext: { data in
        // 임시 파일에 데이터 추가
    },
    onError: { error in
        // 사용자에게 에러 표현
    },
    onCompleted: {
        // 다운로드 된 파일 사용
    })
```

<br>
<br>

## Infinite Observable

``` swift
UIDevice.rxorientation
    .subscribe(onNext: { current in
        switch current {
            case .landscape:
                // 가로모드 배치
            case .portrait:
                // 세로모드 배치
        }
    })
```

<br>
<br>
<br>

# Operator

> `(2 + 5) * 10 - 8'

<br>

``` swift
UIDevice.rx.orientation
    .filter { value in
        return value != .landscape
    }
    .map { _ in
        return "세로모드"
    }
    .subscribe(onNext: { string in
        showAlert(text: string)
    })
```

<br>
<br>
<br>

# Scheduler

<br>

![Scheduler](/images/RxSwift/Scheduler.png)
