Shading
==============

Rectangle Light(Cycles)
-----------------
![image](https://user-images.githubusercontent.com/30430227/130893362-9e19c6e4-2ef4-417f-9dde-e40f7c2c0d25.png)

1. Spot Light > (이미지선명하게)Radius: 0 > Use Node 버튼 클릭
2. 이미지 텍스처 Ctrl + T > Normal -연결  
![image](https://user-images.githubusercontent.com/30430227/130891723-68780ddf-eaf4-4bb1-9579-7c8071c277c7.png)

3. Mapping Node > Location(0.5,0.5) > Scale(2,2)
4. 사각형으로 texture node > repeat->Clip  
![image](https://user-images.githubusercontent.com/30430227/130892588-0b5e5854-6f17-4826-a689-957075ed9066.png)

5. 외곡보정 Divide node  
![image](https://user-images.githubusercontent.com/30430227/130892836-9c7045dd-e81d-4420-a742-36c68d53740c.png)

6. 볼륨라이트  
![image](https://user-images.githubusercontent.com/30430227/130893282-4549410d-b076-4076-8a18-3bc04426781a.png)

7. 볼륨 강도  
![image](https://user-images.githubusercontent.com/30430227/130893613-77b85cf4-ba9c-408f-9390-685e26d222a9.png)
