---
layout: post
title: "addChildViewController:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-04-15T16:43:40+09:00
---
**현재 뷰 컨트롤러의 자식 뷰 컨트롤러로 추가한다.**

----
### 파라미터
childViewController: 자식 뷰 컨트롤러로 추가될 뷰 컨트롤러

### 해설
이 메서드는 현재 뷰 컨트롤러와 파라미터의 자식 뷰 컨트롤러와 부모와 자식간의 관계를 만든다.
이러한 관계는 자식 뷰 컨트롤러의 뷰를 현재 뷰 컨트롤러의 content에 추가하기위해 필수적이다. 만약에 자식 뷰 컨트롤러가 이미 어떠한 container 뷰 컨트롤러의 자식 뷰 컨트롤러라면 이전에 추가된 부모 뷰 컨트롤러의 관계를 지운다.

이 메서드는 custom container 뷰 컨트롤러를 구현에서 호출될 수 있다. 만약에 override를 하려면 super를 꼭 호출해라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621394-addchildviewcontroller?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621394-addchildviewcontroller?language=objc
