P2 Design
==========

Rig Equipment Slot
-------------------

``'Switch, Holder', 'Double hand' and 'Apply Pose as Rest Pose'``

>>> 1. Axe 본 생성 2. Axe 복사 'Axe.Target'  3. Axe - Copy Transform Constraint

![image](https://user-images.githubusercontent.com/30430227/163763040-835b46bc-cf6f-4ada-a515-638fc3305511.png)
![image](https://user-images.githubusercontent.com/30430227/163763094-4f22bb6a-4984-49b7-a79b-38bf334378f0.png)

>>> 1. 도끼 > Vertex Group New 'Axe' > Add Armature Modifier > Edit Mode Selece All > Assgn 'Axe'

![image](https://user-images.githubusercontent.com/30430227/163763629-15d0708e-f529-4fc2-9b95-294c5fc90dbd.png)
![image](https://user-images.githubusercontent.com/30430227/163763641-2b97360a-cdfa-40b3-ae66-1253756f82bf.png)

![image](https://user-images.githubusercontent.com/30430227/163763651-cb856e04-e34d-41a7-af56-1439c627f910.png)

>>> Axe.Target 복사 'Axe.Control' > Copy Transform > Dup Axe.Control 'Axe.Snap' > Parent

![image](https://user-images.githubusercontent.com/30430227/163778826-a4e0bbf4-e3de-457a-8990-4fe6258f2576.png)

>>> Dup Axe.Snap 'Axe.Snap.Hand.R' > Move to Hand > Axe.Control Copy Transform

![image](https://user-images.githubusercontent.com/30430227/163779173-669d40a6-94f8-49bb-b75b-dea68d33a7ad.png)
![image](https://user-images.githubusercontent.com/30430227/163779223-e104871e-fd8b-4c8c-8c7e-6d55737be817.png)

**포즈모드에서 Axe.Snap.hand.R 본을 수정한 후 Rest Bone으로 변환**

![image](https://user-images.githubusercontent.com/30430227/163780115-494984f2-40db-4efd-970a-66bf947060e3.png)

>> Axe.Snap.hand.R Symetry Copy > Copy Trnasform > Switching - 눈 클릭

![image](https://user-images.githubusercontent.com/30430227/163780447-9e35c23f-8251-4c3f-99c5-df5c13e561d3.png)

![image](https://user-images.githubusercontent.com/30430227/163780664-54946c23-211a-4f3e-bb8b-72c0ce714488.png)

>> Dup Axe.Snap 'Axe.Snap.back` > Copy Transform > Parent back, hands

![image](https://user-images.githubusercontent.com/30430227/163781358-35b3ee9d-17d3-4127-990c-68f1898f1168.png)

![image](https://user-images.githubusercontent.com/30430227/163781522-75bcac78-049d-4e07-ac5b-91966b14d8b4.png)

**Axe.Snap.back 본 수정( 회전 축 본 생성) > Axe.Snap.back 복사-이동(Normal 축) > Parent**

![image](https://user-images.githubusercontent.com/30430227/163782555-888468bb-b36b-4583-bb6f-11e245b6aac5.png)

![image](https://user-images.githubusercontent.com/30430227/163782235-ea434b9d-3d71-49c4-9e75-626466f49e56.png)

**Scale 문제 > 본 2번 복사 > Parent 중간본(바깥본 선택 Ctrl-클릭- Shift-가운데 본 선택)>중간본 Parent-root**

![image](https://user-images.githubusercontent.com/30430227/163784235-075e09ca-678c-43fe-abc3-cb05e37c615e.png)

![image](https://user-images.githubusercontent.com/30430227/163785383-f0ab6457-ff3a-400b-8e2c-2ffef5163e59.png)
![image](https://user-images.githubusercontent.com/30430227/163785512-61bf2d2d-2dd3-40dc-8176-815aa925c120.png)

**작은본에 중간본을 Copy Location > Copy Rotation**

![image](https://user-images.githubusercontent.com/30430227/163785676-136be6f7-fe34-4164-a18a-a3a5be62772e.png)
![image](https://user-images.githubusercontent.com/30430227/163786005-6299e138-8e40-49ad-b609-c9f7412f4781.png)

>>> 스위치 본 > Dup Axe.control 'Axe.property' > Custom Properties 'ADD' > Copy as New Driver

![image](https://user-images.githubusercontent.com/30430227/163786559-ed0a8d34-432b-433d-b8b3-b00137493864.png)
![image](https://user-images.githubusercontent.com/30430227/163788987-f1e4a4e6-2a8d-4127-aa58-d431aff4e348.png)

**Influence > Paste Driver > Edit Driver>나머지도(-2, -1, 0)**

![image](https://user-images.githubusercontent.com/30430227/163787812-e79e5022-533f-4f51-b943-d3a451161ce0.png)

![image](https://user-images.githubusercontent.com/30430227/163789242-a9cf51eb-42bc-424a-95a9-794f4f340c1a.png)

**Bone Manager Addon-Snap-back 프로퍼티**

![image](https://user-images.githubusercontent.com/30430227/163789531-42158326-35c3-44d5-85e7-a0c1f962e9db.png)

>>> 양 손 > IK 본 복사 'hand_ik.Snap.L/R' > Parent > Custom Shape Off

![image](https://user-images.githubusercontent.com/30430227/163904889-6eb3f9ff-ab88-4c52-b3ad-6a7e2b132af5.png)
![image](https://user-images.githubusercontent.com/30430227/163905105-ada17688-1290-4f1a-9294-69b9e6542b83.png)

**hand_ik.Snap.L 복사 'hand_ik.SnapT.L' > Copy Transform

![image](https://user-images.githubusercontent.com/30430227/163905437-36b4bf8b-cb13-45eb-a10a-55ce3d17fb00.png)

**New bone 'bothHand' > Parent 'hand_ik.SnapT.L/R >

![image](https://user-images.githubusercontent.com/30430227/163905967-fdc64a7f-d111-4531-948d-9ecf9cbfac6f.png)

>> Custom Properties > Copy as New Driver > Paste

![image](https://user-images.githubusercontent.com/30430227/163906249-0ecb3f5d-8431-4aec-bc80-a524bf3af9f1.png)

![image](https://user-images.githubusercontent.com/30430227/163906406-545ce8fe-054a-4b02-921f-3ec129fc07a2.png)
![image](https://user-images.githubusercontent.com/30430227/163906533-c99db4b5-220b-405a-8c94-2a981d98acd4.png)

**bone Move

![image](https://user-images.githubusercontent.com/30430227/163906997-b58fd272-5d5e-478a-8dc8-cfc5e160364a.png)



