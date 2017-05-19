---
layout: post
title: "UIViewControllerAnimatedTransitioning"
modified:
categories: blog
excerpt:
tags: [UIKit, protocol]
image:
  feature:
date: 2017-05-19T11:00:00+09:00
---
**custom 뷰 컨트롤러 전환을 위해 애니메이션을 구현하는 객체에서 UIViewControllerAnimatedTransitioning 프로토콜을 적용해라. 이 프로토콜의 메소드를 사용하면 animator 객체를 정의 할 수 있다. 이 객체는 일정 시간 내에 뷰 컨트롤러의 화면을 보여주거나 사라지게 전환하기위한 애니메이션을 만든다. 이 프로토콜을 사용하여 생성한 애니메이션은 상호작용하지 않는다. 상호작용적인 전환을 만들려면 애니메이션의 타이밍을 제어하는 다른 객체와 animator 객체를 결합해야한다.**

----
### 해설
animator 객체에서 transitionDuration: 메서드를 구현하여 지속시간을 지정하고 animateTransition: 메서드를 구현하여 애니메이션을 직접 만들어라. 전환과 관련된 객체에 대한 정보는 context 객체의 형태로 animateTransition: 메서드로 전달된다. 
해당 객체에게 제공된 정보를 사용하여 지속시간 동안 target 뷰 컨트롤러의 뷰를 보여주거나 사라지게 할 수 있다.

뷰의 bounds(좌표,크기)가 변경될 때, 뷰는 하위뷰의 위치를 조절한다.
뷰가 하위 뷰의 배치를 조절하기 전에 뷰 컨트롤러는 이 메서드를 override할 수 있다.
이 메서드의 기본구현은 어떠한 일도 실행하지 않는다.

UIViewControllerTransitioningDelegate 프로토콜을 따르는 delegate 객체에서 애니메이터 객체를 만들어라. 뷰 컨트롤러를 presenting 할 때 presentation 스타일을 UIModalPresentationCustom로 설정하고 presented 뷰 컨트롤러의 transition delegate property에 presenting 뷰 컨트롤러를 할당해라. presenting 뷰 컨트롤러는 transitioning delegate로 부터 애니메이션 객체를 찾고 애니메이션을 수행하기 위해 그 객체를 사용한다. present 그리고 dismiss 할 때 다른 animator 객체를 제공 할 수 있다.

user interaction에 뷰 컨트롤러의 전환을 추가하기 위해서 UIViewControllerInteractiveTransitioning 프로토콜을 따르는 커스텀 객체 인 interactive animator 객체와 함께 애니메이터 객체를 사용해야합니다.
interactive 전환에 관한 자세한 내용은 [UIViewControllerInteractiveTransitioning][UIViewControllerInteractiveTransitioning]봐라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontrollerinteractivetransitioning?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UIViewControllerInteractiveTransitioning]: https://developer.apple.com/reference/uikit/uiviewcontrollerinteractivetransitioning?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontrollerinteractivetransitioning?language=objc