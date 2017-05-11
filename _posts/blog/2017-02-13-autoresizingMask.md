---
layout: post
title: "autoresizingMask"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView,instance property]
image:
  feature:
date: 2017-02-13T23:25:00+09:00
---
**상위 뷰의 bounds가 변형될 때 수신자가 어떻게 크기를 변경할 것인가 결정하는 정수 비트 마스크**

----
### 해설
뷰의 bounds가 변형될 때 변형된 뷰는 각각의 하위 뷰의 autoresizing mask에 따라 하위 뷰의 사이즈를 재조정한다. UIViewAutoresizing에 작성된 상수를 c비트 or연산자를 사용해 조합하여 이 마스크의 값을 지정해라. 조합된 이 상수는 상위 뷰에 따라 뷰의 크기가 커지거나 줄어들거나를 명시해준다. 이 프로퍼티의 기본값은 UIViewAutoresizingNone이고 이것은 뷰가 사이즈를 재조정하지 않는다는 것을 명시해 준다.

같은 축을 따라 여러 옵션이 설정되어있는 경우에는 flexible 한 부분에 비례한 크기의 차이를 분배한다. 다른 flexible 한 부분보다 더 flexible 한 부분은 더 커질 것이다. 예를 들어 이 프로퍼티가 UIViewAutoresizingFlexibleLeftMargin 상수 값은 포함이 되어있지않고 UIViewAutoresizingFlexibleWidth 와 UIViewAutoresizingFlexibleRightMargin상수의 값이 지정돼있다면 뷰의 왼쪽 여백은 고정돼있고 뷰의 크기와 오른쪽 여백만이 변화할것이다. 따라서 뷰의 넓이 그리고 뷰의 오른쪽 여백이 증가하는 동안 뷰는 상위 뷰의 왼쪽에 고정되어 있는다.

만약에 autoresizing의 행동이 원하는 데로 정교한 배치를 제공하지 않는다면 custom container view를 사용하고 layoutSubviews메서드를 사용하면 좀 더 정확하게 하위 뷰들을 배치할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622559-autoresizingmask?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622559-autoresizingmask?language=objc
