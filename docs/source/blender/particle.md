Particle
============

라인 튜브 
----------
1. ico Sphere  
![image](https://user-images.githubusercontent.com/30430227/132629225-de709860-db0d-4961-8f27-44045596c465.png)  


2. Particle  
`Render:path, Cache:Bake, gravity:0`  
![image](https://user-images.githubusercontent.com/30430227/132629753-76bc9133-a54c-4bd2-b886-3632a9899145.png)  

`Convert to Mesh`  
![image](https://user-images.githubusercontent.com/30430227/132629834-936727d3-45fc-4949-9f3e-511795749372.png)

`to Curve`  
![image](https://user-images.githubusercontent.com/30430227/132629979-03d8a1f0-2ec7-4485-bf2e-13b8f958846e.png)  

3. 커브세팅  
![image](https://user-images.githubusercontent.com/30430227/132630309-147b366a-5094-4644-bf8f-fffef7a68aec.png)  
![image](https://user-images.githubusercontent.com/30430227/132630357-e47041c5-e98d-4810-b92c-7f8dc175757f.png)  

4. 응용  
![image](https://user-images.githubusercontent.com/30430227/132631804-e1bcbb54-5881-466e-8d78-72931698dcc5.png)  

`Empty > Force Field > Vortex`   
![image](https://user-images.githubusercontent.com/30430227/132631146-a967f0ef-4289-4948-b717-1cbc52dc1b72.png)
![image](https://user-images.githubusercontent.com/30430227/132631160-cd871d43-b655-4c24-9f95-6631721ece9b.png)  


5. Cache Bake > Strand Steps  
![image](https://user-images.githubusercontent.com/30430227/132631430-c9d826d5-7a5b-4b44-bba1-fd14da44cd69.png)  
![image](https://user-images.githubusercontent.com/30430227/132631496-802d766a-b0af-47be-b6f0-d6d226a7ee1b.png)
![image](https://user-images.githubusercontent.com/30430227/132631708-cc1c273f-ccb2-479f-bb82-d1cb8027bf81.png)  



적혈구
--------
1. 모델링  
![image](https://user-images.githubusercontent.com/30430227/132632421-304e95d7-4ca6-4ea6-acdf-9147a8148443.png)
![image](https://user-images.githubusercontent.com/30430227/132632602-a8949259-f3b8-48ac-9faf-0cb086d837f8.png)  

2. 재질  
![image](https://user-images.githubusercontent.com/30430227/132635387-88e49333-1ad3-450d-9cf2-6e389e89b892.png)  
![image](https://user-images.githubusercontent.com/30430227/132635366-04adee31-24fe-489e-973d-364b594d8357.png)  


3. ico sphere > particle  
![image](https://user-images.githubusercontent.com/30430227/132635654-482dcdb5-bec7-4b40-82f2-62ef4fcc7730.png)  
![image](https://user-images.githubusercontent.com/30430227/132635691-0e9cf537-cb13-402a-9963-71c412c4854a.png)  
`Particle Normal:0, Rotation:Randomize:1`  
![image](https://user-images.githubusercontent.com/30430227/132637233-e4173620-62b7-4795-8d27-f162b04f6c1d.png)  
`gravity : off`  
![image](https://user-images.githubusercontent.com/30430227/132637285-8d5c1a56-40a1-4d6a-a046-28742ada57d3.png)  
`Add Empty > Add Force Field(Turblence)`  


4. Make Instances Real > Physics  
![image](https://user-images.githubusercontent.com/30430227/132638156-b878e0d3-fd91-4ff6-bc0e-a0f54f80048f.png)

5. DOF  
`Empty`  
![image](https://user-images.githubusercontent.com/30430227/132640532-97483d54-7010-4f4b-af62-f3598053d881.png)  
`Camera`  
![image](https://user-images.githubusercontent.com/30430227/132640575-78a1521f-acec-49e6-bbdf-1ae940bf7e6d.png)  

6. 배경 노이즈  
![image](https://user-images.githubusercontent.com/30430227/132641110-c6ec4407-c990-4f26-ac12-872b039c1270.png)  
![image](https://user-images.githubusercontent.com/30430227/132641151-0c92428b-0d8d-4c95-b83e-8f1b020f8cf2.png)  


모래 디졸브  
------------
1. Boolean  
![image](https://user-images.githubusercontent.com/30430227/132645309-f340857c-02fc-478b-b36e-fb4d611eaa95.png)  
![image](https://user-images.githubusercontent.com/30430227/132645445-454dc3ae-7ae7-477e-86f4-6549242c6aeb.png)  
![image](https://user-images.githubusercontent.com/30430227/132645529-dfb77fd4-0e9f-46c6-b4f2-76af0bcb9f76.png)  

2. Keyframe  
`position & Rotation`  
![image](https://user-images.githubusercontent.com/30430227/132646009-22fa7f26-fafe-4cb9-8926-922d91938ec6.png)  
`Box 회전하며 내려오는 애니`  
![image](https://user-images.githubusercontent.com/30430227/132646276-85ab740b-373f-481f-b4bd-509937467314.png)  

3. 파티클 용 Slice  
`수지와 Box 복사`  
![image](https://user-images.githubusercontent.com/30430227/132647827-daa7def6-8273-4857-a0bb-a285e03af50b.png)  
![image](https://user-images.githubusercontent.com/30430227/132647974-c3deabef-e354-4b4c-90c7-3799dabcd83c.png)  


4. 파티클  
![image](https://user-images.githubusercontent.com/30430227/132648588-d34d9d8b-05fe-4ae2-9620-3bbcff910630.png)  
`Volume, Random, 파티클 똥 제거 Use Modifier Stack`  
![image](https://user-images.githubusercontent.com/30430227/132650561-c2b6c248-6ffe-4584-8d24-f8c521a6f33f.png)
![image](https://user-images.githubusercontent.com/30430227/132648743-dd4c6eeb-7931-4867-a887-2f0c3d4da5d8.png)  


5. Gravity(9.8 -> 1)  
`공중에 잠시 멈추다 떨어지는 것 같다`  
![image](https://user-images.githubusercontent.com/30430227/132650119-e84ef694-643e-4eae-8366-682753948139.png)  


6. 포스가 함께  
![image](https://user-images.githubusercontent.com/30430227/132651255-ca343eb4-b033-4f0c-a318-67ffd0148840.png)  



7. 파티클 메쉬  
![image](https://user-images.githubusercontent.com/30430227/132651543-e66d22af-7080-4a4d-9ccb-666c6ba0e7f5.png)  
![image](https://user-images.githubusercontent.com/30430227/132651740-3e0a4458-ecf4-4535-b1d0-908dc7cea993.png)  




















