---
title: "[BLOCKCHAIN] GHOST 프로토콜과 이더리움"
layout: post
categories: blockchain
author: "tura"
excerpt: GHOST 프로토콜이 무엇이고, 이더리움에서 어떻게 활용되는지 알아볼게요.
---

<!-- 

  순서

  비트 코인의 문제점 소개
  GHOST Protocol 소개
  이더리움의 적용 사례

-->

# GHOST

<!-- TODO: 문장 보강 -->
GHOST(Greedy Heaviest Observed Subtree) Protocol은 블록 체인에서 메인 체인을 선택하는 방법 중 하나입니다.
이더리움에서는 이걸 조금 수정해서 사용하고 있다고 해요.

## 문제점

비트코인은 10분에 1개씩 블록을 생성합니다. 그 말은 즉 거래를 발생시켜도 최소 10분, 길게는 한 시간에 가깝게 거래 확정이 나기를 기다려야 한다는 말이지요. 왜 이렇게 시간을 길게 한걸까요?

블록 생성 속도가 빠르면 마이너가 동시에 블록을 생성할 가능성이 커지게 됩니다. 블록 체인은 이 중 하나만의 블록을 메인으로 가져가야 하기 때문에 결과적으로 선택되지 못한 **엉클 블록(Unkle Block)**이 많아지게 된답니다.

## 참조 문서

- [이더리움 wiki][modified-ghost-ethereum-wiki]
  이더리움 공식 위키 페이지의 내용입니다. 그리 길지 않고 꽤나 디테일한 내용을 전달하고 있으니 궁금하신 분들은 읽어보세요.

[modified-ghost-ethereum-wiki]: https://github.com/ethereum/wiki/wiki/white-paper#modified-ghost-implementation