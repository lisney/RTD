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


