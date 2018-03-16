---
title: "[Unity] Useful Scripts"
layout: post
categories: unity
author: "tura"
excerpt: 유용한 스크립트를 몇 개 모아보았습니다.
---

### 충돌한 면의 법선 벡터를 기준으로 물체를 회전시키는 방법

```
// 3D
void OnCollisionEnter(Collision col) {
    foreach (ContactPoint hit in col.contacts) {
        Vector3 hitPoint = hit.point;
        Quaternion quat = Quaternion.FromToRotation (Vector3.forward, hit.normal);

        transform.rotation = quat;
    }
}

// 2D
void OnCollisionEnter2D(Collision2D col) {
    foreach (ContactPoint2D hit in col.contacts) {
        Vector2 hitPoint = hit.point;
        Quaternion quat = Quaternion.FromToRotation (
            Vector3.forward,
            new Vector3(hit.normal.x, hit.normal.y, 0));

        transform.rotation = quat;
    }
}
```

<br/>

### 스프라이트 색 변화

```
SpriteRenderer sr = previewObstacle.GetComponent<SpriteRenderer> ();
Color original = new Color (r, b, g, a);
```

<br/>

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

<br/>

### 마우스를 클릭한 각도로 회전하는 방법

이 코드는 '유니티로 배우는 게임 수학 (구부키 류이치 지음)'을 참고하였습니다.

```
using UnityEngine.EventSystems;

    private float rotAngle = 0f;

    void Update () {
        // 마우스 입력이 들어왔을때,
        // UI 관련 오브젝트를 클릭하지 않았다면 (두 번째 조건)
        // 회전 각도를 구합니다.
        if (Input.GetMouseButtonDown (0) &&
            !EventSystem.current.IsPointerOverGameObject ()) {
            rotAngle = GetRotationAngleByTargetPosition (Input.mousePosition);
        }

        // LerpAngle(360도가 넘었을 경우의 처리도 해줌)을 이용해
        // 목표 각도로 회전합니다. (선형 보간)
        gameObject.transform.eulerAngles = new Vector3(0, 0,
            Mathf.LerpAngle (gameObject.transform.eulerAngles.z, rotAngle, Time.deltaTime * 20f));

        // 각도 차이가 매우 작을 경우 회전을 중지합니다.
        if (Mathf.Abs (gameObject.transform.eulerAngles.z - rotAngle) < 0.001f) {
            rotAngle = gameObject.transform.eulerAngles.z;
        }
    }

    // gameObject의 위치와 마우스 포인트 위치의 거리 차이를 이용해
    // 두 위치 사이의 각도를 구합니다.
    float GetRotationAngleByTargetPosition (Vector3 mousePosition) {
        Vector3 selfScreenPoint = Camera.main.WorldToScreenPoint (gameObject.transform.position);
        Vector3 diff = mousePosition - selfScreenPoint;

        float angle = Mathf.Atan2 (diff.y, diff.x) * Mathf.Rad2Deg;

        return angle - 90f;
    }
```
