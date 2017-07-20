---
layout: post
title: "characterAtIndex:"
modified:
categories: blog
excerpt:
tags: [NSString, Instance Method]
image:
feature:
date: 2017-07-20T23:11:00+09:00
---

**지정된 UTF-16 코드 단위 인덱스의 문자를 반환한다.**

---
### 파라미터
 - **Index:** 검색 할 문자의 인덱스.

> **주의할 점**
>
> 만약에 인덱스가 수신자(문자열)의 길이를 넘으면 NSRangeException을 발생시킨다.

### 반환 값
배열의 인덱스에 해당하는 문자.

### 해설
이 메서드를 사용할 떄 rangeOfComposedCharacterSequenceAtIndex: 또는 rangeOfComposedCharacterSequencesForRange: 메서드를 사용하여 문자 경계를 결정해서 서러게이트 문자와 문자 클러스트가 올바르게 처리됩니다.

참고: [https://developer.apple.com/documentation/foundation/nsstring/1414645-characteratindex][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/foundation/nsstring/1414645-characteratindex