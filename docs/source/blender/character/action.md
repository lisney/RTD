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
※ 보외법 또는 외삽은 수학에서 원래의 관찰 범위를 넘어서서 다른 변수와의 관계에 기초하여 변수의 값을 추정하는 과정이다.
#Child Of Constraint 에서 Set Inverse 시 부모의 위치로 이동하지 않는 경우 // 위치를 원점으로 옮긴다음 실행해본다Select to Cursor(원점)
#Reset Pose 문제(모션캡쳐용 T-포즈를 키애니용으로 변환할 때 필요)
포즈를 잡은 상태에서 메쉬모드로 나와 메쉬를 선택한다
Modifier에서 Armature를 Copy한 후 원래 Armature Modifier를 'Apply'한다음
포즈모드로 들어가 Apply Reset Pose한다
#IK 로테이션 문제
=Edit 모드에서 Bone을 꺽어야한다(포즈모드에서하면 안됨)
#손과 발의 IK 본은 Root본에 Parent하고 Target은 힙본에 한다
```

`기즈모 단축키 설정 E-Move, D-Rotate`

`뼈 선택 이동 '[', ']' `

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


