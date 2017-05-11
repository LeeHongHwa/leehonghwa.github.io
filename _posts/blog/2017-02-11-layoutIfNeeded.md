---
layout: post
title: "layoutIfNeeded"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-02-11T22:49:00+09:00
---
**하위 뷰들을 즉각적으로 재배치한다.**

----
### 해설
이 메서드는 하위 뷰들이 그려지기 전에 하위 뷰의 레이아웃을 설정을 강요하기 위해 사용한다. 루트 뷰로부터 메시지를 받는 뷰를 사용하여 이 메서드는 루트에서 시작하는 뷰의 하위 뷰들을 배치한다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622507-layoutifneeded?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622507-layoutifneeded?language=objc