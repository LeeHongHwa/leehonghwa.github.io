---
layout: post
title: "dequeueReusableCellWithReuseIdentifier:forIndexPath:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-24T00:19:00+09:00
---
**재사용 식별자로 지정된 재사용가능한 테이블 뷰 셀 객체를 반환한다. 그리고 그 테이블 뷰 셀 객체를 테이블에 추가한다.**

----
### 파라미터
identifier: 재사용될 셀 객체를 나타내는 스트링. 이 파라미터는 nil이 아니다.<br>

indexPath: 셀의 위치를 나타내는 index path. data source에게 셀에 대한 요청이 있을 경우에 data source는 index path정보를 받는다. 그리고 index path를 전달해야 합니다. index path를 사용해서 테이블 뷰에서의 셀위치를 설정할 수 있다.

### 리턴
재사용 식별자와 관련있는 UITableViewCell 객체. 항상 유요한 셀을 반환한다.

### 해설
성능적인 이유로 인해 테이블 뷰가 tableView:cellForRowAtIndexPath: 메서드 안에서 셀을 row에 할당 할 때 테이블 뷰의 data source는 일반적으로 UITableViewCell 객체를 재사용 한다. 테이블 뷰는 data source가 재사용을 위해 표시 한 UITableViewCell 객체의 queue 또는 목록을 유지한. 테이블 뷰에게 새로운 셀을 제공해 달라고 요청받았을 때 data source 객체는 이 메서드를 호출한다. 이전에 등록한 class 또는 nib 파일을 사용해 새로운 셀을 만들거나 이용 가능한 셀 이 있다면 이 메서드는 기존의 셀을 dequeue 한다.

**중요한 점**<br>
이 메서드를 호출하기 전에 register​Nib:​for​Cell​Reuse​Identifier:​ 또는 register​Class:​for​Cell​Reuse​Identifier:​ 메서드를 사용하여 클래스나 nib file을 등록해야 한다.

만약에 식별된 클래스가 등록이 되있거나 새로운 클래스가 만들어 진다면 이 메서드는 init​With​Style:​reuse​Identifier:​ 메서드를 호출하여 셀을 초기화 할 것이다. nib file에서 만들어진 셀 일 경우 제공된 nib file에서 셀 객체를 불러낼 것이다. 대신에 만약에 기존의 셀 이 재활용이 가능하다면 이 메서드는 셀의 prepareForReuse 메서드를 호출할 것이다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614878-dequeuereusablecellwithidentifie][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614878-dequeuereusablecellwithidentifie