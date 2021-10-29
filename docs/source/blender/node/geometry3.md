Geometry Node 3.0
===================

<br>

Proximity
-------------

`Plane > Geometry Nodes`

![image](https://user-images.githubusercontent.com/30430227/139170734-96c4ffc4-b751-4f5f-8cba-9ebc4962dd59.png)

![image](https://user-images.githubusercontent.com/30430227/139170747-83a6ff4b-8642-44ef-8b6e-cf1126d0e1b7.png)
![image](https://user-images.githubusercontent.com/30430227/139170757-ada24a51-e797-4408-b96b-cd2fcd926414.png)

`Set Position Node`

![image](https://user-images.githubusercontent.com/30430227/139171301-fe474e49-4b91-4b23-b581-fe9c179f79d6.png)
![image](https://user-images.githubusercontent.com/30430227/139171176-0b263d0f-83ac-4b16-8e2f-ea7947732f95.png)

![image](https://user-images.githubusercontent.com/30430227/139171261-4836b9a3-266f-4d60-b73d-556b98a3ef9a.png)
![image](https://user-images.githubusercontent.com/30430227/139171241-a1ff25df-b33a-44b3-8d38-1de4d8f7b2ae.png)

`Geometry Proximity Node - Shrink Warp Modifier`

![image](https://user-images.githubusercontent.com/30430227/139174102-122db5a0-f84c-4988-8826-2fb73314abb1.png)
![image](https://user-images.githubusercontent.com/30430227/139174153-8f800179-979c-4cc8-9bbc-eff3ba94260a.png)

![image](https://user-images.githubusercontent.com/30430227/139174082-b2d2b81e-fc9d-4e18-84b5-0c04445f1ba9.png)
![image](https://user-images.githubusercontent.com/30430227/139174132-b38d12fd-e7fa-4036-bc08-7444c15d02eb.png)

`Shrink Rate > Color > Mix RGB(RGB를 Vector 조절 로 사용가능)`

![image](https://user-images.githubusercontent.com/30430227/139174646-4b9e115e-59af-4570-8905-e9815b712032.png)
![image](https://user-images.githubusercontent.com/30430227/139174598-60ec8b4f-1bc4-4780-80fc-a433123903ff.png)

`FallOff`

![image](https://user-images.githubusercontent.com/30430227/139181689-7ca802b5-cea5-403b-9191-85761b989773.png)

![image](https://user-images.githubusercontent.com/30430227/139181706-998894d9-8aea-4dcb-b48b-294ae05f0c5f.png)

`Instance`

![image](https://user-images.githubusercontent.com/30430227/139182082-26426c99-d280-4b4a-9c2e-2d5af8f41950.png)

![image](https://user-images.githubusercontent.com/30430227/139182098-88223b94-d554-4c64-b197-f43100faf0df.png)

![image](https://user-images.githubusercontent.com/30430227/139182165-653fb62d-30d1-441c-a7ce-2401bf7ab431.png)

<br>

Instance 
----------

`Rotate Normal`

![image](https://user-images.githubusercontent.com/30430227/139263624-1e42f283-acbe-450f-887f-31b5668fc71f.png)

![image](https://user-images.githubusercontent.com/30430227/139263713-0b2de229-165b-4688-a3a5-434e9c376150.png)

![image](https://user-images.githubusercontent.com/30430227/139263532-e8354f09-6727-4a22-96bd-d7f2e084f4df.png)

`Scale Random`

![image](https://user-images.githubusercontent.com/30430227/139265085-5c6da159-5930-45ac-82d8-c4c78b57d4b3.png)
![image](https://user-images.githubusercontent.com/30430227/139265054-bb96b8e4-fe60-4f22-817e-740504aa9cc4.png)


`Proximity Scale`

![image](https://user-images.githubusercontent.com/30430227/139266611-8c917735-a27f-496e-a731-454c1d6bd0bb.png)

![image](https://user-images.githubusercontent.com/30430227/139266820-cd907879-619a-4fe5-8351-8866b07e7ac6.png)

`Proximity Position`

![image](https://user-images.githubusercontent.com/30430227/139269113-4f26a02b-a884-4ddd-8fa8-4c1f042a0551.png)

![image](https://user-images.githubusercontent.com/30430227/139269203-72e22e07-80be-421c-9f7a-33e1bd218f04.png)

<br>

Fire Fly
-----------

1. Box > name 'emitter' > Geometry node

2. Suzi > New Collection > name 'firefly'

![image](https://user-images.githubusercontent.com/30430227/139270900-7ffc0bec-a5c4-4cd4-8105-0086f23497b1.png)

3. Geometry Nodes

`Collection 을 사용하면 Collection 내 모든 모델에 같은 Geometry Nodes효과, Distribute노드는 밀도 조절`

![image](https://user-images.githubusercontent.com/30430227/139271493-61e16aba-6c1f-4e81-9381-92be7669fd98.png)

`Noise Texture Node(0~1의 값) > -0.5 (-0.5~0.5)`

![image](https://user-images.githubusercontent.com/30430227/139274005-0c4450c0-7007-4b81-a31b-78f96120c50d.png)

![image](https://user-images.githubusercontent.com/30430227/139274124-248131dd-0406-48c9-9768-9fc1a05058b1.png)

`fly Animation`

![image](https://user-images.githubusercontent.com/30430227/139274422-e89628cf-e7ff-4403-a3f0-1ac85d4dbe8b.png)

`Instance - Noise Texture 가 랜덤 노드와 같은 효과, Map Range 노드로 효과 키움`

![image](https://user-images.githubusercontent.com/30430227/139275393-9d4b9886-9bc3-4fb8-92d6-172f63d5d8de.png)

![image](https://user-images.githubusercontent.com/30430227/139275579-402ad235-ca23-4cfe-a7d5-ecba94c3a791.png)


`Material`

![image](https://user-images.githubusercontent.com/30430227/139277441-cf6e41ae-26ab-4a73-baf5-811d6876b482.png)

![image](https://user-images.githubusercontent.com/30430227/139277511-44285ad5-86b1-4c97-8677-d97971145322.png)

<br>

수지 뿔 정리 
------------

`뿔을 회전하려면 Multiply 노드를 Rotation 에 연결한다`

![image](https://user-images.githubusercontent.com/30430227/139428452-03449d55-73fb-495b-8c43-511a01b81362.png)

![image](https://user-images.githubusercontent.com/30430227/139428428-da64e71d-767b-4010-b85e-fe7fcc6fc828.png)

`Empty 컨트롤`

![image](https://user-images.githubusercontent.com/30430227/139430777-0c0ceff7-4b71-4e32-bb45-6aa220282e74.png)

![image](https://user-images.githubusercontent.com/30430227/139430837-693d6a64-5d15-419e-ab4a-ff578cece1f5.png)

