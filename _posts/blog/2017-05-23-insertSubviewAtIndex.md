---
layout: post
title: "insertSubview:atIndex:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, Instance Method]
image:
  feature:
date: 2017-05-23T23:30:00+09:00
---
**지정한 인덱스에 하위 뷰를 삽입한다.**

----
### 파라미터
 - **view:** 삽입할 뷰. 이 값은 nil이 될 수 없다.
 - **index:** 뷰를 삽입 할 subviews 속성의 배열에있는 인덱스. subview 인덱스는 0에서 시작하여 subviews수 보다 클 수 없다.

### 해설
이 메서드는 뷰에게 강한 참조를 설정하고 다음 responder를 receiver(새로운 상위 뷰)로 설정한다.

뷰는 상위 뷰를 하나 밖에 가질 수 없다. 뷰가 이미 상위 뷰를 가지고 있고 그 상위 뷰가 receiver가 아니라면 이 메서드는 receiver를 새로운 상위 뷰로 설정하기 전에 이전에 설정된 상위 뷰를 삭제한다.

참고: [https://developer.apple.com/reference/uikit/uiview/1622538-insertsubview?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622538-insertsubview?language=objc