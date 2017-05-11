---
layout: post
title: "viewDidLayoutSubviews"
modified:
categories: blog
excerpt:
tags: [UIKit, instance method]
image:
  feature:
date: 2017-01-15T22:34:00+09:00
---
**이 메서드는 뷰 컨트롤러의 뷰가 자식 뷰들을 배치하고 난 뒤 호출됩니다.**

----
### 해설
뷰 컨트롤러의 뷰의 bounds(좌표,크기)가 변경될 때 뷰는 하위뷰의 위치를 조절한다. 그리고 나서 시스템은 이 메서드를 호출한다.
그러나 뷰의 하위 뷰들이 개별적으로 변할 때마다 이 메서드가 호출된다는 것을 의미하는 것은 아니다.
각각의 하위뷰들은 자신의 레이아웃을 조절 할 책임이 있다.

뷰 컨트롤러는 뷰의 하위 뷰들의 위치를 배치하고 난 뒤에 어떠한 변화를 주고 싶다면 이 메서드를 overrride 할 수 있다.
이 메서드의 기본구현은 어떠한 것도 실행하지 않는다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621398-viewdidlayoutsubviews?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621398-viewdidlayoutsubviews?language=objc
