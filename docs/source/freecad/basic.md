BASIC
=======
1. UI 컬러-Style sheet  
![image](https://user-images.githubusercontent.com/30430227/131780961-02d097a0-22f2-48e0-bbca-710de3ad50fd.png)  

2. 마야 단축키 지정 시 Middel 클릭 Report View 안뜨게  
`show report...on error, ...on warning 체크해제`  
![image](https://user-images.githubusercontent.com/30430227/131781121-c186f8fa-a93c-4beb-8122-109e10ea2daa.png)  

3. Image Plane  
`Image Workbench`  
![image](https://user-images.githubusercontent.com/30430227/132084141-cda0c451-d4ce-46cc-b149-08a3ac0dfcaf.png)


스케치
--------
1. 자동으로 현재 위치에 치수 컨스트레인트 생성  
`점을 선택하고 잠금 컨스트레인트 아이콘 클릭 `  

2. Coinsident 컨스트레인트- 두 점 결합  
`두 점을 드래그해서 선택한다음 아이콘 클릭`  

3. 색상이나 위치 바꾸기  
`좌측 아래 View, Data 콤보창에서 작업 혹은 변형 조절자 보이게 하려면 Part 오른클릭 Transform 선택`  

4. 치수 구속 대신 참조 치수 생성  
![image](https://user-images.githubusercontent.com/30430227/131782080-41dd83a4-b94d-4340-9a02-d6fbe01bd68f.png)  
`버튼 클릭 후 생성 - 색상이 파랗다`  

5. Construction Mode - 가상선 생성  
![image](https://user-images.githubusercontent.com/30430227/131782455-7d8a157b-ed44-4528-af9c-3aadad83e4fd.png)  

6. Datom 평면 사용 - 무게 중심에 점 생성  
```
면을 선택하고 Datom 도형 중 점을 선택한다 > 센터에 점을 생성한다 
> Tree View에서 면과 점을 선택 후 Datom Plane(사각형) 선택
> 점을 중심으로 하는 작업평면 생성
```

7. Pad로 겹친 오브젝트 합치기  
![image](https://user-images.githubusercontent.com/30430227/131791690-e69957e2-c31c-41f8-99cb-c606c08e7686.png)
![image](https://user-images.githubusercontent.com/30430227/131791762-d4511337-ee34-4975-a056-884d288aff54.png)  

![image](https://user-images.githubusercontent.com/30430227/131791737-46b5d4b8-b279-46e7-90c4-40e7fe5a5764.png)  

<br>

파라메트릭-Alias
------------------
![image](https://user-images.githubusercontent.com/30430227/131803448-280762e7-ae6e-470a-8da5-44ca3ca4e195.png)  

Spreadsheet 작업대 > 수치셀의 Alias 가 파라미터이다  
![image](https://user-images.githubusercontent.com/30430227/131802727-4c09dafc-e73e-42a0-b5fe-4fa457c455c9.png)  
  
시트명이 객체명  
`입력방법: 시트명.Alias명`  
![image](https://user-images.githubusercontent.com/30430227/131802975-ecdeb743-1f0b-4114-9048-18a62aefcb85.png)
![image](https://user-images.githubusercontent.com/30430227/131803218-31486d60-6f5c-4c90-858c-84a6501ad637.png)  

보이는 형식을 정할 수도 있다  
![image](https://user-images.githubusercontent.com/30430227/131804267-a28032e9-23de-4861-90a9-587fb29ebfee.png)  
![image](https://user-images.githubusercontent.com/30430227/131804401-50931f43-f95c-48cd-ac6d-4c9289569376.png)  

Curves Workbench -addOn
-------------------
1. 포인트 추가  
`Segment 선택 > 키보드 'i' `  
![image](https://user-images.githubusercontent.com/30430227/131985690-80b8a6b1-b1ed-44b8-980e-0b5c1e44737c.png)  

2. 직선으로 정렬  
`포인트 혹은 세그먼트 선택 > 키보드 'p'`  
![image](https://user-images.githubusercontent.com/30430227/131986156-9d84adc1-25b9-4d38-9f79-fbc97f557376.png)  

3. 포인트 커브에 스냅  
`선택 후 키보드 's'`  
![image](https://user-images.githubusercontent.com/30430227/131986918-c20dff11-8caa-487a-99c3-0002b3badd96.png)  

4. 라인 생성  
`esc 편집모드 벗어난 후 두 점을 선택 후 line 아이콘 클릭`  
![image](https://user-images.githubusercontent.com/30430227/131987612-d437f217-5124-4256-9b41-fd29a8656a19.png)  
<br>

`커브를 잇는 커브 생성: 두 커브 선택 후 B-Spline 선택`  
![image](https://user-images.githubusercontent.com/30430227/131988245-bcfcb467-5db1-43f5-b912-b716ffc34563.png)  

5. 두 방향 스케치 커브에 교차하는 새 커브 생성  
![image](https://user-images.githubusercontent.com/30430227/132084910-419bb887-2a73-49f6-9b7f-2d69b240d9b6.png)  

6. Sweep Profile on 2 rails  

![image](https://user-images.githubusercontent.com/30430227/132086167-ed509ddd-e211-4a62-b89c-b69485d760c2.png)
![image](https://user-images.githubusercontent.com/30430227/132086179-a9bc9324-2d66-4119-b630-9ee74d47ac96.png)  

- 4개의 sketch 를 생성한다
- 2개로 평면을 생성한다(part WB)
- Sweep 2 rails 로 pointCrowd생성(cuve WB)
- Approximate points to NURBS curve or surface

![image](https://user-images.githubusercontent.com/30430227/132086261-14fd865b-772b-4544-8a55-a7097d31794c.png)  
![image](https://user-images.githubusercontent.com/30430227/132086253-1da1a365-70d6-4836-a699-cd600f41fbb5.png)  
![image](https://user-images.githubusercontent.com/30430227/132086232-0ed85f83-d8d7-432a-924c-6e0e8be1fcbf.png)  

