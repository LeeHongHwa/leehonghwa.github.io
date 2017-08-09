---
layout: post
title: "CAGradientLayer"
modified:
categories: blog
excerpt: background color 위에 색상 그라디언트를 그리고 둥근 모서리를 포함한 레이어의 모양으로 채운 레이어
tags: [Core Animation, Class]
image:
feature:
date: 2017-08-09T23:40:00+09:00
---

**background color 위에 색상 그라디언트를 그리고 둥근 모서리를 포함한 레이어의 모양으로 채운 레이어**

---

### 개요
그라디언트 레이어를 사용하여 임의의 수의 색상을 포함하는 색상 그라디언트 만든다. 기본으로 색상은 레이어 전체에 균일하게 분포되지만 선택적으로 그라디언트 색상의 위치를 지정할 수 있다. 
<br><br>

**Listing1** 은 그라디언트를 통해 고르게 분포 된 그라디언트 레이어(4개의 색상의 그라디언트)를 만드는 방법을 보여준다. 레이어를 90° 회전 (π / 2 radians)하면 가로 그라데이션을 만들 수 있다.

<sub>**Listing1** 그라디언트 레이어 만들기</sub>
```objc
gradientLayer.colors = [UIColor.red.cgColor,
                        UIColor.yellow.cgColor,
                        UIColor.green.cgColor,
                        UIColor.blue.cgColor]
     
gradientLayer.transform = CATransform3DMakeRotation(CGFloat.pi / 2, 0, 0, 1)
```

<br><br>
**그림1** 은 그라디언트 레이어의 모양을 보여줍니다.

<sub>**그림1** 색상 그라디언트 레이어</sub>
<figure>
	<img src="/images/colorGradientLayer.png" alt="core ML을 사용하여 앱에 적용 시키는 이미지">
</figure>

참고: [https://developer.apple.com/documentation/quartzcore/cagradientlayer#2825193][apple-doc]

<sub>잘못된 부분이 있다면 알려주시면 바로 수정하겠습니다.</sub>

[apple-doc]: https://developer.apple.com/documentation/quartzcore/cagradientlayer#2825193