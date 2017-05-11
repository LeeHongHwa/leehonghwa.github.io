---
layout: post
title: "addSubview:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-04-04T23:00:00+09:00
---
**수신자의 하위 뷰 리스트 중 마지막에 뷰를 추가한다.**

----
### 해설
이 메서드는 뷰에게 강한 참조를 설정하며 다음 응답자를 수신자(뷰의 새로운 상위 뷰)로 설정한다.
뷰는 하나의 상위 뷰를 가질 수 있다. 만약에 이미 뷰가 상위 뷰를 가지고 있고 뷰가 수신자가 아닌 경우 이 메서드는 이전에 등록된 슈퍼 뷰를 제거한 뒤에 수신자를 뷰의 새로운 상위 뷰로 만든다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622616-addsubview?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622616-addsubview?language=objc
