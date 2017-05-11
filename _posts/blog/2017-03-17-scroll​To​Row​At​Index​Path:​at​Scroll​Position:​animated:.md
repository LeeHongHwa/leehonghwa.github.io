---
layout: post
title: "scroll​To​Row​At​Index​Path:​at​Scroll​Position:​animated:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-17T23:21:00+09:00
---
**index path에서 지정된 row가 화면의 특정 위치에 올 때까지 테이블 뷰를 스크롤한다.**

----
### 파라미터
indexPath: 테이블 뷰의 section index와 row index에 따라 테이블 뷰의 row를 나타내는 index path. NSNotFound는 0번째 row로 스크롤 할 수 있는 유요한 index이다.<br>

scrollPosition: 스크롤이 끝날때 테이블 뷰의 row(위, 가운데, 아래)의 상태적인 위치를 나타내는 상수 유요한 상수의 설명을 보려면 [UITable​View​Scroll​Position][UITable​View​Scroll​Position]를 봐라.<br>

animated: animate 위치의 변화를 animate 주려면 YES를 세팅하고 즉각적으로 변화를 주고싶다면 NO를 세팅해라.

### 해설
뷰 컨트롤러의 뷰의 bounds(좌표,크기)가 변경될 때 뷰는 하위뷰의 위치를 조절한다. 그리고 나서 시스템은 이 메서드를 호출한다.
그러나 뷰의 하위 뷰들이 개별적으로 변할 때마다 이 메서드가 호출된다는 것을 의미하는 것은 아니다.
각각의 하위뷰들은 자신의 레이아웃을 조절 할 책임이 있다.

뷰 컨트롤러는 뷰의 하위 뷰들의 위치를 배치하고 난 뒤에 어떠한 변화를 주고 싶다면 이 메서드를 overrride 할 수 있다.
이 메서드의 기본구현은 어떠한 것도 실행하지 않는다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614997-scrolltorowatindexpath][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UITable​View​Scroll​Position]: https://developer.apple.com/reference/uikit/uitableviewscrollposition?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614997-scrolltorowatindexpath