---
layout: post
title: "CGAffineTransform"
modified:
categories: blog
excerpt:
tags: [Core Graphics]
image:
  feature:
date: 2017-05-25T22:27:00+09:00
---
**2D 그래픽을 그리는 데 사용하는 아핀 변환 행렬.**

----
### 해설
변환은 한 좌표의 점을 다른 좌표의 점에 매핑하는 방법을 지정한다. 아핀 변환은 경로에서 평행선을 유지하지만 길이 또는 각도를 유지하는 것이 필수는 아닌 특별한 유형의 매핑이다. 스케일링, 회전 및 변환은 아핀 변환에서 지원되는 가장 일반적으로 사용되는 조작이지만 기울임도 가능하다.

아핀 변환을 생성, 연결 및 적용하는 방법에 대한 자세한 내용은 [Quartz 2D Programming Guide][Quartz 2D Programming Guide]를 참고해라.

일반적으로 아핀 변환을 직접 생성 할 필요는 없다. CGContext는 현재 아핀 변환을 수정하는 함수를 가지고 있다. 아핀 변환을 재사용하지 않으려면 CGContextScaleCTM, CGContextRotateCTM, CGContextTranslateCTM 또는 CGContextConcatCTM을 사용해라.

참고: [https://developer.apple.com/reference/coregraphics/cgaffinetransform-rb5?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Quartz 2D Programming Guide]: https://developer.apple.com/reference/coregraphics/cgaffinetransform-rb5?language=objc
[apple-doc]: https://developer.apple.com/reference/coregraphics/cgaffinetransform-rb5?language=objc