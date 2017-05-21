---
layout: post
title: "scrollViewDidEndDecelerating:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIScrollViewDelegate, instance method]
image:
  feature:
date: 2017-02-14T23:07:00+09:00
---
**델리게이트에게 스크롤 뷰의 스크롤 이동의 감속이 끝났다(정지)는 것을 알려준다.**

----
### 파라미터
콘텐츠 뷰의 스크롤을 감속시키는 스크롤 뷰의 객체이다.

### 해설
스크롤 뷰는 스크롤의 이동이 정지하면 이 메서드를 호출한다. UIScrollView의 Decelerating 프로퍼티는 감속을 제어한다.

참고: [https://developer.apple.com/reference/uikit/uiscrollviewdelegate/1619417-scrollviewdidenddecelerating?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiscrollviewdelegate/1619417-scrollviewdidenddecelerating?language=objc
