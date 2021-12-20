Logic Brick
=============

1. 카메라 룩

`카메라 뷰`

![image](https://user-images.githubusercontent.com/30430227/146662937-e0432abc-ea22-4479-be53-83c283834e0e.png)

`Logic Brick`

![image](https://user-images.githubusercontent.com/30430227/146663031-d2cf2079-28bf-45eb-bc71-483dcc6cbe1d.png)

`Camera Physics > Dynamic`

![image](https://user-images.githubusercontent.com/30430227/146663299-d6384490-c4fb-4ba3-9510-4acc467d742b.png)

`Keyboard > Motion(Z-local Axis)`

![image](https://user-images.githubusercontent.com/30430227/146663318-a9423e76-e58a-4746-b377-080c6670e719.png)

<br>

2. 캐릭터 카메라 

`Physics > Charactor`

![image](https://user-images.githubusercontent.com/30430227/146663637-848e170f-f12b-42b5-80da-dbe253181a24.png)
![image](https://user-images.githubusercontent.com/30430227/146663645-0a655683-9ef9-4cc2-8749-8b234085060e.png)

`Logic Brick - 좌우`

![image](https://user-images.githubusercontent.com/30430227/146663670-492bdb58-e7c6-48fe-8ff6-56c5362280bf.png)

`Camera -  상하`

![image](https://user-images.githubusercontent.com/30430227/146663684-6ac08789-82d9-4bdd-af9a-3eb7c6bb0ed4.png)

`Camera > Parent(Box)`

![image](https://user-images.githubusercontent.com/30430227/146663749-8e17e4e6-803f-4fee-8e27-8ff3cea31ee4.png)

`박스 > Logic Block > Move`

![image](https://user-images.githubusercontent.com/30430227/146664739-519a6428-7342-4c2d-9341-699e3fe2097a.png)

`Jump Setting`

![image](https://user-images.githubusercontent.com/30430227/146664751-3e9a982b-356a-4303-8716-e90fdc418708.png)

![image](https://user-images.githubusercontent.com/30430227/146664761-39208405-dc35-4c32-a1e2-a937c579c74e.png)

<br>

3. Collision & Screen

`Scene > Camera`

![image](https://user-images.githubusercontent.com/30430227/146664883-a81b91eb-6292-4b8f-bc3d-8133dd463961.png)

![image](https://user-images.githubusercontent.com/30430227/146664971-d898d983-5f25-4ea2-978f-a89c49ce4f85.png)
![image](https://user-images.githubusercontent.com/30430227/146665070-6c5572e9-3195-43a9-8986-e978196952c7.png)

![image](https://user-images.githubusercontent.com/30430227/146664978-f17564e7-5eb5-4a1e-b0dc-7291d5f70ee9.png)

`충돌1(재질): Add Suzy > Add Material`

![image](https://user-images.githubusercontent.com/30430227/146665111-d1ccff68-5441-4372-9326-2523e829e4f7.png)
![image](https://user-images.githubusercontent.com/30430227/146665121-421ceb63-49dc-4274-ba7e-2b378e78d5dc.png)

`Logic Brick > Add Sensors > Collision`

![image](https://user-images.githubusercontent.com/30430227/146665161-ac4a4801-44b1-4d41-8f68-7e5f53379409.png)

![image](https://user-images.githubusercontent.com/30430227/146665194-ef14299e-2904-4e89-98f2-57b6f46a9289.png)

`충돌2(프로퍼티): Suzy > Add Game Property > 박스 Collision M/p 끄고 -> Property 명 입력`

![image](https://user-images.githubusercontent.com/30430227/146665251-7d43aeb5-c717-479e-ad20-85c72cb3f1b8.png)

![image](https://user-images.githubusercontent.com/30430227/146665281-47ff9a36-bfb6-4396-a131-3f614b098726.png)

<br>

4. 버튼 

`씬 ScreenLose > Create Button`

![image](https://user-images.githubusercontent.com/30430227/146665443-71b958c0-8b8b-4d6a-842d-0d388cb1bb76.png)
![image](https://user-images.githubusercontent.com/30430227/146665440-3ea3ec9e-f664-4af8-bbc5-33de76f99168.png)

![image](https://user-images.githubusercontent.com/30430227/146665499-29b9c0fd-1e64-48be-b0d9-cb20c999b4c9.png)

`씬 SceneGame > Mouse cursor Visiblity`

![image](https://user-images.githubusercontent.com/30430227/146665515-3532c3b9-abc1-4596-b78b-1b89708ccca2.png)

<br>

5. 왔다리 갔다리 - State & Movement

`Suzy 선택 > State 추가`

![image](https://user-images.githubusercontent.com/30430227/146665608-4cd7d59c-b247-42fb-a664-34f0e833808f.png)

![image](https://user-images.githubusercontent.com/30430227/146665670-1d011061-3397-45e6-8abc-d18c2ed7a413.png)

![image](https://user-images.githubusercontent.com/30430227/146665678-5f6b37ba-33b9-43ed-b8d8-cba022c1e898.png)

`2초 후 State 변경하기`

![image](https://user-images.githubusercontent.com/30430227/146665729-93d93772-e7b5-4f29-909b-1d4d6c78928a.png)

<br>

6. 죽고 살고 - Message(유언) 남기고 Spawn

`카메라 세팅 - 로직 삭제, Unparent`

![image](https://user-images.githubusercontent.com/30430227/146666171-a6950e3b-959f-434e-b7c9-9845bca6946e.png)

`Logic Block`

![image](https://user-images.githubusercontent.com/30430227/146666224-5450cb94-985c-4bc7-bc74-551e7212d531.png)

`박스 복사 > 이름 'BobNEW' > New Collection으로 이동`

![image](https://user-images.githubusercontent.com/30430227/146666241-5d68fdf8-f413-4acf-9ab2-4c207bdcbda0.png)

`Empty 생성 > Logic Block`

![image](https://user-images.githubusercontent.com/30430227/146666292-17b3c53d-bca2-4660-926b-6a602eb14db2.png)

![image](https://user-images.githubusercontent.com/30430227/146666390-db600ecc-a356-47e0-a4d4-ae1d8c34e7aa.png)

<br>

7. 슈팅 

`Empty > Parent ;  양파링 생성 > Motion > New Collection`

![image](https://user-images.githubusercontent.com/30430227/146696861-14806f0b-51b8-4ace-a72c-c82d74df8cf5.png)

![image](https://user-images.githubusercontent.com/30430227/146696938-f3782fa0-e764-4894-a52e-e9e7bcd2735f.png)

![image](https://user-images.githubusercontent.com/30430227/146696961-4744ebb1-f191-4a31-b1ae-4b0a24ffc060.png)

`Empty > Node Brick`

![image](https://user-images.githubusercontent.com/30430227/146698177-a5036a2e-8c7a-4315-ba4c-15d1d51988c0.png)

`Ring 수정`

![image](https://user-images.githubusercontent.com/30430227/146699090-17c74c47-0252-47bd-aea2-61c8b8258890.png)

![image](https://user-images.githubusercontent.com/30430227/146699357-59aa722e-1583-4e5f-b421-75cbfea522ae.png)

![image](https://user-images.githubusercontent.com/30430227/146699384-8bca9c7e-9694-45a2-9087-1b1b4f73ac2f.png)

<br>

8. 동전 줍기

`New Empty 'Counter' > Add GAme Property`

![image](https://user-images.githubusercontent.com/30430227/146704651-4013e039-bb26-4458-bd60-98cd6e3f147d.png)

![image](https://user-images.githubusercontent.com/30430227/146704723-fb9cd676-85a0-43cb-b31b-ee40bcaff50b.png)

`Box > Add Game Property 'bob'`

![image](https://user-images.githubusercontent.com/30430227/146704692-cbf22ad2-0dbe-42b0-bbe2-56bcb0870920.png)

`수지 충돌 > 메시지`

![image](https://user-images.githubusercontent.com/30430227/146704784-f13a276e-a1a5-4663-a7f8-84dbdc82871a.png)

`Counter > Node Block `

![image](https://user-images.githubusercontent.com/30430227/146704843-a42a0317-6fab-4588-94b8-1838cbba2652.png)

<br>

9. HUD

![image](https://user-images.githubusercontent.com/30430227/146707920-bc025a6b-bc03-4abd-9f5f-2537cc800aff.png)

`Message To 대상 지움`

![image](https://user-images.githubusercontent.com/30430227/146707981-f2cb64f9-e911-42a0-ad9f-9d9f8cf7d2eb.png)

`New Camera 'HUDcam' > New Text 'Counter' > Node Block > 새 Colloction으로 이동`

![image](https://user-images.githubusercontent.com/30430227/146711079-49b45c63-958c-4986-b282-9217a715e6e3.png)

![image](https://user-images.githubusercontent.com/30430227/146711099-77496ddc-c990-4f85-a072-9dedfd723f95.png)

`Timer`

![image](https://user-images.githubusercontent.com/30430227/146711975-f00e6beb-1d23-4af3-a525-4034118d6ce9.png)

![image](https://user-images.githubusercontent.com/30430227/146711988-cdb4f8b5-6e88-46c1-83f0-f268f8e75cf4.png)

![image](https://user-images.githubusercontent.com/30430227/146712013-ae97a1d2-9954-44a3-b132-3186fd3457b0.png)




<br>

10. 






55. Camera Targets

`Track 메뉴 > 카메라, 대상 선택 후`

![image](https://user-images.githubusercontent.com/30430227/146665938-eb64bd99-026b-4d27-80bd-7dc46ac06dde.png)

<br>

7. 








