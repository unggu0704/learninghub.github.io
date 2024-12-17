---
author: "unggu"
date: 2023-11-04 05:37:22 +0800
categories: [Computer Science, Computer Architecture]
tags: [CS, computer architecture]
render_with_liquid: true
comments: true
---
# Fixed Point & Floating Point

> 컴퓨터에서 실수는 어떻게 표현하는가?
> 

## 고정 소수점 (Fixed Point)

- 소수 점이 찍힐 위치를 미리 정해놓고 표현

![Untitled]({{ site.baseurl }}{{ page.url }}/Fixed%20Point%20&%20Floating%20Point%20d5060f6147a341e796a00b53ce4fb737/Untitled.png)

**장점** : 실수를 정수부와 소수[Pipelining.md](Pipelining.md)부로 표현하여 단순하다.

**단점** : 표현의 범위가 너무 적어서 활용하기 힘들다. (정수부는 15bit, 소수부는 16bit)

## 부동 소수점 (Floating Point)

- 가수부(exponent) + 지수부(fraction)로 표현

![Untitled]({{ site.baseurl }}{{ page.url }}/Fixed%20Point%20&%20Floating%20Point%20d5060f6147a341e796a00b53ce4fb737/Untitled%201.png)

- 제한된 비트로 지수부(exponent)와 가수부(fraction)를 표현
    - 지수부를 늘리면? → 범위는 넓어지지만 정밀도는 떨어진다.
    - 가수부를 늘리면? → 범위는 좁아지지만 정밀도는 높아진다.
- 적절한 trade off 필요
- 32-bit Architecture에서의 예시

![Untitled]({{ site.baseurl }}{{ page.url }}/Fixed%20Point%20&%20Floating%20Point%20d5060f6147a341e796a00b53ce4fb737/Untitled%202.png)

- 가수부는 음수 표현도 필요하기에 2의 보수로 표현
- 8bit 지수부($2^(7 - 11227)$로 표현할려는 숫자가 너무 크다면 → **OVerFlow**
- 8bit 지수부($2^(7 - 11227)$로 표현할려는 숫자가 너무 작다면 → **UnderFlow**