---
layout: post
title: "NSURLSessionConfiguration"
modified:
categories: blog
excerpt: 캐시된 응답을 처리하는 방법을 나타내는 상수.
tags: [Foundation, URL Loading System, Class]
image:
feature:
date: 2017-07-24T23:20:00+09:00
---

**configuration 객체는 NSURLSession 객체를 사용하여 데이터를 업로드하거나 다운로드 할 때 사용할 정책 및 행동을 나타낸다.**

---

### 개요
이 객체를 사용하여 session 객체를 초기화하기 이전에 NSURLSessionConfiguration 객체를 설정하는 것이 중요하다. session 객체는 사용자가 제공 한 NSURLSessionConfiguration 객체의 사본을 만들고 해당 설정을 사용하여 session을 설정한다. session 객체가 설정되면 이후에 NSURLSessionConfiguration 객체에 대한 모든 변경 사항이 생겼을 경우 변경 사항을 무시한다. 만약에 설정을 변경하려면 NSURLSessionConfiguration 객체를 update해서 새로운 NSURLSession 객체 만들어야한다.

> **주의할 점**
>
> NSURLRequest의 task에 설정된 정책이 이 객체로 설정된 설정들을 변경할 수 있다. session의 정책이 제한적이지 않다면 request 객체에 지정된 설정이 우선순위가 될 수 있다. 제한 적인 것을 예를 들자면 session 설정에서 셀룰러 네트워킹이 허용되어서 안된다고 지정된 경우 NSURLRequest 객체는 셀룰러 네트워킹을 요청할 수 없다.

configuration 객체에 대한 정보를 얻으려면 [NSURLSession][NSURLSession]을 참고해라.

참고: [https://developer.apple.com/documentation/foundation/nsurlsessionconfiguration][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[NSURLSession]: https://developer.apple.com/documentation/foundation/nsurlsession?language=objc
[apple-doc]: https://developer.apple.com/documentation/foundation/nsurlsessionconfiguration