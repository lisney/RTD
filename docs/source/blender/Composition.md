Composition
==============

EEVEE Shadow Catcher
-------------------------
![image](https://user-images.githubusercontent.com/30430227/132828307-2356455b-a64e-4a91-b914-fa396467d36b.png)  
`Shader to RGB 그림자와 바깥 부분을 합성(Screen)한 것을 Mix Shader의 Fac 에 적용`  
![image](https://user-images.githubusercontent.com/30430227/132828687-9c0cc04a-8426-4976-8a0f-58ac0d599f02.png)

<br>

EEVEE 배경 이미지 제거 
-----------------------
![image](https://user-images.githubusercontent.com/30430227/133018702-bb81548c-8bb4-4dfb-9132-3998333a5bc2.png)
![image](https://user-images.githubusercontent.com/30430227/133018722-e72391fd-dfab-4e65-a2c0-9bd061994c8e.png)  
![image](https://user-images.githubusercontent.com/30430227/133018739-e3f104a5-2305-4d0d-8e42-968f7916c77e.png)  



Volumetric 
------------
![image](https://user-images.githubusercontent.com/30430227/133027508-71a0a0fc-c9cc-4c5e-a44b-6110122ca863.png)  
![image](https://user-images.githubusercontent.com/30430227/133027523-4b4dc6d2-3532-42e8-a708-bb85e9cefc91.png)  



Glass Refraction with Alpha
--------------------------
`Transmission, ScreenSpace Refraction`  
![image](https://user-images.githubusercontent.com/30430227/133032463-c3596062-183f-44a2-9158-0a5b2e756d50.png)
![image](https://user-images.githubusercontent.com/30430227/133032482-b017a4e8-c8f1-4972-b788-bc0d3a9d1157.png)  

![image](https://user-images.githubusercontent.com/30430227/133032236-482caf01-72ce-4d88-848f-79d3974618b0.png)  

`Red Screen`  
![image](https://user-images.githubusercontent.com/30430227/133032322-30cc6e04-2196-48a0-967c-af1e4864b810.png)  
`Composition`  
![image](https://user-images.githubusercontent.com/30430227/133033214-466dd447-defb-49bc-b408-b834339303a2.png)  


Viewport 배경 검게(Studio Background)
----------------------------------------
`Gray -> Black, Preferences>Themes>Theme Space> GradientColors`  
![image](https://user-images.githubusercontent.com/30430227/137238087-310bfb9f-45b0-42db-994b-a95e503ffd20.png)  


F12 랜더 시 Bloom 효과 안보임  
----------------
`View layer 패널 > Bloom 체크`  
![image](https://user-images.githubusercontent.com/30430227/137238242-d79a6145-4326-4fa9-9ee3-c316b7c92769.png)  


Depth 맵 조절
------------
![image](https://user-images.githubusercontent.com/30430227/137240423-85aa8d9b-2880-41b8-bc9d-6c0a70eef792.png)  


랜더 레이어 
------------
`Add View Layer`  
![image](https://user-images.githubusercontent.com/30430227/137240887-f9c4df01-8b90-486b-bf61-96ee62935b40.png)  

`New Collection 에 제외할 박스 넣고 체크 해제(현재 뷰레이어에서는 랜더되지 않는다`  
![image](https://user-images.githubusercontent.com/30430227/137241002-bac59ec3-175e-44dc-bc7c-8a80b7c4bae0.png)  

`Compositor Editor`  
![image](https://user-images.githubusercontent.com/30430227/137241144-607eb5e3-a897-4b50-b00e-73540d715a89.png)
![image](https://user-images.githubusercontent.com/30430227/137241168-5e88c2e9-8ecc-4ef6-a5f8-156e8cbe9dfb.png)  


랜더 패스 추가
---------------
`View Layer 패널에서 Normal 체크하면`  
![image](https://user-images.githubusercontent.com/30430227/137241327-ba159a00-b68e-48b6-a968-b8aa5c1b694d.png)  

`컴포지션 에디터 랜더 레이어 노드에 추가된다`  
![image](https://user-images.githubusercontent.com/30430227/137241413-37857c47-b0b4-485c-a806-9f3225fc87dd.png)  
 


EXR 랜더  
-----------
![image](https://user-images.githubusercontent.com/30430227/137243329-c3ea4d7b-da05-485d-b329-e0ad6fe09cbb.png)  

`AE에서`  
![image](https://user-images.githubusercontent.com/30430227/137243355-bc3792f5-47a4-48c6-b5db-6d12250fb2dd.png)  

`32bit Color`  
![image](https://user-images.githubusercontent.com/30430227/137244466-5581de15-0aca-4917-b376-c7eeea0d0c11.png)  
![image](https://user-images.githubusercontent.com/30430227/137244484-4a844500-8f4c-4164-bd25-e4618ef69416.png)  

`Depth Layer 사용하기 Exposure`  
![image](https://user-images.githubusercontent.com/30430227/137244550-c1976754-f40f-49d6-bcf1-72b2c5a8bbd0.png)  
![image](https://user-images.githubusercontent.com/30430227/137244705-ec0a9139-49b5-4a70-b278-91855fbad43f.png)  



Blender to AE Addon
-----------------------
`AE > File > Script`  
![image](https://user-images.githubusercontent.com/30430227/137243541-c82f07a4-f65f-47b6-a0ae-183e862aeb15.png)  

`주의!!포지션 마커의 Alpha가 0다`  

```
3D 포지션 2D로 변환  
L = thisComp.layer("Null 1");
L.toComp(L.anchorPoint);
```









 
