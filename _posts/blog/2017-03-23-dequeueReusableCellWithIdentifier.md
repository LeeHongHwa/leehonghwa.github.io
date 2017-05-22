---
layout: post
title: "dequeueReusableCellWithIdentifier:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-23T00:48:00+09:00
---
**식별자로 지정된 재사용 가능한 테이블 뷰 셀 객체를 반환한다.**

----
### 파라미터
identifier: 재사용될 셀 객체를 나타내는 스트링. 이 파라미터는 nil이 아니다.

### 리턴
식별자와 연관 있는 UITableViewCell 객체이거나 재사용 셀 큐에 식별자와 관련된 셀이 없는 경우에는 nil을 반환한다.

### 해설
tableView:cellForRowAtIndexPath: 메서드 안에서 셀을 row에 할당할 때 성능적인 이유 때문에 table view’s data source는 일반적으로 UITableView Cell 객체를 재사용 한다. 테이블 뷰는 data source가 재사용을 위해 표시 한 UITableViewCell 객체의 queue 또는 목록을 유지힌디. 테이블 뷰에게 새로운 셀을 제공받을 때 data source객체에서 이 메서드를 요청한다. 이전에 등록한 class 또는 nib파일을 사용해 새로운 셀을 만들거나 이용 가능한 셀이 있다면 이 메서드는 기존의 셀을 dequeue한다.
만약에 재사용 가능한 셀이 없고 class 또는 nib파일을 등록해 놓지 않았다면 이 메서드는 nil을 반환할 것이다.

만약에 식별자로 클래스가 지정하고 새로운 셀을 만들어야 할때 이 메서드는 init​With​Style:​reuse​Identifier:​ 메서드 호출을 통해 셀을 초기화 한다. 이 메서드는 nib파일로 만들어진 셀은 nib파일로 부터 불러온다. 대신에 만약에 기존의 셀이 재사용 가능하다면 이 메서드는 prepare​For​Reuse 메서드를 호출한다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614891-dequeuereusablecellwithidentifie][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614891-dequeuereusablecellwithidentifie
