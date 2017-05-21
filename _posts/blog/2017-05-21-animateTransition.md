---
layout: post
title: "animateTransition:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewControllerAnimatedTransitioning, Instance Method]
image:
  feature:
date: 2017-05-21T16:38:00+09:00
---
**필수 사항.<br>animator 객체에게 전환 애니메이션을 실행하도록 명령한다.**

----
### 파라미터
transitionContext: 전환 정보를 포함 하고 있는 context 객체<br>

### 해설
UIKit은 뷰 컨트롤러를 present, dismiss 할 때 이 메서드를 호출한다. 이 메서드을 사용하여 custom 전환에 관련된 애니메이션을 설정한다. 애니메이션 기반의 뷰 또는 Core Animation을 사용하여 애니메이션을 설정할 수 있다.

모든 애니메이션은 transitionContext의 containerView property로 지정된 뷰에서 실행해야 한다. 보여지는 뷰 (또는 뷰 컨트롤러를 dismiss하는 전환이 포함되있는 경우에 보여지는 뷰)를 컨테이너 뷰 계층에 추가하고 뷰를 지정한 위치로 이동시키는 애니메이션을 설정해라. 대신에 뷰 없이 직접 화면에 그릴 때 이 메서드를 사용하여 CADisplayLink 객체를 구성해라.

transitionContext의 viewControllerForKey: 메소드에서 전환과 관련된 뷰 컨트롤러를 얻을 수 있다. 컨텍스트 객체에 의해 제공되는 정보에 대한 자세한 내용은 [UIViewControllerContextTransitioning][UIViewControllerContextTransitioning]를 봐라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontrolleranimatedtransitioning/1622061-animatetransition?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UIViewControllerContextTransitioning]: https://leehonghwa.github.io/blog/UIViewControllerAnimatedTransitioning/
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontrolleranimatedtransitioning/1622061-animatetransition?language=objc