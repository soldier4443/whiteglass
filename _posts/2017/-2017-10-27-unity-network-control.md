---
title: "[Unity] Network 제어하기"
layout: post
categories: unity
author: "tura"
excerpt: 네트워크 게임에서 각 클라이언트를 식별하고, 플레이어를 제어하는 방법을 알아봅니다.
---

1. `NetworkManager`에 player prefab을 등록합니다.

   <img src="/images/2017/unity-network-player-movement/network-manager-spawn.PNG" width="280" />

   <br/>

2. 플레이어 오브젝트에 `NetworkIdentity` 컴포넌트와 `NetworkTransform` 컴포넌트를 추가합니다.
   이 때 `NetworkIdentity`의 `Local Player Authority`를 체크해주세요.
   이것으로 로컬에서 이 오브젝트에 대한 권한을 얻을 수 있습니다.

   <img src="/images/2017/unity-network-player-movement/player-components.PNG" width="280" />

   `NetworkTransform`에서 Sync mode를 설정하는 것도 잊지 마세요.
   `Sync Transform`을 선택하면 위치/회전/크기 정보만 동기화되고,
   `Sync Rigidbody2D` 혹은 `Sync Rigidbody3D`를 선택하면 물리 효과까지 동기화됩니다. (중력 등!)

   <img src="/images/2017/unity-network-player-movement/player-components-network-transform.png" width="280" />

   <br/>

3. 이제 코딩의 시간입니다. 먼저 `MonoBehaviour` 대신 `NetworkBehaviour`를 상속받아야 합니다.
   `NetworkBehaviour`는 `MonoBehaviour`의 하위 클래스로써, 네트워크 상의 물체를 표현하고 싶을 때 사용합니다.
   모노와는 달리 네트워크 상의 자신이 어떤 상태인지 잘 알고 있지요...

   ```
   public class PlayerMovement : NetworkBehaviour {
       ...
   ```

   이 녀석은 `isLocalPlayer`라는 변수를 가지고 있습니다. 이것으로 우리는
   스크립트를 실행하는 주체가 플레이어인지, 서버인지 알 수 있습니다!! (짝짝짝)

   다음과 같이 스크립트를 구성했습니다. 매 번 업데이트를 할 때 로컬 플레이어인지 체크를 해서,
   만약 그렇지 않다면 이하의 문장들은 실행조차 되지 못하게 막아버리는 것이죠..

   ```
   void Update () {
       if (!isLocalPlayer)
           return;

       move ();
       rotate ();
   }
   ```

   만약 플레이어를 위해서 3인칭/1인칭 카메라를 준비했다면, 여기 빠뜨리면 안되는 것이 있습니다.
   일반적으로 그런 카메라들은 public 멤버로 추가하는 경우가 많습니다.

   저는 인칭 카메라와 미니맵을 사용했는데요, 처음 스크립트를 시작할 때 로컬인지 아닌지에 따라
   이 카메라들을 활성화/비활성화해서 동시 접근을 막았습니다. 아래 소스를 확인하세요.

   ```
   public Camera cam;
   public Camera minimap;

   void Start () {
       if (!isLocalPlayer) {
           cam.enabled = false;
           minimap.enabled = false;
           return;
       }
       ...
   ```

   <br/>

4. 완성! 유용하게 사용하세요~

   <img src="/images/2017/unity-network-player-movement/network-player-movement-sample.PNG" width="800" />

   <br/>


#### 참고 자료
 - [유니티 자습서](https://unity3d.com/kr/learn/tutorials/topics/multiplayer-networking/identifying-local-player?playlist=29690)
