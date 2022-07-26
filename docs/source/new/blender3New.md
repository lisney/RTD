Blender3.1
================

뷰포트 분리 
------------

**뷰포트 별로 다른 카메라를 사용하거나 다른 콜렉션을 보이게 할 수 있다**

![image](https://user-images.githubusercontent.com/30430227/168501778-ad43f81a-a3c7-466a-a636-45de6fd802f9.png)

![image](https://user-images.githubusercontent.com/30430227/168501797-73c55fe6-a730-4b6f-9735-8f767633a7de.png)
![image](https://user-images.githubusercontent.com/30430227/168501823-d3b6decd-cf27-46f5-be47-f8c6cd32902b.png)


도시 -Geometry Nodes
--------------------

![image](https://user-images.githubusercontent.com/30430227/168701804-82da7f98-490e-4364-9f82-5233e3bb7721.png)

![image](https://user-images.githubusercontent.com/30430227/168701865-1b15e853-4344-480a-90b2-f94545e81e0e.png)


`Bevel- 옆으로 돌출했던 상하단 면을 Z-축 방향으로 Scale Down`

![image](https://user-images.githubusercontent.com/30430227/176838832-7bca6186-0100-4b06-9647-d5e099947404.png)
![image](https://user-images.githubusercontent.com/30430227/176838884-573a78c7-86e7-4f28-b02d-14e06f5ca53e.png)
![image](https://user-images.githubusercontent.com/30430227/176839635-5c554456-e310-4642-ac6d-688d095905f2.png)

![image](https://user-images.githubusercontent.com/30430227/176839616-ed96c8db-317d-417a-a368-0950d3e40262.png)


`Convex Hull -열린 면을 닫아주는 효과`

![image](https://user-images.githubusercontent.com/30430227/178129619-1ff383d6-2fb7-42ee-9b81-bb071fd37e33.png)

![image](https://user-images.githubusercontent.com/30430227/178129652-087e07d5-cfda-4983-b409-e202f1152649.png)


`노드 정렬- Node Wrangler>Align -Shift-'='`


`캡처 Attribute - 기본 point는 노말방향 정렬 잘된다`

![image](https://user-images.githubusercontent.com/30430227/176846311-01b07ebf-2d82-4df3-930f-430fb1dd933e.png)
![image](https://user-images.githubusercontent.com/30430227/176846492-cbd06656-b749-490b-b85e-83e9cc27d5d3.png)

![image](https://user-images.githubusercontent.com/30430227/176846365-855553a5-7e63-4233-bf41-953f0ad31661.png)

![image](https://user-images.githubusercontent.com/30430227/176846534-3ea47f9e-5c2c-423e-85a1-55d11bae46a2.png)

`하지만 Mesh to Point를 지나면서 Normal이 리셋되는거같다. 그래서 기존의 Gometry에서 Normal을 캡처하게된다`

![image](https://user-images.githubusercontent.com/30430227/176846658-045902e3-e31b-4d8b-a841-f587002dc193.png)
![image](https://user-images.githubusercontent.com/30430227/176846872-7bb81f6b-bf64-46fb-a473-4bc192b48079.png)
![image](https://user-images.githubusercontent.com/30430227/176847360-0526fe79-e56b-4e44-bcf2-cba2160a63fb.png)

![image](https://user-images.githubusercontent.com/30430227/176846696-fc3b2aed-1f9a-4c85-8574-993a0cda4422.png)
![image](https://user-images.githubusercontent.com/30430227/176846908-11487bee-0f11-4f20-a2e2-264175b8b48b.png)


`Normal 회전`

![image](https://user-images.githubusercontent.com/30430227/176869205-2b538240-6de0-4132-bd1a-bfe84aec8e9d.png)
![image](https://user-images.githubusercontent.com/30430227/176869242-1e66571e-20be-4fb7-9e98-6c9cb2b5d8ec.png)

![image](https://user-images.githubusercontent.com/30430227/176869912-7b1429c6-aad1-4145-83e0-702fd4ee8bcf.png)
![image](https://user-images.githubusercontent.com/30430227/176869980-9cb070d9-8428-4e6a-928c-d42602d29aa1.png)

![image](https://user-images.githubusercontent.com/30430227/176870997-046533f4-d8b2-4bea-99b6-342c9cbac720.png)

![image](https://user-images.githubusercontent.com/30430227/176871032-07a96bbc-445f-4cf9-acb5-2d4463fde754.png)


`화살표 - 벡터차는 앞 점이 종점 즉 가리키는 대상 +Y가 된다`

![image](https://user-images.githubusercontent.com/30430227/178089170-ec1b5d16-0eb4-4b3b-9641-81f749b87c5c.png)
![image](https://user-images.githubusercontent.com/30430227/178089213-1e65cb16-127b-4463-90a4-91a6f20f51fa.png)
![image](https://user-images.githubusercontent.com/30430227/178089217-08b195b9-75fe-4a5a-ae1a-60025d98ff2c.png)

![image](https://user-images.githubusercontent.com/30430227/178089233-2d495271-8f3f-4c18-abb5-292e2b8c3550.png)


`고랑 Map Range 거리가 멀어질 수록 값이 커진다>From 시작 시점과 끝 시점을 좁힌다>to 최대값을 `

![image](https://user-images.githubusercontent.com/30430227/178089663-c288c604-f341-471d-85d5-f87bf2792ce6.png)
![image](https://user-images.githubusercontent.com/30430227/178089656-613c1e50-8ad0-4033-b826-c667b9c9404d.png)

![image](https://user-images.githubusercontent.com/30430227/178089678-a7745cdb-75e2-4e50-aa9c-044e93d6b0ae.png)


`입체 노이즈: RGB Color-CombineXYZ-Vector`

![image](https://user-images.githubusercontent.com/30430227/176868184-56f9466b-118c-4e1c-8ea2-950bf58cdb8a.png)

![image](https://user-images.githubusercontent.com/30430227/176868282-c1189b53-ebee-4d07-a6be-2507159c34dc.png)


`Proximity`

![image](https://user-images.githubusercontent.com/30430227/178130081-f3889088-868f-4e13-8680-21ab89d9121a.png)

![image](https://user-images.githubusercontent.com/30430227/178130102-7e601eb2-8b64-4d5a-8b8f-684b071112c1.png)


`Clamp`

![image](https://user-images.githubusercontent.com/30430227/141369015-d8829dea-a7cd-4924-a3cd-e0883124e28b.png)
![image](https://user-images.githubusercontent.com/30430227/178706059-bccfd9bc-6d82-41c7-8f0d-34b2b5601b39.png)

![image](https://user-images.githubusercontent.com/30430227/141368982-f374d3bf-085f-4700-bc28-f738f0c3cfbf.png)


Sci-Fi - with JSplacement
---------------------

![image](https://user-images.githubusercontent.com/30430227/168704473-f0a2f6fa-6c63-4b2e-a066-745c7afbc09d.png)

![image](https://user-images.githubusercontent.com/30430227/168704521-0b4f463c-90ba-4c67-a422-68c970d7bd59.png)

![image](https://user-images.githubusercontent.com/30430227/168704532-888af031-cba7-4058-9fb1-c705b23a4dff.png)


LoopCut Tip
--------------

```
'E' 동등하게 > 'F' 뒤집기
```

![image](https://user-images.githubusercontent.com/30430227/169924345-b5c88148-418e-4792-8aa9-043f2cbb4c9f.png)
![image](https://user-images.githubusercontent.com/30430227/169924374-9d099778-0f1f-4755-b0ca-fd7b4e0778aa.png)


타임라인 싱크 - PlayHead
-------------------------

**싱크할 Editor창 메뉴 전부 옵션을 켜준다**

![image](https://user-images.githubusercontent.com/30430227/172775343-6d834e22-c5d6-4edd-88b3-9797e582ef18.png)



비디오시퀀스 랜더링 끄기
----------------------

![image](https://user-images.githubusercontent.com/30430227/172777502-202f992f-bdd5-45fe-bc14-cb11835b6224.png)


Bsurface 
----------

1. BSurface Mesh 이용

![image](https://user-images.githubusercontent.com/30430227/176342776-2722cad3-3599-48e7-9b58-801f18fd07dc.png)

`Annotation 사용 > Initialize > Draw > Add Surface`

![image](https://user-images.githubusercontent.com/30430227/176342833-ebedb0cc-a5cf-4e5a-a63b-562a81b3b0eb.png)
![image](https://user-images.githubusercontent.com/30430227/176343351-15dc7178-0aa3-4325-8318-ebcc9a8758ce.png)

![image](https://user-images.githubusercontent.com/30430227/176344292-acb41d07-594d-4cba-85c6-9799a12ed094.png)
![image](https://user-images.githubusercontent.com/30430227/176343374-5e730212-de71-4a11-8c37-5a41b45a0c88.png)

`Grease Pencil 사용 > Draw > Select Grease Pencil > Add Surface`

![image](https://user-images.githubusercontent.com/30430227/176344163-4e40abf0-a1a7-4eea-8bd8-b9207e0f669d.png)
![image](https://user-images.githubusercontent.com/30430227/176344116-bcd606af-0752-41ff-8054-b17023ac94f4.png)

![image](https://user-images.githubusercontent.com/30430227/176344221-974e31fa-deb1-4a2e-baff-5ba345c74a72.png)
![image](https://user-images.githubusercontent.com/30430227/176344292-acb41d07-594d-4cba-85c6-9799a12ed094.png)
![image](https://user-images.githubusercontent.com/30430227/176344332-c78575b9-e4ef-40dd-9cc1-851ec6b72bae.png)

`Grease Pencil 추가 선 그리기 > Auto Toggle ON > Draw > Add Surface`

![image](https://user-images.githubusercontent.com/30430227/176348619-b95cf0c2-67bd-4f44-af3b-9ebef73c8a6e.png)
![image](https://user-images.githubusercontent.com/30430227/176348647-08dc1a3e-b0bb-4d7b-83cd-48b0a2cd65c7.png)

![image](https://user-images.githubusercontent.com/30430227/176348468-07958ada-931a-434e-a422-af943cd955ff.png)

`Curve 추가 > Initialize > Curve 선택 > Add Surface`

![image](https://user-images.githubusercontent.com/30430227/176349084-8bd3fb72-3556-43ee-bcae-e719e50ca875.png)
![image](https://user-images.githubusercontent.com/30430227/176349095-be8967ba-a135-48dc-8846-d4c7601d3375.png)

![image](https://user-images.githubusercontent.com/30430227/176349221-0bfefbf0-ca06-4c89-a920-456971c0e5b4.png)
![image](https://user-images.githubusercontent.com/30430227/176349204-294c334d-79e9-4399-93ae-08918753b7db.png)

`응용 > Add Annotation > Annotation to curves  > Edit curve > 복사 이동 >Add Surface `

![image](https://user-images.githubusercontent.com/30430227/176349479-7e0802c8-3671-41aa-a3f0-3ada052563af.png)
![image](https://user-images.githubusercontent.com/30430227/176350143-132a0041-c0fa-4287-97f4-75bee780afa8.png)

![image](https://user-images.githubusercontent.com/30430227/176350436-f6406988-fef9-4bc3-98bb-2d1b429bf989.png)
![image](https://user-images.githubusercontent.com/30430227/176350394-6d0798da-ac96-460d-9f25-796015d125ec.png)


2. 기존 메쉬 이용 

![image](https://user-images.githubusercontent.com/30430227/176350712-d4621ac7-0ff3-40b1-ac81-294071dee634.png)
![image](https://user-images.githubusercontent.com/30430227/176350726-c8a80965-e8ad-4c3d-b394-a1d910edb4f3.png)

![image](https://user-images.githubusercontent.com/30430227/176350761-1af07f55-1c8a-473a-82eb-149b77af391a.png)

`연속 선택 방향 - 드로잉 라인 방향(세로는 비대칭으로 그린다. 마지막 라인이 한쪽으로 치우치게)`

![image](https://user-images.githubusercontent.com/30430227/176351715-5bd88a09-8bd5-48a4-b9f5-010f6b65c32f.png)

![image](https://user-images.githubusercontent.com/30430227/176351625-b6839ca5-704e-45e4-bcbf-c1a402d0062b.png)
![image](https://user-images.githubusercontent.com/30430227/176351679-5d9e66a7-de1d-49df-9003-fc6c5282ca01.png)

![image](https://user-images.githubusercontent.com/30430227/176352440-03cbee50-4169-486a-a32b-a3c2292a8f80.png)
![image](https://user-images.githubusercontent.com/30430227/176353061-70478c1e-7d44-4309-aebf-6e9390ee4ff9.png)

![image](https://user-images.githubusercontent.com/30430227/176353826-18c033fe-1b6a-48ca-8b44-3fa2a60ff425.png)
![image](https://user-images.githubusercontent.com/30430227/176353849-0b57d174-6b44-4540-8940-c5938ccfcc40.png)

![image](https://user-images.githubusercontent.com/30430227/176353966-c710b149-be56-46ce-8976-fd98fd0a66c8.png)
![image](https://user-images.githubusercontent.com/30430227/176353980-37a0cce5-c845-41a6-9e52-5d2f66bdcfb7.png)

`그리는 순서 > 아래서 위로`

![image](https://user-images.githubusercontent.com/30430227/176354416-82672189-5fa7-46b0-b68e-e0b45b0a7dbd.png)
![image](https://user-images.githubusercontent.com/30430227/176354436-9d9ca840-048a-460a-8c61-37dbe0a75c94.png)


3. 기능 연습 

`3D Cursor위치 이동 드로잉`

![image](https://user-images.githubusercontent.com/30430227/176356866-320fe709-8fa0-4b71-8a99-f13c858074c9.png)

![image](https://user-images.githubusercontent.com/30430227/176354846-f1169f67-8268-4507-9037-738917aa427c.png)
![image](https://user-images.githubusercontent.com/30430227/176354883-4b92407e-8ec2-4350-9cb9-ed245a95187d.png)

![image](https://user-images.githubusercontent.com/30430227/176356748-1614771e-a1dc-40da-be82-773b981aaeff.png)
![image](https://user-images.githubusercontent.com/30430227/176356764-1b47e269-53a7-463f-97e2-9f90dfe7672c.png)
![image](https://user-images.githubusercontent.com/30430227/176356827-94fa2ec3-2216-421f-bc23-4d5ed18704d6.png)

`Grease Pencil > Line > Dup`

![image](https://user-images.githubusercontent.com/30430227/176357365-d1a0f59e-fa28-4894-8db7-861644415ed2.png)

![image](https://user-images.githubusercontent.com/30430227/176357329-717fbc16-a5b4-448c-a479-ba482d0ed551.png)
![image](https://user-images.githubusercontent.com/30430227/176357431-1024c7f2-40d8-4b4a-a1be-46ff0d7f5275.png)

![image](https://user-images.githubusercontent.com/30430227/176357519-7e68bb11-f565-4a2b-9828-62744e9f391f.png)
![image](https://user-images.githubusercontent.com/30430227/176357592-5008353e-d0b0-4f2c-875f-5c1417826e86.png)

![image](https://user-images.githubusercontent.com/30430227/176357716-0b2e9b62-917a-4149-9675-cfad688ba87e.png)
![image](https://user-images.githubusercontent.com/30430227/176357797-e091ff87-aff3-47f3-ae96-cef8f069bdcf.png)


4. 얼굴 Retop

![image](https://user-images.githubusercontent.com/30430227/176384426-82b20395-ab81-471d-b612-f8a1ccdbdc1d.png)

![image](https://user-images.githubusercontent.com/30430227/176384630-d8490aaf-303b-425e-b5c8-8fadabb32c8e.png)
![image](https://user-images.githubusercontent.com/30430227/176384695-bf0377eb-df19-429a-bc1f-e009a5689271.png)

![image](https://user-images.githubusercontent.com/30430227/176384804-a1fc2ba9-81dc-4dee-9369-1d103e22bacc.png)
![image](https://user-images.githubusercontent.com/30430227/176384829-317ee3d1-d505-4dee-a38b-6de5120d6f6c.png)

![image](https://user-images.githubusercontent.com/30430227/176385114-4c8aaa89-ab57-4ba4-af27-a5ca022e7d3b.png)
![image](https://user-images.githubusercontent.com/30430227/176385211-d85b24f2-c6c8-4ba6-8b93-f5300d560ff9.png)

![image](https://user-images.githubusercontent.com/30430227/176385428-ac638195-bd75-49ad-adb5-48aec6e6cbed.png)
![image](https://user-images.githubusercontent.com/30430227/176385468-f2400a18-5b1a-471d-b30c-615c68b0c7ad.png)

![image](https://user-images.githubusercontent.com/30430227/176385587-f3acfb4f-eff3-4492-b466-ff97a44a9996.png)
![image](https://user-images.githubusercontent.com/30430227/176385623-1f6ac94e-0b49-4bd3-a8f4-39046703495a.png)

![image](https://user-images.githubusercontent.com/30430227/176385777-6987ec43-c06e-4aa1-b6e8-0babfbe68189.png)
![image](https://user-images.githubusercontent.com/30430227/176385810-3917ab1f-3f6a-4dc6-88c4-fc4061c8b65d.png)

`왼쪽에서 오른쪽으로 드로잉`

![image](https://user-images.githubusercontent.com/30430227/176386673-be70a16b-0686-49d7-a0df-2eb42934fc68.png)
![image](https://user-images.githubusercontent.com/30430227/176386765-87b81134-4ad3-4380-b44d-20fc0ad5ae29.png)

![image](https://user-images.githubusercontent.com/30430227/176387203-41c8e434-ca8e-4080-af4e-af7cd5b23776.png)
![image](https://user-images.githubusercontent.com/30430227/176387225-e81a359e-fdfd-4d21-b9e6-a6d2082b8a4c.png)

![image](https://user-images.githubusercontent.com/30430227/176387409-81ec43e7-274d-4c72-8171-2888f8350fde.png)
![image](https://user-images.githubusercontent.com/30430227/176387451-165dfc32-e2e4-45d2-84a4-2b80f442bbbd.png)

![image](https://user-images.githubusercontent.com/30430227/176387903-ccfb8407-4a29-4c27-8585-22659276eee2.png)
![image](https://user-images.githubusercontent.com/30430227/176387821-84e3e136-8920-4a55-b965-b496261b3a81.png)

![image](https://user-images.githubusercontent.com/30430227/176388080-f83ac0cf-3684-45f2-9001-ba5ddd679968.png)
![image](https://user-images.githubusercontent.com/30430227/176388105-a474cfd9-abf9-478d-8f47-3979f658a43f.png)

![image](https://user-images.githubusercontent.com/30430227/176388602-8300eee9-d9f6-41f5-9664-c50a2cb3fd1e.png)
![image](https://user-images.githubusercontent.com/30430227/176388689-61ebb253-dddb-422d-afbc-3395746df424.png)

![image](https://user-images.githubusercontent.com/30430227/176388935-8c636e06-e878-4212-95af-901f94ff6ff2.png)
![image](https://user-images.githubusercontent.com/30430227/176388966-71365ebf-004f-4936-ac56-be017dc58a81.png)

![image](https://user-images.githubusercontent.com/30430227/176389190-2f7c3de4-7624-47ef-8035-e74e8d9fdf6c.png)
![image](https://user-images.githubusercontent.com/30430227/176389225-c985aaf1-4ebd-480e-a83d-80fe9cb10b0d.png)


5. 토폴로지 참고

![image](https://user-images.githubusercontent.com/30430227/176596779-e0520982-a1f3-4815-bfa7-355074e8b000.png)

![image](https://user-images.githubusercontent.com/30430227/176596811-7dfa73cf-adfe-47fc-9e22-2d67d31874c4.png)

![image](https://user-images.githubusercontent.com/30430227/176597192-48ee1b74-b544-443f-bc0a-5c135e523b61.png)
![image](https://user-images.githubusercontent.com/30430227/176597162-f3844f0c-6573-4b01-a0b5-943d2af90c79.png)

![image](https://user-images.githubusercontent.com/30430227/176597362-ed1d34bb-a23b-471b-bf75-8f0af19da1e8.png)

![image](https://user-images.githubusercontent.com/30430227/176597397-4a735d0c-5982-48ee-a02d-8912b2df6edd.png)


**Hand Modeling1**

![image](https://user-images.githubusercontent.com/30430227/176600935-5865418e-022d-438d-809e-7d6ec2da5c7f.png)
![image](https://user-images.githubusercontent.com/30430227/176600893-7a2dbb28-7b59-471e-90d6-daae00f25b70.png)

![image](https://user-images.githubusercontent.com/30430227/176601128-28c190c4-039c-42db-a034-3bc052e7b9a6.png)
![image](https://user-images.githubusercontent.com/30430227/176601250-d2650c84-c58b-4922-b56b-cbef583d989a.png)
![image](https://user-images.githubusercontent.com/30430227/176601363-02f4cf89-b7f9-44bb-9cb5-f0ea41a8ba05.png)

![image](https://user-images.githubusercontent.com/30430227/176601516-41fcd6ec-dbe8-40b8-8819-3ac98a649caf.png)
![image](https://user-images.githubusercontent.com/30430227/176601533-abfa87a0-5a2f-4f7d-8e3f-1d6526b52b6c.png)
![image](https://user-images.githubusercontent.com/30430227/176601643-292d283d-334d-437a-b664-691f9095ea82.png)
![image](https://user-images.githubusercontent.com/30430227/176601767-c07c706f-c51b-4c03-9d65-f840192a0521.png)

![image](https://user-images.githubusercontent.com/30430227/176602161-791c74c8-eb03-4947-acf0-8d47efc9d108.png)
![image](https://user-images.githubusercontent.com/30430227/176604253-f1182218-9b01-4de1-84b7-5ffdaa4c4a2b.png)


**Hand Modeling2**

![image](https://user-images.githubusercontent.com/30430227/176604603-e3862e72-2b04-4c54-a1c5-b32ca632af94.png)
![image](https://user-images.githubusercontent.com/30430227/176604679-d966a1cc-0465-4101-8025-c55bd40ba09d.png)
![image](https://user-images.githubusercontent.com/30430227/176604953-1ac6448b-8fc2-4c94-9d24-06399555da07.png)
![image](https://user-images.githubusercontent.com/30430227/176605107-b883f7cb-a3a1-4af5-81d0-4400e561b22e.png)

![image](https://user-images.githubusercontent.com/30430227/176605548-9292b738-8464-403b-a21e-b1ed31668b5d.png)
![image](https://user-images.githubusercontent.com/30430227/176605613-13b3c813-6fef-4767-bdab-cee26fd63949.png)

![image](https://user-images.githubusercontent.com/30430227/176605921-7f5a5bec-5d7e-4fbf-95d9-eef20d0f993e.png)
![image](https://user-images.githubusercontent.com/30430227/176606275-f4cb709c-3b8d-4853-8d1d-75f4cb901894.png)
![image](https://user-images.githubusercontent.com/30430227/176607404-4c949fc5-a945-4315-86d2-0d3d194efc79.png)


**Foot Modeling**

![image](https://user-images.githubusercontent.com/30430227/176607678-57e124ad-0b7b-4511-b6bc-17cf7e239540.png)
![image](https://user-images.githubusercontent.com/30430227/176607828-98167881-c157-44aa-bc0a-e51df9689faf.png)
![image](https://user-images.githubusercontent.com/30430227/176608383-8bc9ef38-56d0-43ac-8574-1bb925e521f9.png)

![image](https://user-images.githubusercontent.com/30430227/176608927-c9c5070d-ed94-47fd-befa-cd8e2564d7b6.png)
![image](https://user-images.githubusercontent.com/30430227/176609252-7168377f-6704-4a05-a023-7d988ec0b686.png)

![image](https://user-images.githubusercontent.com/30430227/176610171-1988b3fc-dea9-4f47-bdb1-43c4a53ee4b5.png)

![image](https://user-images.githubusercontent.com/30430227/176610486-0e670eab-e183-4475-9006-0caecaa4c9b3.png)
![image](https://user-images.githubusercontent.com/30430227/176610518-2c607bff-4eca-4909-baa8-8df3de7830ff.png)
![image](https://user-images.githubusercontent.com/30430227/176610705-bcc2ff69-b7e4-464f-b836-898b3b254fcf.png)

![image](https://user-images.githubusercontent.com/30430227/176611447-f1521813-17e9-4366-9753-4539ea4f2df9.png)
![image](https://user-images.githubusercontent.com/30430227/176611619-6e6ada4b-d973-4fad-9076-feeeec54d914.png)
![image](https://user-images.githubusercontent.com/30430227/176612354-bcfcbeae-e920-45f1-9c18-84944f4c93b1.png)


Outline 
--------------

![image](https://user-images.githubusercontent.com/30430227/179001037-d68ba0ed-ac5e-43c3-95de-e9c343897c8f.png)


Tri to Quad
-------------

`Ctrl-X  dissolve`

![image](https://user-images.githubusercontent.com/30430227/180921049-23f9d06f-e37b-414a-97eb-e51f3d17efeb.png)
![image](https://user-images.githubusercontent.com/30430227/180921071-1836b9d6-5504-497b-ad76-c5ed270b328b.png)


![image](https://user-images.githubusercontent.com/30430227/180921200-1f5bdee8-d645-4115-b5ba-088090669be3.png)
![image](https://user-images.githubusercontent.com/30430227/180921357-17524748-a21b-4f7a-87e7-914694b42f7e.png)

`Edge Select + Select Sharp Edges > Edge Crease Shift-E > 1`

![image](https://user-images.githubusercontent.com/30430227/180921477-a17be0f7-34f8-4ed4-9e62-0ed27b9c29d1.png)
![image](https://user-images.githubusercontent.com/30430227/180921628-6b184db4-87aa-4a9e-97c8-c70bbc3b23a1.png)

`Subdivide >Apply > Select All >Edge Crease Shift-E > -1`

![image](https://user-images.githubusercontent.com/30430227/180921823-e15c3f34-e70f-4d4d-a78e-26a6cc840774.png)

![image](https://user-images.githubusercontent.com/30430227/180921868-153ba2d1-b49f-461a-98ad-14cf817d9759.png)
![image](https://user-images.githubusercontent.com/30430227/180921909-66c50e02-04c1-40de-9159-a9039fda049a.png)


`디테일 추가 - Solidify > Remesh:Smooth`

![image](https://user-images.githubusercontent.com/30430227/180922455-cf30b76b-4861-4ad1-8d81-a74c32235947.png)
![image](https://user-images.githubusercontent.com/30430227/180922496-099a8691-240f-481c-9cd3-465a90ced104.png)



