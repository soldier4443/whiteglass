---
title: "[ANDROID] build variants, product flavors와 Android Studio 3에서 달라진 점"
layout: post
categories: android
author: "tura"
---

build variants와 product flavors는 기능에 따라서 다양한 버전의 앱을 구성하거나, 개발 및 출시 버전을 관리할 때 유용합니다.
이 기능들은 module 레벨의 build.gradle에서 설정할 수 있습니다.

## Build Variants

한국어로 빌드 변형이라고 하는 이 녀석은 **어떠한 형태의 빌드**인지를 나타냅니다.
기본적으로 안드로이드 스튜디오에는 debug와 release라는 변형이 있습니다.

아래 코드를 보세요. release 버전에서는 proguard를 활성화해서 불필요한 코드를 최적화시키고,
변수의 이름을 난독화시켜 디컴파일로 인한 보안 문제를 방지합니다. debug 버전에서는 기존의 applicationId에 ".debug" 라는 이름을 추가해서
디버그 빌드라는 것을 나타내고 있습니다. (Gradle plugin 레퍼런스는 [여기로](http://google.github.io/android-gradle-dsl/current/index.html))

```
android {
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }

        debug {
            applicationIdSuffix ".debug"
        }
    }
}
```


## Product Flavors

제품 버전은 build variants와 비슷하게 동작합니다. 말 그대로 **어플리케이션의 제품 구성**을 의미하죠.
예를 들어, 데모 버전의 앱과 유료 버전의 앱을 만들고 싶을 때, 아래와 같이 설정할 수 있습니다.

```
android {
    productFlavors {
        demo {
            applicationIdSuffix ".demo"
            versionNameSuffix "-demo"
        }
        full {
            applicationIdSuffix ".full"
            versionNameSuffix "-full"
        }
    }
}
```

이렇게 정의된 build variants와 proudct flavors는 다음과 같은 4개의 변형을 만들어 냅니다.

`demoDebug, fullDebug, demoRelease, fullRelease`


## 그래서 이걸 어디에 써먹지...?

버전에 따라서 설정을 다르게 할 수 있는 건 좋은데, 어디에 활용해야 할지 의문이 생깁니다.
이렇게 빌드 구성을 하면, 구성에 따라서 서로 다른 소스 세트를 만들 수 있습니다. 기본적인 기능은 main/ 소스 세트에 두고,
각 빌드 별로 필요하거나 불필요한 기능을 추가/제거할 수 있지요. 예를 들어 유료 버전에서는 광고를 제거하고, 무료 버전에서는 광고를 포함시키는 식입니다.


참고 문헌
 - [안드로이드 공식 페이지](https://developer.android.com/studio/build/build-variants.html)
 - [안드로이드 Testing codelab](https://codelabs.developers.google.com/codelabs/android-testing/index.html?index=..%2F..%2Findex#0)
