Modeling Issues 
================

`Subdivide 는 지름을 줄인다 4각/8각 실린더`  
![image](https://user-images.githubusercontent.com/30430227/138055156-98871bae-40b3-42bb-a9e0-6b4e7504d851.png)
![image](https://user-images.githubusercontent.com/30430227/138055385-ac4614b1-4658-4a16-86f1-8ed7717f4a53.png)  



도랑 
-------

1. 격자  
![image](https://user-images.githubusercontent.com/30430227/138047443-b9de505d-d42b-4ee7-b688-154792ca56b2.png)  


2. Circle Select  
![image](https://user-images.githubusercontent.com/30430227/138047543-32547736-7ca2-4587-a78d-45f5fae8894d.png)  


3. Subdivide  
![image](https://user-images.githubusercontent.com/30430227/138047654-2d73f41d-c1b5-48d5-9079-51887ce669fb.png)  



4. Knife  
![image](https://user-images.githubusercontent.com/30430227/138047724-92916e2d-b7b5-4acd-a576-674f2cf0fea2.png)  


5. Smooth Vertex or Move GG   

![image](https://user-images.githubusercontent.com/30430227/138052500-bbd9e116-ea2c-49d0-a252-a6ccfec664f5.png)

![image](https://user-images.githubusercontent.com/30430227/138047809-b894fa33-7d19-43f1-b38c-ed5340d97af8.png)  


6. Bevel  
`Shortest path`  
![image](https://user-images.githubusercontent.com/30430227/138048353-cc0b2599-4df2-4bec-b46f-68b63623142f.png)  

`Bevel`  
![image](https://user-images.githubusercontent.com/30430227/138048727-5005256d-28d8-49b3-9b3f-82018f7fa2c7.png)  

7. Move Center Line  
![image](https://user-images.githubusercontent.com/30430227/138048868-c24550f8-ae3c-4111-806f-ec42f3285adc.png)  


Mesh Analysis  
---------------

![image](https://user-images.githubusercontent.com/30430227/138389189-d291f59b-a003-49aa-a5e9-f39f3c1cd8fb.png)  

![image](https://user-images.githubusercontent.com/30430227/138389168-2d743126-82ee-44d9-8682-f44dfc480247.png)  
`Intersect - 겹침, 더블 체크`  



Boolean 디스플레이 문제 시  
-------------------------
`boolean Addon > Wireframe 체크 끈다`  
![image](https://user-images.githubusercontent.com/30430227/138401403-23e16c2a-4ea6-4c0a-9963-90cc3b458fc7.png)  




면을 좌표평면에 
----------------
![image](https://user-images.githubusercontent.com/30430227/138409740-ccfe595f-34e4-4925-a187-a5fc205ecd3b.png)  


`Edit mode > Orientations Normal > Add Face`  
![image](https://user-images.githubusercontent.com/30430227/138409789-402c1783-fa8d-4e16-9e90-34269d114e32.png)
![image](https://user-images.githubusercontent.com/30430227/138409878-47628f76-a7b9-4d57-ae90-62cf49cf0f1d.png)  


`Select All > 후크 Ctrl - H`  
![image](https://user-images.githubusercontent.com/30430227/138410220-b615e66d-bef9-48c7-835d-27ac333458e6.png)  


`Apply to Transform Orientation`  
![image](https://user-images.githubusercontent.com/30430227/138410654-eba6f30f-74db-4dd3-ba35-40e475d0318e.png)
![image](https://user-images.githubusercontent.com/30430227/138410524-3dd9055c-4fd4-47b2-ab21-89a407d9b856.png)


`Apply Hook > Clear Rotate/Location`  



불린 메쉬 한방에 복사  
--------------------
`Ctrl - D > Alt - C(Mesh)`  
![image](https://user-images.githubusercontent.com/30430227/138414031-005fbb15-65be-400b-82e6-814bb7526c66.png)

![image](https://user-images.githubusercontent.com/30430227/138414086-cd6e7c0a-484a-43a5-9a18-af71f5047ca3.png)
![image](https://user-images.githubusercontent.com/30430227/138414129-4a8b138a-4cc0-4dca-b004-95c1f296b3a6.png)




Face > Intersect(Knife)
------------------------
`Face 모드 > 절단 파트 선택 > Intersect(Knife)`  

![image](https://user-images.githubusercontent.com/30430227/138415128-c5c26b2d-1e25-47c6-ae76-11719316eaf4.png)
![image](https://user-images.githubusercontent.com/30430227/138415177-4b4f0fbe-943d-495a-8b29-f460b92eea2a.png)



펴기 팁 
----------

1. Face Orientation 사용

`Cursor to Selected > Transform Orientations > Face 선택 '+' `  
![image](https://user-images.githubusercontent.com/30430227/138432509-f7a90f27-7a24-4b0c-94a3-2790578aa9e7.png)

`pivot 3D 커서 > 면 선택 > Scale Z: 0`

![image](https://user-images.githubusercontent.com/30430227/138433024-e8f803f1-f13a-4e13-82aa-cb13c415aafb.png)
![image](https://user-images.githubusercontent.com/30430227/138432974-56112ae2-5f88-4688-b722-745670637bc4.png)

<br>
2. Loop Tools 사용

`Select > Hide Unselected 'Shift-H'`  

![image](https://user-images.githubusercontent.com/30430227/138433983-6fc024bc-5f45-4af7-9cdc-b2be2a9bcb1b.png)
![image](https://user-images.githubusercontent.com/30430227/138434099-b93e8350-9524-466a-9989-e745c804b6d8.png)

`Loop > Flatten`

![image](https://user-images.githubusercontent.com/30430227/138434173-85539f88-a5da-4283-9b55-d1db81dec8ee.png)
![image](https://user-images.githubusercontent.com/30430227/138434225-4e1cc275-ec86-456f-b7fd-80fd33553692.png)



