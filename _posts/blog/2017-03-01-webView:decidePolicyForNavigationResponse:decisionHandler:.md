---
layout: post
title: "webView:decidePolicyForNavigationResponse:decisionHandler:"
modified:
categories: blog
excerpt:
tags: [UIKit, WKNavigationDelegate, instance method]
image:
  feature:
date: 2017-03-01T21:10:00+09:00
---
**탐색에 관한 응답이 알려진 후 탐색을 허락할지 취소할지 결정한다.**

----
### 파라미터
webview: 델리게이트 메서드를 호출하는 웹 뷰 <br>
navigationResponse: 탐색 응답에 관한 정보 <br>
decisionHandler: 탐색을 허락할지 취소할지 결정할때 호출될 block. block은 하나의 파라미터를 받고 WKNavigationResponsePolicy 열겨형 타입의 상수 중 하나다.

### 해설
델리게이트는 block을 즉각적으로 호출하거나 block을 저장할 수 있다 또한 시간이 지나고 비동기로 호출할 수 있다.

참고: [https://developer.apple.com/reference/webkit/wknavigationdelegate/1455643-webview?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/webkit/wknavigationdelegate/1455643-webview?language=objc
