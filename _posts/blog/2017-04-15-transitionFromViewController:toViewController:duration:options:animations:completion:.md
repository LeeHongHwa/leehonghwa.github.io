---
layout: post
title: "transitionFromViewController:toViewController:duration:options:animations:completion:"
modified:
categories: blog
excerpt:
tags: [UIKit, UIViewController, instance method]
image:
  feature:
date: 2017-04-15T17:00:00+09:00
---
**두개의 자식 뷰 컨트롤러 간의 전환**

----
### 파라미터
fromViewController: 현재 부모 뷰 컨트롤러의 뷰 계층에 보이는 뷰의 뷰 컨트롤러 <br>

toViewController: 뷰 계층에 현재 보이지 않는 뷰의 자식 뷰 컨트롤러 <br>

duration: 애니메이션의 총 지속 시간(초). 0을 전달하면 애니메이션을 적용하지 않고 변경 사항이 적용된다. <br>

option: 어떻게 애니메이션을 나타 내는지에 관한 mask option. <br>

animations: 뷰에게 전달할 변경사항에 관한 block 객체. 뷰 계층 구조에서 뷰의 애니메이션 가능한 속성을 프로그래밍 방식으로 변경한다. 이 block은 파라미터가 없고 반환 값이 없다. 이 파라미터는 NULL이면 안된다. <br>

completion: 애니메이션이 완료된 후에 호출될 block. 이 block 은 다음과 같은 파라미터를 가진다.<br>(finished: 만약에 애니메이션이 완료 되었다면 YES. 그렇지 않고 건너뛰어 졌다면 NO) <br>

### 해설
이 메서드는 두 번째 뷰 컨트롤러의 뷰를 뷰 계층 구조에 추가 한 다음 애니메이션 block에 정의 된 애니메이션을 수행한다. 애니메이션이 완료되면 뷰 계층 구조에서 첫 번째 뷰 컨트롤러의 뷰가 제거된다.

이 메서드는 custom container 뷰 컨트롤러의 구현에서 호출 될수 있다. 만약에 이 메서드를 override를 한다면 사용자는 super를 호출 해야한다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621363-transitionfromviewcontroller][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621363-transitionfromviewcontroller