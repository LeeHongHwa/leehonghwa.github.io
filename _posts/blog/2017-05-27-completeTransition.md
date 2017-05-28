---
layout: post
title: "completeTransition:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewControllerContextTransitioning, Instance Method]
image:
  feature:
date: 2017-05-27T00:01:00+09:00
---
**필수 사항. 전환 애니메이션이 완료되었음을 시스템에 알린다.**

----
### 파라미터
 - **didComplete:** present된 뷰 컨트롤러로의 전환이 성공적으로 완료되면 YES, 원래의 뷰 컨트롤러가 계속 보인다면 NO

### 해설
애니메이션이 완료된 후 이 메서드를 호출하여 시스템에 전환 애니메이션이 완료되었음을 알린다. 전달할 파라미터는 애니메이션이 성공적으로 완료되었는지를 나타내야 한다. 상호적인 애니메이션의 경우 이 메서드 이외에도 finishInteractiveTransition 또는 cancelInteractiveTransition 메서드를 호출해야 한다. 이 메서드를 호출하는 가장 좋은 장소는 애니메이션 completion block이다.

이 메서드의 기본 구현은 animator 객체의 animationEnded: 메서드를 호출하여 마지막 순간의 정리를 수행할 수 있는 기회를 제공한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontrollercontexttransitioning/1622042-completetransition?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontrollercontexttransitioning/1622042-completetransition?language=objc