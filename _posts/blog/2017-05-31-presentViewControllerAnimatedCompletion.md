---
layout: post
title: "presentViewController:animated:completion:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, Instance Method]
image:
  feature:
date: 2017-05-31T22:49:00+09:00
---
**뷰 컨트롤러를 모달로 보여준다.**

----
### 파라미터
 - **viewControllerToPresent:** 현재 뷰 컨트롤러 위에 보여줄 뷰 컨트롤러.
 - **flag:** presentation 애니메이션을 적용하려면 YES, 그렇지 않으면 NO를 전달해라.
 - **completion:** presentation이 끝난 후 실행할 블록. 이 블록은 반환 값이없고 파라미터를 사용하지 않는다. 이 블록은 nil을 지정할 수 있다.

### 해설
horizontally regular environment 에서, 뷰 컨트롤러는 modalPresentationStyle 프로퍼티에 의해 지정된 스타일로 제공됩니다. horizontally compact environment 에서 뷰 컨트롤러는 기본적으로 전체 화면으로 보인다. viewControllerToPresent 객체와 연결된 presentation controller 와 적응가능한 delegate를 연결하면 presentaiton 스타일을 동적으로 수정할 수 있다.

이 메서드를 호출 한 객체가 presentaiton을 처리하는 객체가 아닐 수도 있다. 각 presentaiton 스타일에는 동작을 관리하는 다른 규칙이 있다. 예를 들어 전체 화면 presentaiton은 전체 화면을 다루는 뷰 컨트롤러에 의해 만들어 져야한다. 만약에 현재 뷰 컨트롤러가 전채화면을 채우는 요청을 수행 할 수 없는 경우 뷰 컨트롤러 계층 구조에서 presentaiton을 처리해야 하는 뷰 컨트롤러와 가장 가까운 부모에게 전달하고 그 부모는 요청을 처리하거나 전달할 수 있다.

이 메서드는 뷰 컨트롤러를 표시하기 전에 presentaiton 스타일을 기반으로 뷰 컨트롤러의 뷰의 크기 조정한다. 대부분의 presentation 스타일의 경우 결과 뷰는 presented 뷰 컨트롤러의 modalTransitionStyle 프로퍼티에서 transition 스타일을 사용하여 애니메이션을 사용하여 화면에 보인다. 사용자 정의 presentations의 경우, presented 뷰 컨트롤러의 transitioning delegate를 사용하여 애니메이션을 사용하여 화면에 보인다. 현재 context presentations의 경우 현재 뷰 컨트롤러의 transition 스타일을 사용하여 화면에 애니메이션을 적용 할 수 있다.

completion handler는 presented 뷰 컨트롤러에서 viewDidAppear: 메서드가 호출 된 후에 호출된다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621380-presentviewcontroller?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621380-presentviewcontroller?language=objc