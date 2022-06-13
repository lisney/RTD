FreeCAD
========

shape binder
---------------

```
기존 Part의 면, 선 등을 참조로 사용

- Sketch용으로 선택 시 기존 Part는 Hide > Tree View 대신 ViewPort에서 선택
```

![image](https://user-images.githubusercontent.com/30430227/171528434-4f659b7a-14e1-4e7b-8bce-efe84cb74cbe.png)

![image](https://user-images.githubusercontent.com/30430227/171528395-2cdfdfbb-f6a0-4d6c-91e2-4da2ca0f20f9.png)

`slot > 빨간 두 점 위치고정 coincident -error> Solver (click to select) > Delete 버튼`

![image](https://user-images.githubusercontent.com/30430227/171528552-e5c9f164-8f6f-4a7b-8820-86edbae8c3c9.png)
![image](https://user-images.githubusercontent.com/30430227/171528911-6d32cc1f-137f-4973-bfbf-937896bf782f.png)

![image](https://user-images.githubusercontent.com/30430227/171528715-17b084f3-efa9-488d-b953-0223d618635c.png)

`새 Body 이동 > Pad > 이후 기존 Body의 Sketch를 변경하면 새 Body가 따른다`

![image](https://user-images.githubusercontent.com/30430227/171529184-9f8b3047-a7c1-4b3f-aa75-3f748c7517ff.png)
![image](https://user-images.githubusercontent.com/30430227/171529237-50e475b4-8e1c-45ba-867f-53e9d3048730.png)


sub-Shape binde(초록색)
-----------------------

```
Part WB에서 생성한 Cube에는 기본적으로 Shape Binder가 안 먹힌다

-면 추가 방법 > 면을 선택 후 Cube아이콘을 Binder 아이콘으로 드랙한다(Ctrl-Drag 하면 새로 선택한 면으로 리셋)
```

![image](https://user-images.githubusercontent.com/30430227/171530982-4a4322f3-01c4-4025-b8d2-a4cf8157c8b9.png)

![image](https://user-images.githubusercontent.com/30430227/171530959-64311fe3-b3fb-40cf-8bb6-fdadbe098e1a.png)


Part Cube를 PartDesign에서 사용하려면 
--------------------------------------

`Cube 선택 > New Body 버튼 클릭(혹은 드랙해서 넣는다)`

![image](https://user-images.githubusercontent.com/30430227/171535186-2fdff7e9-b3de-436c-a6e0-61b47bda4eb6.png)

![image](https://user-images.githubusercontent.com/30430227/171534532-fd53bfbc-ccf0-4a19-82eb-408041f2ca70.png)
![image](https://user-images.githubusercontent.com/30430227/171534441-6c7fe209-a3d9-4c91-9eb6-4cfa5d49f231.png)


원형 테두리 글씨
----------------

![image](https://user-images.githubusercontent.com/30430227/172741431-996c2843-0127-4b73-8b39-8b28e6834a0c.png)

**Sketcher WB > 가이드스케치(도넛)&프로파일스케치(호)**

![image](https://user-images.githubusercontent.com/30430227/172741592-15078c49-afe8-4dae-a98f-fff5a73d9772.png)

**Part WB > Revolve(Z축방향 회전-서피스)**

![image](https://user-images.githubusercontent.com/30430227/172741763-b6751264-e78a-4c36-a0fd-35c40c3d2f77.png)

**Draft WB > ShapeString**

![image](https://user-images.githubusercontent.com/30430227/172741902-ab53b66f-2f22-4d52-ae59-54f2618c26b6.png)

**Sketcher WB > 컨스트럭션 박스 그리기**

![image](https://user-images.githubusercontent.com/30430227/172742011-9686696a-7b15-4c4f-bce0-b3c1a9596ad0.png)

**Curver WB > 원둘레(느낌표버튼) > 스케치선택 후 서피스 선택 > Map a Sketch > Extra Objects**

![image](https://user-images.githubusercontent.com/30430227/172742293-6a01e59e-53e4-4ef3-b8da-7698ebc9d983.png)

![image](https://user-images.githubusercontent.com/30430227/172742385-556b6836-f094-478d-bffe-b030bf082e69.png)


LatticeA
----------

1. Sketcher WB - 2 스케치

![image](https://user-images.githubusercontent.com/30430227/173260626-4e20e493-44a5-434f-a213-6c0c00da2c2e.png)

![image](https://user-images.githubusercontent.com/30430227/173260644-74b0c6f5-6002-466e-9b48-ffe9dce881d9.png)


2. Part WB - Extrude > Taper Angle

![image](https://user-images.githubusercontent.com/30430227/173260681-11e10093-a989-4925-8082-84e84938534a.png)

![image](https://user-images.githubusercontent.com/30430227/173260710-8f6f4d51-f55a-47c3-b627-874c431c97d6.png)


3. Lattice2 WB 

![image](https://user-images.githubusercontent.com/30430227/173260742-51fd28fb-cc9f-40a6-bd4e-3ebcb5ec880b.png)
![image](https://user-images.githubusercontent.com/30430227/173260877-1e24c120-f523-44d0-840b-dbde5329e918.png)

![image](https://user-images.githubusercontent.com/30430227/173260790-5badca95-c26e-44f0-a1e4-6a385d63c83e.png)

![image](https://user-images.githubusercontent.com/30430227/173260812-604790f5-2ac7-4a5d-9e18-54bc63d4e181.png)


`Extrude, LinearArray 차례로 선택 후`

![image](https://user-images.githubusercontent.com/30430227/173260933-3f788b60-214b-4da9-b187-1efe2e37cf66.png)

![image](https://user-images.githubusercontent.com/30430227/173260917-80bfc61b-3d98-4933-809f-d77be40dcbfa.png)


4. Draft WB - Extrude 클론 > Transform

![image](https://user-images.githubusercontent.com/30430227/173261017-54d89d7a-7e35-4b10-8b10-2251a39ff295.png)

![image](https://user-images.githubusercontent.com/30430227/173261058-ba87a63d-1486-4e87-a03f-27174d691cb7.png)


5. Part WB - Extrude, Extrude001 선택 후 Make Compound

![image](https://user-images.githubusercontent.com/30430227/173261175-d8fe6697-c9d0-450a-b0fc-ee27249395fe.png)

`Populate LinearArray... 속성에서 Lattice Populate Object를 Extrude에서 Compound로 바꿈 > Refresh`

![image](https://user-images.githubusercontent.com/30430227/173261340-5fa00ec1-a771-4b12-8ac7-a60f3e7af85b.png)

![image](https://user-images.githubusercontent.com/30430227/173261289-6d504129-65ca-4684-b739-2e23dbfd5e96.png)
![image](https://user-images.githubusercontent.com/30430227/173261302-aa69a96a-6de6-4108-8b63-3152e461523b.png)


6. Lattice2 WB 

![image](https://user-images.githubusercontent.com/30430227/173261591-59082e72-79e1-4381-99fb-5b945a01ab12.png)
![image](https://user-images.githubusercontent.com/30430227/173261625-36c4f89c-870f-498c-899c-44452852fadc.png)

`Reverse`

![image](https://user-images.githubusercontent.com/30430227/173261657-0241c0c5-3864-43c4-a679-7dac0fef963f.png)
![image](https://user-images.githubusercontent.com/30430227/173261680-549696b2-eaab-494a-a6bc-2eb987b5ebb6.png)

`Populate... - LinearArray001 선택 > `

![image](https://user-images.githubusercontent.com/30430227/173261766-69e21f25-36de-4494-966e-2da486113e60.png)

`LinearArray001 - Count: 9`

![image](https://user-images.githubusercontent.com/30430227/173261787-ae18c0b9-2887-4493-ae20-82d8a69e6cf3.png)

`Compound`

![image](https://user-images.githubusercontent.com/30430227/173265132-29a801bb-fdad-4e3f-81ca-a35c25a2990a.png)

