---
layout: post
title: "endIgnoringInteractionEvents"
modified:
categories: blog
excerpt:
tags: [UIKit, UIApplication, instance method]
image:
  feature:
date: 2017-04-15T16:52:00+09:00
---
**터치와 연관된 이벤트에 관한 처리를 시작하라고 수신자에게 알린다.**

----
### 해설
beginIgnoringInteractionEvents 메서드를 호출 한 후 애니메이션 또는 전환이 끝나면 일반적으로이 메서드를 호출합니다. 이 메서드의 중첩 호출은 beginIgnoringInteractionEvents 메소드의 중첩 호출과 일치해야한다.

참고: [https://developer.apple.com/reference/uikit/uiapplication/1622938-endignoringinteractionevents?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiapplication/1622938-endignoringinteractionevents?language=objc