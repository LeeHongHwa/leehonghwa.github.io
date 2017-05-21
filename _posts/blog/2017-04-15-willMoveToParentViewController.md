---
layout: post
title: "willMoveToParentViewController:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-04-15T16:40:20+09:00
---
**container 뷰 컨트롤러로 부터 뷰 컨트롤러가 추가되거나 제거되기 전에 이 메서드를 호출한다.**

----
### 파라미터
parent: 부모 뷰 컨트롤러, 만약에 부모 뷰 컨트롤러가 없다면 nil

### 해설
만약에 container 뷰 컨트롤러를 구현했다면 removeFromParentViewController:메서드를 호출하기 전에 자식 뷰 컨트롤러에서 willMoveToParentViewController:메서드를 호출하고 부모 값 nil을 전달해야 한다.

custom container 뷰 컨트롤러가 addChildViewController: 메서드를 호출할 때, addChildViewController:는 자동적으로 willToParentViewController: 메서드를 호출하여 뷰 컨트롤러가 추가하기 전에 부모 뷰 컨트롤러의 자식으로 추가된다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621381-willmovetoparentviewcontroller][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621381-willmovetoparentviewcontroller