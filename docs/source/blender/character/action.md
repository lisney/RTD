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
