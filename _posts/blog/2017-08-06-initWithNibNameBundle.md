---
layout: post
title: "initWithNibName:bundle:"
modified:
categories: blog
excerpt:
tags: [UIViewController, Instance Method]
image:
feature:
date: 2017-08-06T23:05:00+09:00
---

**지정된 번들에 있는 nib 파일로 초기화된 뷰 컨트롤러를 반환한다.**

---

### 파라미터
 - **nibNameOrNil:** 뷰 컨트롤러와 연결할 nib 파일의 이름. nib 파일 이름은 leading path 정보를 포함해서는 안됩니다. nil을 지정하면 [nibName][nibName] 프로퍼티가 nil로 설정된다.
 - **nibBundleOrNil:** nib 파일을 검색할 번들. 이 메서드는 먼저 번들의 프로젝트 디렉토리에서 nib 파일을 찾은 다음 Resources 디렉토리를 찾는다. 이 파라미터가 nil 이면 개요에 설명된 방법대로 nib 파일을 찾는다.

### 반환 값
새로 초기화 된 UIViewController 객체.

### 개요
스토리보드를 사용하여 뷰 컨트롤러와 뷰를 정의할 때 뷰 컨트롤러 클래스를 직접 초기화하지 않는다. 대신 뷰 컨트롤러는 Segue가 호출될 때 자동으로 인스턴스화되거나 프로그래밍 적으로 앱이 스토리보드의 instantiateViewControllerWithIdentifier:를 호출해 인스턴스화된다. 스토리보드로부터 뷰 컨트롤러를 인스턴스화할 때 iOS는 이 메서드 대신 initWithCoder: 메서드를 호출하여 새로운 뷰 컨트롤러를 초기화하고 nib name 프로퍼티를 스토리보드에 저장된 nibfile에 저장한다.

지정한 nib 파일이 바로 로드 되지 않고 처음으로 뷰 컨트롤러의 뷰에 접근할 때 로드 된다. nib 파일이 로드된 후에 추가적인 작업을 하고 싶다면 viewDidLoad 메서드를 override 해서 그 부분에 추가적인 작업을 진행해라.

nibName 파라미터를 nil로 지정하고 loadView 메서드를 override 하지 않았으면 [nibName][nibName] 프로퍼티에 설명된대로 nib 파일을 검색한다.

뷰 컨트롤러가 뷰를 로드하는 방법에 대한 자세한 내용은 [View Controller Programming Guide for iOS][View Controller Programming Guide for iOS] 참고해라.

참고: [https://developer.apple.com/documentation/uikit/uiresponder/1621113-becomefirstresponder?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[nibName]: https://developer.apple.com/documentation/uikit/uiviewcontroller/1621487-nibname?language=objc
[View Controller Programming Guide for iOS]: https://developer.apple.com/library/content/featuredarticles/ViewControllerPGforiPhoneOS/index.html#//apple_ref/doc/uid/TP40007457
[apple-doc]: https://developer.apple.com/documentation/uikit/uiresponder/1621113-becomefirstresponder?language=objc