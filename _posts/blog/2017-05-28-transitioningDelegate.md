---
layout: post
title: "transitioningDelegate"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, Instance Property]
image:
  feature:
date: 2017-05-28T15:03:00+09:00
---
**전환 애니메이터, 대화 형 컨트롤러 및 사용자 지정 프리젠 테이션 컨트롤러 개체를 제공하는 대리자 개체입니다.**

----
### 해설
뷰 컨트롤러의 modalPresentationStyle 속성이 UIModalPresentationCustom 인 경우 UIKit은 프로퍼티 개체를 사용하여 뷰 컨트롤러에 대한 transitions과 presentations을 사용하게 한다. transitioning delegate 객체는 UIViewControllerTransitioningDelegate 프로토콜을 따르는 custom 객체이다. 이 delegate의 역할은 화면 상에 이 뷰 컨트롤러의 뷰를 애니메이트하는 데 사용되는 애니메이터 객체를 제공하고, 선택 사항으로 추가적인 크롬 및 애니메이션을 제공하는 presentation controller를 제공한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621421-transitioningdelegate?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621421-transitioningdelegate?language=objc