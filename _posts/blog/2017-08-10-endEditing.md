---
layout: post
title: "endEditing:"
modified:
categories: blog
excerpt:
tags: [UIView, Instance Method]
image:
feature:
date: 2017-08-10T23:30:00+09:00
---

**뷰(또는 뷰에 텍스트 필드가 포함된 뷰)의 first responder status를 해제한다.**

---

### 파라미터
 - **force:** 강제로 first responder status를 해제하려면 YES 설정해라.

### 반환 값
뷰의 first responder status가 해제됐다면 YES 그렇지 않다면 NO.

### 개요
이 메서드는 현재 뷰와 하위 뷰의 계층에서 first responder인 텍스트 필드를 찾는다. 만약에 메서드가 그 텍스트 필드를 찾았다면 텍스트 필드의 first responder를 해제할 것을 요청하고 만약에 이 메서드의 파라미터를 YES로 설정한다면 텍스트 필드에게 first responder를 해제할 것을 요청하지 않고 강제로 해제한다.

참고: [https://developer.apple.com/documentation/uikit/uiview/1619630-endediting?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/uikit/uiview/1619630-endediting?language=objc