VFX
======

Water Ripple
---------------

![image](https://user-images.githubusercontent.com/30430227/163669388-86e49d30-ffdb-4d7e-a245-ee894fbc9acb.png)

``Dynamic Paint``

![image](https://user-images.githubusercontent.com/30430227/163669414-91324f49-d0ef-41a3-9432-ab27e9251233.png)

![image](https://user-images.githubusercontent.com/30430227/163669447-443079fe-f920-4381-be26-e6e54a0c1793.png)


Light Path Node
---------------

>> Is Diffuse Ray

![image](https://user-images.githubusercontent.com/30430227/164210201-8b47475b-0685-465c-b7cb-6e5cf2679384.png)

![image](https://user-images.githubusercontent.com/30430227/164210441-e20c865d-a406-496c-a644-54344c654dbb.png)

>> Is Camera Ray

![image](https://user-images.githubusercontent.com/30430227/164212518-72738fca-dcee-40af-893d-7eb6bec1a351.png)
![image](https://user-images.githubusercontent.com/30430227/164213335-804bf712-99af-473d-b8dd-2a9b1cdbd880.png)

![image](https://user-images.githubusercontent.com/30430227/164213363-b1cfcaaa-fa00-49e2-9d2a-f80aba60b044.png)

>> Is Shadow Ray - 투명 재질을 통과할 때만 효과

![image](https://user-images.githubusercontent.com/30430227/164213511-76733319-51bf-40a5-bcea-d3d6a4cf9078.png)

![image](https://user-images.githubusercontent.com/30430227/164213544-d7dbdf86-5df7-4098-b868-0fe194230986.png)

>> Is Diffuse Ray

![image](https://user-images.githubusercontent.com/30430227/164214418-62169e74-1cdd-4815-9147-b42ee70f6c5d.png)

![image](https://user-images.githubusercontent.com/30430227/164214450-8be14507-6ecb-467d-9861-8b7a836a3005.png)

>> Is Glossy Ray - 거울(Is Reflection,완전/불완전 반사 모두), 유리 포함

![image](https://user-images.githubusercontent.com/30430227/164214628-ae410f28-38a2-4e57-99af-e2c37673c0b1.png)

>> 유리 빼기(Is Transmission Ray)

![image](https://user-images.githubusercontent.com/30430227/164215073-6c521628-150c-4b7d-af35-54a05927b7e0.png)

![image](https://user-images.githubusercontent.com/30430227/164215105-fe109982-ccc7-4028-8908-bfae653f0292.png)

>> Is Singular Ray 완전반사, 유리

![image](https://user-images.githubusercontent.com/30430227/164217223-b45ee16a-506b-4d91-b03b-f8c5af72a733.png)

![image](https://user-images.githubusercontent.com/30430227/164217262-a7c62dd5-b0f1-4572-9674-ca52ca1e7030.png)

![image](https://user-images.githubusercontent.com/30430227/164217314-a11ebe60-7ae6-497f-901c-06cdec74eca8.png)
![image](https://user-images.githubusercontent.com/30430227/164217291-f7526928-1aa3-4bdf-91f4-0a7c3bc1a289.png)


Caustics-화선(굴절되어나온 꽃? 광선)
---------------------------

>>> EEVEE

![image](https://user-images.githubusercontent.com/30430227/164346587-7078ae05-1c44-4b72-b7b4-e644f1ba13f7.png)

``Is Shadow Ray``

![image](https://user-images.githubusercontent.com/30430227/164352427-ee102b74-62e2-4183-a8b0-87b53e3a3535.png)

![image](https://user-images.githubusercontent.com/30430227/164352447-4ed24f22-4993-44e7-846c-399e0d3cfbcd.png)

``Fresnel - Gemoetry Node``

![image](https://user-images.githubusercontent.com/30430227/164352487-08021657-307b-4ce9-8a97-9bccfed6c573.png)
![image](https://user-images.githubusercontent.com/30430227/164352954-7172ee6e-3991-478e-be61-18687a5f242b.png)

![image](https://user-images.githubusercontent.com/30430227/164352533-8a6d6d9f-f13b-4889-9ac8-3638c6bc9857.png)

![image](https://user-images.githubusercontent.com/30430227/164352917-c4344f26-dadd-45ea-a112-6b600752cbd8.png)

**NodeGroup**

![image](https://user-images.githubusercontent.com/30430227/164353713-6182f331-d008-4fd1-bf84-d01b12a401af.png)

![image](https://user-images.githubusercontent.com/30430227/164353863-04252c27-89c2-4a60-a9e9-ffe0531e1306.png)

``3 Point Light - R,G,B``

![image](https://user-images.githubusercontent.com/30430227/164354468-afafa9a2-9bf4-46f2-b470-bdafd7d3cfcd.png)


>>> Empty - Damped Track(New Point Light) > Point Light(Empty to Parent)

![image](https://user-images.githubusercontent.com/30430227/164355343-c0b4610e-3662-49d2-9b40-7c88fa323e36.png)

>>> 거리 멀어지면 효과 없애기 Point Light - Driver

``거리에 따라 파워 떨어지게``

![image](https://user-images.githubusercontent.com/30430227/164357668-49dfb1f0-79d5-4466-928c-17e80e5a49a7.png)
![image](https://user-images.githubusercontent.com/30430227/164357579-b10f00a2-22d7-4eaa-b215-d8013835209f.png)

![image](https://user-images.githubusercontent.com/30430227/164357568-a65d88da-2e03-4436-9e86-4a29cfed95eb.png)

``수정-max(0,(5 - dist) * power)``

![image](https://user-images.githubusercontent.com/30430227/164357717-959035c6-ba2a-4371-8fc8-7965c8bbb491.png)










