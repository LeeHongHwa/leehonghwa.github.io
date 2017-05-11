---
layout: post
title: "layerClass"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance property]
image:
  feature:
date: 2017-04-02T21:54:00+09:00
---
**해당 클래스의 객체의 레이어를 만들기 위해 사용되는 클래스를 반환한다.**

----
### 반환
뷰의 core animation layer를 만들기 위해 사용되는 클래스

### 해설
기본값으로 이 메서드는 CALayer 클래스를 반환한다.
필요에 따라 하위 클래스들은 이 메서드를 override 할 수 있고 다른 레이어 클래스를 반환할 수 있다. 예를 들어 큰 스크롤 영역을 보여주기 위해 화면분할을 사용하는 경우에 사용자는 이 메서드를 override 할 수 있고 CATiled​Layer 클래스를 반환할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622626-layerclass?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622626-layerclass?language=objc