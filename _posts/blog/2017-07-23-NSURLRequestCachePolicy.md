---
layout: post
title: "NSURLRequestCachePolicy"
modified:
categories: blog
excerpt: 캐시된 응답을 처리하는 방법을 나타내는 상수.
tags: [NSURLRequest, Enumeration]
image:
feature:
date: 2017-07-23T17:50:00+09:00
---

**캐시된 응답을 처리하는 방법을 나타내는 상수.**

---

### 개요
HTTP 프로토콜의 경우 NSURLRequestUseProtocolCachePolicy 정책의 동작이 NSURLRequest에서 일어난다.

**그림 1**<br>
HTTP 및 HTTPS에 대한 NSURLRequestUseProtocolCachePolicy 의사 결정 트리

<figure>
	<img src="/images/NSURLRequestCachePolicy.png" alt="NSURLRequestCachePolicy이 NSURLRequest에서 실행되는 것을 설명하는 이미지">
</figure>

**간단히 말하면**<br>

1. 요청에 대해 캐시 된 응답이 존재하지 않으면 URL loading system이 원본 소스에서 데이터를 가져온다.

2. 캐시 된 응답이 매번 유효성을 다시 확인해야 하지 않고 캐시 된 응답이 만료 날짜를 지나지 않고 유효한 응답이라면 URL loading system에서 캐시 된 응답을 반환한다.

3. 캐시 된 응답이 유효하지 않거나 유효성 검사가 필요한 경우 URL loading system은 원본 소스에 HEAD 요청을 보내 리소스가 변경되었는지 확인한다.  리소스가 변경되었다면 URL loading system은 원본 소스에서 데이터를 가져온다. 리소스가 변경되어 있지 않다면 캐시 된 응답을 리턴한다.

RFC 2616, 섹션 13 ([http://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html#sec13][w3])에서는 이러한 의미를 자세히 설명한다.

참고: [https://developer.apple.com/documentation/foundation/nsurlrequestcachepolicy][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[w3]: https://www.w3.org/Protocols/rfc2616/rfc2616-sec13.html#sec13
[apple-doc]: https://developer.apple.com/documentation/foundation/nsurlrequestcachepolicy