Rigify 1 - 기존방식
===================

1. Bone

`In Front Axies: 1, 무릎 joint는 좀 더 앞쪽으로`

![image](https://user-images.githubusercontent.com/30430227/138624555-099165bf-4aa5-4625-84e0-3cbab4d0611e.png)

![image](https://user-images.githubusercontent.com/30430227/138624653-80413044-676b-4f08-9bfe-ef996674ba08.png)
![image](https://user-images.githubusercontent.com/30430227/138624713-e02ec165-d4bb-4af7-bfe1-124f8abdbb2a.png)

`F2 - rename`

![image](https://user-images.githubusercontent.com/30430227/138624885-15b929d9-dc82-4804-9e55-4f278b9ef3bd.png)
![image](https://user-images.githubusercontent.com/30430227/138627379-d9c1afbe-7acb-4b0c-8d60-5f45af52702d.png)


![image](https://user-images.githubusercontent.com/30430227/138624993-43912069-19a9-4334-9edb-5da1f6bf0dee.png)

`Move`

![image](https://user-images.githubusercontent.com/30430227/138625099-d2cb9ce9-1c9c-4ab8-a994-90e8ba0a8454.png)

`Add Bone  'spine'A`

![image](https://user-images.githubusercontent.com/30430227/138625312-f5e6aab5-5c76-4dd4-9e38-46922a70c144.png)
![image](https://user-images.githubusercontent.com/30430227/138625401-cf98505a-8ab5-4437-913b-38e64f1ad8f4.png)

`neck, head`

![image](https://user-images.githubusercontent.com/30430227/138625522-a9e6b61c-2b2f-447f-b083-ec7b06d2115d.png)

`Add Bone 'upper_arm.L, lower_arm.L'`

![image](https://user-images.githubusercontent.com/30430227/138625736-0acf4935-d964-4340-a197-96260aeb3123.png)
![image](https://user-images.githubusercontent.com/30430227/138625753-58a56037-0b99-4204-b144-0daac59d0166.png)

`hand.L`

![image](https://user-images.githubusercontent.com/30430227/138625964-18fccf1e-b442-432d-a968-2453c7f2fe20.png)

`collar.L`

![image](https://user-images.githubusercontent.com/30430227/138626396-e3784e52-a1ad-4138-8f08-fb62bdf9de9d.png)
![image](https://user-images.githubusercontent.com/30430227/138626432-85f2ad17-2df0-44fc-98d5-65ce02e29823.png)

![image](https://user-images.githubusercontent.com/30430227/138626488-a6058617-bc51-4f25-9458-a81788afb7dc.png)

`Extrude Bone 'pelvis.L'`

![image](https://user-images.githubusercontent.com/30430227/138626825-8a9423fc-70c8-444e-9a34-f6c378f3e7c4.png)

`Parent`

![image](https://user-images.githubusercontent.com/30430227/138626865-a987fb8d-6cca-4c89-a947-0fbb8196323d.png)

![image](https://user-images.githubusercontent.com/30430227/138626960-03b7aca8-d22f-480b-91ce-ac39ee545493.png)

![image](https://user-images.githubusercontent.com/30430227/138627000-2298d9c7-0b3e-442f-b787-241000279b70.png)

![image](https://user-images.githubusercontent.com/30430227/138627058-f11bf7bc-bc10-48cc-bf38-ebd8da2ef0d8.png)

`Add Bone root'`

![image](https://user-images.githubusercontent.com/30430227/138627631-42cb3f8a-6541-47cb-8a2d-b19fcd1d9671.png)

`Copy rootBone & Scale & Move 'pelvis_control'`

![image](https://user-images.githubusercontent.com/30430227/138627776-67ba6b48-aac6-484f-bcfc-3c5954783db3.png)

`Parent`

![image](https://user-images.githubusercontent.com/30430227/138627881-edd48738-e7f2-4eb1-8d48-d4432504681b.png)

![image](https://user-images.githubusercontent.com/30430227/138627929-9041ff99-35ca-405a-baff-465856ae9235.png)

<br>

2. 컨트롤

`extrude & Clear Parent 'IK.L'`

![image](https://user-images.githubusercontent.com/30430227/138628230-b97fa6fa-cf21-4299-ae60-ea49d39a07e6.png)

`IK Constraint`

![image](https://user-images.githubusercontent.com/30430227/138641713-f0f9354d-1f92-4b56-92de-5cf641a2ab4a.png)

`Chain Length: 2, Lock IK`

![image](https://user-images.githubusercontent.com/30430227/138642125-e9b8dc75-3938-4674-a2d4-af3652ec29ac.png)

`Extrud >Clear Parent > Move 'pole.L'`

![image](https://user-images.githubusercontent.com/30430227/138642267-9acb220b-d13f-40e7-8961-f5dbdec1d41b.png)
![image](https://user-images.githubusercontent.com/30430227/138642284-c70409da-aec3-420a-b45d-720e14ac9530.png)

![image](https://user-images.githubusercontent.com/30430227/138642453-49075c35-e5a0-408e-a914-2edd148f17a3.png)

`pole > Parent`

![image](https://user-images.githubusercontent.com/30430227/138642647-5949df89-f531-4da7-a2b7-5fe0b34d05c8.png)

`IK bone > Parent`

![image](https://user-images.githubusercontent.com/30430227/138644828-e21768ef-3fc1-424f-9ccd-b1b1e385b9bd.png)

`foot > Clear Parent > CopyLocation`

![image](https://user-images.githubusercontent.com/30430227/138642973-d8342d72-6027-4b73-bcde-64d771ab3f0e.png)

![image](https://user-images.githubusercontent.com/30430227/138643093-96a62461-b3a9-4e6b-86f4-6835ed6f57ce.png)

`Head/Tail: 1`

![image](https://user-images.githubusercontent.com/30430227/138643237-0cccd22b-02c8-4ab6-b3fc-95a84e267e93.png)

![image](https://user-images.githubusercontent.com/30430227/138643252-4676b9a4-5088-4ad3-8649-78b5a3294376.png)
![image](https://user-images.githubusercontent.com/30430227/138643268-08b29f1a-3b3b-4e74-89c9-de1b67e6ca9b.png)

`Symmetrize`

![image](https://user-images.githubusercontent.com/30430227/138644419-0b10900e-5737-4772-9f52-2bc0e23fdef2.png)

<br>

3. Controls > Deform

![image](https://user-images.githubusercontent.com/30430227/138645156-f730ba6f-53a9-4b40-b1fb-61bc25f7768b.png)

`Alt 클릭, 선택한 모두에 적용`

![image](https://user-images.githubusercontent.com/30430227/138645223-28c3647d-882a-405a-a65c-addeab6f8add.png)


<br>

4. Weight

![image](https://user-images.githubusercontent.com/30430227/138645547-a9c55f50-2501-47a9-8b2e-984ed3d4353c.png)

<br>

5. Custom Shape

![image](https://user-images.githubusercontent.com/30430227/138645848-fd15fb8f-74cc-414c-81cb-ab2796302800.png)

![image](https://user-images.githubusercontent.com/30430227/138645882-0d78fc05-f6c0-4e61-b7aa-a3a9d762e22a.png)
![image](https://user-images.githubusercontent.com/30430227/138645929-5fc82bca-0f9c-42f0-9603-f19b2ff323e8.png)

![image](https://user-images.githubusercontent.com/30430227/138645963-e64f5f8a-968d-421a-83b5-76b83fe31fec.png)
![image](https://user-images.githubusercontent.com/30430227/138645997-e38193e4-9d7a-42bf-99e3-918aae7a9341.png)

![image](https://user-images.githubusercontent.com/30430227/138646022-b2361a30-22ac-46cc-bc78-db89cc7b60be.png)
![image](https://user-images.githubusercontent.com/30430227/138646057-6b3e7e57-f1c8-466b-bcef-d1034a6f2d07.png)

![image](https://user-images.githubusercontent.com/30430227/138646097-52e8417e-14c9-4455-96d2-78cc61c954d1.png)

![image](https://user-images.githubusercontent.com/30430227/138646155-85155370-267f-4472-abb2-08f10b333755.png)


