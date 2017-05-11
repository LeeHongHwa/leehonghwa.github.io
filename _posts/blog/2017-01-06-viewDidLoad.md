---
layout: post
title: "viewDidLoad"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-01-06T12:50:00+09:00
---
**뷰 컨트롤러가 뷰 계층을 메모리에 적재할 때 이 메서드는 불린다.**

----

뷰 계층이 nib file에서 적재되든 프로그래밍적으로 loadView메서드에서 적재되든 상관없이 이 메서드는 불린다.
사용자는 보통 뷰(nib file에서 적재된 뷰)에 대해서 추가적인 초기화를 하기위해 이 메서드를 override 한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621495-viewdidload?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621495-viewdidload?language=objc
