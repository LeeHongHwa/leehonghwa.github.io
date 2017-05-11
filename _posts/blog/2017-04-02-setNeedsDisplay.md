---
layout: post
title: "setNeedsDisplay"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, instance method]
image:
  feature:
date: 2017-04-02T21:57:20+09:00
---
**수신자의 전체 bounds 사각형을 다시 그려야한다고 표시한다.**

----
### 해설
시스템에게 뷰의 contents 가 다시 그려질 필요가 있다고 알리기 위해 사용자는 이 메서드를 사용하거나 setNeedsDisplayInRect: 메서드를 사용할 수 있다. 이 메서드는 요청을 기록한 후 즉시 리턴합니다. 뷰는 다음 드로잉 사이클까지 실제로 다시 그려지지 않는다. 이 시점에서 모든 무효화된 뷰가 업데이트 된다.

**중요한 점** <br>
만약에 CAEAGLLayer 객체의 뒤에 있다면 이 메서드는 아무런 효과가 없다. content를 그리기 위해 UIKit이나 Core Graphic같은 native 드로잉 기술 사용한다.

뷰의 모양 또는 content가 변경될 때 다시 뷰가 다시 그려지는 것을 요청하기 위해서 이 메서드를 사용한다. 만약 뷰의 간단한 기하학 적인 변화가 일어 난다면 이 메서드는 일반적으로 뷰를 다시 그리지 않는다. 대신에 뷰의 contentMode 프로퍼티의 값에 따라 기존의 content가 조정된다. 기존의 content를 다시 보여주는 것은 변화하지 않은 content를 다시 그리는 필요가 없어 성능을 향상시킨다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622437-setneedsdisplay?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622437-setneedsdisplay?language=objc