---
layout: post
title: "invalidate"
modified:
categories: blog
excerpt:
tags: [Foundation, NSTimer, instance method]
image:
  feature:
date: 2017-02-16T09:03:00+09:00
---
**수신자가 다시 시작하는 것을 중지하고 수신자의 실행 루프를 제거하는 것을 요청한다.**

----
### 해설
이 메서드는 NSRunLoop 객체로부터 timer를 제거하는 유일한 방법이다. NSRunLoop 객체는 invalidate 메서드가 리턴되기 직전 또는 그 후에 timer에 대한 강한 참조를 제거한다.
만약 target 또는 user info 객체가 설정돼있다면 수신자는 target 또는 user info 객체에 대한 자신의 강한 참조를 제거한다.\

### 특별 고려 사항
timer가 설치돼 있는 쓰레드로부터 이 메세지를 보내야 한다. 만약에 이 메세지를 다른 쓰레드에 보낸다면 timer와 관련된 input source는 실행 루프에서 제거되지 않을것이다. 그리고 이 떄문에 쓰레드가 제대로 종료되지 않을 수 있다.

참고: [https://developer.apple.com/reference/foundation/nstimer/1415405-invalidate?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/foundation/nstimer/1415405-invalidate?language=objc
