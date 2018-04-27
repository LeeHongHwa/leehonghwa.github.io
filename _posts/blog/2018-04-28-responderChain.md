---
layout: post
title: "Responder Chain"
modified:
categories: blog
excerpt:
tags: [Documentation, UIKit, Responder Chain]
image:
  feature:
date: 2018-04-28T02:00:00+09:00
---
**항상 사용하는 터치 어떻게 처리될까?**

----

어느 날 `"Touch는 어떻게 일어나는지 아시나요?”` 라는 질문을 받았을 때 머리가 띵한 느낌이 났다. 
가장 많이 쓰면서 알지도 못하고 썼구나 하는 자기반성을 하게 되며 이 공부를 하게 되었다.
`질문해주신 분 정말 감사합니다!`

애플 문서에 나와있겠지 하고 검색해보니 아니나 다를까 [https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/understanding_event_handling_responders_and_the_responder_chain][apple-doc] 이렇게 잘 나와있었다.

위의 링크 내용을 참고하여 이해한 대로 설명하겠다.<br>

---
#### Understanding Event Handling, Responders, and the Responder Chain

이벤트는 `UIResponder 클래스`의 객체가 받고. 이를 상속받는 클래스는 `UIView, UIViewController, UIApplication`이다.<br>
responder 객체의 역할은 raw 한 이벤트를 전달받으면 이 이벤트를 처리하거나 다른 responder 객체에게 보낸다.<br>
앱에 이벤트가 들어왔을 경우에 UIKit은 first reponder 객체에게 이벤트를 전달하고 이 객체가 이벤트를 처리하지 않는다면 위에서 말했듯이 다른 responder 객체에게 이 이벤트를 전달한다.<br>
UIKit은 기본적으로 어떻게 이벤트를 responder에게 전달하는지에 대한 규칙이 있지만 이 규칙은 사용자에 따라서 바뀔 수 있다.<br>

아래 사진을 보면 기본적인 responder chain을 볼 수 있다.<br>
구조는 UILabel, UITextField, UIButton 밑에 UIView가 2개 있는 앱이다.<br>
이 구조에서 이벤트가 들어왔을 때 아무도 이벤트를 처리하지 않는다면 이벤트가 어떻게 이동하는지 설명하겠다.<br>

	1. 사용자가 textField에 이벤트를 일으키면
	2. textField에서 부모 View에게 이벤트를 전달하고 
	3. 이어서 또 부모 view에게 보낸다. 
	4. 자신의 부모 view가 없다면즉 해당 view가 root view라면 바로 window에 전달하는 것이 아니라 자신의 view controller에게 이벤트를 전달한다 
	5. 그리고 view controller는 window에게 보내고 
	6. UIApplication 객체에게 보내고 
	7. UIApplicationDelegate에게 전달한다.

<figure>
	<img src="/images/responder_chain.png" alt="responder chain">
</figure>

위에서 언급한 first reponder를 판단할때 아래 기준으로 판단한다.<br>
#### First Responder

	Touch events
	touch가 일어난 주체가 first responder이다.

	Press events (게임기와 연동)
	focus되어 있는 주체가 first responder이다.

	Shake-motion events (말 그대로 흔들기)
	사용자 또는 UIKit에서 기본으로 설정한 객체가 first responder이다.

	Remote-control events (미디어 볼륨, 다음곡 재생 등등)
	사용자 또는 UIKit에서 기본으로 설정한 객체가 first responder이다.

	Editing menu messages (텍스트 복사, 붙여쓰기 등등)
	사용자 또는 UIKit에서 기본으로 설정한 객체가 first responder이다.

<sub>
**주의** <br>
accelerometers, gyroscopes, magnetometer같은 motion 이벤트는 위의 responder chain을 따르지 않는다. 대신 Core Motion은 사용자가 지정한 객체에게 전달된다. 자세한것은 [Core Motion Framework][Core Motion Framework]을 보면 된다.
</sub>

#### Control 처리

	1. UIControl을 상속받은 객체에 이벤트가 발생하면 
	2. 그 객체의 addTarget:action:controlEvents메서드에 설정된 target에게 action message를 보낸다. 
	3. action message는 event는 아니지만 responder chain을 활용할 수 있다. 만약 target이 nil이라면 위에서 설명한 responder chain순서대로 해당 이벤트에 대한 메서드를 구현한 객체를 찾는다. Editing menu messages를 예로 들자면 cut(_:), copy(_:), paste(_:) 를 구현한 responder 객체를 찾는다.
	4. gesture recognizer를 추가한 view가 있다면 gesture recognizer가 우선으로 event를 받는다 하지만 제대로 event를 처리하지 않는다면 
	5. 다음 view에게 넘어가고 또 적절한 처리가 없다면 responder chain 대로 흘러간다.

<sub>
**주의** <br>
터치 위치가 뷰의 범위 밖에있는 경우 hitTest (_ : with :) 메소드는 해당 뷰와 모든 하위 뷰를 검색하지 않는다. 예를들면 clipsToBounds 속성이 false 인 경우이고 view의 크기보다 큰 하위 view가 있어도 하위 view는 터치를 받지 못한다.<br>
UiKit은 Touch가 처음 일어날때 해당 객체에 UITouch 객체를 만들며 touch가 끝나면 해제된다. touch 영역이 변경되거나 속성이 변경된다면 UIKit은 UITouch 객체를 업데이트 시켜준다.
</sub>

#### Responder Chain 변경

Responder Chain의 next 속성을 재정의 함으로서 기본 responder chain을 변경할 수 있다. next 속성에 다음 responder가 됬으면 하는 객체를 반환해주면 된다.

	많은 UIKit 클래스가 이미 이 속성을 재정의 하고 특정 객체를 반환하고 있다.
	5가지의 예를 들자면
	1. 기본은 다음 responder는 super view이지만 responder view가 view controller의 root view이면 next 속성의 반환값은 view controller 이다.
	2. responder chain이 window의 root view controller까지 왔다면 next 속성은 window 이다.
	3. presented 된 view controller라면 next 속성은 presenting view controller 이다.
	4. UIWindow 객체의 next 속성은 UIApplication 객체 이다.
	5. UIApplication 객체의 next 속성은 app delegate이다.(단 UIResponder의 클래스를 상속받은 객체이면서 view. view controller, app객체가 아니어야 한다.)



<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/understanding_event_handling_responders_and_the_responder_chain
[Core Motion Framework]: https://developer.apple.com/library/content/documentation/Miscellaneous/Conceptual/iPhoneOSTechOverview/CoreServicesLayer/CoreServicesLayer.html#//apple_ref/doc/uid/TP40007898-CH10-SW27
