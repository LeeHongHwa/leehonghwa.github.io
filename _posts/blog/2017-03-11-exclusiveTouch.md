---
layout: post
title: "exclusiveTouch"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance property]
image:
  feature:
date: 2017-03-11T22:58:20+09:00
---
**수신자가 터치 이벤트를 단독적으로 처리할 것인지에 대한 여부를 나타내는 boolen 값**

----
### 해설
프로퍼티 값을 YES로 설정하는 것을 통해 수신자는 같은 윈도우에 있는 다른 부들에 터치 이벤트의 전달을 차단한다.
프로퍼티의 기본값은 NO이다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622453-exclusivetouch][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622453-exclusivetouch
