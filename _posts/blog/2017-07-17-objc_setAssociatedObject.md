---
layout: post
title: "objc_setAssociatedObject"
modified:
categories: blog
excerpt:
tags: [Objective-C, Function]
image:
feature:
date: 2017-07-17T23:10:00+09:00
---

**주어진 key와 주어진 메모리관리 시멘틱을 사용하여 주어진 객체에 연관된 값을 저장한다.**

---
### 파라미터
 - **object:** 연관 소스 객체, 값이 저장될 객체.
 - **key:** value의 key 값.
 - **value:** 객체의 key와 연관된 값. 기존에 연관된 값이 지워졌다면 nil을 반환한다.
 - **policy:** 연관 값에 대한 정책.(메모리 관리 시멘틱) 가능한 값을 보려면 [Associative Object Behaviors.][Associative Object Behaviors]을 참고해라.

참고: [hhttps://developer.apple.com/documentation/objectivec/1418509-objc_setassociatedobject?language=objc][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[Associative Object Behaviors]: https://developer.apple.com/documentation/objectivec/objective_c_runtime/associative_object_behaviors?language=objc

[apple-doc]: https://developer.apple.com/documentation/objectivec/1418509-objc_setassociatedobject?language=objc