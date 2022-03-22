new 3.0
========

1. Custom shape 변형

![image](https://user-images.githubusercontent.com/30430227/148144258-d0ac3416-a262-444d-8a49-a8446ff319f8.png)

<br>

2. Clear Constraint:  Ctrl-Alt-C

<br>

3. Bendy bone / Scale

![image](https://user-images.githubusercontent.com/30430227/148144931-9218b029-727d-46c4-98dc-d7ae3b476edd.png)
![image](https://user-images.githubusercontent.com/30430227/148144956-f72e6e7a-92a8-4654-a724-d554ced3f772.png)

![image](https://user-images.githubusercontent.com/30430227/148145233-a43ac1f9-beb5-45d8-8494-f2dae4b85c20.png)
![image](https://user-images.githubusercontent.com/30430227/148145275-29a0a708-8981-4180-8ffd-b298f729c682.png)

<br>

4. Pose Library - 애드온, 기본으로 설치되어 있음

`생성은 프로퍼티 'Create Pose Asset'버튼 , 사용은 어셋 Browser에서`

![image](https://user-images.githubusercontent.com/30430227/148146128-776e923a-a44c-42c6-b6fb-6d10f6c4a157.png)
![image](https://user-images.githubusercontent.com/30430227/148146147-3aa1c775-10d0-4c39-95f8-0116b80448d8.png)

<br>

`Thumnail: Camera View > Pose Library - 라이브러리에 생성안될 때는 키프레임 생성`

![image](https://user-images.githubusercontent.com/30430227/148146433-23552b3d-1d46-4bb3-b9c2-337fcecd46b1.png)
![image](https://user-images.githubusercontent.com/30430227/148146418-0e3d5a6d-e69f-4e5f-999e-5a62257f154d.png)

<br>

5. Stretch to 컨스트레인트에 Swing(그네) 옵션 추가?

![image](https://user-images.githubusercontent.com/30430227/148146939-c8fcd038-fbf3-40ff-ace2-5d97bf7cab8b.png)

<br>

6. 옷에 Weight 복사 시 'Bone Heat Weighting' 에러나면..(VRoid 중복 버텍스 문제)

`모델 복사 > Merge by Distance > Armature Deform >>`
`원본모델 > With Empty Group > 원본/복사모델 선택 > Transform Weight(NearestFace, SourceLayer:By Name)`

![image](https://user-images.githubusercontent.com/30430227/148148922-9e4019c3-f648-4a03-9621-4ea8b3ed416e.png)

<br>

7. 포니테일 - basic.copy_chain(Rigify) 

![image](https://user-images.githubusercontent.com/30430227/148182797-3fd5dc7e-aa60-446d-84dd-b610a045fccd.png)

<br>

`Multi Rename - Ctrl-F2`

![image](https://user-images.githubusercontent.com/30430227/148182907-b5f24559-962a-46fb-aa2c-e886d43eccda.png)

<br>

`테일본 > Move New Layer > Rig Layers 에 추가하기 - Text Editor 'rig_ui.py' 파일 수정`

![image](https://user-images.githubusercontent.com/30430227/148184783-ad54789f-6247-41f6-b543-1d8dc30ec7b9.png)
![image](https://user-images.githubusercontent.com/30430227/148185393-e4de20c7-677a-48e0-9dcb-17919871a53d.png)

![image](https://user-images.githubusercontent.com/30430227/148185364-2a5676cc-7871-4771-8e2b-5dbc1d15e163.png)

<br>

8. Wiggle Bone - 키프레임 가능, Spring Bone - 키프레임 불가능, 자연스런 모션 - Pose Mode에서 적용해야한다`

<br>

9. 근육 - Shape Key 

![image](https://user-images.githubusercontent.com/30430227/148206635-3eef3ade-069d-496d-aa1f-0b49a5e2695e.png)
![image](https://user-images.githubusercontent.com/30430227/148206588-7759b645-778c-4b55-bfa1-b9e9a2d96219.png)

`Shape Key > Value 오른클릭 Add Driver`

![image](https://user-images.githubusercontent.com/30430227/148206750-21a32ffa-43ad-4239-bfe2-2a8879a2e092.png)
![image](https://user-images.githubusercontent.com/30430227/148206813-629ee1c7-8f65-4186-a2f1-924b38e27ad8.png)

<br>

New 3.1
--------

![image](https://user-images.githubusercontent.com/30430227/158087579-80579db4-9908-4ed8-ab02-35a29ecb1034.png)

`Add Shape(PoseMode)`

![image](https://user-images.githubusercontent.com/30430227/158087726-89cbe126-0519-4e74-b8a7-321d81820be8.png)

`delete Armature`

![image](https://user-images.githubusercontent.com/30430227/158087782-88b58046-705e-46ce-9af1-b68033accb23.png)

`Inflate`

![image](https://user-images.githubusercontent.com/30430227/158088112-f85c5d9d-1b54-457a-9e11-07d1a6356a35.png)


