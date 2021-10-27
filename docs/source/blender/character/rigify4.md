Rigify 4
==========

<br>

Rigify Basic
-------------

`본 생성 > Edit Mode`

![image](https://user-images.githubusercontent.com/30430227/138868561-3869e116-4501-4ba5-97d8-39d5aeccaf80.png)

`기존 본 삭제 > Basic.copy_chain`

![image](https://user-images.githubusercontent.com/30430227/138868670-0d293f75-f5a7-4e5f-b85b-6b01d0f5c08f.png)

`Generate Rig`

![image](https://user-images.githubusercontent.com/30430227/138868878-eff9621b-3d8a-4f2c-8f58-129627045a0a.png)

`Edit Mode > Add Bone > Subdivide`

![image](https://user-images.githubusercontent.com/30430227/138869184-9193d457-c6f7-4995-b8ad-d60e6bd9ebda.png)

`Pose Mode > Rigify Type`

![image](https://user-images.githubusercontent.com/30430227/138869635-239dceee-f0aa-49ac-a00e-df315fd3cedb.png)

![image](https://user-images.githubusercontent.com/30430227/138869722-7d3fdf16-0d1e-41bf-a777-5fc9fcbe09a0.png)

`Generate Rig`

![image](https://user-images.githubusercontent.com/30430227/138869830-a80d601b-8fed-4f78-915e-8dbd2e7366b0.png)


<br>

Custom Rig 1
-------------

1. Bone

![image](https://user-images.githubusercontent.com/30430227/138995359-5cd3802c-c5ca-4759-bb21-d2aad3bb1c18.png)

`Edit Mode > Delete > Add Leg > Edit`

![image](https://user-images.githubusercontent.com/30430227/138995533-2da3090d-39a7-4c38-bb8d-4f1c10731d32.png)

![image](https://user-images.githubusercontent.com/30430227/138995562-69329c66-086b-44be-a179-ef3d9a8644f7.png)
![image](https://user-images.githubusercontent.com/30430227/138995803-00cb2481-0deb-40cb-a56f-b1f4dfc912a6.png)

`Add Bone 'spine'`

![image](https://user-images.githubusercontent.com/30430227/138999232-0cfcf54c-c95b-4cd3-aa12-0dd5f31005d8.png)
![image](https://user-images.githubusercontent.com/30430227/138999309-4e6e8a20-c754-470c-b32a-5f9888536017.png)

`Pose Mode > Rig Type: Basic_spine`

![image](https://user-images.githubusercontent.com/30430227/138999459-3ed23a2f-49a4-497a-b784-fda63f10054b.png)

![image](https://user-images.githubusercontent.com/30430227/138999481-00329065-52a2-4774-8bad-61057fbd4920.png)

`Add Arm 'limbs.arm'`

![image](https://user-images.githubusercontent.com/30430227/138999859-126cffdf-58f8-4e7e-8c10-74acab37842f.png)

`Add Bone > 'collar.L' > basic_super_copy > Parent > Parent to spine`

![image](https://user-images.githubusercontent.com/30430227/138999894-c8fda52e-07e7-46c1-a53f-fc1699aa1b80.png)

![image](https://user-images.githubusercontent.com/30430227/139000092-2551277e-7f0a-47bf-ab88-737b67b0130b.png)

![image](https://user-images.githubusercontent.com/30430227/139000726-1eaaa749-7bae-4aee-925b-c09ab55d1849.png)

`Extrude > 'pelvis.L' > basic_super_copy(No Control) >Parent > Parent to spine`

![image](https://user-images.githubusercontent.com/30430227/139000312-03eff134-3cfb-4f59-9a65-d9421a8d983e.png)

![image](https://user-images.githubusercontent.com/30430227/139000771-72d31573-8ffc-421d-a277-9044180e5d0c.png)

`spine_super_head > Parent - 목 본의 위치는 spine의 위치와 같아야 한다`

![image](https://user-images.githubusercontent.com/30430227/139000449-cc716432-f5ca-43b9-99b1-e71c1d8147c6.png)

![image](https://user-images.githubusercontent.com/30430227/139000519-22ecd94d-0fc5-49f1-81ac-7b41fa0cce2d.png)

![image](https://user-images.githubusercontent.com/30430227/139000852-c33723e8-604f-4ebd-8090-0eb663e7f46d.png)

`Pose Mode > Connect chain 체크`

![image](https://user-images.githubusercontent.com/30430227/139000968-84bd2545-46fa-4948-9304-0334b46cd14e.png)

`Symmetrize`

![image](https://user-images.githubusercontent.com/30430227/139001045-ca63a37f-4592-41ff-aa0f-214bb1f4fda0.png)

`spine_basic_tail`

![image](https://user-images.githubusercontent.com/30430227/139001366-3b1c6496-d3da-4ab8-aa20-e565e7b76b3d.png)

`rotate > Edit > Extrude > Parent to spine`

![image](https://user-images.githubusercontent.com/30430227/139001720-37334607-de65-45c8-acea-cb1ab3fe5153.png)

![image](https://user-images.githubusercontent.com/30430227/139001785-f20e3c53-fc13-4134-9f51-0b5faf8620ec.png)
![image](https://user-images.githubusercontent.com/30430227/139001799-1c604217-838e-440b-a386-86dc7dd3f370.png)

`Add Bone > 'ear.L','ear1.L' > Parent to Head > Pose Mode 'limbs.simple_tentacle'`

![image](https://user-images.githubusercontent.com/30430227/139002039-27239c16-ab7a-4be6-a0bd-41816e912b86.png)
![image](https://user-images.githubusercontent.com/30430227/139002070-e43f93a1-cfa3-4507-a3e8-cbfadbe200e8.png)

![image](https://user-images.githubusercontent.com/30430227/139002161-89ba5925-a91d-4d8f-9fc0-ce9325f3264c.png)

<br>

2. Generate Rig

![image](https://user-images.githubusercontent.com/30430227/139002438-9f4996d8-e445-4e0d-838b-a853468ea57d.png)

<br>

Custom Rig 2
---------------

1. Bone

`Single Bone > Edit Mode > Delete > 'limbs.leg'`

![image](https://user-images.githubusercontent.com/30430227/139008086-826bc315-5523-44aa-8946-6946250dc1b5.png)

`Move > Edit`

![image](https://user-images.githubusercontent.com/30430227/139008232-42335c76-805c-4abc-8dc9-153d75ccd276.png)
![image](https://user-images.githubusercontent.com/30430227/139008267-7766b6aa-4d45-47fb-a000-7e6a969ccae2.png)

`spines.basic_spine`

![image](https://user-images.githubusercontent.com/30430227/139008393-d5e85329-83a2-45fd-820b-82c5c4d226d3.png)

![image](https://user-images.githubusercontent.com/30430227/139008513-00357de8-df92-4316-9cc0-e689d7824b8d.png)
![image](https://user-images.githubusercontent.com/30430227/139008552-e581351c-b428-4883-b319-b8d7b8c19797.png)

`limbs.arm`

![image](https://user-images.githubusercontent.com/30430227/139008898-83ec101c-f2e0-43f3-8bf5-a0b6361ddf1f.png)

![image](https://user-images.githubusercontent.com/30430227/139008919-5eb698e4-081c-49cb-8fcd-0b5d38ff83fd.png)

`limbs.simple_tentacle > Delete > 'finger', 'finger1 > Edit`

![image](https://user-images.githubusercontent.com/30430227/139008983-025aa61f-ac74-4347-b230-e00031b2d862.png)

![image](https://user-images.githubusercontent.com/30430227/139009027-d8490421-be0b-4e7c-a68e-d141a07833dc.png)
![image](https://user-images.githubusercontent.com/30430227/139009292-18053cd4-8ad3-4a08-b113-63727c4926e4.png)

`Duplicate`

![image](https://user-images.githubusercontent.com/30430227/139009348-d0cd46c4-51ca-4c97-b017-c45f4fd86918.png)

`Simmetrize`

![image](https://user-images.githubusercontent.com/30430227/139010044-73e6dcde-6e74-4dad-aed6-d286f4a9b9a0.png)

`spines.super_head > Dissolve Bone`

![image](https://user-images.githubusercontent.com/30430227/139010218-53f55d1e-389a-4eda-bf39-159b1c0af08f.png)

![image](https://user-images.githubusercontent.com/30430227/139010260-dd360a0a-005e-4de7-b4db-1522e73ab522.png)

![image](https://user-images.githubusercontent.com/30430227/139010452-ab785eae-5acc-4db5-882f-173e9170db76.png)
![image](https://user-images.githubusercontent.com/30430227/139010473-5322aa82-6a90-441c-8edd-c0b5091297a9.png)

![image](https://user-images.githubusercontent.com/30430227/139010668-b6eb5afb-9f18-4329-8145-65790257ca50.png)

`Pose Mode > Connect Chain`

![image](https://user-images.githubusercontent.com/30430227/139010690-6dad30ac-7114-4d8b-b69b-c313ef1b6947.png)

![image](https://user-images.githubusercontent.com/30430227/139010719-5767e11c-186a-45ef-892b-13516205b256.png)

`Edit Mode > Add Bone > 'tentacle.L' > Extrude`

![image](https://user-images.githubusercontent.com/30430227/139010881-8310ec27-6f60-4dfc-834f-131a2e089b56.png)
![image](https://user-images.githubusercontent.com/30430227/139010940-ef23c5e1-64f6-4273-928b-49c05466c90d.png)

`Pose Mode > limbs.simple_tentacle`

![image](https://user-images.githubusercontent.com/30430227/139011072-69c278f0-8e93-4709-9383-dfe6e1f9db2a.png)

`Simmetrize > Extrude`

![image](https://user-images.githubusercontent.com/30430227/139011324-3aabe692-4268-4e7e-830b-bb3d60c1a568.png)
![image](https://user-images.githubusercontent.com/30430227/139011364-4015bd9d-da98-41be-9b40-e254362afd95.png)

`Add Bone > 'eye' > Rig Type: Deform Uncheck > 눈 알의 중심으로 이동 Select to Cursor(Not offset)`

![image](https://user-images.githubusercontent.com/30430227/139012295-3d7f8a1b-1eba-4edf-b384-c09ab4d5b3b1.png)

![image](https://user-images.githubusercontent.com/30430227/139011628-d3c01956-6cf8-4bed-bde2-ac6bf9f318f1.png)

![image](https://user-images.githubusercontent.com/30430227/139011862-e9b5575c-d98b-4a0e-b239-74b276245116.png)

![image](https://user-images.githubusercontent.com/30430227/139012141-fd87c610-59b3-4061-acbe-7e11f0a3bb10.png)

`Extrude > 'pelvis.L' > Rig Type: Control Uncheck > Simmetrize`

![image](https://user-images.githubusercontent.com/30430227/139012538-302d906e-e3bb-4dd1-ae23-42066412586c.png)
![image](https://user-images.githubusercontent.com/30430227/139012563-16caaa7a-98f0-4b96-ac37-ed05c488c087.png)

![image](https://user-images.githubusercontent.com/30430227/139012754-dd86f5e0-b7c1-4e0a-8708-0b218a206e8f.png)

`Copy pelivs > Batch Rename - 펠비스, 체스트, 스컬 본은 말단 본의 변형 영역을 제한한다`

![image](https://user-images.githubusercontent.com/30430227/139013190-fc1791a1-dfde-478d-a79d-c57a1b528daa.png)

![image](https://user-images.githubusercontent.com/30430227/139013312-b46c65a1-6ba7-4b47-bf04-452ce184e6d7.png)

`Copy chest > Batch Rename`

![image](https://user-images.githubusercontent.com/30430227/139013527-97245fa3-baeb-448f-ac91-9d174ebcf7f4.png)

![image](https://user-images.githubusercontent.com/30430227/139013561-84ff2f47-222a-48fa-9b12-d4d9b23269dd.png)

`Parent`

![image](https://user-images.githubusercontent.com/30430227/139013819-1bc2d354-b719-414d-9c25-f9cf501fdf73.png)

![image](https://user-images.githubusercontent.com/30430227/139013776-bf64e22e-dd3d-4a79-9c75-c092f1062d1c.png)

![image](https://user-images.githubusercontent.com/30430227/139013875-abb08649-fcd5-4c9b-b8d0-12f2e3da1db5.png)

![image](https://user-images.githubusercontent.com/30430227/139013978-b813ccf7-53ef-4dad-9caa-90111c27bdfe.png)

![image](https://user-images.githubusercontent.com/30430227/139014061-3813faaf-6089-49c4-87c9-90e98e76b979.png)

![image](https://user-images.githubusercontent.com/30430227/139014129-8e6fb335-276f-4cb2-acce-edc3a64b1ecf.png)

![image](https://user-images.githubusercontent.com/30430227/139014299-28a2bf6d-4702-4974-850d-2e4dd3fdc464.png)

<br>

2. Generate Rig

![image](https://user-images.githubusercontent.com/30430227/139014552-864e024d-23de-41e9-a2b2-0e511113d67d.png)

`눈 Weight > 눈 메쉬 와 릭 쉐이프 선택 후 Pose Mode `

![image](https://user-images.githubusercontent.com/30430227/139015251-7a8ceecd-74b4-4199-9366-9d776646e1c7.png)

![image](https://user-images.githubusercontent.com/30430227/139016368-fa04b9ad-12fb-4fd7-8f6b-d1d7a299379d.png)





