---
layout: post
title: (swift) BASIC_04. ScreenTransition (화면 전환)
description: "(swift) 화면 전환"
tags: [swift, basic, 공부]
comments: true
---

> # [swift] BASIC_04. ScreenTransition (화면 전환)

<br>

# 화면 전환

## 화면 전환 방법
소스코드를 통해 전환하는 방식과, Storyboard를 통해 전환하는 방식이 있다.  
 - View Controller의 View 위에 다른 View를 가져와 전환하기
 - View Controller에서 다른 View Controller를 호출하여 전환하기
 - Navigation Controller를 사용하여 화면 전환하기
 - 화면 전환용 객체 Segueway(세그웨이)를 사용하여 화면 전환하기

<br>
<br>
<br>

# View Contorller에서 다른 View Controller를 호출하여 전환하기

## Declaration 1
``` swift
func present(_ viewControllerToPresent: UIViewController, animated flag: Bool, completion: (() -> Void)? = nil)
```
## Parameters 1
```
viewControllerToPresent
 - The view controller to display over the current view controller's content.

flag
 - Pass true to animated the presentation; otherwise, pass false

completion
 - The block to execute after the presentation finishes. This block has no return value and takes no parameters. You may specify nil for this parameter.
```

<br>
<br>


## Declaration 2
``` swift
func dismiss(animated flag: Bool, completion: (() -> Void)? = nil)
```

## Parameters 2
```
flag
 - Pass true to animate the transition.

completion
 - The block to execute after the view controller is dismissed. This block has no return value and takes no parameters. You may specify nil for this parameter.
```

<br>
<br>
<br>

# Navigation Controller를 사용하여 화면 전환하기

## Declaration 1
``` swift
func pushViewController(_ viewController: UIViewController, animated: Bool)
```

## Parameters 1
```
viewController
 - The view controller to push onto the stack. This object cannot be a tab bar controller. If the view controller is already on the navigation stack, this method throws an exception.

 animated
  - Specify true to animate the transition or false if you do not want the transition to be animated. You might specify false if you are setting up the navigation controller at launch time.
```

<br>
<br>

## Declaration 2
``` swift
func popViewController(animated: Bool) -> UIViewController?
```

## Parameters 2
```
animated
 - Set this value to true to animate the transition. Pass false if you are setting up a navigation controller before its view is displayed.
```

## Return Value
```
The view controller that was popped from the stack.
```

<br>
<br>
<br>

# 화면 전환용 객체 Segueway(세그웨이)를 사용하여 화면 전환하기

## Segueway
 - 세그웨이에는 두 개의 ViewController 사이에 연결된 화면 전환 객체를 의미한다.
 - 스토리보드를 통해 출발지와 목적지를 직접 지정하는 방식을 말한다.
 - Segueway를 사용하면 따로 코드를 사용하지 않고 화면을 전환할 수 있다.

<br>
<br>

## Action Segueway
 - 출잘점이 ViewController 자체인 경우
  
<br>
<br>

## Manual Segueway
 - 출발점이 Button 등 ViewController가 아닌 경우를 말한다. 
 - Action Segueway, Trigger Segueway라고도 한다.
  
<br>
<br>

## Action Segueway 종류
 - Show: 가장 일반적인 Segueway로 Navigation Controller를 사용하면 화면 전환 시 ViewController가 ViewStack에 쌓이게 된다.
 - Show Detail: 스플릿 뷰에서 주로 사용한다. 아이폰에서 사용하게 되면 Show Segueway Action과 똑같이 동작하지만, 아이패드에서 사용하게 되면 스플릿 뷰에 Master&Slave 구조로 작동한다.
 - Present Modally: 이전 ViewController를 덮으면서 새로운 화면이 나타나게 된다.
 - Present As Popover: 아이패드에서 사용되는 것으로, 팝업 창을 띄울 때 사용한다. (아이폰에서는 사용하지 않는다.)
 - Custom: 사용자가 원하는 방식으로 커스텀하여 사용한다.