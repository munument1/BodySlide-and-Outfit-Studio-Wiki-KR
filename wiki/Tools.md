## ![Transform Tool](http://i.imgur.com/PiYJAb4.png) 트랜스폼 도구 (F)
트랜스폼 도구를 사용하면 메시를 3차원 모든 방향으로 이동, 회전, 크기 조절을 할 수 있습니다. **화살표를 드래그하면 이동, 원을 드래그하면 회전, 정육면체를 드래그하면 크기 조절**이 선택된 쉐이프에 적용됩니다.

[![Transform Tool](http://i.imgur.com/rl3KvqBb.png)](http://i.imgur.com/rl3KvqB.png)

## 정점 이동 (Move Vertex)
정점 이동 도구를 사용하면 뷰포트에서 직접 단일 정점을 드래그하여 옮길 수 있습니다.

이 도구는 툴바에 표시된 다음과 같은 도구 옵션들과 함께 작동합니다:

* **Merge Vertex (정점 병합)**: 동일한 메시의 근처 정점에 스냅(Snap)하여 틈새를 메웁니다.
* **Weld Vertex (정점 용접)**: 별도의 UV 좌표를 유지하면서 근처 정점에 스냅합니다.
* **Edge Slide (엣지 슬라이드)**: 선택된 정점을 연결된 엣지를 따라 미끄러지듯 이동시킵니다.
* **Restrict To Surface**, **Restrict To Plane**, **Restrict To Normal**: 드래그하는 정점의 이동 방식을 각각 표면, 평면, 법선 방향으로 제한합니다.

**Merge Vertex**나 **Weld Vertex**를 사용할 때, 선택한 점이 메시의 경계(Boundary)에 있지 않으면 Outfit Studio가 경고를 표시합니다. 보통 경계 정점이 더 안전한 대상이기 때문입니다.

드래그 방식 대신 수치를 직접 입력하여 단일 정점을 편집하고 싶다면, **Colors 탭**이 아닌 곳에서 **V** 키를 눌러 정점 이동(Move Vertex) 대화 상자를 여세요.

## ![Vertex Selection](http://i.imgur.com/qiGhRPw.png) 정점 선택 (Q)
마스크 브러시와 마찬가지로 이 모드에서는 단일 정점들을 선택하거나 선택 해제할 수 있습니다. 정점 위로 마우스를 드래그하면 **마스크 해제/선택**이 되고, CTRL 키를 누른 채 드래그하면 **마스크 처리/선택 해제**가 됩니다.

[![Vertex Edit](http://i.imgur.com/JUticrPb.png)](http://i.imgur.com/JUticrP.png)

## 메시 편집 (Mesh Editing)
#### ![Collapse Vertex](https://i.imgur.com/xRYZ0kG.png) 정점 허물기 (Collapse Vertex)
메시 정점을 클릭하여 삭제할 수 있게 해 주는 도구입니다. 정점은 다른 정점들과 최대 3개까지만 연결되어 있어야 합니다. 연결이 정확히 3개인 경우, 정점들을 연결하는 삼각형이 하나 추가되어 구멍이 생기지 않도록 합니다.

허물기 전  
![Before](https://i.imgur.com/pk6gzG4.png)  
허물기 후  
![After](https://i.imgur.com/o0vfLx6.png)

허물기 전  
![Before](https://i.imgur.com/AGbioQx.png)  
허물기 후  
![After](https://i.imgur.com/EE1Z83T.png)

#### ![Flip Edge](https://i.imgur.com/mS4jfga.png) 엣지 반전 (Flip Edge)
메시 엣지를 클릭하여 반전시킬 수 있게 해 주는 도구입니다. 해당 엣지가 표면의 경계선이거나 용접된 부분이면 안 됩니다. 엣지 양옆의 두 삼각형은 반대쪽 정점 쌍이 연결되도록 두 개의 새로운 삼각형으로 교체됩니다.

반전 전  
![Before](https://i.imgur.com/ghQwnKF.png)  
반전 후  
![After](https://i.imgur.com/OiHwAIb.png)

#### ![Split Edge](https://i.imgur.com/HpMM2LL.png) 엣지 분할 (Split Edge)
메시 엣지를 클릭하여 새 정점과 함께 둘로 나눌 수 있게 해 주는 도구입니다. 인접한 삼각형들도 둘로 나뉩니다. 새로운 정점은 표면의 곡률(Curvature)에 맞춰 조정된 엣지의 중간 지점에 생성됩니다.

분할 전  
![Before](https://i.imgur.com/MpaoHHm.png)  
분할 후  
![After](https://i.imgur.com/v14SWJn.png)

분할 전  
![Before](https://i.imgur.com/7KHGSKR.png)  
분할 후  
![After](https://i.imgur.com/PascrIx.png)
