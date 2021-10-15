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

`Local Space - 기존 위치가 0`  
![image](https://user-images.githubusercontent.com/30430227/137477994-c276d0a8-5ea8-4207-80bd-3bf314835889.png)  
![image](https://user-images.githubusercontent.com/30430227/137478088-ca95a394-197f-4a40-9146-7dbab666638d.png)  

`Target 이 드라이버가된다`  
![image](https://user-images.githubusercontent.com/30430227/137478185-c2847f58-2002-48bd-adf9-c3e48d7defb9.png)  
![image](https://user-images.githubusercontent.com/30430227/137478228-75893cdc-f5a5-46d3-8e8d-ada26eca85a1.png)  

![image](https://user-images.githubusercontent.com/30430227/137478272-86f535fd-5ab9-4695-a42a-dc8d3e13c743.png)  
















