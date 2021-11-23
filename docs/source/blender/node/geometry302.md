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

Position Selection 
---------------------

![image](https://user-images.githubusercontent.com/30430227/142760747-512c8e2c-a831-43f4-8b8c-211e3f79a8c5.png)

![image](https://user-images.githubusercontent.com/30430227/142760749-3b3e20e9-4069-42af-88c9-afbfdc836d3d.png)

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



