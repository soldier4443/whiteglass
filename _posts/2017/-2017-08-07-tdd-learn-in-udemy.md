---
title: "[TDD] Learn in Udemy..?"
layout: post
categories: test-driven-development
author: "tura"
---

이번에 [Udemy][Udemy]라는 사이트를 알게 되었습니다. 유료로 강의를 사서 듣는 사이트입니다.
그런데 처음 들어가니까 6시간동안 모든 강의가 11000원씩이어서... 대략 6개의 강의를 곧바로 질렀습니다. 와우!

우선.. Udacity, Coursera같은 무료 강의와 비교했을 때 좀 더 실무적인 내용이 많은 것 같습니다.
TDD와 Kotlin, Spring과 Android에 대한 강의를 신청했는데, 강의에서 사용하는 예제가 현실성있고 써봄직한(...) 예제들입니다.

켄트 벡의 TDD를 공부하면서, 모듈 단위 객체나 연산 객체는 테스트가 직관적인데
입/출력 인터페이스나 객체 사이 관계는 어떻게 해결해야 하는걸까 고민이 생겼습니다.

[Learn Test Driven Development in Java][TDD in Udemy]

위 강의에서 Test double이라는 개념(저만 몰랐던 것 같습니다...)을 보여주는 샘플 예제가 있는데
그 내용이 상당히 좋아서 비슷한 방식으로 구현해보려고 합니다.

기본적으로 TDD는 코드를 작성하기 이전에 테스트 코드를 먼저 작성해서 프로그램을 개발하게 되고,
그렇기 때문에 구체적인 구현의 의존하기보다 어떤 기능을 제공할 것인가, 즉 인터페이스에 의존하게 됩니다.
TDD에서 단위 테스트는 테스트를 받는 대상에 대해서 독립적이어야 하므로
테스트 더블, IoC(Inversion of Control)와 DI(Dependency Injection)는 TDD를 작성할 때 정말 유용한 개념들입니다.

[단위 테스트와 테스트 더블][test-double]
[IoC와 DI에 대해서 알아보자][IoC-DI]

네트워크나 DB접근같이 *번겁고 귀찮고 나중에 구현하고 싶은* 기능들을 구현하는 대신,
그 기능을 해줄 것으로 기대되는 인터페이스를 만들고 인터페이스를 사용해서 테스트를 합니다.
테스트를 작성할 때, 마치 프레임워크를 만드는 것처럼 작성하는 것이지요.



내일 다시 작성!!



[Udemy]: https://www.udemy.com/
[TDD in Udemy]: https://www.udemy.com/learn-test-driven-development-in-java/learn/v4/overview
[IoC-DI]: http://pks424.tistory.com/entry/IoC-DI%EB%9E%80
[test-double]: https://medium.com/@SlackBeck/%EB%8B%A8%EC%9C%84-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%BC%80%EC%9D%B4%EC%8A%A4%EC%99%80-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EB%8D%94%EB%B8%94-test-double-2b88cccd6a96
