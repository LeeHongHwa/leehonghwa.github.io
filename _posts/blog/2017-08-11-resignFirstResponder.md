---
layout: post
title: "resignFirstResponder"
modified:
categories: blog
excerpt:
tags: [UIResponder, Instance Method]
image:
feature:
date: 2017-08-11T23:55:00+09:00
---

**윈도우의 first responder status를 해제하도록 수신자 객체에게 알린다.**

---

### 개요
기본 구현은 first responder status를 해제하고 YES를 반환한다. custom responders에서 이 메서드를 override 하여 객체 상태를 업데이트하거나 선택 영역에서 highlight 표시를 제거하는 등의 다른 작업을 수행할 수 있다. first responder status를 해제하지 않으려면 NO를 반환할 수도 있다. 이 메서드를 override 하는 경우 코드의 특정 지점에서 super(슈퍼 클래스 구현)를 호출해야 한다.

참고: [https://developer.apple.com/documentation/uikit/uiresponder/1621097-resignfirstresponder?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/uikit/uiresponder/1621097-resignfirstresponder?language=objc