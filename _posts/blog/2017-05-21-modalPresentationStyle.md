---
layout: post
title: "modalPresentationStyle"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, Instance Property]
image:
  feature:
date: 2017-05-21T15:32:00+09:00
---
**modally 하게 보여지는 뷰 컨트롤러의 presentation 스타일.**

----
### 해설
presentation 스타일은 modally 하게 보이는 뷰 컨트롤러가 어떻게 화면에 보이게 되는지 결정한다. horizontally compact 상황에서는 modal 뷰 컨트롤러는 항상 꽉찬 화면으로 보이고 horizontally regular environment에서는 다른 presentation 옵션을 설정할 수 있다. 사용 가능한 presentation 스타일 리스트와 transiion 스타일에 대해서 알고 싶다면 [UIModalPresentationStyle][UIModalPresentationStyle] 상수 설명을 참고해라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621355-modalpresentationstyle?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UIModalPresentationStyle]: https://developer.apple.com/reference/uikit/uimodalpresentationstyle?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621355-modalpresentationstyle?language=objc