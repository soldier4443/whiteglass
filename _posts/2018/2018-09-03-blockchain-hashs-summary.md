---
title: "[BLOCKCHAIN] 여러 가지 Hash"
layout: post
categories: blockchain
author: "tura"
excerpt: 헷갈리는 해시 값들. 이번에 한 번 제대로 정리해봅니다.
---

Hash 값에 대한 개념을 정리해보겠습니다.

## Hash Function

블록 체인에서 빼놓고 이야기할 수 없는 것 중 하나가 바로 [Hash Function][hash-wikipedia]입니다.

Hash Function은 **어떤 입력을 고정된 입력으로 매핑**하는 함수인데요. 암호학에서는 **어떤 값을 해시 값으로 바꾸는 건 쉽지만 다시 돌리는 건 어렵다**는 점을 이용해 여러 분야의 보안에 활용하고 있습니다.

앞으로 아래 그림과 같이 `x`의 해시 값을 `h(x)`으로 정의해서 사용하겠습니다.

<img src="/images/2018/hash/hash-function.PNG" class="image fit" style="width: 440px" alt="해시 함수">

## Hash Chain

Hash Chain은 해시 함수의 개념을 확장한 것으로,
해시 함수의 결과에 **다시 해시 함수를 적용**하는 개념이라고 볼 수 있습니다.

<img src="/images/2018/hash/hash-chain.PNG" class="image fit" alt="해시 체인">


## Hash Tree



[hash-wikipedia]: https://ko.wikipedia.org/wiki/%ED%95%B4%EC%8B%9C_%ED%95%A8%EC%88%98