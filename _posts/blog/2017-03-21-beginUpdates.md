---
layout: post
title: "beginUpdates"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance method]
image:
  feature:
date: 2017-03-21T00:33:00+09:00
---
**테이블 뷰의 section 그리고 row를 삽입, 삭제, 선택하는 메서드의 호출을 시작해라.**

----
### 해설
만약에 바로뒤에 삽입하는 것과 삭제 그리고 선택의 동작(예를 들면 cellForRowAtIndexPath: 그리고 indexPathsForVisibleRows)을 동시에 animate하기원한다면 이 메서드를 호출해라. 이 메서드 다음에 endUpdates 메서드를 사용하여 셀을 다시로드하지않고 row의 높이를 변경하는 애니메이션을 적용 할 수 있다. 이 메서드의 그룹은 endUpdates로 끝나야 한다. 이 메서드의 쌍은 중첩될 수 있다. 만약에 이 블락 안에서 셀을 삽입과 삭제 그리고 선택하지 않았다면 row의 숫자 같은 테이블 속성은 유효하지 않다. 그룹안에서 reloadData를 부르지 마라 만약에 이메서드를 그룹 안에서 호출한다면 모든 애니메이션을 직접 수행해야합니다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614908-beginupdates?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614908-beginupdates?language=objc