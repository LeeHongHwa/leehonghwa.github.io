---
layout: post
title: "viewWillLayoutSubviews"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-01-07T16:19:00+09:00
---
**이 메서드는 뷰 컨트롤러의 뷰가 자식 뷰들을 배치하기 직전에 불린다.**

----
### 해설
뷰의 bounds(좌표,크기)가 변경될 때, 뷰는 하위뷰의 위치를 조절한다.
뷰가 하위 뷰의 배치를 조절하기 전에 뷰 컨트롤러는 이 메서드를 override할 수 있다.
이 메서드의 기본구현은 어떠한 일도 실행하지 않는다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621437-viewwilllayoutsubviews?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621437-viewwilllayoutsubviews?language=objc
