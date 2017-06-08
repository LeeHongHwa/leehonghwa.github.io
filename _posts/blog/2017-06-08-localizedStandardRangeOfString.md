---
layout: post
title: "localizedStandardRangeOfString:"
modified:
categories: blog
excerpt:
tags: [NSString, Instance Method]
image:
  feature:
date: 2017-06-08T23:20:00+09:00
---
**대소문자를 구별하지 않고 locale-aware search를 수행하여 수신자 문자열의 첫 번째 부분 부터 발생 범위를 찾아 반환한다. 같은 부분이 두 부분 이상 이라면 첫번째 부분의 범위만 반환됨.**

---
### 파라미터
 - **str:** 검색할 문자열. 이 파라미터는 nil이면 안된다.

### 반환 값
수신자 문자열에 파라미터와 같은 문자열이 있다면 해당하는 범위를 반환하고 그렇지 않다면 {NSNotFound, 0}를 반환한다.

참고: [https://developer.apple.com/documentation/foundation/nsstring/1413574-localizedstandardrangeofstring?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/foundation/nsstring/1413574-localizedstandardrangeofstring?language=objc