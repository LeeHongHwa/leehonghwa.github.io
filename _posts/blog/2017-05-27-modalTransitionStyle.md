---
layout: post
title: "modalTransitionStyle"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, Instance Property]
image:
  feature:
date: 2017-05-27T23:39:00+09:00
---
**뷰 컨트롤러를 표시할 때 사용할 transition 스타일이다.**

----
### 해설
이 프로퍼티는 presentViewController:animated:completion: 메서드를 사용하여 보일 때 뷰 컨트롤러의 화면이 어떻게 애니메이션 될지 결정한다. 전환 타입을 변경하려면 뷰 컨트롤러가 보이기 전에 이 프로퍼티를 설정해야 한다. 이 프로퍼티의 기본값은 UIModalTransitionStyleCoverVertical이다. 

사용 가능한 transition 스타일 목록, transition 스타일과 사용 가능한 presentation 스타일과의 호환성에 대해서는 [UIModalTransitionStyle][UIModalTransitionStyle] 상수 설명을 참조해라.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621388-modaltransitionstyle?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[UIModalTransitionStyle]: https://developer.apple.com/reference/uikit/uimodaltransitionstyle?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621388-modaltransitionstyle?language=objc