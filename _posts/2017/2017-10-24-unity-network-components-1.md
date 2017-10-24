---
title: "[Unity] Network 개념 정리"
layout: post
categories: unity
author: "tura"
---

### NetworkBehaviour 클래스

`NetworkBehavior` 클래스는 `MonoBehaviour`를 상속받은 클래스로써,
네트워크에 관련된 기능을 사용하려는 스크립트에서 `MonoBehaviour` 대신 상속받습니다.

```
public class BallOnNetwork : NetworkBehavior {
    ...
```

`NetworkBehaviour`를 사용하면 좋은 점을 정리 해보았습니다.

 - 네트워크 관련 여러 액션 수행
 - 네트워크 관련 콜백 호출 가능
 - 자동으로 서버와 클라이언트 간 동기화

이 `NetworkBehaviour`를 사용하기 위해서는 `NetworkIdentity`라는 컴포넌트가 필요하다고 합니다.

<br/>

### NetworkIdentity 컴포넌트

`NetworkIdentity`는 지극히 단순한 컴포넌트입니다. 네트워크 내에서 특정 GameObject를 구분하기 위해서 필요하죠.
서버는 NetworkIdentity를 가지고 있는 GameObject를 생성할 때, `NetworkIdentity.NetworkInstanceId`를 새로 할당하고
이를 클라이언트에서 설정하게 됩니다. 일종의 주민등록번호라고 생각하면 좋을 것 같네요.

기본적으로 네트워크가 들어가는 게임에서, 네트워크 액션(서버 생성, 클라이언트 접속 등)에 따라
GameObject를 제어하기 위해서는 이 `NetworkIdentity` 컴포넌트가 꼭 필요합니다.
조금 전에 언급한 `NetworkBehaviour`를 사용하기 위해서도 필요하다는 걸 확인했습니다.

<br/>


#### 참고 자료
 - [유니티 레퍼런스](https://docs.unity3d.com/ScriptReference/Networking.NetworkBehaviour.html)
