---
layout: post
title: "tableView:willDisplayCell:forRowAtIndexPath:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableViewDelegate, instance method]
image:
  feature:
date: 2017-02-23T23:19:00+09:00
---
**델리게이트에게 테이블 뷰가 특정 row의 셀을 그리려고 한다고 전달한다.**

----
### 파라미터
tableview: 델리게이트에게 이 이벤트가 일어날 것이라고 알려주는 테이블 뷰 <br>
cell: 테이블 뷰가 row를 그릴 때 사용할 테이블 뷰 셀 객체 <br>
indexPath: 테이블 뷰의 row를 식별하는 index path

### 해설
테이블 뷰가 셀을 사용해 row를 그리기 전에 이 메세지를 델리게이트에게 보낸다.
이로 인해 델리게이트가 셀이 보이기  전에 셀을 커스터마이즈 할 수 있다.
또한 델리게이트는 테이블 뷰에의해서 기존에 설정된 프로퍼티를 재정의 할 수 있다.
예를 들면 선택과 배경 색상을 바꿀 수 있다. 델리게이트가 반환한 후에 row가 슬라이드 인, 아웃 될 때 테이블 뷰는 alpha와 frame 프로퍼티를 설정한다.

참고: [https://developer.apple.com/reference/uikit/uitableviewdelegate/1614883-tableview?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableviewdelegate/1614883-tableview?language=objc
