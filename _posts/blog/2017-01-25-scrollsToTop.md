---
layout: post
title: "scrollsToTop"
modified:
categories: blog
excerpt:
tags: [UIKit, UIScrollView, instance property]
image:
  feature:
date: 2017-01-25T23:21:00+09:00
---
**scroll-to-top 제스처를 사용할 수 있는지 없는지를 관리하는 Boolean 값**

----
### 해설
scroll-to-top 제스처는 상태 바를 탭 하는 제스처를 뜻한다. 사용자가 이러한 제스처를 했을때 시스템은 상태 바 가장 가까이에 있는 스크롤 뷰에게 상단으로 스크롤하라고 요청한다. 만약에 스크롤 뷰의 scrollsToTop 프로퍼티의 값이 NO로 설정되어 있다면 스크롤 뷰의 delegate는 scrollViewShouldScrollToTop:메서드에서 NO를 반환한다. 또는 content가 이미 상단에있는 경우 어떠한 일도 일어나지 않는다.

스크롤 뷰가 컨텐츠 뷰의 상단으로 스크롤 한 후 스크롤 뷰는 delegate에게 scrollViewDidScrollToTop: 메서드 메시지를 보낸다.

scrollsToTop 프로퍼티의 기본값은 YES이다.

### 주의사항
아이폰에서 화면에 한 개 이상의 스크롤 뷰를 가지고 있다면 scrollsToTop 프로퍼티의 값이 YES로 설정되어 있어도 scroll-to-top 제스처를 사용할 수 없다.

참고: [https://developer.apple.com/reference/uikit/uiscrollview/1619421-scrollstotop?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiscrollview/1619421-scrollstotop?language=objc