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



