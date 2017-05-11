---
layout: post
title: "multipleTouchEnabled"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance property]
image:
  feature:
date: 2017-03-11T22:58:00+09:00
---
**수신자가 다중 터치 이벤트를 처리할 것인지에 대한 여부를 나타내는 boolen 값**

----
### 해설
수신자가 다중 터치 이벤트를 처리할 것인지에 대한 여부를 나타내는 boolen 값.
프로퍼티의 값이 YES로 설정하면 수신자가 다중 터치와 관련된 모든 터치의 순서를 받는다.
프로퍼티의 값이 NO로 설정하면 다중 터치 순서 중에 첫 번째 터치만 수신자는 받는다.
프로퍼티의 기본값은 NO이다.
이 프로퍼티가 NO 일 때 같은 윈도우에서의 다른 뷰들은 여전히 터치 이벤트를 받는다.
만약에 뷰에서 다중 터치 이벤트를 단독적으로 처리하고 싶다면 이 프로퍼티와 exclusiveTouch 프로퍼티의 값을 YES로 설정해라.

참고: [https://developer.apple.com/reference/uikit/uiview/1622519-multipletouchenabled?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622519-multipletouchenabled?language=objc
