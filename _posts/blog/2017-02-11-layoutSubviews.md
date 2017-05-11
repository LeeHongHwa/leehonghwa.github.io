---
layout: post
title: "layoutSubviews"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-02-11T22:44:00+09:00
---
**서브 뷰들을 배치한다.**

----
### 해설
이 메서드의 기본 구현은 iOS 5.1 이하 버전에서는 어떠한 것도 실행하지 않는다.
그렇지만 그 이후 버전에서의 기본 구현은 서브 뷰들의 위치나 크기를 결정하는 제약조건을 사용한다. 

하위 클래스는 이 메서드를 하위 클래스의 뷰들을 보다 정확하게 배치하기 위해 재정의 할 수 있다. autoresizing과 하위 뷰의 동작에 따른 constraint가 원하는 행동을 하지 않을 경우에만 이 메서드를 재정의 해야 한다. 하위 뷰의 프레임을 설정하기 위해서 이 메서드를 재정의 할 수 있다. 

강제로 배치를 update 하기 위해서는 이 메서드를 직접 호출하지 말고 다음에 그려질 것이 update 하기 이전에 setNeedsLayout 메서드를 호출해라 만약에 뷰들을 즉각적으로 update 하기 위해서는 layoutIfNeeded 메서드를 호출해라

참고: [https://developer.apple.com/reference/uikit/uiview/1622482-layoutsubviews?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622482-layoutsubviews?language=objc
