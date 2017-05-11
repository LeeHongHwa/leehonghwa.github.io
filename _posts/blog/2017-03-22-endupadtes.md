---
layout: post
title: "endupdates"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-22T00:54:00+09:00
---
**테이블 뷰의 row 그리고 section을 삽입, 삭제, 선택 또는 reload를 하는 메서드 호출을 종료한다.**

----
### 해설

메서드를 호출하면 beginUpdates의 시작과 테이블 뷰의 section과 row를 삽입, 삭제, 선택 그리고 reload 메서드 호출들을 묶을 수 있다. 이 메서드를 호출할 때 테이블 뷰 동작들을 동시에 animate한다. beginUpdates의 실행과 endUpdates는 nested될 수 있다. 만약에 이 블럭안에서 셀을 삽입, 삭제, 그리고 선택하지 않으면 row count같은 테이블 뷰의 속성은 유효하지 않다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614890-endupdates?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614890-endupdates?language=objc
