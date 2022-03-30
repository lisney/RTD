Action B
===========

```
기존 Pose Library 등록 포즈 순차(사이클) 선택  Alt-L > 마우스 휠 or 키보드 Left/Right
```

![image](https://user-images.githubusercontent.com/30430227/160534842-3e4d1891-2f25-4c0d-a7b2-61c5121397a1.png)

<br>

걷기 
-----

```
Pose Library
Contact > Down > Pass > Up > Contact (0~24프레임)
상체를 살짝 앞으로 구부리고 얼굴은 정면, heel_ik를 사용해 발가락 구부린다
Up포즈에서 앞으로 추진하기위해 Pass포즈에서는 약간 뒤로 즁심이동(Torso)
Pass,Up 시 골반은 올라간 발쪽으로 기울어지며 무게중심(torso)은 반대로 이동
Paste Pose Flipped
Down,Up은 없는게 자연스러운가..
```

![image](https://user-images.githubusercontent.com/30430227/160539612-9801a095-c102-4fda-ac7a-7cb19e8d51f0.png)
![image](https://user-images.githubusercontent.com/30430227/160539587-90405510-5a0d-43ac-94e0-eb986bbe9aed.png)

`0,24프레임Contact > 12프레임Flip> 6,18프레임Pass ...순으로 Alt-L, Pose Copy는 해당프레임PlayHead`

![image](https://user-images.githubusercontent.com/30430227/160538607-284751bd-4f10-4359-9e99-f6113306bf8d.png)
![image](https://user-images.githubusercontent.com/30430227/160538632-5f6706cd-9002-4236-bcc4-cc8ff4ff2975.png)
![image](https://user-images.githubusercontent.com/30430227/160538660-7746fa36-3a63-4118-b659-1e253b9a48c3.png)
![image](https://user-images.githubusercontent.com/30430227/160540144-3707a206-e721-4b3e-8203-69f707c092aa.png)

`Tip. Pass전에 뒷 발을 힘차게 차주면 추진력이 생긴다`

![image](https://user-images.githubusercontent.com/30430227/160543735-d52a626b-6e40-48b5-8203-3a9841f8303e.png)

<br>

뛰기 
-----

`Contact > (Down) > Kickoff >(Up)> Contact`

![image](https://user-images.githubusercontent.com/30430227/160557223-8791cd65-c9d5-4cd6-a1b6-c1a7048e73ff.png)

`팔은 덩치 크면 밖으로 벌린다, 앞 뒤 홀드하고 휘두르는 동작을 빠르게한다`

![image](https://user-images.githubusercontent.com/30430227/160557310-2b18c8e1-c351-4c18-80f5-2f1d11cd037a.png)
![image](https://user-images.githubusercontent.com/30430227/160557344-a6feb1f6-e2eb-4735-9814-f8f0f4847348.png)
![image](https://user-images.githubusercontent.com/30430227/160558478-4840d2e3-80f6-4269-94a3-9d1059f22551.png)

`허리 구부리기 Nonlinear::Combine > Tab Key 키프레임 편집`

![image](https://user-images.githubusercontent.com/30430227/160564752-f8703e51-ecd5-4a66-9a93-d1ec17bbd5ea.png)

![image](https://user-images.githubusercontent.com/30430227/160564857-6b8edbaf-8959-43e7-9641-b99139bad6b3.png)

`팔 앞으로 왔을 때 구부린다`

<br>

몬스터 모션
-----------

`rig에 Bone추가 'shield' > 메쉬 & rig 선택 후 Pose모드> shield본 Parent>ChildOf-Set Inverse`

![image](https://user-images.githubusercontent.com/30430227/160578069-c69053a7-9f0f-4dd6-975d-f6cd68f068c9.png)
![image](https://user-images.githubusercontent.com/30430227/160578171-ace0d19d-a6de-4c50-b04a-38b9793565f6.png)

1. 숨쉬기 

`0, 24프레임 기본 포즈 전체 키 > AutoKey`

![image](https://user-images.githubusercontent.com/30430227/160595704-e20cddbb-30df-41d2-add4-99cead10cffb.png)

`12 torso 대각선 위/아래, 올라갈 때 - 머리 숙이고, 가슴 펴고, torst(척추) 숙이고`

`6, 18 방패-상완(펴짐회전,팔 구부림)/(꼬임회전, 팔 펴짐)`

![image](https://user-images.githubusercontent.com/30430227/160597410-0ca608ed-7ca7-410b-a76f-5dfb3aae6aff.png)
![image](https://user-images.githubusercontent.com/30430227/160597429-49774dd2-e9e4-4ac3-8dd0-61c0d036911c.png)

<br>

2. 공격 

`얼굴은 정면, 몸은 뒤로 뺐다가 앞으로 나간다, 양 팔은 수평, 공격전 breakdown-칼을 뒤로 쭉편다`

![image](https://user-images.githubusercontent.com/30430227/160728639-08ccdef0-b220-4c1a-92fa-7ad8c1ca0662.png)

![image](https://user-images.githubusercontent.com/30430227/160728548-73777954-1654-4904-a485-7e0cf7bef97d.png)
![image](https://user-images.githubusercontent.com/30430227/160728588-746f4d10-49a1-4e11-86fb-3d788c08ab49.png)
![image](https://user-images.githubusercontent.com/30430227/160728616-72927b56-0a5d-4b7e-9b45-a2524cf997e2.png)

`0.idle > 5.anticipation > 10.hold > 12.attack>14.followthrough(팔 끝까지 회전) >20.hold>24.idle`

`5프레임 breakdown 수정(오른팔 살짝 내리고, 왼팔 펴고)>공격 시 웨이브-torst..arm>14.방패(팔) 회전`

<br>

3. 피격 

`0.idle > 2.damage > 7.hold > 16.idle`

![image](https://user-images.githubusercontent.com/30430227/160735100-929daab6-bbdd-443a-be25-29cd52043a11.png)
![image](https://user-images.githubusercontent.com/30430227/160735133-f0ac72f8-50d8-4416-bc6c-1da8b23e6dde.png)

`1.방패로 막을려다가 팡>waist다음에 가슴,머리,팔...돌아올 때도`

<br>

캐릭터 모션 
-----------

1. 공격 대기 동작 - 좌우(정면이 아니라 발 벌린 방향) 폴짝폴짝..TOP뷰에서

`0.18.36.torso & footIK선택 이동`

![image](https://user-images.githubusercontent.com/30430227/160760565-75766db4-785f-44f3-bc03-e3403fe54a94.png)
![image](https://user-images.githubusercontent.com/30430227/160760531-47a0d3ed-be4c-4497-8212-297802230d7b.png)

`2.20.hold > 9.27.폴짝 - torso,spine,chest 펴고 머리 내린다`

![image](https://user-images.githubusercontent.com/30430227/160761578-d9fd0c41-9af5-4ea4-9663-34853b98ed25.png)

`좌우 발 Overlapping - Shift-E 앞발(hold.2>heel.2>off), 뒷발은 2프레임 Offset 출발`

`좌우 팔은 몸과 Overlapping - 올라가는 중간 프레임에 내려간다`

![image](https://user-images.githubusercontent.com/30430227/160764300-ab402f04-0ed9-42f3-a0ca-fd46a353f81d.png)















