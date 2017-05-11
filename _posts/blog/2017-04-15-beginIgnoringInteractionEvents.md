---
layout: post
title: "beginIgnoringInteractionEvents"
modified:
categories: blog
excerpt:
tags: [UIKit, UIApplication, instance method]
image:
  feature:
date: 2017-04-15T16:50:00+09:00
---
**터치 이벤트와 연관된 처리를 지연하라고 수신자에게 알린다.**

----
### 해설
일반적으로 animation 또는 transition이 시작하기 전에 이 메서드는 호출한다. 호출은 endIgnoringInteractionEvents 메서드와 중첩된다.

참고: [https://developer.apple.com/reference/uikit/uiapplication/1623047-beginignoringinteractionevents?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiapplication/1623047-beginignoringinteractionevents?language=objc
