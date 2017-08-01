---
layout: post
title: "awakeFromNib"
modified:
categories: blog
excerpt:
tags: [NSObject, Instance Method]
image:
feature:
date: 2017-08-01T22:25:00+09:00
---

**수신자가 Interface Builder archive또는 nib 파일에서 로드 된 후 서비스(사용)를 준비한다.**

---

### 개요
nib 로딩 인프라는 각 객체(nib 아카이브에서 다시 만들어진 객체)에 awakeFromNib 메시지를 전송하지만 아카이브의 모든 객체가 로드되고 초기화된 후에 만 메시지를 받을 수 있다. 객체가 awakeFromNib 메시지를 받았다면, 모든 outlet과 액션 연결이 이미 설정되어있는 것이 보장된다.

awakeFromNib의 부모의 구현을 호출하여 부모 클래스에 필요한 추가 초기화를 수행할 수 있는 기회를 제공해야 한다. 이 메서드의 기본 구현은 아무것도 하지 않지만 많은 UIKit 클래스는 기본 구현이 아닌 추가적인 다른 구현을 제공한다. awakeFromNib 메서드 구현에서 임의의 시점에서 슈퍼 구현을 호출할 수 있다.

> **주의할 점**
>
> Interface Builder의 테스트 모드에서 이 메시지는 로드 된 Interface Builder 플러그인에서 인스턴스화된 객체로 전송된다. 플러그인 링크는 객체를 정의하는 코드를 포함한 프레임워크와 다르기 때문에 객체가 정의된 후에 인터페이스 빌더는 awakeFromNib 메서드를 호출할 수 있다. Xcode 프로젝트 용으로 사용자가 만든 custom 객체도 마찬가지이다. Interface Builder는 해당 객체의 정의된 아웃렛과 액션에 대해서만 알고 있다. 실제 코드에 대한 접근 권한이 없다.

인스턴스화 프로세스 중에 아카이브의 각 객체는 아카이브 된 것을 해제하지 않고 유형에 적합한 메서드로 초기화된다. UIView 및 UIViewController의 모든 하위 클래스를 포함하여 NSCoding 프로토콜을 준수하는 모든 객체는 initWithCoder : 메서드를 사용하여 초기화된다. NSCoding 프로토콜을 따르지 않는 모든 객체는 그들의 init 메서드를 사용하여 초기화된다. 모든 객체가 인스턴스화되고 초기화된 후, nib 파일을 불러오는 코드는 outlet을 다시 설정하고 다른 객체와 액션 연결을 다시 설정한다. 그런 다음 객체의 awakeFromNib 메서드를 호출합니다. Nil 파일을 로딩하는 과정에 대한 정보를 더 보고 싶다면 Nib Files in Resource Programming Guide을 참고해라.

> **중요한 점**
>
> 아카이브에서 객체가 인스턴스화되는 순서는 보장되지 않으므로 초기화 메서드가 계층의 다른 객체에 메시지를 보내면 안 된다. 다른 객체에 대한 메시지는 awakeFromNib 메서드 내에서 안전하게 보낼 수 있다.

일반적으로 awakeFromNib는 디자인 타임에 수행할 수없는 추가 설정이 필요한 객체에 구현한다. 예를 들어 사용자가 설정한 기본값을 지정하기 위해 또는 다른 컨트롤의 값과 연결하기 위해 이 메서드를 사용할 수 있다. 또한 개별 컨트롤을 응용 프로그램의 이전 상태로 복원하는 데 사용할 수도 있다.

참고: [https://developer.apple.com/documentation/objectivec/nsobject/1402907-awakefromnib?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/objectivec/nsobject/1402907-awakefromnib?language=objc