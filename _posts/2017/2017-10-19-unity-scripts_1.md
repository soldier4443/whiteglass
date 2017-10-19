---
title: "[Unity] 유용한 스크립트들 정리 1"
layout: post
categories: unity
author: "tura"
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


### 스프라이트 색 변화

```
SpriteRenderer sr = previewObstacle.GetComponent<SpriteRenderer> ();
Color original = new Color (r, b, g, a);
```
