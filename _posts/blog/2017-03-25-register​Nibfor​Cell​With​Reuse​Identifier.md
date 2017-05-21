---
layout: post
title: "register​Nib:​for​Cell​With​Reuse​Identifier:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-25T11:34:00+09:00
---
**식별자로 지정된 테이블 뷰 셀을 포함하는 nib 객체를 등록한다.**

----
### 파라미터
nib: 셀을 만들기 위해 사용되는 nib 객체.<br>
identifier: 셀의 재사용을 위한 식별자. 이 파라미터는 nil을 지정할 수 없으며 빈 문자열 또한 지정할 수 없다.

### 해설
셀을 dequeueing 하기 전에 테이블 뷰에게 어떻게 셀을 만들지 알려주기 위해 이 메서드 또는 register​Class:​for​Cell​Reuse​Identifier:​ 메서들 호출한다. 만약에 현재 지정된 타입의 셀이 없을 경우에 자동으로 테이블 뷰는 새로운 셀을 만들기 위해 받은 정보를 사용한다.

만약에 이전에 등록된 클래스나 nib파일이 같은 재사용 식별자라면 nib 파라미터에 세팅한 nib이 이전에 등록된 식별자를 대체한다. 지정된 재사용 식별자로부터 nib 파일을 제거하기 위해서 nib 파라미터에 nil을 세팅할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614937-registernib][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614937-registernib
