Action
=======

Pose Library
----------------

```
$포즈 라이브러리에는 현재 레이어 본의 정보를 저장한다.
저장: 저장할 본을 선택하고 '+' 버튼을 누른다
적용: 돋보기 버튼(선택한 본만 적용된다, 아무것도 선택하지 않으면 전체 본에 적용된다)
#Pose 미러복사(오른 클릭 Copy, Paste X-Flip Pose)
뼈의 이름 끝에 .L, .R 붙여야된다 
#Pose 자동선택 // Ctrl + L + MouseWheel(순차적으로 선택된다)
#라이브러리 저장 안될 때 // 회색방패 아이콘을 켜고 저장한다.
#Shift + E :: pose.breakdown, DopeSheet에서는 Set Keyframe Extrapolaton(보외법)
※ 보외법 또는 외삽은 수학에서 원래의 관찰 범위를 넘어서서 다른 변수와의 관계에 기초하여 변수의 값을 추정하는 과정.
#Child Of Constraint 에서 Set Inverse 시 부모의 위치로 이동하지 않는 경우 
// 위치를 원점으로 옮긴다음 실행해본다Select to Cursor(원점)
#Reset Pose 문제(모션캡쳐용 T-포즈를 키애니용으로 변환할 때 필요)
포즈를 잡은 상태에서 메쉬모드로 나와 메쉬를 선택한다
Modifier에서 Armature를 Copy한 후 원래 Armature Modifier를 'Apply'한다음
포즈모드로 들어가 Apply Reset Pose한다
#IK 로테이션 문제
=Edit 모드에서 Bone을 꺽어야한다(포즈모드에서하면 안됨)
#손과 발의 IK 본은 Root본에 Parent하고 Target은 힙본에 한다
```

![image](https://user-images.githubusercontent.com/30430227/159687653-343efa55-ff03-4cf0-bab5-b5c6f18788a1.png)
![image](https://user-images.githubusercontent.com/30430227/159688362-0e0fa0b6-2005-447d-8fce-0003cf61b4d6.png)

![image](https://user-images.githubusercontent.com/30430227/159687676-75d4d8d0-cd34-4a62-b95c-88093ef33219.png)
![image](https://user-images.githubusercontent.com/30430227/159687711-50b8e887-9f27-49fb-af8b-cc534b6d59a9.png)

```
Timeline Editor - 키프레임 마름모 컬러 바꾸기 단축키 'R'
Marker - M > Ctrl-M(Rename)
Curve Editor - 특정 요소의 커브만 보이게 Shift-H, 모두 나타나게 Alt-H

툴아이콘 메뉴(기즈모) 단축키 설정 E-Move, D-Rotate
Select Mirror 단축키 변경 Alt-M
뼈 선택 이동 '[', ']' 
```

`Break down - 키 프레임 다음으로 중요, 예)진자 운동`

<br>

포즈 생성
----------

`저장할 본들을 선택하고 >Create Pose Asset - 손만 선택하면 손만 적용된다`

![image](https://user-images.githubusercontent.com/30430227/159226043-3684d1e1-7198-4f35-abae-9f57a4313e25.png)
![image](https://user-images.githubusercontent.com/30430227/159226084-13ab206c-278c-4d78-bd64-d4027ff39965.png)

![image](https://user-images.githubusercontent.com/30430227/159225890-b418feca-2fb4-412b-b7bd-beb6e082996a.png)

`Thumbnail - Asset Browser > Generate Preview Icon`

![image](https://user-images.githubusercontent.com/30430227/159226206-7dd48971-e808-49bb-9497-d75990fd68f4.png)

`Interactive Blend - 드랙하면 대상 포즈로 점점 바뀐다, 3D뷰의 프로퍼티에서는 아이콘에서 바로 드랙> FlipPose 미러 `

![image](https://user-images.githubusercontent.com/30430227/159226697-a00b30d0-a181-4ac2-a146-f5a21ac9740e.png)
![image](https://user-images.githubusercontent.com/30430227/159226737-28302d83-1096-4fb9-8a17-b04d59c00689.png)


펀칭 동작 - AutoKey
---------------------

1. Staging - 펀칭 동작은 정면보다 옆 방향이 보기 좋다

![image](https://user-images.githubusercontent.com/30430227/159426288-64375e21-fd13-4b05-9cb2-cf31d8cceb63.png)

5. Anticipation - 준비자세(기대-사전동작, 동작을 예측하게하는 역할)

![image](https://user-images.githubusercontent.com/30430227/159428690-0cd8974b-80d6-4b53-b9aa-7c566f7b9389.png)

15. 머무는 타이밍 - 스쿼시(준비 동작을 좀 더 크게 준다, break down)

18. 공격 - 뒷 발 앞으로 내딛고 > 팔은 몸과 동시에 움직이지 않는다

![image](https://user-images.githubusercontent.com/30430227/159431220-796e6b83-f2d8-43c9-a4c3-abb96439099a.png)

20. 팔 뻗기 - Squash & Stretch 

`팔 IK 모드로 바꿈 - 스트레치 전에 스쿼시를 준다, 머리와 허리를 살짝 숙인다`

![image](https://user-images.githubusercontent.com/30430227/159435615-c8ffd91d-0511-48a3-83f8-188bc028e5bb.png)

25. Stretch > 돌아옴, 머리와 허리도 살짝 편다

![image](https://user-images.githubusercontent.com/30430227/159435767-6d136c44-a522-4256-88b9-510222c04e2a.png)

30. 머리와 허리 다시 살짝 숙인다(반동)

<br>

점프 동작 
-----------

5. Anticipation - 허리, 머리는 숙이고

![image](https://user-images.githubusercontent.com/30430227/159442900-71687f70-2b5f-47c9-922e-615061a7079e.png)

10. 머무는 동작 - 준비자세 좀 더(Moving hold, Extream)

![image](https://user-images.githubusercontent.com/30430227/159443413-6ec5d6eb-9c06-4d85-982c-851f15d5238d.png)

13. 점프 - 허리, 머리를 편다

![image](https://user-images.githubusercontent.com/30430227/159444086-2d09e149-067a-43f6-8208-86dc8cf61513.png)

18. 최고점 

![image](https://user-images.githubusercontent.com/30430227/159444645-475910d3-979a-495c-84fa-477c315d53c0.png)

<br>

활 쏘기
-----

```
Child Of > Visual Transfrom(현재 위치를 자식의 원점으로), Position/Influence Set Key
>Next Frame > Clear Inverse(부모 영향 벗어남), Influence ->0`
```

5. Anticipation - 화살/활은 위치를 잡은 후 Child of> Set Inverse

![image](https://user-images.githubusercontent.com/30430227/159646040-90ba619d-951b-4232-94ed-c005e021e506.png)
![image](https://user-images.githubusercontent.com/30430227/159647090-967146b1-7fb1-4a00-842f-411ba9764770.png)

15. 시위 당긴다(Moving hold, Extream) - 발을 벌린다, 고개를 활 쪽으로 기울인다, 움츠림

![image](https://user-images.githubusercontent.com/30430227/159647161-a7fd7a02-f9cb-4d0d-ad26-f9a990265ff4.png)

17. 시위를 놓는다 - 오른 팔/머리도 뒤로 젖히고, 몸은 화살에 이끌리듯 살짝 앞으로 나간다(Follow Through. 움츠림 

`화살 > 15-Visual Transform, Clear Inverse , SetKey(Influence) > 16-SetKey(Influence:0)`

`활현 -반동으로 앞쪽으로 > 22 - 뒤쪽 반동 > 25 - 제자리`

![image](https://user-images.githubusercontent.com/30430227/159647182-d4e90683-318d-4ced-927b-3f0e27b36ff8.png)
![image](https://user-images.githubusercontent.com/30430227/159648277-cf65523a-8f09-47c4-ad7e-10ebd95a0dde.png)

25. 팔 내린다, 몸 원래위치로

![image](https://user-images.githubusercontent.com/30430227/159649793-5a88c04e-ddd1-4550-9520-34804204213e.png)

<br>

봉 돌리기
----------

`카메라-Stage >키 pose 생성-Frame by Frame > 키 사이 간격 벌림-Timing > Break down>설득력-Stage`

0. 봉의 위치를 오른손 > Child Of 'hand_fk.R > Set Inverse(손에 붙인다)

![image](https://user-images.githubusercontent.com/30430227/159819108-e79310fe-5e16-4781-9314-2da86f9401fc.png)
![image](https://user-images.githubusercontent.com/30430227/159817326-a374356f-59be-46b6-8366-2ebada5c8203.png)

1. 기본 자세 

![image](https://user-images.githubusercontent.com/30430227/159819248-03b79ab7-99e5-4bd4-826c-53fa649424bf.png)

2. 공격 준비 - 왼발 축으로 180도 회전 오른발 앞으로 딛는다, 시선 정면

![image](https://user-images.githubusercontent.com/30430227/159823439-546e408b-dc7f-4750-aae6-06aa92f480db.png)

3. 공격 - 시계방향으로 회전 

![image](https://user-images.githubusercontent.com/30430227/159824514-5738a0ee-d08f-415e-89ca-98c6459b94f1.png)
![image](https://user-images.githubusercontent.com/30430227/159824525-e5070a0f-2acd-4b11-b5e4-29e4cbc6b530.png)

`Timing`

![image](https://user-images.githubusercontent.com/30430227/159824869-8be9fd80-1da9-4249-bffd-7db285b7ee62.png)

5. Break Down - 머리, 오른팔, 왼팔 순으로 돌아간다(웨이브), 무게중심 뒤쪽

![image](https://user-images.githubusercontent.com/30430227/159826254-bcf62550-837e-41f6-9791-d10e8a3117c0.png)

7. 손목 Break Down - 봉 회전

![image](https://user-images.githubusercontent.com/30430227/159826773-f81e57e0-03cb-45d7-a421-17b7c81e02d8.png)
![image](https://user-images.githubusercontent.com/30430227/159826984-55f64d21-f9ae-48a0-9676-6e54402947be.png)

28. Follow Throuth, 반동 - 몸이 펴진다, 팔등의 긴장이 풀린다

![image](https://user-images.githubusercontent.com/30430227/159828558-bdf47bb6-3883-481a-a4dc-dd2a5a68ec6d.png)

19.  Extream 

![image](https://user-images.githubusercontent.com/30430227/159828859-d9d10207-42bb-4798-8cb3-3bc43d37927a.png)




