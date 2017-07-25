---
layout: post
title: "NSURLCache"
modified:
categories: blog
excerpt:
tags: [Foundation, URL Loading System, Class]
image:
feature:
date: 2017-07-25T00:20:00+09:00
---

**URL 요청을 캐시된 응답 객체와 연결해주는 객체.**

---

### 개요
NSURLCache 클래스는 NSURLRequest 객체를 NSCachedURLResponse에 매핑하여 URL로드 요청에 대한 응답에 대한 캐싱을 구현한다. NSURLCache 클래스는 복합 메모리 및 디스크 캐시를 제공하며 메모리 및 디스크상의 크기를 모두 조작 할 수 있다. 캐시 데이터가 지속적으로 저장되는 경로를 제어 할 수도 있다.

> **주의할 점**
>
> iOS에서 앱이 실행되지 않고 있을때 기기의 디스크 공간이 부족하다면 시스템이 디스크 캐시를 제거 할 수 있다.

### 스레드 안전성
iOS 8 이상 및 macOS 10.10 이상에서는 NSURLCache가 스레드로부터 안전하다. 동시에 NSURLCache 인스턴스 메소드가 여러 실행 컨텍스트에서 안전하게 호출 될 수 있지만 cachedResponseForRequest: 그리고 storeCachedResponse:forRequest: 같은 메소드는 동일한 요청에 대한 응답을 읽거나 쓰려고 시도 할 때 피할 수없는 경쟁 조건을 가지고 있음을 알고 있어야 한다. NSURLCache의 하위 클래스는 NSURLCache의 스레드 안전성과 같은 방식으로 오버라이드 된 메소드를 구현해야 한다.

참고: [https://developer.apple.com/documentation/foundation/nsurlcache][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/foundation/nsurlcache