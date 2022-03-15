Geometry Node 3.0
===================

<br>

Proximity
-------------

`Plane > Geometry Nodes`

![image](https://user-images.githubusercontent.com/30430227/158289596-efb778ad-0bbd-4576-b290-2ccfc7cb2d28.png)

![image](https://user-images.githubusercontent.com/30430227/158289616-27c826b5-a41c-468a-86c5-509f52bec9e9.png)

`FallOff`

![image](https://user-images.githubusercontent.com/30430227/158289865-1f380ad5-069f-4e30-bc7a-4d4099e3a657.png)

![image](https://user-images.githubusercontent.com/30430227/158289896-7bc48b3c-6fa8-4b64-8ae4-353b0491839c.png)

`Instance Scale`

![image](https://user-images.githubusercontent.com/30430227/158291581-7c3c81fb-b1d4-4744-ab16-f1a2fc754b78.png)

![image](https://user-images.githubusercontent.com/30430227/158291610-410e3244-6353-4db9-ab9a-235bdb747517.png)

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

<br>

고무공 
-------

![image](https://user-images.githubusercontent.com/30430227/139502055-31320d25-3c7e-42d6-8f3f-0472141f17d7.png)

`Random Rotate - 3 Vector 값을 동시에: 마우스로 선택한 상태에서 오른 쪽으로 드랙`

![image](https://user-images.githubusercontent.com/30430227/139502607-762590e6-d433-472d-9822-d26396915238.png)

