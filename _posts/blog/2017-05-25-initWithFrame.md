---
layout: post
title: "initWithFrame:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIView, Instance Method]
image:
  feature:
date: 2017-05-25T21:40:00+09:00
---
**지정된 사각형 프레임을 사용하여 새로 할당 된 뷰 객체를 초기화하고 반환한다.**

----
### 파라미터
 - **frame:** 뷰의 사각형 프레임 (포인트 단위). 프레임의 좌표는 추가 하려고 하는 슈퍼 뷰에서의 상대적인 좌표이다. 이 메서드는 사각형 프레임을 사용하여 그에 따라 center 프로퍼티와 bounds 프로퍼티를 설정한다.

### 반환 값
초기화 된 뷰 객체

### 해설
새로운 뷰 객체는 사용하기 전에 윈도우의 뷰 계층 구조에 삽입되어야 한다. 코드로 뷰 객체를 생성하는 경우, 이 메서드는 UIView 클래스의 지정된 초기화 메서드이다. 하위 클래스는 이 메서드를 재정의 하여 사용자 지정 초기화를 수행 할 수 있지만, 구현의 시작 부분에 super를 호출해야 한다.

Interface Builder를 사용하여 인터페이스를 설계하는 경우, 이 메서드는 다음 뷰 객체가 nib 파일에서 불러와질 때 호출되지 않는다. nib 파일에서 객체는 재구성되고 initWithCoder: 메소드를 사용하여 초기화된다. 이 메서드는 nib 파일에 저장된 속성과 일치하도록 뷰의 속성을 변경한다. nib 파일에서 뷰를 불러오는 방법에 대한 자세한 내용은 [Resource Programming Guide][Resource Programming Guide]를 참조해라.

참고: [https://developer.apple.com/reference/uikit/uiview/1622488-initwithframe][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Resource Programming Guide]: https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/LoadingResources/Introduction/Introduction.html#//apple_ref/doc/uid/10000051i
[apple-doc]: https://developer.apple.com/reference/uikit/uiview/1622488-initwithframe