---
title: "Tura의 github blog입니다!"
layout: post
categories: tura
author: "tura"
---

## 왜 github 블로그를 만들었을까??
처음 블로그에 포스팅을 해야겠다고 마음 먹은 것이 약 1년 전이었습니다. domain을 직접 구하고, wordpress를 이용해서 블로그를 구축했습니다.

워드프레스를 이용해서 조금 포스팅을 하다 보니, 불편한 점들이 몇몇 보였습니다.

1. 수정/관리가 쉽지가 않습니다.
2. code snippets를 넣을만한 방법이 plugin 밖에 없었습니다. (그런데 그 플러그인때문에 블로그가 막혔었습니다... 물론 고쳤지만)
3. 한국에서의 인지도가 낮습니다. 때문에 관련 자료가 부족한 편입니다.
4. 도메인을 관리하는게 너무 귀찮았습니다. 난 네트워크나 서버, 웹쪽은 잘 모르는데...

처음에는 **티스토리**를 생각했습니다. 많은 사람들이 이미 티스토리를 가지고 개발자 블로그를 꾸며 놓았고, 레이아웃도 마음에 들었습니다.
그런 제가 github 블로그를 만들기로 마음 먹은 이유는.. **초대장을 몇 번이나 달라고 부탁했는데 초대장을 안줘서!!** 입니다.

그래 어디 한 번 해봐라 하고 다른 방법을 찾던 중.. 이 블로그를 만났습니다.

[Github Blog 플랫폼 선택!][hcn1519]

이 글을 읽고 바로 github blog를 만들어야겠다고 결심했습니다. 그래서 만들었습니다.

## 삽질, 삽질, 삽질..
[recovery man 블로그][recovery-man-blog]

위의 사이트를 통해 손쉽게 지킬 테마를 가지고 github blog를 만들 수 있습니다. (**관련 지식이 부족하시다면 테마를 고를 때 간단한 테마를 고르는 것을 추천드립니다!! react같은 것을 쓰는 테마들은 그와 관련된 설치도 필요하고 여러모로 어렵습니다..**)

지킬 테마를 github blog에 적용하기 위해서는 각자의 방식으로 만들어진 지킬 테마를 적절하게 변경해야 합니다.
그렇지 않으면 테마가 적용되지 않거나, 404 Error를 만나 절망에 빠질지도 모릅니다.. `(네, 제가 그랬습니다..)`

그래서 저는 먼저 jekyll로 빈 사이트를 하나 만들어보고, 그 다음에 테마가 적용된 사이트를 만드는 것을 추천드리고 싶습니다.

github blog를 jekyll 테마를 통해서 만드는 과정에서 겪은 여러 가지 어려움들을 정리해보았습니다.


### 1. Windows에서 jekyll을 사용하려면 여러 가지 고려해야할 사항이 많습니다.
jekyll은 기본적으로 Linux와 Mac만을 지원합니다. 때문에 윈도우 운영체제에서 jekyll을 사용하기 위해서는 조금 다른 방법이 필요합니다.
다행히 Window에서 jekyll을 돌려본 분들이 이미 계십니다.

[Windows에서 Github Page와 Jekyll로 블로그 생성하기][windows-jekyll]

이 블로그를 통해서 jekyll을 가지고 블로그를 만들어 볼 수 있습니다. 하지만 위에 글에서는...

> 그냥 마크다운으로 글을쓰고 YAML로 메타정보를 기입하고 간간히 Liquid 를 사용하면된다.

**이런 무책임한!?**

저는 Markdown도 잘 모르고, YAML이나 Liquid는 완전 처음 듣는 것들이고
또 웹도 잘 모르기때문에 제가 원하는 형태의 블로그를 꾸미기에는 무리가 있었습니다.
YAML과 Liquid를 알아보려고 삽질을 많이 했는데, 글 쓰고 있는 지금도 잘 모릅니다.
자세히 몰라도 대략적인 내용만 검색해서 얻어갈 수 있는 정도라면 문제 없습니다.

우선 이렇게 jekyll을 이용해서 블로그를 한 번 만들어 보면서
windows에서 jekyll을 사용할 때 필요한 사항들을 알았습니다.
이제 이쁜 테마를 한 번 적용해봅시다!!


### 2. jekyll과 jekyll+github는 다릅니다.
저는 테마를 직접 구성할 정도로 css를 잘 다루지 못하기 때문에, 그리고 시간 절약을 위해서
다른 분들이 만들어놓은 테마를 사용했습니다! 아래 링크를 참조하세요.

[recovery man 블로그][recovery-man-blog]

자, 이렇게 테마를 이용해서 github blog를 만들었습니다. 그런데 문제가 몇 가지 있었습니다.

1. local에서 변경 사항을 바로 확인해볼 방법을 잘 모르겠습니다. 이대로라면 수정 사항이 매 번 발생할 때마다 commit하고 push를 해야합니다.
2. 위의 방법으로도 문제가 해결되지 않습니다. 디렉토리 구성이 다릅니다.

1번은 repository에서 `jekyll serve`를 실행하면 되는데, 이 때 발생하는 문제들은 대개
google 검색을 통해 쉽게 해결할 수 있습니다. 다만 문제가 되는 것은 2번입니다.

#### 1
첫 번째로 발생할 수 있는 문제는 *source* 태그로 인한 문제입니다. 우선 다음 글을 봅시다.

[configuring jekyll][configuring-jekyll]

위 글에서 확인할 수 있는 것은, github page와 jekyll이 *_config.yml* 파일을 오버라이딩, 즉 덮어쓰기하기 때문에
바꾸면 안되는 부분이 있다는 것입니다.

우리가 눈여겨봐야 할 부분은 *source* 태그입니다. 이 태그는 `[your repo's top level directory]` 라고 되어 있습니다.
즉, repository의 최상위 디렉토리입니다. *_config.yml* 파일에 혹시 *source* 태그가 설정되어 있다면 당장 지워버리세요!
*baseurl* 태그도 마찬가지로, ""(빈 문자열) 로 설정해야합니다.. (이 내용은 recoveryman 블로그에 나와있습니다.)

그런데 *source* 태그가 다르게 적용되어 있다면, 실제로 소스가 저장되어 있는 위치 역시 최상위 디렉토리가 아닐 겁니다.
그럴 경우 소스가 저장되어 있는 디렉토리에 있는 컨텐츠들을 최상위 디렉토리로 옮기면 됩니다. (저는 됐습니다..)

간단하게 git bash에서 다음과 같이 설정해봅시다. (*source* 태그의 값이 *src* 일 경우)

``` bash
(최상위 디렉토리에서)
mv src/* .
rm -rf src
```

#### 2
두 번째로 발생할 수 있는 문제는 테마가 제대로 적용되지 않는 문제입니다.
이 문제 역시 github와 jekyll이 함께 사용되었을 때의 특수성때문에 발생합니다. 아래 글을 확인해보세요.

[customizing jekyll][customizing-jekyll]

위 글을 보면 jekyll의 테마를 customizing하기 위해서 `/assets/css/style.scss` 파일을 생성하라고 명시되어 있습니다.
제 테마의 경우, 이 파일이 `/assets/main.scss` 로 되어있어 테마가 적용되지 않았습니다.

``` bash
(최상위 디렉토리에서)
mkdir assets/css
mv assets/main.scss assets/css/style.scss
```

파일을 옮김으로써 문제를 해결했습니다.


## 무엇을 더 해볼까..!!

이렇게 블로그를 만들고 나니 해보고 싶은 것들이 많이 생겼습니다. 한 번 정리해보자면 다음과 같습니다.

1. 글씨체 설정하기. 지금 한글 폰트가 별로 맘에 들지 않습니다...
2. jekyll 설정 공부. 일단 만들긴 했는데.. *_config.yml* 에 있는 설정들이 뭘 의미하는지 궁금하네요.
3. 그간 공부해왔던 내용 정리. 공부하면서 항상 정리해보고 싶다는 생각을 했습니다. (그래서 블로그를 시작하기도 했구요.)
4. 블로그 꾸미기. 아직은 **내꺼** 라는 느낌이 잘 안듭니다. 근데 이건 나중에.. (웹 ㅠㅠ)

[recovery-man-blog]:      http://recoveryman.tistory.com/321
[hcn1519]:                http://hcn1519.github.io/articles/2016-02/blog_setting
[run-jekyll-on-windows]:  http://jekyll-windows.juthilo.com/
[windows-jekyll]:         http://hurderella.tistory.com/131
[configuring-jekyll]:     https://help.github.com/articles/configuring-jekyll/
[customizing-jekyll]: https://help.github.com/articles/customizing-css-and-html-in-your-jekyll-theme/
