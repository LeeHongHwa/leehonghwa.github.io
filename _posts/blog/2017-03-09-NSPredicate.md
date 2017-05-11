---
layout: post
title: "NSPredicate"
modified:
categories: blog
excerpt:
tags: [Foundation, NSPredicate, Class]
image:
  feature:
date: 2017-03-09T23:02:00+09:00
---
**NSPredicate 클래스는 fetch 또는 메모리 필터에 관한 검색을 제한하는데 사용되는 논리 조건을 정의하는데 사용된다.**

----
### 개요
predicate를 사용하여 영구 저장소에 있는 객체의 내용이나 객체의 메모리 필터링에 사용되는 논리 조건을 표현한다.
[NSComparisonPredicate][NSComparisonPredicate], [NSCompoundPredicate][NSCompoundPredicate], and [NSExpression][NSExpression]의 객체로부터 predicate를 만드는 것이 일반적이지만 사용자는 NSPredicate의 클래스 메서드를 사용하여 분석된 문자열 형태로 predicate를 만들곤 한다.
문자열 형태의 predicate의 예를 들면

  - grade == "7" 또는 firstName like "Shaffiq"같은 간단한 비교
  - name contains[cd] "itroen" 같은 대소문자 그리고 발음기호와 구분 없는 검색
  - (firstName like "Mark") 또는 (lastName like "Adderley") 같은 논리 연산

사용자는 관계에 대한 predicate를 작성할 수 있다. 예를 들면

  - group.name like "work*"
  - ALL children.age > 12
  - ANY children.age > 12

또한 작동을 위한 predicates를 만들수 있다. 예를 들면 @sum.items.price < 1000 자세한 문법에 대해서는 [Predicate Programming Guide][Predicate Programming Guide]를 참고해라.

또한 변수를 포함한 predicates를 만들어 실행시 구체적인 값을 대체하기 전에 predicates를 미리 정의할 수 있다. OS X v10.4에서는 predicates 변수를 사용하는 경우에 2단계의 프로세스가 필요하다. 
자세한 건 [predicateWithSubstitutionVariables:][predicateWithSubstitutionVariables:] 와 [evaluateWithObject:][evaluateWithObject:]를 참고해라.
macOS 10.5이후에서는 두 가지의 프로세스가 결합된 [evaluateWithObject:substitutionVariables:][evaluateWithObject:substitutionVariables:]를 사용하면 된다.

참고: [https://developer.apple.com/reference/uikit/uiviewcontroller/1621398-viewdidlayoutsubviews?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[NSComparisonPredicate]: https://developer.apple.com/reference/foundation/nscomparisonpredicate?language=objc
[NSCompoundPredicate]: https://developer.apple.com/reference/foundation/nscompoundpredicate?language=objc
[NSExpression]: https://developer.apple.com/reference/foundation/nsexpression?language=objc
[Predicate Programming Guide]: https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Predicates/AdditionalChapters/Introduction.html#//apple_ref/doc/uid/TP40001789
[predicateWithSubstitutionVariables:]: https://developer.apple.com/reference/foundation/nspredicate/1413227-predicatewithsubstitutionvariabl?language=objc
[evaluateWithObject:]: https://developer.apple.com/reference/foundation/nspredicate/1417924-evaluatewithobject?language=objc
[evaluateWithObject:substitutionVariables:]: https://developer.apple.com/reference/foundation/nspredicate/1407759-evaluatewithobject?language=objc
[apple-doc]: https://developer.apple.com/reference/uikit/uiviewcontroller/1621398-viewdidlayoutsubviews?language=objc