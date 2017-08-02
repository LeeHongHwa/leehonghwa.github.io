---
layout: post
title: "application:didFinishLaunchingWithOptions:"
modified:
categories: blog
excerpt:
tags: [UIApplicationDelegate, Instance Method]
image:
feature:
date: 2017-08-02T22:30:00+09:00
---

**델리게이트에게 실행 프로세스가 거의 완료되었으며 앱 실행 준비가 거의 완료되었음을 알린다.**

---

### 파라미터
 - **application:** 싱글턴 앱 객체.
 - **launchOptions:** 값이 있다면 앱이 시작된 이유에 대한 dictionary 정보를 가지고 있다. 사용자가 앱을 직접 시작한 경우 이 값은 아마도 빈값일 것이다. 값에 접근 가능한 키 그리고 처리하는 방법에 대한 자세한 내용은 [Launch Options Keys][Launch Options Keys]를 참고해라.

### 반환 값
앱이 URL 리소스를 처리할 수 ​​없거나 사용자의 작업을 처리할 수 없으면 NO, 그렇지 않으면 YES를 반환한다. 원격 알림(APNs)의 결과로 앱이 실행되면 반환 값은 무시된다.

### 개요
이 메서드 (및 willFinishLaunchingWithOptions:메서드)를 사용하여 앱의 초기화를 완료하고 마지막으로 앱에 대한 어떠한 설정을 수정 및 작성할 수 있다. 이 메서드는 상태 복원 후 앱의 윈도우 및 기타 UI가 표시되기 전에 호출된다. 이 메서드에서 반환값이 반환된 후 어느 시점에서 시스템은 다른 델리게이트 메서드를 호출하여 앱을 활성 상태(foreground) 또는 background 상태로 이동시킨다.

이 메서드는 launchOptions dictionary에 대한 정보를 받아 처리할 마지막 기회이다. 응용 프로그램에서 willFinishLaunchingWithOptions: 메서드에서 이에 대한 처리를 하지 않는다면 이 메서드에서 적절한 처리를 해야 한다.

앱 델리게이트가 아닌 객체는 이 메서드가 반환값을 반환하고 나서 UIApplicationDidFinishLaunchingNotification을 관찰할 수 있다. 그리고 그 notification의 userInfo에서 launchOptions에 대한 값을 받아볼 수 있다.

> **중요한 점**
>
> 앱을 초기화하려면 applicationDidFinishLaunching: 메서드는 오래된 버전에서만 실행되기 때문에 이 메서드와application:willFinishLaunchingWithOptions: 메서드를 사용하는 것이 좋다.

이 메서드의 반환 값과 application:willFinishLaunchingWithOptions: 메서드의 반환값이 결합되어 URL의 처리 여부를 결정한다. 두 메서드 중 하나가 NO를 리턴하면 URL은 처리되지 않는다. 메서드 중 하나를 구현하지 않으면 구현된 메서드의 반환 값만 고려된다.

참고: [https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622921-application?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Launch Options Keys]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/launch_options_keys?language=objc

[apple-doc]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622921-application?language=objc