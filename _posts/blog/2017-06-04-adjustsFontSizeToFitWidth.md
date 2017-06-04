---
layout: post
title: "adjustsFontSizeToFitWidth"
modified:
categories: blog
excerpt:
tags: [UIKit, UILabel, Instance Property]
image:
  feature:
date: 2017-06-04T18:16:00+09:00
---
**제목 문자열을 label의 사각형 bound에 맞추기 위해 폰트 크기를 줄여야하는지에 대한 여부를 나타내는 부울 값.**

---
### 해설
일반적으로 레이블 텍스트는 font 프로퍼티에서 지정한 글꼴로 그려진다. 이 프로퍼티를 YES로 설정하고 text 프로퍼티의 text가 label의 사각형 bound를 초과하는 경우 label은 문자열이 그 크기에 맞을 때까지 또는 최소 글꼴 크기에 도달 할 때까지 글꼴 크기를 줄인다.이 프로퍼티의 기본값은 NO이다. YES로 변경하면 minimumScaleFactor 프로퍼티를 수정하여 적절한 최소 글꼴 크기도 설정해야한다.

참고: [https://developer.apple.com/reference/uikit/uilabel/1620546-adjustsfontsizetofitwidth?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uilabel/1620546-adjustsfontsizetofitwidth?language=objc