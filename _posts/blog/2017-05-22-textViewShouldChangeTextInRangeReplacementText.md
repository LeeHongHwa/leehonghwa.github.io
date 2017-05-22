---
layout: post
title: "textView:shouldChangeTextInRange:replacementText:"
modified:
categories: blog
excerpt:
tags: [UIKit, UITextViewDelegate, Instance Method]
image:
  feature:
date: 2017-05-22T23:56:00+09:00
---
**지정된 텍스트를 텍스트 뷰에서 대체할지 말지 delegate 에게 묻는다.**

----
### 파라미터
 - **textView:** 변경 내용이 포함 된 text view.
 - **range:** 현재의 선택 범위. 범위의 길이가 0이면 범위는 현재의 insertion point를 반영한다. 사용자가 Delete 키를 누르면 범위의 길이는 1과 빈 문자열 개체가 하나의 문자를 대체한다.
 - **text:** 삽입 할 텍스트.

### 리턴
이전 텍스트를 새 텍스트로 대체가 필요한 경우 YES를 반환하고 대체 작업을 중단해야하는 경우 NO를 반환한다.

### 해설
텍스트 뷰는 사용자가 새 문자를 입력하거나 기존 문자를 제거 할 때마다 이 메서드를 호출한다. 이 메서드의 구현은 optinal이다. 텍스트 뷰 저장소에 저장되기 전에 이 메서드를 사용하여 텍스트를 바꿀 수 있다. 예를 들어, 맞춤법 검사기가 이 메서드를 사용하여 맞춤법이 틀린 단어를 올바른 단어로 바꾸 수 있다.

참고: [https://developer.apple.com/reference/uikit/uitextviewdelegate/1618630-textview?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/uikit/uitextviewdelegate/1618630-textview?language=objc