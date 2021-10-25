Nature
========

물결 
--------
![image](https://user-images.githubusercontent.com/30430227/131272921-dff4155a-c504-41c5-bb92-df120d4f6396.png)  
![image](https://user-images.githubusercontent.com/30430227/131272936-d72bef53-30f9-4d50-aa13-46105b8864c5.png)  

<br>

Fast Clouds
------------
1. 모델링  
`센터에 point Light`  
![image](https://user-images.githubusercontent.com/30430227/132815000-3bf44bff-b08d-4767-9c8a-3d07b097f24c.png)  

2. Material  
![image](https://user-images.githubusercontent.com/30430227/132815388-a9d0abf5-2990-4b6a-9f8c-fbbd21bf0bc7.png)  
![image](https://user-images.githubusercontent.com/30430227/132815452-28a4f332-712d-4fe0-a8c3-a71d372528eb.png)  
`Render Property`  
![image](https://user-images.githubusercontent.com/30430227/132815546-7272b1ca-d2a7-47c4-9a39-90100843c0a1.png)  

3. 적층  
![image](https://user-images.githubusercontent.com/30430227/132816878-67fa0c96-30d8-4ad7-aef1-335c2259c2b2.png)  
![image](https://user-images.githubusercontent.com/30430227/132821559-74d458de-57bc-4527-a123-28c7c977f221.png)  


4. Scale Z  
![image](https://user-images.githubusercontent.com/30430227/132819525-606e4a40-8925-485f-85ee-05ddf3d5bc34.png)  

5. Render  
![image](https://user-images.githubusercontent.com/30430227/132819618-794af610-ef3d-4129-9398-76c6bfd16f72.png)
![image](https://user-images.githubusercontent.com/30430227/132819859-03c55c6a-cce0-4f97-9b01-b1144a2abd19.png)  

![image](https://user-images.githubusercontent.com/30430227/132819904-220d8f87-5690-4606-903c-2147bf759758.png)



Snow Material 
--------------
1. Weight Paint  
![image](https://user-images.githubusercontent.com/30430227/133707886-8f25828e-96b3-4cce-a464-1683b188d794.png)  


2. Subdivide, Displace  
`Voronoi`  
![image](https://user-images.githubusercontent.com/30430227/133708154-7e4d8eab-59dc-4645-93db-6da4be36b720.png)
![image](https://user-images.githubusercontent.com/30430227/133708135-d8b7caeb-7287-45ac-92d1-ee4b5dd4d196.png)  

3. Subdivide, Displace 추가  
`Wood:: Band Noise:: size: 0.01`  
![image](https://user-images.githubusercontent.com/30430227/133708468-2ea832bd-ca74-44c9-a8f2-569027101f12.png)
![image](https://user-images.githubusercontent.com/30430227/133708519-52f8baf4-5bd1-4df9-a27f-8f4976b76c52.png)
![image](https://user-images.githubusercontent.com/30430227/133708542-f441cf0a-cdbc-40de-9329-e3581896321b.png)  

4. Shading  
`World Map, Subsurface: 1, Transmission: 0.5, Blend Mode: Alpha Blend`  
![image](https://user-images.githubusercontent.com/30430227/133709114-dceaf8cb-034e-460c-9f5d-30f115985d39.png)
![image](https://user-images.githubusercontent.com/30430227/133709152-90a5cd0d-5838-4382-99a4-94e573276f06.png)  



Rain Drop 
-------------
![image](https://user-images.githubusercontent.com/30430227/133740715-529b139d-203c-47d8-850d-fac1307bdfb8.png)  

`Subdivide, Dynamic Paint::Canavs::Wave::Damping: 0.01`  
![image](https://user-images.githubusercontent.com/30430227/133740906-01409523-4c80-45b6-aae5-ba39dbd3ea95.png)
![image](https://user-images.githubusercontent.com/30430227/133740836-48be5d63-67cd-44c7-8061-21db8134b84b.png)  

`Particle::Object, Dynamic Paint::Brush`  
![image](https://user-images.githubusercontent.com/30430227/133740965-fda526d0-e812-4301-a33d-6c54855bce9a.png)  
![image](https://user-images.githubusercontent.com/30430227/133741110-b047cbe0-136b-4b20-92b4-ae7560f80dbc.png)  


Ocean
----------
1. Resolution Viewport: 22, Choppiness(변동성): 0.6  
![image](https://user-images.githubusercontent.com/30430227/133741677-4b23d780-623c-4b52-9aa9-241d79cee809.png)  

2. Foam  
![image](https://user-images.githubusercontent.com/30430227/133743988-0e723bce-44d2-469d-9350-0332619102e0.png)
![image](https://user-images.githubusercontent.com/30430227/133743892-7d578b4b-58df-4d21-8429-99f0762439e1.png)  

`Subtract Noise Textue(Clamp 체크)`  
![image](https://user-images.githubusercontent.com/30430227/133744145-7bde7c60-0932-43e8-a08b-d5128f918ffc.png)

`환경 맵 적용, Principled BSDF::Transmission: 1, IOR: 1.333`  
![image](https://user-images.githubusercontent.com/30430227/133744499-76e4fe57-ad8b-4989-92dc-4431b419f5b9.png)  
![image](https://user-images.githubusercontent.com/30430227/133744420-995b5d11-b77e-4b26-a644-43abf8897b77.png)  


먹구름  
---------
`Ocena`  
![image](https://user-images.githubusercontent.com/30430227/134004609-b5f627a6-7fc6-4fde-8a53-05a118b89358.png)  
![image](https://user-images.githubusercontent.com/30430227/134004648-a27c8e17-86b0-4b39-9297-d703e545ee9a.png)  

`Select Boundary Loop, Scale Z: 0, Z 두께 얇게`  
![image](https://user-images.githubusercontent.com/30430227/134005041-ef95b9c5-8d26-46fe-a7c9-ad2de2ec9c5a.png)  

![image](https://user-images.githubusercontent.com/30430227/134005136-6708544c-2e87-4510-8e26-f9065357b8d2.png)  
`Area/Sun Light`  
![image](https://user-images.githubusercontent.com/30430227/134008283-fe61d468-c5b8-48ff-a031-8ba06955d792.png)  
![image](https://user-images.githubusercontent.com/30430227/134008324-12a7af52-f674-4be1-9d74-b6631798b949.png)  









