---
layout: post
title: "viewWillAppear"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-01-07T16:19:00+09:00
---
**이 메서드는 뷰(뷰 컨트롤러의 뷰)가 뷰 계층에 추가될 것이다.라는 것을 뷰 컨트롤러에게 알려준다.**

----
### 파라미터
animated: YES이면 뷰는 애니메이션을 사용해 윈도우에 추가 된다.

### 해설
이 메서드는 뷰 컨트롤러의 뷰가 뷰 계층에 추가되기 직전, 뷰를 보여주기 위한 애니메이션이 설정되기 전에 불린다.

사용자는 뷰를 보여주는것과 관련된 추가적인 작업을 하기위해 이 메서드를 override 할 수 있다.
예를 들면 보여지는 뷰의 방향이나 스타일에 맞게 상태 바의 방향, 스타일을 변경 하도록 이 메서드를 사용할 수 있다.
만약에 이 메서드를 override 한다면 반드시 구현부에 super를 호출해야 한다.

뷰 컨트롤러에 의해 어떻게 뷰가 뷰 계층에 추가 되는지 그리고 발생되는 메서드의 순서를 더 알고 싶다면  Supporting Accessibility를 봐라.

**주의**<br>
popover의 내부에 있는 뷰 컨트롤러에 의해서 뷰가 보여진다면 그 뷰가 사라질때는 뷰(popover 내부에 있는 기존 뷰)에서 이 메서드는 불리지 않는다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621510-viewwillappear?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621510-viewwillappear?language=objc
