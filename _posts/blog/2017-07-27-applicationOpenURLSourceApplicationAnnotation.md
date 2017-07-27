---
layout: post
title: "application:openURL:sourceApplication:annotation:"
modified:
categories: blog
excerpt:
tags: [UIApplicationDelegate, Instance Method]
image:
feature:
date: 2017-07-27T23:15:00+09:00
---

**델리게이트에게 URL로 식별 된 리소스를 열도록 요청한다.**

---
> **더 이상 사용되지 않는 메서드**
>
> 이 메서드 대신에 application:openURL:options: 메서드를 사용해라.

### 파라미터
 - **application:** 싱글턴 앱 객체.
 - **url:** 보여주려고 하는 URL 리소스. 이 리소스는 네트워크 리소스 또는 파일이 될 수 있다. Apple에 등록 된 URL 체계에 대한 정보는 Apple URL Scheme Reference를 참조해라.
 - **sourceApplication:** URL을 열도록 앱을 요청하는 앱의 번들 ID.
 - **annotation:** 수신앱과 정보를 교환하기 위해 소스 앱이 제공하는 [프로퍼티 목록][property-list].

### 반환 값
델리게이트가 요청을 성공적으로 처리 한 경우 YES 또는 URL 리소스 열기 시도가 실패한 경우 NO를 반환한다.

### 설명
이 메소드를 구현하면 지정된 URL이 열리고 이에 따라 사용자 인터페이스가 업데이트된다. 앱을 실행하여 URL을 열어야하는 경우 앱은 willFinishLaunchingWithOptions: 및 application:didFinishLaunchingWithOptions: 메서드를 먼저 호출 한 후에 이 메소드를 호출한다. 앞에 언급한 메서드의 반환 값은 이 메서드가 호출되지 않도록하는 데 사용할 수 있다. 앱이 이미 실행 중이면 앞에 언급한 메서드가 불리지 않고 이 메서드 만 호출된다.

URL이 document interaction controller를 통해 열린 파일을 참조하는 경우 annotation parameter에는 URL과 함께 보내려고하는 소스 앱이 추가 데이터로 포함될 수 있다. 이 데이터의 형식은 전송 된 앱에 의해 정의되지만 데이터는 property list에 넣을 수있는 객체로 구성되어야 한다.

AirDrop 또는 document interaction controller를 통해 응용 프로그램에 전송 된 파일은 응용 프로그램의 홈 디렉토리에있는 Documents/Inbox 디렉토리에 저장된다. 앱이 디렉토리의 파일을 읽고 삭제할 수있는 권한이 있지만 쓰기 권한이 없다. 파일을 수정하려면 먼저 파일을 다른 디렉토리로 이동해야한다. 또한 해당 디렉토리의 파일은 일반적으로 데이터 보호를 사용하여 암호화된다. 이 메서드가 호출되기 전에 파일이 보호되고 사용자가 장치를 잠그면 파일의 내용을 즉시 읽을 수 없다. 이 경우 URL을 저장하고 나중에 이 메서드에서 NO를 반환하는 대신 파일을 열어봐라. app 객체의 [protectedDataAvailable][protectedDataAvailable] 속성을 사용하여 데이터 보호가 현재 활성화되어 있는지 확인한다.

이 메서드와 매칭되는 notification은 없다.

참고: [https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623073-application?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[protectedDataAvailable]: https://developer.apple.com/documentation/uikit/uiapplication/1622925-protecteddataavailable?language=objc

[property-list]: https://developer.apple.com/library/content/documentation/General/Conceptual/DevPedia-CocoaCore/PropertyList.html#//apple_ref/doc/uid/TP40008195-CH44

[apple-doc]: https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623073-application?language=objc