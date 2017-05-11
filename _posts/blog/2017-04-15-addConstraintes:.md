---
layout: post
title: "addConstraintes:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-04-15T16:37:00+09:00
---
**수신자의 뷰 또는 수신자의 하위 뷰 레이아웃에 관한 다양한 제약조건을 추가한다.**

----
### 파라미터
constraints: 뷰에 추가될 제약 조건의 배열. 모든 제약 조건은 자신의 뷰 또는 뷰의 하위뷰만 참조할 수 있다.

### 해설
모든 제약조건은 수신자의 뷰 범위 내에 있는 뷰만 포함되어야 한다. 특히 다른 뷰들은 수신자의 뷰를 포함하거나 수신자의 하위 뷰를 포함해야한다. 뷰에 추가된 제약조건들은 뷰가 소유하고 있다. 각 뷰의 제약조건들을 평가할 때 사용되는 좌표 시스템은 뷰에서 소유하고 있는 제약조건 좌표 시스템이다.

iOS 8.0 또는 그 이후의 버전에서는 addConstraint:메서드를 직접적으로 호출하지 않고 NSLayoutConstraint 클래스의 activateConstraint: 메서드를 호출한다. activateConstraint: 메서드는 자동적으로 제약 조건을 정확한 뷰에 추가한다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622513-addconstraints?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622513-addconstraints?language=objc