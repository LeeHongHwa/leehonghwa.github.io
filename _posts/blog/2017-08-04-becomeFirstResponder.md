---
layout: post
title: "becomeFirstResponder"
modified:
categories: blog
excerpt:
tags: [UIResponder, Instance Method]
image:
feature:
date: 2017-08-04T23:55:00+09:00
---

**이 객체를 윈도우의 첫 번째 응답자로 만들기 위해 UIKit에 요청한다.**

---

### 반환 값
만약에 지금 이 객체가 첫번째 응답자라면 YES, 그렇지 않다면 NO를 반환한다.

### 개요
수신자 객체를 첫 번째 응답자로 하고 싶을 때, 이 메서드를 호출한다. 이 메서드를 호출한다고 해서 수신자 객체가 반드시 첫 번째응답자가 되는 것은 아니다. UIKit은 현재의 첫 번째 응답자에게 첫 번째 응답을 해제하라는 요청을 보낸다. 이 경우 UIKit은 이 메서드를 호출한 객체에게 canBecomeFirstResponder 메서드를 호출한다. 이 메서드는 기본적으로 NO를 반환한다. 이 객체가 첫 번째 응답자가 되는 데 성공하면 첫 번째 응답자를 대상으로 하는 이벤트가 이 객체에 전달되고 input view가 있는 경우 UIKit은 객체의 input view를 표시하려고 한다.

엑티비티 한 뷰 계층 구조의 일부가 아닌 뷰에서 이 메서드를 호출하지 마라. 해당 객체의 윈도우 프로퍼티를 확인하여 뷰가 화면에 있는지(엑티비티) 확인할 수 있다. 윈도우 프로퍼티가 nil이 아닌 유효한 값이라면 현제 뷰 계층에서 엑티비티 상태이고,  nil 이면 뷰가 액티비티 한 상태가 아니다.

사용자 응답자에서 이 메서드를 재정의 하여 객체의 상태를 업데이트하거나 highlighting the selection 같은 작업을 수행할 수 있다. 이 메서드를 오버라이드 하는 경우는, 구현 코드 안에서 super를 호출해야 한다.

참고: [https://developer.apple.com/documentation/uikit/uiresponder/1621113-becomefirstresponder?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/uikit/uiresponder/1621113-becomefirstresponder?language=objc