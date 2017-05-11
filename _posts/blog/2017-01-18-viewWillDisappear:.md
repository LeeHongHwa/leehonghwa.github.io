---
layout: post
title: "viewWillDisappear:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-01-18T23:30:00+09:00
---
**뷰 컨트롤러에게 뷰 컨트롤러의 뷰가 뷰 계층에서 제거되기 직전이라는 것을 알려준다.**

----
### 파라미터
animated: 만약에 YES라면 뷰의 사라짐은 애니메이션화된다.

### 해설
뷰 계층으로부터 뷰가 삭제되고 있는 중이라는 것에 대한 응답으로 이 메서드가 호출된다.
뷰가 실제적으로 제거되기 직전, 애니메이션이 설정되기 전에 이 메서드가 불린다.

서브 클래스는 이 메서드를 override 할 수 있다.
그리고 이 메서드의 override를 통해 변경 사항을 편집(뷰의 first responder의 상태를 해지하는 것, 다른 연관된 일들을 수행하는 것) 할 수 있다. 예를 들면 뷰가 처음으로 보이게 되었을 때 이전 viewDidDisappear:메서드에서 에서 만들어진 상태창의 방향 또는 변화 변화를 되돌리기 위해 이 메서드를 사용할 수 있다.
만약에 이 메서드를 override 한다면 반드시 구현부 안에서 super를 호출해야 한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621485-viewwilldisappear?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621485-viewwilldisappear?language=objc
