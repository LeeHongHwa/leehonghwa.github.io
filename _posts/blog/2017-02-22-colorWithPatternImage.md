---
layout: post
title: "colorWithPatternImage:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIColor, instance method]
image:
  feature:
date: 2017-02-22T22:51:00+09:00
---
**특정한 이미지를 사용하여 색상 객체를 만들고 반환한다.**

----
### 파라미터
image: 패턴 색상을 만들 때 사용할 이미지

### 리턴
패턴 색상

### 해설
패턴 색상을 사용하여 단색으로 면이나 선을 채울 수 있다.
그리는 동안 주어진 영역을 덮기 위해 필요한 만큼 패턴 색상의 이미지가 타일처럼 붙여진다.
기본적으로 반환되는 색상의 phase는 0이다. 0은 이미지의 왼쪽 위 모퉁이부터 그려진다는 것을 뜻한다.
색상을 현재 색상으로 만들고 나서 CGContextSetPatternPhase 메서드를 사용하면 phase를 변경할 수 있다.

참고: [https://developer.apple.com/reference/uikit/uicolor/1621935-colorwithpatternimage][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uicolor/1621935-colorwithpatternimage