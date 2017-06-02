---
layout: post
title: "enumerateSubstringsInRange:options:usingBlock:"
modified:
categories: blog
excerpt:
tags: [Foundation, NSString, Instance Method]
image:
  feature:
date: 2017-06-02T23:30:00+09:00
---
**지정된 문자열 범위에서 지정된 형식의 하위 문자열을 열거한다.**

----
### 파라미터
 - **range:** 하위 문자열을 열거하는 문자열의 범위.
 - **opts:** 하위 문자열 및 열거 스타일의 유형을 지정하는 옵션.
 - **block:** 열거를 위해 실행 된 블록. 블록은 아래의 4가지 파라미터를 가진다.

 1. substring: 열거된 문자열
 2. substringRange: 수신자의 열거 된 문자의 범위.
 3. enclosingRange: 하위 문자열뿐만 아니라 뒤에 오는 구분자 또는 필러 문자도 포함하는 범위입니다. 예를 들어, 줄의 경우 enclosingRange에 줄 종결자가 포함됩니다. 열거 된 첫 번째 문자열의 enclosingRange에는 문자열 앞에 나오는 문자도 포함됩니다. 연속적인 둘러싸 기 범위는 겹치지 않도록 보장되며 열거 형 범위의 모든 단일 문자는 한 개만 둘러싸는 범위에 포함됩니다.
 4. stop: 블록이 * stop = YES를 설정하여 열거를 중지하는 데 사용할 수있는 부울 값에 대한 참조입니다. 건드리지 말아라. 그렇지 않으면 멈춘다.

### 해설
이 메서드가 NSMutableString의 인스턴스로 전송되면 enclosingRange 내에있는 한 변이 (삭제, 추가 또는 변경)가 허용됩니다. 돌연변이 후 처리 된 범위의 길이가 돌연변이에 맞게 조정 된 후 처리 된 범위 바로 다음 범위에서 열거가 계속됩니다. 열거자는 길이의 변경이 지정된 범위에서 발생한다고 가정합니다.

예를 들어 블록이 위치 N에서 시작하는 범위에서 호출되고 블록이 제공된 범위의 모든 문자를 삭제하면 다음 호출은 범위의 인덱스로 N을 전달합니다. 이전 범위의 변이가 문자열을 변경하여 다음 하위 문자열이 이미 열거 된 범위를 포함하도록 확장하는 경우에도 마찬가지입니다. 예를 들어, 문자열 "Hello World"가 단어를 통해 열거되고 블록이 "Hello"를 "Hello"로 변경하여 "HelloWorld"를 형성하면 다음 열거 형은 "HelloWorld"가 아닌 "World"를 반환합니다.

참고: [https://developer.apple.com/reference/foundation/nsstring/1416774-enumeratesubstringsinrange?language=objc][apple-doc]


<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/reference/foundation/nsstring/1416774-enumeratesubstringsinrange?language=objc