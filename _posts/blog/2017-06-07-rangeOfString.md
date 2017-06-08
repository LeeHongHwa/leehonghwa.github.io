---
layout: post
title: "rangeOfString:"
modified:
categories: blog
excerpt:
tags: [NSString, Instance Method]
image:
  feature:
date: 2017-06-07T22:55:00+09:00
---
**수신자에 지정된 문자열의 첫 번째 부분( 문자열에 여러 부분이 있어도 처음부분만)의 범위를 찾아 반환한다.**

---
### 파라미터
 - **searchString:** 검색 할 문자열.

### 반환 값
NSRange 구조체는 파라미터와 일치한 첫 번째 부분의 위치와 길이를 제공한다.
파라미터와 같은 문자열을 찾을 수 없거나 파라미터가 빈 문자라면("") {NSNotFound, 0}을 반환한다.

### 해설
angeOfString : options : 에서 옵션 없이 실행한다.
NSString 객체는 Unicode canonical equivalence of their code point sequences 를 검사하여 비교된다. 동등한 구성된 문자 시퀀스가 일치하는 경우 반환 된 범위의 길이와 파라미터의 범위가 다를 수 있다.

> **중요한 점**
>
> 사용자에게 제공되는 텍스트로 작업 할 때 이 메서드 대신에 [localizedStandardRangeOfString:][localizedStandardRangeOfString:] 메서드를 사용해라.

참고: [https://developer.apple.com/documentation/foundation/nsstring/1410144-rangeofstring][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[localizedStandardRangeOfString:]: https://leehonghwa.github.io/blog/blog/localizedStandardRangeOfString/
[apple-doc]: https://developer.apple.com/documentation/foundation/nsstring/1410144-rangeofstring