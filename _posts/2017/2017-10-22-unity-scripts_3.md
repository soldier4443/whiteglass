---
title: "[Unity] 유용한 스크립트들 정리 3"
layout: post
categories: unity
author: "tura"
---

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
