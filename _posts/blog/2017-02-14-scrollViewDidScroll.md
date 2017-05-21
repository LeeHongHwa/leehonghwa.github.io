---
layout: post
title: "viewDidLayoutSubviews"
modified:
categories: blog
excerpt:
tags: [UIKit, UIScrollViewDelegate, instance method]
image:
  feature:
date: 2017-02-14T22:04:00+09:00
---
**수신자 안에서 사용자가 콘텐츠 뷰를 스크롤 할 때 델리게이트에게 알려준다.**

----
### 파라미터
scrollView: 스크롤이 일어나는 스크롤 뷰 객체

### 해설
보통 델리게이트는 이 메서드를 구현하여 스크롤 뷰로부터 변화된 content offest을 얻거나 콘텐츠뷰의 영향을 받는 부분을 그려준다.

참고: [https://developer.apple.com/reference/uikit/uiscrollviewdelegate/1619392-scrollviewdidscroll?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiscrollviewdelegate/1619392-scrollviewdidscroll?language=objc
