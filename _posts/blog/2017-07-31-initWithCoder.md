---
layout: post
title: "initWithCoder:"
modified:
categories: blog
excerpt:
tags: [NSCoding, Instance Method]
image:
feature:
date: 2017-07-31T23:25:00+09:00
---

**필수 메서드** <br>
**주어진 언아카이버 데이터로 초기화된 객체를 반환한다.**

---

### 파라미터
 - **decoder:** 언아카이버 객체.

### 반환 값
decoder 데이터를 사용하여 초기화된 객체(self)

### 설명
일반적으로 initWithCoder: 에서 self를 반환한다. 디코딩 후에 다른 객체로 대체해야하는 경우 awakeAfterUsingCoder:에서 작업을 수행 할 수 있다.

참고: [https://developer.apple.com/documentation/foundation/nscoding/1416145-initwithcoder][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/foundation/nscoding/1416145-initwithcoder