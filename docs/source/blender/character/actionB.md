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









