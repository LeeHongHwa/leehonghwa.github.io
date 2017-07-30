---
layout: post
title: "application:handleOpenURL:"
modified:
categories: blog
excerpt:
tags: [UIApplicationDelegate, Instance Method]
image:
feature:
date: 2017-07-30T22:30:00+09:00
---

**델리게이트에게 URL로 식별 된 리소스를 열도록 요청한다.**

---
> **더 이상 사용되지 않는 메서드**
>
> 이 메서드 대신에 [application:openURL:options:][application:openURL:options:] 메서드를 사용해라.

### 파라미터
 - **application:** 싱글턴 앱 객체.
 - **url:** URL (Universal Resource Locator)을 나타내는 객체. Apple에 등록 된 URL 체계에 대해서는 [App Programming Guide for iOS 부록][App Programming Guide for iOS 부록]을 참조해라.

### 반환 값
대리자가 요청을 성공적으로 처리 한 경우 YES, URL을 처리하려는 시도가 실패하면 NO를 반환한다

### 설명
만약에 [application:openURL:sourceApplication:annotation:][application:openURL:sourceApplication:annotation:] 메서드를 구현했다면 이 메서드 대신에 [application:openURL:sourceApplication:annotation:][application:openURL:sourceApplication:annotation:]메서드가 호출된다. 

이 메서드는 대리자에서 willFinishLaunchingWithOptions: 및 application:didFinishLaunchingWithOptions: 메서드에서 모두 NO를 반환하면 호출되지 않는다. 만약에 두 메서드 중에 하나만 구현되 있을경우 구현된 메서드의 반환값에 따라서 이 메서드의 호출 여부가 결정된다. 만약에 application:didFinishLaunchingWithOptions: 메서드 대신에 applicationDidFinishLaunching: 메서드만 구현했다면 앱이 초기화되고 나서 이 메서드는 특정 URL을 열기 위해서 호출될 것이다. 

앱이 일시 중지되거나 백그라운드에서 실행되는 동안 URL이 도착하면이 메소드를 호출하기 전에 시스템이 앱을 포 그라운드로 이동시킨다.

이 메서드와 동일한 notification은 없다.

참고: [https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622964-application?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[application:openURL:options:]: https://leehonghwa.github.io/blog/applicationOpenURLOptions/

[App Programming Guide for iOS 부록]: https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007072

[application:openURL:sourceApplication:annotation:]: https://leehonghwa.github.io/blog/applicationOpenURLSourceApplicationAnnotation/

[apple-doc]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622964-application?language=objc