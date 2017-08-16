---
layout: post
title: "scrollViewDidScroll"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-02-11T22:47:00+09:00
---
**수신자의 현재 배치를 무효화하고 다음에 배치가 update될 때 재배치하게 실행한다.**

----
### 해설
하위 뷰의 레이아웃을 조정하기 위해 메인 스레드에서 이 메서드를 호출해라. 이 메서드는 요청을 기록하고 즉시 반환한다. 
이 메서드는 즉시 업데이트를 적용하는 것이 아니고 다음 업데이트 주기가 될 때까지 기다린다. 그로 인해 뷰들의 레이아웃을 업데이트하기 이전에 뷰들의 레이아웃을 무효화할 수 있다. 
이로 인해 모든 레이아웃 업데이트를 하나의 업데이트 주기에 통합할 수 있다. 이러한 점은 보통 성능 향상에 도움을 준다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622601-setneedslayout?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622601-setneedslayout?language=objc