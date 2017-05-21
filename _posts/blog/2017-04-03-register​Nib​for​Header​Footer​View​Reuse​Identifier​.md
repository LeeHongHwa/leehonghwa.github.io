---
layout: post
title: "register​Nib:​for​Header​Footer​View​Reuse​Identifier:​"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-04-03T22:51:00+09:00
---
**특정 식별자를 가지고 있는 테이블 뷰의 header 또는 footer의 포함한 nib 객체를 등록한다.**

----
### 파라미터
nib: header또는 footer view를 만들기 위해 사용하는 nib 객체. 이 파라미터는 nil이 될 수 없다. <br>
identifier: header와 footer vview의 재사용 식별자. 이 파라미터는 nil 또는 빈 문자열이 될 수 없다.

### 해설
header 또는 footer view를 dequeueing하기 전에 테이블 뷰에게 어떻게 새로운 객체를 만들지 알려주기 위해 이 메서드를 호출하거나 register​Class:​for​Header​Footer​View​Reuse​Identifier: 메서드를 호출 한다. 만약에 특정한 타입의 뷰가 재사용 큐에 있지않다면 제공된 정보를 사용하여 자동으로 새로운 객체를 만든다.

만약에 이전에 등록한 클래스나 nib 파일이 같은 재사용 식별자가 있다면 nib 파라미터에 지정한 nib이 이전 항목을 대체합니다. 지정한 재사용 식별자를 해제하려면 nib파라미터에 nil을 설정할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614921-registernib][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614921-registernib
