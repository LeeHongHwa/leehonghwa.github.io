---
layout: post
title: "boundingRectWithSize:options:attributes:context:"
modified:
categories: blog
excerpt:
tags: [UIKit, NSString, Instance Method]
image:
  feature:
date: 2017-06-01T23:22:00+09:00
---
**지정된 그래픽 환경의 지정된 사각형 내에서 주어진 옵션 및 display 특성을 사용하여 그려진 리시버(문자열)에 대한 bounding rect를 계산하여 반환한다.**

----
### 파라미터
 - **size:** 사각형 사이즈.
 - **options:** 문자열을 그리는 옵션.
 - **attributes:** 문자열에 적용된 문자 속성에 관한 딕셔너리. 이 속성은 NSAttributedString 객체에 적용될 수 있는 속성과 동일하지만 NSString 객체의 경우 속성은 문자열 내의 범위가 아닌 전체 문자열에 적용된다.
 - **context:** 수신자가 사용할 문자열 드로잉 환경이며 minimum scale factor 및 tracking adjustments 을 지정한다.

### 반환 값
주어진 옵션과 display 특성을 사용하여 그려진 수신자의 bounding rect. 이 메서드로부터 반환받은 Rect의 origin은 0, 0이다.

### 해설
줄 수가 많은 텍스트를 정확하게 그리고 크기를 알아내려면 options 파라미터에 NSStringDrawingUsesLineFragmentOrigin을 전달해라.

이 메서드는 반환된 CGRect의 크기 구성 요소에서 float 크기를 반환한다. 반환된 크기를 이용해 뷰의 사이즈를 재조정해주려면 ceil 함수를 사용하여 가장 가까운 정수로 값을 올려야 한다.

이 메서드는 문자열의 문자의 실제 bounds를 반환한다. 문자의 일부(예:공백)는 전달된 파라미터의 레이아웃 제약 조건과 겹칠 수 있으므로 반환된 CGRect의 너비 값이 size 파라미터의 너비 값을 초과할 수 있다.

참고: [https://developer.apple.com/reference/foundation/nsstring/1524729-boundingrectwithsize][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/foundation/nsstring/1524729-boundingrectwithsize