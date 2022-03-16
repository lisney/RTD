Geometry Node 3.0 E
======================

Plexus
-------

1. Modeling

![image](https://user-images.githubusercontent.com/30430227/141607978-e7c5271b-b560-446b-8588-aac1058b98f4.png)

![image](https://user-images.githubusercontent.com/30430227/141608164-f06e2339-c649-43e4-9303-3d876447c793.png)

2. Animation

`displace Modifier`

![image](https://user-images.githubusercontent.com/30430227/141608216-b5fd3963-dba2-4c9b-a072-4eb0c8396274.png)

![image](https://user-images.githubusercontent.com/30430227/141608192-9222ce77-ae28-4cc8-ba30-eb34a177939a.png)

<br>

네비게이터 
----------

1. 모델링 

![image](https://user-images.githubusercontent.com/30430227/141614519-10bef8d0-c59e-422f-b58d-49892426554e.png)
![image](https://user-images.githubusercontent.com/30430227/141614530-4657ed89-aab1-44ed-ac24-bb83244143c3.png)

![image](https://user-images.githubusercontent.com/30430227/141614535-4f26707d-4a9e-4d9b-98a3-77ebce622fde.png)

![image](https://user-images.githubusercontent.com/30430227/141614611-c5093118-9b14-4a95-aace-c3107109ad79.png)

2. Geometry Nodes 

![image](https://user-images.githubusercontent.com/30430227/141615062-cdb00e40-c77b-4f0d-bb94-224cdeb73647.png)

![image](https://user-images.githubusercontent.com/30430227/141615167-e95f970a-1df3-4e3d-8b2a-3b490e022172.png)

3. Animation - 따라와~

`Trim Curve Node`

![image](https://user-images.githubusercontent.com/30430227/141615195-6feeb72a-cb94-4ace-840b-7cc300a980cf.png)

<br>

축구공 
----------

1. Modeling 

`IcoSphere > Subdivide > Decimate(Planar)`

![image](https://user-images.githubusercontent.com/30430227/141855309-83f3fb7d-1052-4add-bf57-c3d430a5233b.png)

2. G-Nodes

![image](https://user-images.githubusercontent.com/30430227/141860287-800bdaae-da4b-46a5-910c-bf99f05fb276.png)
![image](https://user-images.githubusercontent.com/30430227/141860388-37896eb5-be6a-4356-a595-e5cd82b0bcdf.png)

![image](https://user-images.githubusercontent.com/30430227/141860717-53532a42-8994-449e-9d7c-d1bafb8e5808.png)

3. Mographic

`회전 타겟 - X축 기준으로 좌우(Z출도 추가한다)`

![image](https://user-images.githubusercontent.com/30430227/141862112-d5b0d943-924d-4663-875c-c47a9e4d9b66.png)

![image](https://user-images.githubusercontent.com/30430227/141862152-360990e3-177c-4cf1-a3cc-50c270e59ef7.png)

![image](https://user-images.githubusercontent.com/30430227/158541498-29a6f88d-1142-4989-a512-10077fb9cd94.png)

![image](https://user-images.githubusercontent.com/30430227/158541546-a04e9e05-498b-44a9-83a0-e233357651ba.png)

`스케일 - Bounding Box`

![image](https://user-images.githubusercontent.com/30430227/141863961-d60f629f-9f56-470c-a556-3d6d7da361ca.png)

![image](https://user-images.githubusercontent.com/30430227/141863946-9bf473e4-833b-4529-8814-7ad3ec4d1d1e.png)

`박스 - Wire display, Not Render > Bounding Box - Min 아래끝 점, Max 대각선 끝 점`

![image](https://user-images.githubusercontent.com/30430227/141864965-aae07b3a-4a1d-4444-81a5-6574b76d92c3.png)
![image](https://user-images.githubusercontent.com/30430227/141865312-b8034ae6-3a33-477c-9d43-ac1fc6bc7a4a.png)

`Box -Relative, Divide -Clamp 체크`

![image](https://user-images.githubusercontent.com/30430227/141865354-69d211d1-86b4-4819-8cd1-ab361c5e299b.png)

<br>

깃털 
----------

1. 모델링 

`Plane > Subdivision > Copy > Move Z > 위 아래 다른 머티리얼`

![image](https://user-images.githubusercontent.com/30430227/141928835-f6ee6dd4-713a-4f4c-8874-29d78a433ab9.png)

2. Geometry Nodes 

![image](https://user-images.githubusercontent.com/30430227/141928874-a6b183dd-b656-4053-aa1e-95b42c19fc24.png)

`Rotate Euler > X-축값`

![image](https://user-images.githubusercontent.com/30430227/141928937-909a46cb-9acf-4043-9b9c-7d2b81ba463d.png)

3. 컨트롤러 추가 Empty

![image](https://user-images.githubusercontent.com/30430227/141929406-16c55d8b-ee85-4b44-9d32-63a5d59f50a3.png)

![image](https://user-images.githubusercontent.com/30430227/141929455-2e0a7521-afac-483f-b200-255f5b4c8dc4.png)

![image](https://user-images.githubusercontent.com/30430227/141929602-117d41c4-ce1f-4b13-9cdb-82d83b0743e0.png)

<br>

Mograph - Transition
----------------------

![image](https://user-images.githubusercontent.com/30430227/143584944-99e9fce2-ef3f-4d4b-a1e1-ae63d78834a7.png)

![image](https://user-images.githubusercontent.com/30430227/143584972-7b595d45-54d4-434e-a71e-6cba7748dd9f.png)

`위 다른 방법`

![image](https://user-images.githubusercontent.com/30430227/146342509-63b3ac63-b992-4b47-9e6d-353e8a5ff7aa.png)

`Proximity > Mix input Color Change`

![image](https://user-images.githubusercontent.com/30430227/143585499-3b731f83-7b9d-4007-8225-12832c39a603.png)

![image](https://user-images.githubusercontent.com/30430227/143585596-3b281c8c-221e-4f5f-a777-987eaa88324c.png)

`폭발 - Normal `

![image](https://user-images.githubusercontent.com/30430227/143585783-4f841b85-c622-47a3-b9f3-3cdca64a3707.png)

![image](https://user-images.githubusercontent.com/30430227/143586123-e3f4bd1b-1c7d-4fd4-aa72-d5f732d1cf15.png)

`Separate`

![image](https://user-images.githubusercontent.com/30430227/143586480-620eac1e-2d5e-420f-89bb-750e6275857f.png)

![image](https://user-images.githubusercontent.com/30430227/143586498-e4c19843-cee6-451d-84de-c023bb77ed71.png)

`Join - Wirefraem`

![image](https://user-images.githubusercontent.com/30430227/143586850-441bcd78-3402-4e8a-a955-3e555f744b29.png)
![image](https://user-images.githubusercontent.com/30430227/143587028-e2008d48-e2fa-4de5-af83-307e7a895610.png)

![image](https://user-images.githubusercontent.com/30430227/143587069-51b022d4-8738-4773-b7dd-4f7f13f65605.png)

`Delete Geometry`

![image](https://user-images.githubusercontent.com/30430227/143591357-231daa56-fe9e-4a86-aec6-1f0b5883e2ff.png)

`조금 수정 - Add 따로`

![image](https://user-images.githubusercontent.com/30430227/143591166-bb75d78f-b347-4a09-b989-7447d4786f88.png)

![image](https://user-images.githubusercontent.com/30430227/143591222-c839d62d-3b8c-4b94-a6a1-e3693a67be80.png)

<br>

체인
------

`Plane`

![image](https://user-images.githubusercontent.com/30430227/143678768-2ee9914a-1d22-4bf7-8288-1b0593a9f334.png)
![image](https://user-images.githubusercontent.com/30430227/143678776-3efa88a2-e23a-4bbd-9e99-047eb4826154.png)

`Subdivide`

![image](https://user-images.githubusercontent.com/30430227/143678786-61f2387c-9db3-487a-8d63-9734394f176d.png)
![image](https://user-images.githubusercontent.com/30430227/143678804-cd3eab26-e4b8-4b70-bcea-75a15659cdcc.png)

`Geometry Nodes`

![image](https://user-images.githubusercontent.com/30430227/143678599-a41f82aa-d48a-4d6c-bc89-2c673c7d303b.png)

![image](https://user-images.githubusercontent.com/30430227/143678628-a7fdad63-f0cb-45af-a445-f1e71cb2261d.png)

`Bezier Curve 로도 된다`

![image](https://user-images.githubusercontent.com/30430227/143678743-bb9a77e5-9403-4d16-b5bb-64fb4478c6c7.png)

<br>

새싹 - Sprout
----------------

`Quadratic Bezier > Trim Curve `

![image](https://user-images.githubusercontent.com/30430227/143853835-7a1b2bf1-fb15-422f-8dfe-2dac24a75dff.png)

![image](https://user-images.githubusercontent.com/30430227/143853944-bbb4a88a-802b-43ab-8c70-b5990f5ebced.png)

<br>

빌딩기초
---------

![image](https://user-images.githubusercontent.com/30430227/144708458-f78a1cc1-3951-4d89-98dd-36599cae91d2.png)

![image](https://user-images.githubusercontent.com/30430227/146309669-637ff988-dcbf-4600-af07-85cf2b2b1c18.png)

<br>

파도 
-----

`Plane > Subdivision(7, Optimal Display & Use Limit Surface 체크 해제)`

![image](https://user-images.githubusercontent.com/30430227/145156333-2d1f340a-ba49-4c23-b77a-ce885609fb81.png)

![image](https://user-images.githubusercontent.com/30430227/145156512-8b47934f-53f7-43cd-862c-63efec308e55.png)

`Add Noise`

![image](https://user-images.githubusercontent.com/30430227/145157595-ab080845-1cff-433a-a236-841ce9b4d1d2.png)

![image](https://user-images.githubusercontent.com/30430227/145157617-f4ccfd66-8f25-47fb-b348-5ac1c3843288.png)

`Detail - Multiply 추가`

![image](https://user-images.githubusercontent.com/30430227/145157742-e783b02c-9dba-41c5-a09d-14b9fcf08be6.png)

![image](https://user-images.githubusercontent.com/30430227/145157796-1f5d661e-a01d-4b1a-8331-73a48092e3af.png)

`재질`

![image](https://user-images.githubusercontent.com/30430227/145158175-778c03c7-0fdf-470e-86bd-884228281ed4.png)
![image](https://user-images.githubusercontent.com/30430227/145158326-ba91cf8a-03be-4334-b4e0-9b3c2b38757f.png)

![image](https://user-images.githubusercontent.com/30430227/145158356-e54e0273-0a4d-4ccb-b965-65bf5087b55c.png)

<br>

염주 
----

![image](https://user-images.githubusercontent.com/30430227/147225522-19ed58fe-fbb9-4acc-a573-8bfb5872973f.png)

`Random Per Island - Cycles에서만 작동한다(Realize Instances 필요)`

![image](https://user-images.githubusercontent.com/30430227/147225721-cf94602b-44af-4524-aa54-24e21d9d6e38.png)

![image](https://user-images.githubusercontent.com/30430227/147225799-8db24597-9682-4b9a-8817-f7828a831f83.png)

<br>

무한 피라미드 박스 
------------

![image](https://user-images.githubusercontent.com/30430227/147841431-5e086c99-5661-4515-a721-1973dd529f85.png)

![image](https://user-images.githubusercontent.com/30430227/147841455-cd5543ee-dd6a-4177-a2b6-cdb188f0f756.png)

![image](https://user-images.githubusercontent.com/30430227/147841463-998fddc6-ec5b-4b82-a29c-69372404fb40.png)

<br>

무한 꽃잎 
-----------

![image](https://user-images.githubusercontent.com/30430227/147842074-af12053d-6b03-47c5-bfc2-983528a76f95.png)

![image](https://user-images.githubusercontent.com/30430227/147842151-7eed9309-65c9-4b2d-bbc5-9a88f6991b2a.png)

![image](https://user-images.githubusercontent.com/30430227/147842157-f22fa79e-de53-4daf-a95c-d9f687df6603.png)




