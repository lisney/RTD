Rigging
===========

Custom Property
---------------
1. Rot > Property Value '1.0,' 입력하면 아래쪽에 나타남 > Euler Angles 선택  
![image](https://user-images.githubusercontent.com/30430227/130902550-5b991d78-b7ed-4f52-af95-ec893ce60c81.png)

2. Property Value '1.0, 1.0,1.0' XYZ 
3. '.0,.0,.0,.0 Linear Color  
RGB로 바꾼 후  
![image](https://user-images.githubusercontent.com/30430227/130913389-94abea42-9307-4701-b15f-c34f093a31e5.png)

4. 1 정수, 1.0 실수
5. 커스텀 값에서 Copy As Driver  
![image](https://user-images.githubusercontent.com/30430227/130905238-b21ad6f9-28ad-4bd5-91a5-7fa335743f30.png)

6. 대상에 붙여넣기  
![image](https://user-images.githubusercontent.com/30430227/130905298-88b96740-88c0-49f1-9874-e3f15135e81a.png)

7. 0/1 Boolean 뷰포트 디스플레이/모디파이 디스플레이 온/오프
<br>

Child of
----------
![image](https://user-images.githubusercontent.com/30430227/131270242-53817b55-12b4-4276-a208-1268c353d111.png)  
![image](https://user-images.githubusercontent.com/30430227/131270322-2496e15c-ee47-4e40-9800-9007bce7757c.png)

밀대가 닿는 시점에서 키프레임  
![image](https://user-images.githubusercontent.com/30430227/131270425-40944619-515f-463f-8fe4-c372464c0f60.png)  
![image](https://user-images.githubusercontent.com/30430227/131270412-b5e37d0d-4842-4cac-8843-e50032d5efbb.png)  

한 프레임 이동 후 키프레임-Clear Inverse>Set Inverse(기존 원점을 지우고 타킷에 원점설정)  
![image](https://user-images.githubusercontent.com/30430227/131270552-e35f0559-6bfd-427f-915d-ed139f77defe.png)  
![image](https://user-images.githubusercontent.com/30430227/131270494-7da9aa06-8e39-4ef3-9e11-4a78eb0e4b4e.png)  
![image](https://user-images.githubusercontent.com/30430227/131270522-1d0c8302-49b3-44c5-9040-9c105c32a5aa.png)  

다음 타킷에 전달  
한 프레임 이동 후 새타킷에 위와같은 키프레임(Clear->Set Inverse)  
Visual Transform(부모 상대적 위치 벗어남) 후 키프레임(Transform, Influence)  
![image](https://user-images.githubusercontent.com/30430227/131271315-e9dd8ead-3d61-4685-9cef-f7d1e1625aef.png)  
![image](https://user-images.githubusercontent.com/30430227/131271358-21f0d3fe-351a-454d-812d-9baea1b32be4.png)  

다음 타킷도 마찬가지  
![image](https://user-images.githubusercontent.com/30430227/131271790-325a724d-a069-4818-98f8-57f4bc3bd93e.png)


Transfer Weights
------------------
- 몸과 옷을 따로 웨이트 적용  
몸을 먼저 본에 적용한 후  
옮길 오브젝트(옷같은)는 Empty 적용  
![image](https://user-images.githubusercontent.com/30430227/131273429-604cf4e5-2316-4f13-b9ec-c9979f571cca.png)  

몸 선택 후 옷 선택 후 Weight Paint 모드  
![image](https://user-images.githubusercontent.com/30430227/131273759-1ce4dd4e-1a92-4223-b638-13f7216fadfb.png)  
![image](https://user-images.githubusercontent.com/30430227/131273848-9755f8ae-5fe2-4ada-b6d9-693b19e7afe6.png)  



카메라 드라이브 
---------------
1. Copy as New Driver  
![image](https://user-images.githubusercontent.com/30430227/137431840-fcefb907-7949-495e-95fa-e3bba085ef5f.png)  
![image](https://user-images.githubusercontent.com/30430227/137431983-f6ce03da-d296-4e38-9f72-6c6a04a2e33d.png)  



2. Paste Driver  
![image](https://user-images.githubusercontent.com/30430227/137432066-41102168-5e40-46e6-8bdd-b77ea49b8fcb.png)  
![image](https://user-images.githubusercontent.com/30430227/137432103-09b0f0c7-f1b4-416b-97bf-a3d2052046c0.png)  


3. Edit Driver  
![image](https://user-images.githubusercontent.com/30430227/137432233-b78a4edd-967f-49dd-9255-fb904083033a.png)  
![image](https://user-images.githubusercontent.com/30430227/137433397-5c048be0-f398-4dc4-a8d3-d948ed2a33e6.png)
![image](https://user-images.githubusercontent.com/30430227/137433465-cab7d1cc-c717-49af-aa30-95d422ae2955.png)  

`카메라 다가가면 X-방향으로 비킨다`  
![image](https://user-images.githubusercontent.com/30430227/137433537-f46e6271-0411-4864-8cdb-0115e92c2c6b.png)  

<br>

Image Size -가로세로비 
--------------------------

`Boolean Intersect > 상하좌우 vertex Hook > 오른쪽 위 Hook선택 > X- Copy Driver -오른쪽 아래 붙여넣기 > Y-Copy Driver - 왼쪽 위 붙여넣기`

![image](https://user-images.githubusercontent.com/30430227/143068897-6489699e-d8fa-4af9-9e59-79ba8a509dea.png)







