---
layout: post
title: "tableView(_:commit:forRowAt:)"
modified:
categories: blog
excerpt:
tags: [Swift, UITableViewDataSource, Instance Method]
image:
feature:
date: 2017-08-15T12:55:00+09:00
---

**데이터 소스에게 수신자의 지정된 행을 삽입하거나 삭제하도록 요청한다.**

---
### 파라미터
 - **tableview:** 삽입, 삭제를 요청하는 테이블 뷰 객체.
 - **editingStyle:** indexPath에 명시된 특정 행에 요청된 삽입 또는 삭제에 관한 셀 편집 스타일. 사용 가능한 삽입 또는 삭제에 관한 편집 스타일.
 - **indexPath:** 테이블 뷰의 행을 나타내는 index path.

### 개요
사용자가 테이블 뷰에서 UITableViewCell 객체와 연결된 삽입(초록색 더하기) 컨트롤 또는 삭제 버튼을 누르면 테이블 뷰는 이 메시지를 data source에게 보내 변경 내용을 반영하도록 요청한다. 사용자가 삭제(빨간색 빼기) 컨트롤을 탭 하면 테이블 뷰에 삭제 버튼이 표시되어 사용자에게 삭제에 대한 정보를 보여준다. data source는 UITableView의 insertRows(at:with:) 또는 deleteRows(at:with:) 메서드를 호출하여 삽입 또는 삭제를 반영한다.

테이블 뷰의 스와이프 삭제 기능(사용자가 삭제 버튼을 보기 위해 가로로 스와이프 하는 기능)을 사용하기 위해서 이 메서드를 구현해야 한다.

이 메서드의 구현 내에서 setEditing(_:animated:)을 호출하면 안 된다. 만약에 반드시 setEditing(_:animated:)을 사용해야 한다면 perform(_:with:afterDelay:) 메서드를 사용하여 이 메서드를 지연된 후에 호출해라.

참고: [https://developer.apple.com/documentation/uikit/uitableviewdatasource/1614871-tableview][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/uikit/uitableviewdatasource/1614871-tableview