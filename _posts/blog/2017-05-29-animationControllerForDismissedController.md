---
layout: post
title: "animationControllerForDismissedController:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewControllerTransitioningDelegate, Instance Method]
image:
  feature:
date: 2017-05-29T22:40:00+09:00
---
**뷰 컨트롤러를 사라지게 할 때 사용할 transition 애니메이터 객체를 delegate에게 요청한다.**

----
### 파라미터
 - **dismissed:** 곧 사라질 뷰 컨트롤러 객체

### 리턴 값
뷰 컨트롤러를 사라지게 할 떄 사용할 애니메이터 객체 또는 custom transition을 사용하여 뷰 컨트롤러를 사라지게 하지 않으려는 경우에는 nil이다. 반환하는 객체는 상호적이 아닌 고정 길이 애니메이션을 수행 할 수 있어야한다.

### 해설
이 메서드를 사용하여 UIViewControllerAnimatedTransitioning 프로토콜의 메서드를 구현하는 객체를 만들고 반환해라. 해당 프로토콜 구현은 화면에 사라지는 뷰 컨트롤러의 모양을 애니메이션화 해야한다. dismissed 파라미터를 사용하여 애니메이터 객체를 초기화하거나 전환 애니메이션을 준비하는 데 필요한 작업을 수행해라. 뷰 컨트롤러를 사라지게 할 때 지정된 뷰 컨트롤러들에 대해 custom transition 애니메이션을 구현하지 않으려면 이 메서드에서 nil을 반환해라.

> **주의 사항:**
>
> 상호작용 적인 애니메이터 객체를 사용하여 뷰 컨트롤러의 사라지는 것을 관리하려는 경우 이 메서드를 구현해야한다. 이 메서드에서 반환 한 애니메이터 객체는 애니메이션을 실행한다. 상호작용 적인 애니메이터 객체는 애니메이션 자체가 아닌 애니메이션의 타이밍만 관리한다.

transition 애니메이션 객체에 관한 정보는 [UIViewControllerAnimatedTransitioning][UIViewControllerAnimatedTransitioning]를 참고해라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontrollertransitioningdelegate/1622047-animationcontrollerfordismissedc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UIViewControllerAnimatedTransitioning]: https://developer.apple.com/reference/uikit/uiviewcontrolleranimatedtransitioning?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontrollertransitioningdelegate/1622047-animationcontrollerfordismissedc