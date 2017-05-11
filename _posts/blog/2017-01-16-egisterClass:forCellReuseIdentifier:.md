---
layout: post
title: "registerClass:forCellReuseIdentifier:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-01-16T23:06:00+09:00
---
**새로운 테이블 셀을 만들때 사용하는 클래스를 등록한다.**

----
### 파라미터
cellClass: 테이블에서 사용할 셀의 클래스<br>
identifier: 셀의 재사용을 위한 identifier, 이 파라미터는 nil,빈 문자열이면 안된다.

### 해설
어떠한 셀을  dequeueing하기 전에  어떻게 새로운 셀을 만들어야 할지 테이블 뷰에게 알려주기 위해 
이 메서드를 호출하거나 registerNib:forCellReuseIdentifier: 메서드를 호출한다.
만약에 재사용하고자 하는 셀의 타입이 reuse queue에 없다면 테이블 뷰는 자동적으로 새로운 셀 객체를 만들기 위해 제공된 정보를 사용한다.

만약에 동일한 reuse identifier를 가지고 있는 클래스 또는 nib파일을 등록했다면 cellClass 파라미터에 지정된 클래스가 이전 항목을 대체한다. 
지정한  reuse identifier의 등록을 해제하려면 cellClass에 nil을 지정 할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614888-registerclass][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614888-registerclass
