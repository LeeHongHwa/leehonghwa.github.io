---
layout: post
title: "transitionDuration:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewControllerAnimatedTransitioning, Instance Method]
image:
  feature:
date: 2017-05-21T15:58:00+09:00
---
**필수 사항.<br>animator 객체에게 변환 애니메이션 지속 시간(초)을 요청한다.**

----
### 파라미터
transitionContext: 변환하는 동안 사용할 정보를 포함 하고 있는 context 객체<br>

### 반환 값
custom 변환 애니메이션 지속 시간(초)

### 해설
UIKit는 이 메서드를 호출하여 애니메이션의 타이밍 정보를 가져온다. 지정한 값은 animateTransition: 메서드로 애니메이션을 설정할 때 사용하는 값과 동일해야 한다. UIKit는 이 값을 사용하여 전환과 관련된 다른 개체의 동작을 동기화한다. 예를 들어, 네비게이션 컨트롤러는 이 값을 사용하여 네비게이션 바의 변화를 동기화합니다.

반환 값을 결정할 때 실행 시간에 user interaction 을 지원하여도 화면 전환 중에는 user interaction 이 없다고 가정한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontrolleranimatedtransitioning/1622032-transitionduration?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontrolleranimatedtransitioning/1622032-transitionduration?language=objc