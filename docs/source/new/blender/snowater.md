Snowater
=========


Snow trace
--------------

1. Cylinder - Remesh > 바닥 메쉬 삭제

![image](https://user-images.githubusercontent.com/30430227/185727638-37b8cee3-4731-4501-8de1-22957905126b.png)
![image](https://user-images.githubusercontent.com/30430227/185727647-e9c8823f-28d4-4a2a-b45b-9d6ceeb540d1.png)

![image](https://user-images.githubusercontent.com/30430227/185727675-cee9e770-1e9f-47dd-b594-4ccdc8c99fc4.png)

`Subdivide - 눈덩이 지나갈 자리`

![image](https://user-images.githubusercontent.com/30430227/185727737-d2fb5cb9-beb0-4484-9fc7-cc639b6083a7.png)
![image](https://user-images.githubusercontent.com/30430227/185727742-9187a774-aba0-461c-8061-f24b96eb0f52.png)


2. Weight Paint > Display Modifier

![image](https://user-images.githubusercontent.com/30430227/185727816-e4f6954e-1423-450a-8f52-fa671b78eeeb.png)
![image](https://user-images.githubusercontent.com/30430227/185727855-7363d84f-cea8-4f22-8c80-cdc9631d0df1.png)

![image](https://user-images.githubusercontent.com/30430227/185727858-1e96e376-0bdd-4ef8-b32f-ff60a1e0bb4a.png)


3. 수지

![image](https://user-images.githubusercontent.com/30430227/185727938-ba4b8e6f-6c6b-470c-8266-aa1a6053a228.png)
![image](https://user-images.githubusercontent.com/30430227/185727951-e091c3ce-0a25-482a-b415-db92f630c91b.png)


`수지 RigidBody Animated Key, 1~5Frame 애니메이션키(Position, Rotate), 5/6 Animated 키 On/Off`

![image](https://user-images.githubusercontent.com/30430227/185728145-83062878-9836-4307-9651-570e0932950b.png)

![image](https://user-images.githubusercontent.com/30430227/185728087-0e712521-901f-4427-be14-babfca36f28d.png)
![image](https://user-images.githubusercontent.com/30430227/185728045-b054141f-2e38-4851-9fe2-598e6c166d07.png)


`바닥, 수지 Friection - 수지 회전 멈추고 미끄러지게`

![image](https://user-images.githubusercontent.com/30430227/185728168-6432be08-7a07-4f0f-88ef-9795f5a2a824.png)
![image](https://user-images.githubusercontent.com/30430227/185728265-8128c7c9-9c99-4eda-a357-8f31f43c0209.png)


4. Bake Keyframe(1~120) > 바닥 Rigid Body 지우고 Z축 방향으로 이동(수지 파묻히게)

![image](https://user-images.githubusercontent.com/30430227/185728331-8de37e1c-dfad-4505-a5ea-7b8354f9257c.png)
![image](https://user-images.githubusercontent.com/30430227/185728409-3f68fb6e-ec04-4e92-bd6b-c703a99cd373.png)


5. Dynamic Paint 

`바닥 - Surface Type:Displace`

![image](https://user-images.githubusercontent.com/30430227/185728492-e208132b-b49f-441b-a941-132920b4c571.png)

![image](https://user-images.githubusercontent.com/30430227/185779554-6e7d385c-2526-45f2-99b2-867c3c3943bc.png)


6. 바닥 displace

![image](https://user-images.githubusercontent.com/30430227/185780640-a45eb7a4-48d0-4dda-958c-bb5fe5a1c834.png)

![image](https://user-images.githubusercontent.com/30430227/185780647-151fd088-22c7-42bd-bbc8-4b8bb77d402f.png)
![image](https://user-images.githubusercontent.com/30430227/185780660-6bcf2d38-c110-444d-83e8-891c8793d8ba.png)

`Light`

![image](https://user-images.githubusercontent.com/30430227/185780820-5ff3c90b-6991-459c-90e8-841717591220.png)

![image](https://user-images.githubusercontent.com/30430227/185780788-aa10000e-74c8-4704-ab9c-c6a277d49dff.png)
![image](https://user-images.githubusercontent.com/30430227/185780848-a6f4500d-7b22-4616-abad-4733efaaa0df.png)


7. Particle - 나중에 인스턴스 오브젝트로 바꾼다 

![image](https://user-images.githubusercontent.com/30430227/185780952-6f53eb19-6baa-4bd0-a47c-3641f62618b4.png)
![image](https://user-images.githubusercontent.com/30430227/185780961-64c7b173-6339-4d2f-ac6a-5f48fc1b6d3d.png)

`ShrinkWrap`

![image](https://user-images.githubusercontent.com/30430227/185781198-49768b52-13e1-403a-a79f-4bb1e3933010.png)
![image](https://user-images.githubusercontent.com/30430227/185781203-aff0ea53-1932-4214-9d7c-ce6eb31c21b2.png)

![image](https://user-images.githubusercontent.com/30430227/185781423-dc15c756-c27b-40ff-84e7-224bb64e53ad.png)

![image](https://user-images.githubusercontent.com/30430227/185781291-d7411e32-0737-4f7f-9586-986827360287.png)
![image](https://user-images.githubusercontent.com/30430227/185781434-3bab284f-2aa1-4511-afea-2ce6ef98c8df.png)

![image](https://user-images.githubusercontent.com/30430227/185781552-e55abbc0-d5f4-4a41-ae03-53540d3fdc02.png)


`바닥 - Stickness, Damping, Friction`

![image](https://user-images.githubusercontent.com/30430227/185781486-85b71b36-0a97-481a-8278-0fac7a2d2809.png)

![image](https://user-images.githubusercontent.com/30430227/185781495-f7ee40ab-02b0-48fb-9331-4470953bbb57.png)


`수동 키프레임`

![image](https://user-images.githubusercontent.com/30430227/185781098-69235859-43a5-4d19-853c-fd3e97ca2c42.png)
![image](https://user-images.githubusercontent.com/30430227/185781094-fd09aabf-70a3-48fd-9128-ee5413c59057.png)




6. Snow Shader - Cycle

![image](https://user-images.githubusercontent.com/30430227/185780248-095f1e9a-33e2-4436-98e6-ba3061e403d3.png)

`Displace Set`

![image](https://user-images.githubusercontent.com/30430227/185780263-77af12f3-4821-4750-b41e-8b0121f180a1.png)

![image](https://user-images.githubusercontent.com/30430227/185780307-dc0bdae4-00c8-401f-9b36-fbbfcb6114c5.png)



Fluid 
---------

1. Flow, Domain

![image](https://user-images.githubusercontent.com/30430227/185729150-b8d7765b-433d-47ab-a4a6-e4c2cfea763f.png)
![image](https://user-images.githubusercontent.com/30430227/185729145-1da9af3d-beda-4801-a4fb-b33a23aadb91.png)

![image](https://user-images.githubusercontent.com/30430227/185729176-3549ff31-2f1c-476d-9d78-3c1735fba2cf.png)
![image](https://user-images.githubusercontent.com/30430227/185729174-9bd6a33e-914f-465f-8aef-f2c001fbe560.png)

`Voxel Size - Resolution Division`

![image](https://user-images.githubusercontent.com/30430227/185729186-5a76b0eb-3113-44de-8979-3c95d7886f80.png)

2. Cache 

`Replay - 실행 바로보기, Modular - 계산Bake 후 실행, Is Resumable - 멈춘 지점에서 이어서 계산`

![image](https://user-images.githubusercontent.com/30430227/185729370-a107a093-ee3c-4480-a277-f1804571c064.png)
![image](https://user-images.githubusercontent.com/30430227/185729521-99ed4abf-32b0-416b-9cbd-7a81393d2fa4.png)

![image](https://user-images.githubusercontent.com/30430227/185729654-25e6e7d7-ed30-40d0-a565-a13cf35548ad.png)
![image](https://user-images.githubusercontent.com/30430227/185729644-833ab137-54c8-49fa-ac51-f6568db37b25.png)


3. Flow 박스 사이즈 변경 업데이트 - 도메인 Use Adaptive Time Steps 체크 껏다 켬(사이즈 변경하면 복셀 갯수도 바뀐다)

![image](https://user-images.githubusercontent.com/30430227/185729751-dfb002cd-b171-4c59-9c5c-3d449d170338.png)
![image](https://user-images.githubusercontent.com/30430227/185729788-f7de1df1-170c-4530-8ca4-a10747b55d9c.png)

![image](https://user-images.githubusercontent.com/30430227/185729758-694d266f-d783-4115-a3bb-3132a6e08e62.png)


4. 수도꼭지 - Inflow(Use Adaptive...체크)

![image](https://user-images.githubusercontent.com/30430227/185729931-1c154032-d9b7-426c-9819-71cf3c0c001b.png)

![image](https://user-images.githubusercontent.com/30430227/185729938-1f98d0f3-1f63-431c-9231-deaa8559a96f.png)


5. CFL Number(유체역학-시뮬레이션 스케일, 값이 낮을 수록 정밀), Timesteps Max/Min-컴퓨터가 알아서 프레임 단계를 결정

![image](https://user-images.githubusercontent.com/30430227/185730220-927fccc5-dacc-440e-8946-42ebbbfc406b.png)
![image](https://user-images.githubusercontent.com/30430227/185730226-b69a1744-553d-4a3a-b081-c503082b4aad.png)

`Time Setp 높이면 자연스럽게 연결`

![image](https://user-images.githubusercontent.com/30430227/185730252-5a54769b-3302-430c-9f2f-c8f53bbc6e82.png)
![image](https://user-images.githubusercontent.com/30430227/185730257-fc40aa05-3537-4148-a0bd-56c160193d53.png)

`CFL`

![image](https://user-images.githubusercontent.com/30430227/185730291-ee660da0-bcc1-422c-90c2-b60c656f689a.png)
![image](https://user-images.githubusercontent.com/30430227/185730307-afddc73a-c1e9-4f33-8bf8-4bb8d4ae4d17.png)

![image](https://user-images.githubusercontent.com/30430227/185730296-6ac732a2-0f93-4a56-af91-e7ba86a9e708.png)
![image](https://user-images.githubusercontent.com/30430227/185730303-e17582cc-2f4c-4b97-94eb-d05325d005fa.png)


6. 중력 활성 - Scene 중력을 끈다

![image](https://user-images.githubusercontent.com/30430227/185730355-07be8ccb-dd99-4676-ba23-26f3a64b2133.png)
![image](https://user-images.githubusercontent.com/30430227/185730363-0c14c81a-e5c2-4538-8c75-bfd9619d5b25.png)


7. Obstacle

![image](https://user-images.githubusercontent.com/30430227/185730445-5d2e2def-2630-4be3-8fa3-92b293791bc1.png)
![image](https://user-images.githubusercontent.com/30430227/185730453-0d257c79-a1f7-46cd-8053-e2ab88b33964.png)

![image](https://user-images.githubusercontent.com/30430227/185730511-e3a5d556-4a5c-4d2b-9ef0-18a58876b93a.png)


`Delete in Obstacle - 내부 파티클 제거`

![image](https://user-images.githubusercontent.com/30430227/185730471-1b86eed6-83ad-4955-85ba-4fe4a18c6352.png)
![image](https://user-images.githubusercontent.com/30430227/185730465-b460cdf8-1947-450a-9e5f-ecaf60a6d6c1.png)


8. Simulation Method 

![image](https://user-images.githubusercontent.com/30430227/185730644-5c5ed3a1-416a-4d9c-8401-2460ae640c6c.png)

![image](https://user-images.githubusercontent.com/30430227/185730663-a61a06b6-58d3-49cf-8034-d414d1e10cce.png)

![image](https://user-images.githubusercontent.com/30430227/185730715-045e1407-1c8a-4357-b832-a5d012687c37.png)

`System Maximun - 시뮬레이션 계산 파티클 수, 0: 자동계산`

`Particle Radius - 파티클 크기`


9. Mesh

![image](https://user-images.githubusercontent.com/30430227/185730989-402dc068-a67e-49a1-a4c3-6df3072a2431.png)

`Radius - 날카롭거나 둥글둥글`

![image](https://user-images.githubusercontent.com/30430227/185731003-7585567c-8740-42da-a91a-a62c163864eb.png)

![image](https://user-images.githubusercontent.com/30430227/185730971-1ebcbaaa-eca1-426e-b591-a623dca5fd6d.png)

`Use Speed Vectors -모션블러 가능`

`Positive/Negative - 부드럽거나 계단현상(3D앨러어싱?)`

![image](https://user-images.githubusercontent.com/30430227/185731129-d549c79a-e03b-44ee-af43-eecd2e33bcf5.png)
![image](https://user-images.githubusercontent.com/30430227/185731135-946933eb-fe9c-4890-a157-fd2e4611e900.png)


10. Viscosty - 꿀

![image](https://user-images.githubusercontent.com/30430227/185731181-8927acca-c97b-42b1-bd19-f365f46d9ce1.png)


11. Diffusion - 확산

![image](https://user-images.githubusercontent.com/30430227/185731279-43d5ef19-2d06-498e-ac28-76cf29c86ecb.png)


12. 
