---
layout: post
title: "application:openURL:options:"
modified:
categories: blog
excerpt:
tags: [UIApplicationDelegate, Instance Method]
image:
feature:
date: 2017-07-29T00:03:00+09:00
---

**델리게이트에게 URL로 식별 된 리소스를 열도록 요청하고 launch option 딕셔너리를 제공한다.**

---

### 파라미터
 - **application:** 싱글턴 앱 객체.
 - **url:** 보여주려고 하는 URL 리소스. 이 리소스는 네트워크 리소스 또는 파일이 될 수 있다. Apple에 등록 된 URL 체계에 대한 정보는 [Apple URL Scheme Reference][Apple URL Scheme Reference]를 참조해라.
 - **options:** URL 처리옵션에 관한 dictionary 객체. 사용가능한 key와 이를 처리하는 방법에 대한 자세한 내용은 [UIApplicationOpenURLOptionsKey][UIApplicationOpenURLOptionsKey]를 참조해라. 기본적으로이 파라미터의 값은 빈 dictionary 객체이다.

### 반환 값
대리자가 요청을 성공적으로 처리 한 경우 YES, URL을 처리하려는 시도가 실패하면 NO를 반환한다.

### 설명
이 메서드는 willFinishLaunchingWithOptions: 및 application:didFinishLaunchingWithOptions: 메서드에서 모두 NO를 반환하면 호출되지 않는다. 만약에 두 메서드 중에 하나만 구현되 있을경우 구현된 메서드의 반환값에 따라서 이 메서드의 호출 여부가 결정된다. 만약에 application:didFinishLaunchingWithOptions: 메서드 대신에 applicationDidFinishLaunching: 메서드만 구현했다면 앱이 초기화되고 나서 이 메서드는 특정 URL을 열기 위해서 호출될 것이다. 

앱이 일시 중지되거나 백그라운드에서 실행되는 동안 URL이 도착하면이 메소드를 호출하기 전에 시스템이 앱을 포 그라운드로 이동시킨다.

이 메서드와 동일한 notification은 없다.

참고: [https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623112-application?preferredLanguage=occ][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Apple URL Scheme Reference]: https://developer.apple.com/library/content/featuredarticles/iPhoneURLScheme_Reference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007899

[UIApplicationOpenURLOptionsKey]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/uiapplicationopenurloptionskey?language=objc

[apple-doc]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623112-application?preferredLanguage=occ