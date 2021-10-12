Shading
==============

Rectangle Light(Cycles)
-----------------
![image](https://user-images.githubusercontent.com/30430227/130893362-9e19c6e4-2ef4-417f-9dde-e40f7c2c0d25.png)

1. Spot Light > (이미지선명하게)Radius: 0 > Use Node 버튼 클릭
2. 이미지 텍스처 Ctrl + T > Normal -연결  
![image](https://user-images.githubusercontent.com/30430227/130891723-68780ddf-eaf4-4bb1-9579-7c8071c277c7.png)

3. Mapping Node > Location(0.5,0.5) > Scale(2,2)
4. 사각형으로 texture node > repeat->Clip  
![image](https://user-images.githubusercontent.com/30430227/130892588-0b5e5854-6f17-4826-a689-957075ed9066.png)

5. 외곡보정 Divide node  
![image](https://user-images.githubusercontent.com/30430227/130892836-9c7045dd-e81d-4420-a742-36c68d53740c.png)

6. 볼륨라이트  
![image](https://user-images.githubusercontent.com/30430227/130893282-4549410d-b076-4076-8a18-3bc04426781a.png)

7. 볼륨 강도  
![image](https://user-images.githubusercontent.com/30430227/130893613-77b85cf4-ba9c-408f-9390-685e26d222a9.png)

8. 라이트 패스(투명)  
![image](https://user-images.githubusercontent.com/30430227/131054252-4e8fd3aa-7f0b-4eea-ae14-9cdce9150fa1.png)  
![image](https://user-images.githubusercontent.com/30430227/131054325-f6ab8a94-e285-4a16-a91a-c3cba65974d1.png)

9. 라이트 패스(카메라)  
![image](https://user-images.githubusercontent.com/30430227/131054465-4903d517-6bf1-4219-9af5-d29fba6177a8.png)  
![image](https://user-images.githubusercontent.com/30430227/131054486-ba8689fb-d545-4a3d-ae40-158b857159cd.png)

<br>

파장 
-------
![image](https://user-images.githubusercontent.com/30430227/131340763-e21be114-ee2a-4164-8732-f1cfe9117d69.png)  
![image](https://user-images.githubusercontent.com/30430227/131340914-e13d6fed-7832-483b-bed6-bedf2a090ef7.png)  
![image](https://user-images.githubusercontent.com/30430227/131341112-ab97158f-a968-4173-ac35-9a974623ce45.png)  
애니  
![image](https://user-images.githubusercontent.com/30430227/131341213-f1a69515-cc81-4894-8ae5-86e4c6a34877.png)  

<br>

하프톤 
-------
![image](https://user-images.githubusercontent.com/30430227/131341841-447346e8-0bbe-46a9-9c2e-e6519b66743b.png)  
![image](https://user-images.githubusercontent.com/30430227/131342082-de30e6ec-3794-4569-a146-660369040c70.png)  
Mix   
![image](https://user-images.githubusercontent.com/30430227/131342020-3fd0d158-fb3e-44f5-af56-36b671a6cd4a.png)  
Factor  
![image](https://user-images.githubusercontent.com/30430227/131342296-7106b5c8-ce38-49a2-92d8-54621bfb2d0b.png)  
![image](https://user-images.githubusercontent.com/30430227/131342331-f723e089-caed-4548-bd05-077b1c7b47ca.png)  


매트캡  
----------
![image](https://user-images.githubusercontent.com/30430227/133017792-8d19762b-22a9-426b-8c07-a0a09f686f78.png)  

![image](https://user-images.githubusercontent.com/30430227/133017778-6f957e90-dafb-4489-ad0f-d01e4d81f560.png)  


텍스처 랜덤 반복  
----------------
1. Voronoi 패턴 
![image](https://user-images.githubusercontent.com/30430227/133054085-8b67bbcb-2c92-4b07-b111-0822d8e57c56.png)  
![image](https://user-images.githubusercontent.com/30430227/133054147-3c185656-30a9-43c1-a5fe-3401f55d5307.png)  


2. 경계 마스크 
![image](https://user-images.githubusercontent.com/30430227/133054261-14f84e1f-97c8-4b4d-a8f1-053783d605cc.png)  
![image](https://user-images.githubusercontent.com/30430227/133054282-2daf95e3-a255-43dd-a66b-c9f08ca5217e.png)  

3. 믹스  


Anisotropic 
---------------
![image](https://user-images.githubusercontent.com/30430227/133103705-575855f1-7de4-4d59-a362-b578eb37af9b.png)  
![image](https://user-images.githubusercontent.com/30430227/133103786-1ad7bd62-aed2-4167-a8da-d4f73ccd918e.png)  



Abstract Animation Loop
-------------------------
![image](https://user-images.githubusercontent.com/30430227/133734320-cf62333c-8a85-4f6a-9835-385d03cba9d9.png)  
![image](https://user-images.githubusercontent.com/30430227/133734352-2ba62c25-f49a-4617-b6b4-0b0429bea5d4.png)  

`ColorRamp Animation`  
![image](https://user-images.githubusercontent.com/30430227/133734448-7db52cad-d5f1-4157-b518-71f3a39211e4.png)
![image](https://user-images.githubusercontent.com/30430227/133734410-1531c23a-7c6d-485d-94a7-779004d61e49.png)  


금속 
-------------------
1.Gold  
`Color: #ffc125`  
![image](https://user-images.githubusercontent.com/30430227/133871680-2896cc4e-3e3d-49e9-bb48-68cc3e57472a.png)  

`랜더 모드에서 Scene World 끄기`  
![image](https://user-images.githubusercontent.com/30430227/133871707-89faef57-01f0-4cac-a070-5bad8966add7.png)  


`Metallic, Roughness`  
![image](https://user-images.githubusercontent.com/30430227/133871726-67718f69-bc6d-460b-b845-3d75bf9d34e8.png)
![image](https://user-images.githubusercontent.com/30430227/133871809-87868f2c-11a0-486c-a9de-79e03ae2969e.png)  
 
 
`Screen Space Reflections::Max Roughness`  
![image](https://user-images.githubusercontent.com/30430227/133871770-3941d944-944a-4819-ae41-cf80287d4e86.png)
![image](https://user-images.githubusercontent.com/30430227/133871780-25cf2be2-138b-4e46-b46e-c78659600502.png)  


2. Silver  
`Color: #c0c0c0`  
![image](https://user-images.githubusercontent.com/30430227/133871853-ae94dd3a-b5fa-432b-80e4-fdd0ac99a5d3.png)  

3. Cooper  
`Color: #b87333,  old: #cd7f32`  
![image](https://user-images.githubusercontent.com/30430227/133871901-f74c1245-b42c-4fb8-9ea3-6e673fab1165.png)
![image](https://user-images.githubusercontent.com/30430227/133871947-3802d824-b565-4705-9f5d-8d8952c2082b.png)  


4. Steel  
`Noise - Bump`  
![image](https://user-images.githubusercontent.com/30430227/133872096-2ee22679-7695-4b90-ab24-b003636f0433.png)  

![image](https://user-images.githubusercontent.com/30430227/133872088-d20b780b-9feb-4bfc-b856-bd9f5d0a0864.png)
![image](https://user-images.githubusercontent.com/30430227/133872091-5a1d6504-ce0d-4430-86bb-b61e0e9749ea.png)  


5. Brushed Steel  
```
거리 입력은 블렌더 장치에서 가장 높은 범프의 '높이'입니다. 강도 입력은 높이 맵의 전체 스케일입니다. 
```
![image](https://user-images.githubusercontent.com/30430227/133872247-a68b4831-ac3e-4afe-9f71-71daf67730cc.png)  
![image](https://user-images.githubusercontent.com/30430227/133872252-5b2bb342-e32b-4a36-962a-6abb0589b2ca.png)  


네온사인 
------------
1. 글자  
![image](https://user-images.githubusercontent.com/30430227/133872523-598a4f4c-80f9-4aa1-8454-b0ea8f116032.png)  

2. Light Probe  
![image](https://user-images.githubusercontent.com/30430227/133872587-cf863cf7-fab9-4bbe-b3ac-10c8ed8f8ed9.png)  
![image](https://user-images.githubusercontent.com/30430227/133872616-f88dc25f-bff4-495f-b4de-17c23d41afa2.png)  

3. Bake Indirect Light  
![image](https://user-images.githubusercontent.com/30430227/133872724-d7598bec-e77b-4de0-a784-da99e635933d.png)  
![image](https://user-images.githubusercontent.com/30430227/133872852-aecb6b0c-0b7e-49e9-8f5f-41c9b8cc366d.png)  


4. Add Point Light  
![image](https://user-images.githubusercontent.com/30430227/133872829-b4fb48cc-dffc-4db9-ace4-38f9a150330c.png)  



에너지 링 
----------
![image](https://user-images.githubusercontent.com/30430227/133916804-ab051b9e-990a-4179-a3dd-45f26b863b76.png)  
![image](https://user-images.githubusercontent.com/30430227/133916812-36e13e2c-c8e7-4b9f-b0a9-db583823e67b.png)  

`Voronoi`  
![image](https://user-images.githubusercontent.com/30430227/133917135-79b60b81-92b0-434d-adcf-dc194cd8c603.png)  
![image](https://user-images.githubusercontent.com/30430227/133917139-a312e4ce-9a3f-4169-aba3-26b883c8f253.png)  

![image](https://user-images.githubusercontent.com/30430227/133917147-5f31080c-50e7-4d99-961b-765ab0d235e0.png)
![image](https://user-images.githubusercontent.com/30430227/133917146-f5d82343-5261-4b1e-aef0-daaa290c3826.png)  

`에너지 FX`  
![image](https://user-images.githubusercontent.com/30430227/133917254-9805aaed-a2cd-406e-8605-ee5846c2e731.png)
![image](https://user-images.githubusercontent.com/30430227/133917271-65d0f187-3cef-4a96-807f-9178421c4225.png)  

![image](https://user-images.githubusercontent.com/30430227/133917359-c0db1977-302d-415e-83e0-0d15289e8d62.png)
![image](https://user-images.githubusercontent.com/30430227/133917365-bbafe2b1-4dd2-432d-a232-9d5613a289dc.png)  



나무바닥 
-------------
`블록 8단계 = Ceil 8단계`  
![image](https://user-images.githubusercontent.com/30430227/133986803-b093cd08-a719-4cce-bb33-cbd5f91ff241.png)
![image](https://user-images.githubusercontent.com/30430227/133986692-aca583e5-81b0-436f-a443-5e0a6c683b70.png)  

`White Noise Texture-Random X-position`  
![image](https://user-images.githubusercontent.com/30430227/133986970-8db993da-e931-4805-aed0-ad60b689861b.png)  
![image](https://user-images.githubusercontent.com/30430227/133987035-d744a2ce-b378-4f8b-a331-3c9c888847ef.png)  

![image](https://user-images.githubusercontent.com/30430227/133987614-67b6af3e-c9f7-43f5-b32c-1159324c2095.png)  
![image](https://user-images.githubusercontent.com/30430227/133987670-fecfb270-d721-4e01-985d-bc5169b1ac6b.png)  

`Wood - Wave Texture`  
![image](https://user-images.githubusercontent.com/30430227/133989040-c4a0b4a4-258e-44dc-94a7-9929c9acabec.png)  
![image](https://user-images.githubusercontent.com/30430227/133989070-fe14134b-fd4f-4f20-8ad2-6d637c78ec83.png)  

![image](https://user-images.githubusercontent.com/30430227/133989156-500fa1b7-efad-4819-940f-5f1c71a6a3bc.png)  
![image](https://user-images.githubusercontent.com/30430227/133989137-278e43c8-df83-4c01-ae0d-c65eb0bc90c6.png)  

`Mix`  
![image](https://user-images.githubusercontent.com/30430227/133989410-742dfa42-0e94-45c1-8421-9a81a29a957b.png)
![image](https://user-images.githubusercontent.com/30430227/133989362-96aa962d-f451-4d1a-8440-4eb83a5fbaf9.png)  

![image](https://user-images.githubusercontent.com/30430227/133989583-e308c769-3599-4e20-9c41-f6b9fc336c12.png)  
![image](https://user-images.githubusercontent.com/30430227/133989644-05dc772d-96c8-496b-a76c-f517e6bfa275.png)  


실크 헤어  
------------

1. 커브(Extrude)  
![image](https://user-images.githubusercontent.com/30430227/136890855-0e2788c6-f8e7-4354-8cf0-70faf4ef3eb3.png)  


2. Shading  
`Vector Transform(Z) > Separate(X) > Noise`  
![image](https://user-images.githubusercontent.com/30430227/136893751-307c53b1-608b-416a-a128-96940876a407.png)  
![image](https://user-images.githubusercontent.com/30430227/136893784-777693b2-1482-4ad6-ace8-2fbcd854033f.png)  

![image](https://user-images.githubusercontent.com/30430227/136894267-5a26d1b4-8167-40f6-ab7f-e324036e171a.png)  























