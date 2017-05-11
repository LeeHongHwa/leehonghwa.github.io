---
layout: post
title: "viewDidDisappear:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-01-19T23:32:00+09:00
---
**뷰 컨트롤러에게 뷰 컨트롤러의 뷰가 뷰 계층에서 지워졌다는 것을 알려준다.**

----
### 파라미터
animated: 만약에 YES라면 뷰의 사라짐은 애니메이션화된다.

### 해설
뷰를 숨기거나 해지하는 것과 관련된 추가적인 일을 하기 위해서 이 메서드를 override 할 수 있다. 만약 이 메서드를 override 한다면 구현부에서 반드시 super를 호출해야 한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621477-viewdiddisappear?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621477-viewdiddisappear?language=objc
