---
layout: post
title: "sizeWithAttributes:"
modified:
categories: blog
excerpt:
tags: [NSString, Instance Method]
image:
  feature:
date: 2017-06-13T00:03:00+09:00
---
**지정된 속성으로 그려졌을때, 수신자가 차지하는 사각형 사이즈를 반환한다.**
---
### 파라미터
 - **attrs:** 문자열에 적용 할 텍스트 속성 dictionary. 이 dictionary는 NSAttributedString 객체에 적용될 수있는 것과 동일한 속성이지만 NSString 객체의 경우 속성은 문자열 내의 범위가 아닌 전체 문자열에 적용된다.

### 반환 값
지정된 속성으로 그릴 때 수신자가 차지하는 사각형 사이즈.

### 해설
이 메서드는 소수 크기를 반환합니다. 뷰의 크기를 조절하기 위해서 반환된 크기를 사용하려면 ceil 함수를 사용하여 가장 가까운 정수로 값을 올림해야 한다.

참고: [https://developer.apple.com/documentation/foundation/nsstring/1531844-sizewithattributes?preferredLanguage=occ][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/foundation/nsstring/1531844-sizewithattributes?preferredLanguage=occ