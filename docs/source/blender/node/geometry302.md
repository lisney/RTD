Geometry Node 3.0 Basic 2
===========================

1. Modular % 나머지

`y - 홀수 줄 선택 - 인덱스 넘버(0,0),(0,1)...`

![image](https://user-images.githubusercontent.com/30430227/142209164-8777ba97-c87c-4e9b-9c88-63e9cffd24c2.png)

![image](https://user-images.githubusercontent.com/30430227/142209532-fba822bb-3e99-494f-9db0-74c89686f226.png)

`X - 홀수 줄 선택`

![image](https://user-images.githubusercontent.com/30430227/142209849-1152a833-6929-4e8a-a9c4-f2cc68a76bb0.png)

![image](https://user-images.githubusercontent.com/30430227/142209878-c6ce4ad2-5433-49ce-9fd8-0c53a3036b18.png)


<br>

Normalize
-----------

`벡터의 시작점은 (0,0) 방향은 대상의 Location`

![image](https://user-images.githubusercontent.com/30430227/142745614-3bf0e92c-ec14-45f9-8792-3c7b78500411.png)

![image](https://user-images.githubusercontent.com/30430227/142745662-1b769a6e-a480-49c5-a1c2-8467443b436d.png)

`그룹 Input`

![image](https://user-images.githubusercontent.com/30430227/142745688-0d490141-5c68-4af2-9f86-f23cd47e1641.png)

`Relative`

![image](https://user-images.githubusercontent.com/30430227/142745761-3538ddd0-6f38-4396-ad97-4faa7cf31a84.png)

![image](https://user-images.githubusercontent.com/30430227/142745723-feb3fb0e-6308-4c84-baad-8757d72281d8.png)
![image](https://user-images.githubusercontent.com/30430227/142745767-2f14aec9-2f45-432f-92c7-22b594790084.png)

<br>


베타 서포터 - raycaster 
----------------------

![image](https://user-images.githubusercontent.com/30430227/142764151-146c91c4-3533-44fa-a895-1766635ccae0.png)

`Normal Z - 아래로 향한 오버행 선택 > Cube > Set Position - 스케일 원짐 > Instance 스케일 - Raytrace Distance`

![image](https://user-images.githubusercontent.com/30430227/142764439-51caedbc-4257-404a-a4c3-2ddd1d0b288b.png)

<br>

베타 서포터 - 커브형식
---------------------

![image](https://user-images.githubusercontent.com/30430227/142790330-71e0e1d5-d575-4bfa-9dfb-ec124402a131.png)

`BezierCurve > Raycast > Curve to Mesh`

![image](https://user-images.githubusercontent.com/30430227/142790373-57eb8fef-dacd-4834-b388-161c4c04f5f9.png)
![image](https://user-images.githubusercontent.com/30430227/142790460-b4bd2f17-6ad1-4205-91f0-b28fcd32a0b4.png)

![image](https://user-images.githubusercontent.com/30430227/142798041-3b949a3e-a4c7-405b-a7a1-0a320aa3489a.png)

![image](https://user-images.githubusercontent.com/30430227/142798074-bbd3801d-58d3-4604-b1d8-09b188586119.png)

`바닥면 선택 > Set Position > 불린 컷`

![image](https://user-images.githubusercontent.com/30430227/142790330-71e0e1d5-d575-4bfa-9dfb-ec124402a131.png)

![image](https://user-images.githubusercontent.com/30430227/142798268-fbd25687-075d-4b3f-a666-37986251c559.png)

<br>

3점 포인트 좌표
--------------

![image](https://user-images.githubusercontent.com/30430227/142960906-d5cdc4ad-7d03-461b-866d-1e4959a6abef.png)

![image](https://user-images.githubusercontent.com/30430227/142960949-d0c1cfe6-4e70-44f0-9505-ed49c535a85f.png)

![image](https://user-images.githubusercontent.com/30430227/142961194-2bcd3a46-2f9b-477b-941d-fc87a7548297.png)
![image](https://user-images.githubusercontent.com/30430227/142961138-df290237-484b-4d3b-b1a7-44df70ff9544.png)

`X-축의 위치가 음의 방향이면 위치가 틀어진다 `

![image](https://user-images.githubusercontent.com/30430227/142962604-d12d61bf-92c5-47f6-aaf6-a2e7ea022369.png)
![image](https://user-images.githubusercontent.com/30430227/142962625-390b2696-617c-4e71-865a-ff9cb9b6d216.png)

`조건문 - X위치 비교 Less Than > Switch`

![image](https://user-images.githubusercontent.com/30430227/142970663-d4bb1577-0369-4463-a673-e1a7673000a4.png)

<br>

Switch - hide/show
--------------------

![image](https://user-images.githubusercontent.com/30430227/143079816-72901cab-76b4-4ff8-adc4-530a70a865be.png)

![image](https://user-images.githubusercontent.com/30430227/143079748-5fdecdee-a16a-481c-8870-3ef2e7524c4a.png)
![image](https://user-images.githubusercontent.com/30430227/143079780-51837dcf-8961-4f54-be73-47e182a4a30d.png)

![image](https://user-images.githubusercontent.com/30430227/143079994-cccc38da-2f31-49de-9520-d4eea55e2dc0.png)

<br>


Proximity
----------

1. 트랙 투 - 나만 바라봐

`Align Euler to Vector X or Y`

![image](https://user-images.githubusercontent.com/30430227/143552887-20e8b195-809c-4613-88b0-90cac989df1d.png)
![image](https://user-images.githubusercontent.com/30430227/143552992-7c08758a-ae9b-4129-9084-c253e198e042.png)

![image](https://user-images.githubusercontent.com/30430227/143553073-e6e79951-a8e9-481e-8003-75f03802dd4f.png)

`Align Eular to Vector 추가 > Rotate Euler`

![image](https://user-images.githubusercontent.com/30430227/143553573-1ce32b10-85c9-4aea-83de-1b25fab00395.png)

![image](https://user-images.githubusercontent.com/30430227/143553693-4b47d923-bda3-4ade-91d0-96d2c184782f.png)

`Material`

![image](https://user-images.githubusercontent.com/30430227/143555536-f478463f-cb31-46ab-9cc7-15623fbe28e3.png)

![image](https://user-images.githubusercontent.com/30430227/143555618-9791ad07-54f5-4058-88f7-956fe7109104.png)


`참고`

![image](https://user-images.githubusercontent.com/30430227/143537432-f936b1bc-13c8-4351-8ae3-dcd7fd16dc54.png)

![image](https://user-images.githubusercontent.com/30430227/143537464-eb94f46e-dedb-4cb2-a7a6-3d7c3bd169d7.png)

<br>

2. 고랑

![image](https://user-images.githubusercontent.com/30430227/143581157-5d3c3763-b248-4aeb-98cc-f463d56d2ab7.png)

![image](https://user-images.githubusercontent.com/30430227/143581396-6bcfc255-ce2b-45eb-b760-55a28af819a6.png)

![image](https://user-images.githubusercontent.com/30430227/143581435-2f329359-6138-403e-889d-b635473cc633.png)

![image](https://user-images.githubusercontent.com/30430227/143581203-69c4bc8e-d2e6-4fe3-aa07-2aaae41355d2.png)

![image](https://user-images.githubusercontent.com/30430227/143581239-ada775bf-e293-4be0-a82e-837ee0f110f9.png)

UV Map
---------

1. 불러오기

`Vector Math`

![image](https://user-images.githubusercontent.com/30430227/143571401-ee2aad2c-3ae1-489b-b800-851e287cdf51.png)

![image](https://user-images.githubusercontent.com/30430227/143571512-81da2e1e-349e-4487-bcda-a9602fee36ec.png)
![image](https://user-images.githubusercontent.com/30430227/143571584-856bb3c1-8aa0-42ab-ad46-9590191607b9.png)

`내보내기`

![image](https://user-images.githubusercontent.com/30430227/143571713-4475d1cc-734d-4afb-92c8-dd1e70245a51.png)
![image](https://user-images.githubusercontent.com/30430227/143571749-86e7806e-6f69-4b82-8ade-5d77d8bf7c2f.png)

2. Subdividion Surface 기존 UV 적용과 비교

![image](https://user-images.githubusercontent.com/30430227/143572134-ee47ca5f-bcce-4e36-bd34-d899ee1f75f3.png)

![image](https://user-images.githubusercontent.com/30430227/143572314-31dada10-dbf7-4d12-881c-85036b138d92.png)
![image](https://user-images.githubusercontent.com/30430227/143572452-e1ea25ef-0f4e-4423-aa27-ed18b8717b8c.png)

![image](https://user-images.githubusercontent.com/30430227/143572563-d391cdeb-2ef6-4ed8-ae0f-8b31b5359c35.png)

`수정`

![image](https://user-images.githubusercontent.com/30430227/143572858-94985f3d-7658-48fd-9aa5-51a5af01e22d.png)
![image](https://user-images.githubusercontent.com/30430227/143572826-562a0d04-5134-4664-83cc-9749fe11b493.png)

![image](https://user-images.githubusercontent.com/30430227/143573182-d7d75dfc-9554-49b9-a608-1f7627d82f4b.png)

![image](https://user-images.githubusercontent.com/30430227/143573345-0f7c6ee7-3ded-4d55-aa54-129f42638ddd.png)

`Proxy 아웃`

![image](https://user-images.githubusercontent.com/30430227/143573540-f8bcd09a-e7e6-46d7-a713-3271ad4acbb3.png)

![image](https://user-images.githubusercontent.com/30430227/143573600-5250f12b-4585-4853-80cd-ddb811fc3b27.png)

![image](https://user-images.githubusercontent.com/30430227/143573998-ddbf091d-673c-45b1-b083-9bdf682c6629.png)

![image](https://user-images.githubusercontent.com/30430227/143574053-9ece2954-0e1f-4bc5-b31b-f54d57be179f.png)

<br>

Extrude Mesh Node
--------------------

![image](https://user-images.githubusercontent.com/30430227/149046634-00ced166-7d0b-4879-a5ce-47b41cb63d13.png)

![image](https://user-images.githubusercontent.com/30430227/149046754-5a705464-2d5b-4833-9493-46ed8a921566.png)

![image](https://user-images.githubusercontent.com/30430227/149046893-ffd46c1d-5218-454b-a7da-a90f5ad692e8.png)









