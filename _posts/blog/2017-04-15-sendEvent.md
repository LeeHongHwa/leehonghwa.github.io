---
layout: post
title: "sendEvent:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIApplication, instance method]
image:
  feature:
date: 2017-04-15T17:16:00+09:00
---
**앱 안의 적절한 응답 객체에게 이벤트를 전달한다.**

----
### 파라미터
event: 관련된 터치를 포함한 이벤트에 관한 정보를 캡슐화한 UIEvent 객체

### 해설

필요한 경우 UIApplication을 서브 클래싱하고 이 메서드를 재정의하여 들어오는 이벤트를 가로챌수 있다.
가로챈 모든 이벤트들은 자신의 구현 파일에서 이벤트를 처리하고 super sendEvent:event 메서드를 통해 이벤트를 전달해야한다

참고: [https://developer.apple.com/reference/uikit/uiapplication/1623043-sendevent?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiapplication/1623043-sendevent?language=objc