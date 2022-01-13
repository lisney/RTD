Sculpt
========

```
Trim브러시 //Strength를 1로, Area Plane를 LOck한다 //Curve를 평평한걸로

스컬핑 시 Mesh Topology, 영역 주변만 영향을 받게 //Front Faces Only를 체크한다

'Gravity' //Options > Options > Gravity

Area Plan Lock : 터치 평면에서만 작업가능(작업영역고정, 노말방향으로고정),
Scrape/Peaks 는 평면으로 깍고, Flatten 은 평면을 쌓?는다

ctrl + 1,2,3 섭디

Blob과 Inflate 차이점 : Blob은 한방향, Inflate은 양방향

##스컬핑 브러시 단축키 설정
** Draw Curve(커브의 EditMode에서 베벨값, Shift+Right(ActionMouse)로 드랙. curve.draw, WaitForInput 체크X 
   paint.brush_select  
   가령 키보드 M에 마스크브러시를 설정한다면.
   Sculp Tool에서 마스크를 선택한다.
** Toggle 은 키를 반복해서 누르면 이전 브러시로 돌아간다.

** 스컬핑브러시 라소 마스크 단축키 설정
    paint.mask_lasso_gesture
    shift+ctrl+레프트마우스

** Dynatopo 와 Symmetry XYZ 단축키 설정하기
    sculpt.dynamic_topology_toggle(ctrl + D)//wm.context_toggle//tool_settings.sculpt.use_symmetry_x
    
```

1. Remesh    
`Shift + R > Ctrl + R`  
![image](https://user-images.githubusercontent.com/30430227/132807187-8b34137b-813f-473d-9968-6c7564d5e77d.png)  


2. Hide Show FaceSets 단축키(블렌더 기본 단축키로 지정)  
`Maya 단축키 'H' 를 sculpt.face_set_change_visibility 로 바꿈`  
![image](https://user-images.githubusercontent.com/30430227/137685503-a5cbe01e-3cd4-408c-8ec2-3d2e363baf9e.png)  


3. 시뮬레이션 영역 - 붓 바깥 원 영역(회색)  
`Local- 원 영역 내부/ Global- 전체 영역/ Dynamic- 로컬영역(원 영역)의 위치가 마우스 따라 변경`  
![image](https://user-images.githubusercontent.com/30430227/137698593-40d3a536-8565-4768-b031-47f81cb393a8.png)  
![image](https://user-images.githubusercontent.com/30430227/137698731-668aa8c4-19b4-4a0b-a91d-1e3d7b2656d1.png)  


4. 핀 포인트(당김 점) - 마스크를 사용한다  
![image](https://user-images.githubusercontent.com/30430227/137706169-0d141bbf-7fb5-4482-8df1-c52138acd09c.png)  

`Inflate - Simulation Area > Dynamic - 효과 키울려면 Cloth Mass 줄인다`  
![image](https://user-images.githubusercontent.com/30430227/137706509-23ffb2f2-017e-4553-a52f-d56e40876111.png)  


`Pinch Point`  
![image](https://user-images.githubusercontent.com/30430227/137706661-80d309ef-1dea-4f1c-a461-5865eb1e3689.png)  


`Inflate(튀어나옴) 하지않고 센터로 집중 - Expand > Ctrl(반대) + 드래그 `  
![image](https://user-images.githubusercontent.com/30430227/137706985-e7d1f3a4-da7b-44e6-99e9-20d176fab858.png)  




바느질 
--------
1. 모델링 
![image](https://user-images.githubusercontent.com/30430227/132803853-c13f265f-56d2-4f53-a270-34fbe83d937f.png)  
![image](https://user-images.githubusercontent.com/30430227/132803924-ee21ef4f-11b7-44ef-809e-f715ce841082.png)
![image](https://user-images.githubusercontent.com/30430227/132803962-a57ef050-301f-47d1-81c2-3e3f404ee36f.png)  

![image](https://user-images.githubusercontent.com/30430227/132804265-d9d6e85d-fccd-4e8d-a28f-23af695e9fd9.png)
![image](https://user-images.githubusercontent.com/30430227/132804406-cf0cf61a-51cd-4a65-b18d-507c54e7fdbd.png)  

2. 카메라  
![image](https://user-images.githubusercontent.com/30430227/132804624-7ddff3e4-1b5c-487f-8d8d-d1fcf0e90b10.png)
![image](https://user-images.githubusercontent.com/30430227/132804702-ad6e4912-6482-4771-b204-2f621194155a.png)  

3. Sculpting  
![image](https://user-images.githubusercontent.com/30430227/132811799-c14d96f8-5ab6-4531-ad61-e5129d56adf5.png)
![image](https://user-images.githubusercontent.com/30430227/132804732-bbfcaf8d-53f7-4a68-b4d5-07fcc1d5071f.png)  
`Join 2 Meshes- Sculpt Texture의 Rake 방향은 세로이다`  
![image](https://user-images.githubusercontent.com/30430227/132806663-41e23944-af68-43ff-ad01-72f9ded03245.png)  
![image](https://user-images.githubusercontent.com/30430227/132806688-a604fea7-4a54-44ef-9de9-a11459f23295.png)  
`Texture Coodinate 대신 Geometry`  
![image](https://user-images.githubusercontent.com/30430227/133007245-b3f6f757-c487-48a8-a044-42c347615768.png)  


![image](https://user-images.githubusercontent.com/30430227/132809767-20046b5f-5fb4-45cd-a4d8-25d2d41134e0.png)  
`Rake 체크, Stroke Method: Curve, Space: 60 정도`  
![image](https://user-images.githubusercontent.com/30430227/132809823-00c4b572-217c-4b4c-8d5b-c9900d5492ca.png)  
`Curve Draw: Ctrl + R-Mouse`  
![image](https://user-images.githubusercontent.com/30430227/132810067-edeca65c-0790-4e0d-87c2-b20f59df90fc.png)  

4. Bake  
![image](https://user-images.githubusercontent.com/30430227/132810257-5a43177f-f3f1-4c13-992f-1c908339425d.png)
![image](https://user-images.githubusercontent.com/30430227/132810883-820800b3-7145-4690-b2c6-c83c5f2d06a9.png)  

![image](https://user-images.githubusercontent.com/30430227/132811518-cdb76a3e-2c54-4efb-ad94-bb420c78f832.png)
![image](https://user-images.githubusercontent.com/30430227/132811534-8546e60b-dd61-4c28-8bc2-14f9b77e9452.png)  

<br>

Hardsurface퀵팁 
---------------

1. 홈파기 - Layer Brush, 한 번 파인 깊이로 고정

![image](https://user-images.githubusercontent.com/30430227/149243758-665e5e29-3ef7-47ad-a3ee-5cb2b142e624.png)
![image](https://user-images.githubusercontent.com/30430227/149243770-31de86df-5a75-44b9-b034-d6e6529f51d4.png)

`Layer brush > Strength: 1 > - 모드 > Persistent 체크, 버튼 클릭 > 단축키 'e' Line`

![image](https://user-images.githubusercontent.com/30430227/149243827-c6c9b858-0bc5-4a46-9afa-a7593d3b189b.png)
![image](https://user-images.githubusercontent.com/30430227/149243852-89b0d91c-cc34-4d2f-afea-5bbc89123293.png)

<br>

2. Mask Brush 

`Mask Feather: 1 > Strength: 2 - 분명하게 선택`

![image](https://user-images.githubusercontent.com/30430227/149244342-5f1f6701-25ef-4ad6-a2ab-31d9178aac87.png)

`Stroke Method 'e' > Curve 생성 'Ctrl + R-클릭' > 베지어커브 'Ctrl + R-드랙' > 브러시 사이즈 'f' > 생성 'Ctrl - L클릭'`

![image](https://user-images.githubusercontent.com/30430227/149244874-11fc6eb2-7172-478f-9c41-355812f8aace.png)
![image](https://user-images.githubusercontent.com/30430227/149244977-73a72be3-c0fa-4dd7-b5a5-7c189b754481.png)

`반전 'Ctrl - i' > Move or Inflate(Mesh Filter Brush) `

![image](https://user-images.githubusercontent.com/30430227/149245543-5d1d4d3c-3d7a-41cf-ab61-3eb8be96d73b.png)

![image](https://user-images.githubusercontent.com/30430227/149245522-b62a7be0-acd7-4dcc-ad01-700c905ab074.png)
![image](https://user-images.githubusercontent.com/30430227/149245471-feb13109-99b9-4617-8226-d6536e8ab73a.png)

`Shrink Mask 두 번 > Remesh 스포이드 체크 후 Paint 체크 > Smooth(Mesh Filter Brush) -L클릭 드래그`

![image](https://user-images.githubusercontent.com/30430227/149245904-10363ed6-e6f8-4396-81dd-a7157d52a7f2.png)
![image](https://user-images.githubusercontent.com/30430227/149245924-d992fbe3-0ecd-4d15-9a41-be5004235216.png)

![image](https://user-images.githubusercontent.com/30430227/149245697-ada2fcdf-0cd3-4320-8472-80f007481d22.png)

<br>

3. Alpha Texture

`Drack Dot > Mapping: Area Plane > Falloff: Constant(왼쪽 단추)`

![image](https://user-images.githubusercontent.com/30430227/149246804-fb42e570-33f1-4ebf-b30b-536fea05f1aa.png)

![image](https://user-images.githubusercontent.com/30430227/149246441-84ba824d-2709-4a50-996b-a59e8ae70f93.png)
![image](https://user-images.githubusercontent.com/30430227/149246487-6d4bcfcc-c4de-4c0c-abd9-97fd0cd735c1.png)
![image](https://user-images.githubusercontent.com/30430227/149246747-cc5c2b75-62a1-4ef7-a322-afb4b9129b03.png)






