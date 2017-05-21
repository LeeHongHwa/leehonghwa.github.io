---
layout: post
title: "beginAppearanceTransition:animated:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, Instance Method]
image:
  feature:
date: 2017-05-21T21:13:00+09:00
---
**자식 뷰 컨트롤레에게 모양을 변경하도록 지시한다.**

----
### 파라미터
 - **isAppearing:** 만약에 자식 뷰 컨트롤러의 뷰가 뷰 계층구조에 추가되고 있다면 YES 그렇지 않고 제거되고 있다면 NO를 설정해라.
 - **animated:** 전환이 animated 되고 있다면 YES를 설정해라.

### 해설
만약에 custom container controller 를 구현하는 경우에는 이 메서드를 사용하여 자식 뷰 컨트롤러에게 뷰가 나타나거나 사라지려 한다고 말해라. viewWillAppear:, viewWillDisappear:, viewDidAppear:, 또는 viewDidDisappear: 메서드 에서 직접적으로 호출하면 안된다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621387-beginappearancetransition?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621387-beginappearancetransition?language=objc