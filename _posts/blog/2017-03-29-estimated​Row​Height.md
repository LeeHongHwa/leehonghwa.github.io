---
layout: post
title: "estimated​Row​Height"
modified:
categories: blog
excerpt:
tags: [UIKit, UITableView, instance property]
image:
  feature:
date: 2017-03-29T23:43:00+09:00
---
**테이블 뷰의 어림잡은 높이**

----
### 해설
행의 높이를 음수가 아닌 값으로 제공하면 테이블 뷰를 로딩하는 성능을 향상 시킬 수 있다.
테이블에 가변 높이 row가 포함되어 있으면 테이블을 로드할 떄 가변하는 모든 row의 높이를 계산하는 데 많은 비용이 부과 될 수 있다.
estimation 을 사용하면 로드 시간에서 스크롤하는 시간까지의 기하학 계산 비용의 일부를 연기할 수 있다.

self-sizing 테이블 뷰 셀을 만들때 이 메서드와 셀의 사이즈를 결정하는 제약사항이 필요하다.
기본 값은 0 이며 이는 estimate를 하지 않는다는 것을 의미한다.

참고: [https://developer.apple.com/reference/uikit/uitableview/1614925-estimatedrowheight?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitableview/1614925-estimatedrowheight?language=objc