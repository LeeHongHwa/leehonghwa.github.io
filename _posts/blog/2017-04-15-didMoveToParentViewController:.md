---
layout: post
title: "didMoveToParentViewController:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-04-15T17:03:00+09:00
---
**container 뷰 컨트롤러로 부터 뷰 컨트롤러가 제거되거나 추가될 때 호출한다.**

----
### 파라미터
parent: 부모 뷰 컨트롤러, 만약에 부모 뷰 컨트롤러가 없다면 nil

### 해설
container에 추가된 후에 어떠한 처리를 하기위해 뷰 컨트롤러는 override 할 수 있다.

만약에 container 뷰 컨트롤러를 구현했다면 새로운 뷰 컨트롤러로의 전환이 완료된 후 하위 뷰 컨트롤러의 didMoveToParentViewController: 메서드를 호출해야하며, 전환이 없으면 addChildViewController: 메서드를 호출 한 직후에 호출해야 한다.

자식 뷰컨트롤러를 제거한 후에 removeFromParentViewController 메서드는 자동적으로 자식 뷰 컨트롤러의 didMoveToParentViewController: 메서드를 호출한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621405-didmovetoparentviewcontroller][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621405-didmovetoparentviewcontroller