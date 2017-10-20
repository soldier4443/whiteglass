---
title: "[Unity] 유용한 스크립트들 정리 2"
layout: post
categories: unity
author: "tura"
---

### 씬을 전환하는 방법

먼저 [File] - [Build Settings...] (Ctrl + Shift + B) 에서 빌드할 Scene을 선택해야 합니다.

<img src="/images/2017/unity-scripts_2/build-settings.png" width="400" />

```
using UnityEngine.SceneManagement;

public void changeScene (int sceneNumber) {
    SceneManager.LoadScene (sceneNumber);
}

public void changeScene (string sceneName) {
    SceneManager.LoadScene (sceneName);
}
```

`SceneManager`에는 이외에도 GameObject를 다른 Scene으로 옮기는 등의 기능이 있습니다.

<br/>

### 씬을 전환해도 GameObject를 유지시키는 방법

음악 재생과 같이 여러 씬을 이동해도 유지되어야 하는 기능에 적합합니다.
방법은 아주 간단합니다.

```
DontDestroyOnLoad (gameObject);
```
