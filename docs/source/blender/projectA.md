ProjectA
============



페인트 브러시 
--------------

1. 모델링  

`붓자루 모양 메쉬 & 붓 털용 평면`  
![image](https://user-images.githubusercontent.com/30430227/137464237-c8960a82-9fa1-4fef-b8b2-4b25c09eaed6.png)  


2. 붓 털 Particle(Hair)  

`Advance - Random`    
![image](https://user-images.githubusercontent.com/30430227/137464374-d5002929-6641-4234-bcfe-db6605309ccc.png)  


`Velocity > Normal(붓의 길이), Randomize(자연스런 모양)`  
![image](https://user-images.githubusercontent.com/30430227/137464619-719d1e01-8b77-40db-8916-e67ece78cbf3.png)

`털 본 - Name 'Tip' > Inverse Kinematics - Chain Length: 1`  
![image](https://user-images.githubusercontent.com/30430227/137465639-d22660b8-0cd5-4147-9af7-fa6f29a0e9eb.png)  
![image](https://user-images.githubusercontent.com/30430227/137467353-eba9cf65-7cb3-4577-9ad7-45c6e985c7c6.png)


`털 Modifier > Lattice`  
![image](https://user-images.githubusercontent.com/30430227/137465849-b610eefd-1313-4f19-98bb-38b62362f676.png)  
![image](https://user-images.githubusercontent.com/30430227/137465909-c5793996-7cb8-423f-9b87-45dfc97153ea.png)  

`Lattice 선택 > Armature Modifier 추가`  
![image](https://user-images.githubusercontent.com/30430227/137466124-9cfe98b3-59cf-4097-b24f-7480180f4631.png)  

`Lattice Vertex Weight - 본 Name 'Tip'`  
![image](https://user-images.githubusercontent.com/30430227/137466743-fcb7d830-086b-4b24-9c2a-3c1efdc29589.png)
![image](https://user-images.githubusercontent.com/30430227/137466789-87b901a7-f6f4-48e7-8a22-bf9d7ded46a6.png)  

![image](https://user-images.githubusercontent.com/30430227/137466834-70d716d1-5ad1-42eb-9f6d-b2e9eb5cfc63.png)
![image](https://user-images.githubusercontent.com/30430227/137466863-b33cb4c2-4771-4dcb-b303-326f0d2eadc9.png)  

![image](https://user-images.githubusercontent.com/30430227/137466993-9afc0a88-812d-49d9-a7d7-496b4a71d142.png)  


3. 붓 전체 이동용 Empty  

`IK Empty 제외 모든 부분 선택 후 Parent`  
![image](https://user-images.githubusercontent.com/30430227/137468410-2fd534dc-0ce5-44f5-ad49-9bc0b776c69b.png)  

`이동해보면 Bend 된다`  
![image](https://user-images.githubusercontent.com/30430227/137468582-e6395052-bfdb-4add-9dbf-ed51b264449e.png)  


4. Driver 대용 Transformation Constraint  

`Local Space - 선택 위치가 0`  
![image](https://user-images.githubusercontent.com/30430227/137477994-c276d0a8-5ea8-4207-80bd-3bf314835889.png)  
![image](https://user-images.githubusercontent.com/30430227/137478088-ca95a394-197f-4a40-9146-7dbab666638d.png)  

`Target 이 드라이버가된다`  
![image](https://user-images.githubusercontent.com/30430227/137478185-c2847f58-2002-48bd-adf9-c3e48d7defb9.png)  
![image](https://user-images.githubusercontent.com/30430227/137478228-75893cdc-f5a5-46d3-8e8d-ada26eca85a1.png)  

![image](https://user-images.githubusercontent.com/30430227/137478272-86f535fd-5ab9-4695-a42a-dc8d3e13c743.png)  


`Transformation 을 추가하여 X 위치에 따라 Z 위치가 이동하게 하여 붓 끝의 중력 효과를 줄 수도 있다`  


5. 브러시 Limit Constraint(기존 로컬 위치)  
![image](https://user-images.githubusercontent.com/30430227/137481496-b76f2a42-edbd-4025-b6b4-5057414d54ce.png)  

![image](https://user-images.githubusercontent.com/30430227/137481605-645c3f39-644d-40e1-b57d-87b817c8c7c2.png)  
![image](https://user-images.githubusercontent.com/30430227/137481638-f158fdc1-e115-4490-9a6b-631638ea26f0.png)  



6. 브러쉬 각도 조절  
`Track Constraint :: Object > Track >`  
![image](https://user-images.githubusercontent.com/30430227/137672592-1d678d07-5606-46a3-8a8a-cb2d62203abe.png)
![image](https://user-images.githubusercontent.com/30430227/137672773-5571f93d-9a59-4846-9e49-6503a896fa3a.png)  

![image](https://user-images.githubusercontent.com/30430227/137672646-b578bc6a-52b5-4660-8ec2-0e93a1ab1ee8.png)  
![image](https://user-images.githubusercontent.com/30430227/137672670-8c202149-11d6-4d6d-b009-5563414751a4.png)  


7. 메인컨트롤  
![image](https://user-images.githubusercontent.com/30430227/137672972-649e8cc0-858e-4e1a-93d1-bae2ebde9938.png)  

`Parent`  
![image](https://user-images.githubusercontent.com/30430227/137673053-1bb68ace-6f35-4540-8f56-73e4ceeb1c57.png)  
![image](https://user-images.githubusercontent.com/30430227/137673241-d001a2ed-e5d1-4d1f-848c-07f77aab3bce.png)  


8. 페인트 메쉬  
`Hair 메쉬를 복사해서`  
![image](https://user-images.githubusercontent.com/30430227/137679081-7d5b9133-86c5-4a72-b36a-91ce93af7d5d.png)  
![image](https://user-images.githubusercontent.com/30430227/137679106-1c508bc5-156d-40dd-a4eb-926dfb191e27.png)
![image](https://user-images.githubusercontent.com/30430227/137679133-fe47cb1b-6ab0-4955-b283-9cce9be17a55.png)  


`Parent to Bone`  
![image](https://user-images.githubusercontent.com/30430227/137680800-1fe47582-2aeb-4231-bf15-590c861e93da.png)  

![image](https://user-images.githubusercontent.com/30430227/137680775-5f3a692d-0881-4fc7-adf7-e647dd8072a0.png)  



9. Dynamic Paint  

































