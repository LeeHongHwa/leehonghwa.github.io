---
layout: post
title: "NSCharacterSet"
modified:
categories: blog
excerpt:
tags: [Foundation, NSCharacterSet, Class]
image:
  feature:
date: 2017-06-04T18:20:00+09:00
---
**NSCharacterSet 객체는 유니 코드 호환 문자 집합을 나타낸다. NSString, NSScanner 객체는 NSCharacterSet 객체를 사용하여 문자를 그룹화하여 검색 작업을 수행하고 검색 중에 특정 문자 집합을 찾을 수 있다. 클러스터의 두 공용 클래스 인 NSCharacterSet과 NSMutableCharacterSet은 정적 및 동적 문자 집합에 대한 프로그래밍 방식 인터페이스를 각각 선언한다.**

---
### 해설
이 클래스를 사용하여 생성 한 객체를 character set objects라고 한다.(혼동이 생기지 않는 경우 character sets라고 한다.). 클래스 클러스터의 성격 때문에 character set objects는 NSCharacterSet 또는 NSMutableCharacterSet 클래스의 실제 인스턴스가 아니라 그들의 private한 하위 클래스 중 하나의 객치이다. 문자 집합 객체의 클래스는 private이지만 인터페이스는 public이며 NSCharacterSet 및 NSMutableCharacterSet과 같은 추상 상위 클래스로 선언된다. character set objects는 NSCopying 및 NSMutableCopying 프로토콜을 채택했기 때문에 복사하는 것이 편하다.

NSCharacterSet 클래스의 객체는 유니 코드 문자 집합을 관리하며 프로그래밍 인터페이스를 선언한다.(유니 코드에 대한 정보는 [NSString][NSString] 클래스 클러스터 사양 참조해라). NSCharacterSet의 기본 원시 메소드 인 characterIsMember: 는 인터페이스의 다른 모든 인스턴스 메소드에 대한 기초를 제공한다. NSCharacterSet의 하위 클래스는 적절한 동작을 위해이 메소드와 mutableCopyWithZone 을 구현해야 한다. 최적의 성능을 위해, 하위 클래스는 bitmapRepresentation을 override 해야한다. 그렇지 않으면 모든 유니 코드 값에 characterIsMember: 가 작동한다.

NSCharacterSet은 Core Foundation의 CFCharacterSetRef와 함께 "toll-free bridged"이다. toll-free bridged에 대한 자세한 내용은 [toll-free bridged][toll-free bridged]을 참조해라.

> **Swift Foundation Overlay**
>
> Foundation 프레임 워크에 대한 스위프트 오버레이는 NSCharacterSet 클래스와 해당 가변 하위 클래스 인 NSMutableCharacterSet에 연결되는 CharacterSet 구조를 제공한다. CharacterSet 값 타입은 NSCharacterSet reference type과 동일한 기능을 제공하며 두 가지는 Objective-C API와 상호 작용하는 Swift 코드에서 서로 바꿔서 사용할 수 있다. 이 동작은 Swift가 표준 문자열, 숫자 및 컬렉션 유형을 해당 Foundation 클래스에 연결하는 방법과 유사하다.

값 유형에 대한 자세한 내용은 The Swift Programming Language (Swift 3.1)에서 [Classes and Structures][Classes and Structures]와 Using Swift with Cocoa and Objective-C (Swift 3.1)에서[Working with Cocoa Frameworks][Working with Cocoa Frameworks]참고해라.

참고: [https://developer.apple.com/reference/foundation/nscharacterset?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[NSString]: https://developer.apple.com/reference/foundation/nsstring?language=objc
[toll-free bridged]: https://developer.apple.com/library/content/documentation/General/Conceptual/CocoaEncyclopedia/Toll-FreeBridgin/Toll-FreeBridgin.html#//apple_ref/doc/uid/TP40010810-CH2
[Classes and Structures]: https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13
[Working with Cocoa Frameworks]: https://developer.apple.com/library/content/documentation/Swift/Conceptual/BuildingCocoaApps/WorkingWithCocoaDataTypes.html#//apple_ref/doc/uid/TP40014216-CH6
[apple-doc]: https://developer.apple.com/reference/foundation/nscharacterset?language=objc