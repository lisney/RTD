Physics
=============
<br>

젤리
--------
![image](https://user-images.githubusercontent.com/30430227/126725922-846a202c-c5f0-4154-b6c3-dcc4e6ba610e.png)  
![image](https://user-images.githubusercontent.com/30430227/126725079-8f96a5db-3574-46f6-930b-2c4855fd4c99.png)

` softbody > goal 체크해제, Bending: 2, pull/push: 0.75`

![image](https://user-images.githubusercontent.com/30430227/126725055-a99273ea-eb23-4084-aa3f-4c68eb0e3886.png)

`Transmission: 1, 유리같은재질`

![image](https://user-images.githubusercontent.com/30430227/126725199-3e8cb556-82cb-40bf-8569-2aeb245def9c.png)

` vertex parent, 자식선택 > 부모선택 > EditMode`


베게 
------
1. 박스  

![image](https://user-images.githubusercontent.com/30430227/133077761-3b357d8a-f3c5-4587-90ce-e6e35b5f5d77.png)
![image](https://user-images.githubusercontent.com/30430227/133077721-b658f21c-4751-4226-a979-8ace8bce9646.png)  
![image](https://user-images.githubusercontent.com/30430227/133078239-d4e167e6-1ca4-4f1e-ab71-3914fdcd461f.png)  


2.  큐션  
`바닥 Softbody $ Cloth Friction: 50, 공으로 눌러 모양 만듬`  
![image](https://user-images.githubusercontent.com/30430227/133079189-290fd4a4-abb8-4cbc-b28c-fc512f10cb43.png)  


3. pin  
`Gravity: 0, Pressure: 10`  
![image](https://user-images.githubusercontent.com/30430227/133079496-c2c46db7-4ae0-4b28-bf42-aab2386585d4.png)
![image](https://user-images.githubusercontent.com/30430227/133080230-49eda33e-7f43-439b-a9ed-8bb6d5603dc2.png)  



연기
-----
```
Flow::
Initial Temperature: 스모크 속도
Surface Emission: 표면 방출량(적을 수록 보기좋다?)
Texture Offset: animate 


```

1. Follow Path  
![image](https://user-images.githubusercontent.com/30430227/133711346-c69937a6-e4d7-4ed3-8af3-ff90ddb25fc6.png)
![image](https://user-images.githubusercontent.com/30430227/133711372-332d7ce6-c18e-4b3f-ac15-c92a71778dd2.png)  

2. Quick Effect  
![image](https://user-images.githubusercontent.com/30430227/133711539-e218d9f4-d1f2-4a36-9d05-0781f929b7c7.png)
![image](https://user-images.githubusercontent.com/30430227/133711585-abca29a3-dd90-4290-be2a-d090b341803c.png)  

`Domain Dissolve`  
![image](https://user-images.githubusercontent.com/30430227/133713067-31208996-3eb5-4d0b-ba76-23a0dc5902b9.png)
![image](https://user-images.githubusercontent.com/30430227/133713082-1ea4dc2e-14c7-4a7c-ac1b-5b82015cdda2.png)  

`Bake 버튼?`  
![image](https://user-images.githubusercontent.com/30430227/133725459-cefdd5b2-88ad-4763-9ec6-ca1854090b5c.png)  

`Domain Material`  
![image](https://user-images.githubusercontent.com/30430227/133731538-92ffd8ba-0acb-4f5b-9c74-b5eb8597f278.png)
![image](https://user-images.githubusercontent.com/30430227/133731516-d462c374-3f86-4913-89d6-aa0539d1d5e6.png)  

`Render::Bloom, Volumetrics`  
![image](https://user-images.githubusercontent.com/30430227/133731905-c30e06cd-dc2d-400f-8832-998e2b33ed1f.png)
![image](https://user-images.githubusercontent.com/30430227/133731854-b9c6cdca-f206-4e0a-b70e-dbd2c20505a3.png)


 
 
 Puffy Cloth 
---------------

1. Cylinder > Top 평면 복사 후 Separate > Inset , 마지막은 Merge Vertex  
![image](https://user-images.githubusercontent.com/30430227/137719174-4bd665ff-fca9-4d6d-b060-7422986d63dd.png)  


`Vertex Groups`  
![image](https://user-images.githubusercontent.com/30430227/137719356-190ab987-485c-4eef-b1b7-702c215a6d34.png)


2. Displace - 위로 살짝 올려줌`  

![image](https://user-images.githubusercontent.com/30430227/137719675-2d26b5ad-6398-47a0-ab50-dec760e0505c.png)  


3. Cloth  
4. 
`Cloth > Pressure: 3 Gravity: 0, Shrinking Factor: -0.2`  
![image](https://user-images.githubusercontent.com/30430227/137719759-b031d6a9-fce8-4ee9-969b-dcf144a3349d.png)  
![image](https://user-images.githubusercontent.com/30430227/137720405-c7b44e74-5631-400d-a40a-8b07d224df71.png)  

`Subdivide - 순서 Cloth 위로 올린다`  
![image](https://user-images.githubusercontent.com/30430227/137720620-4799fe05-acc1-46f6-bfd7-d6d12ae6e686.png)  

![image](https://user-images.githubusercontent.com/30430227/137722326-a149de69-b550-4bcc-9be2-d0db8fbeccf5.png)


`Subdivide를 추가하면 Detail 추가됨`  








