Rigging
-------

**커스텀 프로퍼티 - 회전값 Expression**

``Copy New Driver > Paste Driver(Rotate) > to Radian(radians(prop))`` 

![image](https://user-images.githubusercontent.com/30430227/161925933-d7cbf67c-0a12-449b-95ae-298750baa68c.png)
![image](https://user-images.githubusercontent.com/30430227/161926179-6717b206-60de-412e-b2f5-5b7f1af2b283.png)

**If Expression**

.. code-block:: console 

 0 if switch == 1 or switch == 3 else 1
 switch 가 1 또는 3이면 0 그렇지 않으면 1
 
![image](https://user-images.githubusercontent.com/30430227/162124508-c6f53a30-e953-4c6c-9b30-78dc573cc521.png)
![image](https://user-images.githubusercontent.com/30430227/162124324-193e9849-a6f4-4228-9190-e3cb55a77b7c.png)


Sci-Fi Door
------------

![image](https://user-images.githubusercontent.com/30430227/162122820-8eca7cf7-51e9-444f-a91b-594712058e3a.png)
![image](https://user-images.githubusercontent.com/30430227/162122927-bb807f9b-0dc9-442d-b578-1b224cb8cb60.png)

``사라지는 문 Lattice > Shape Key``

![image](https://user-images.githubusercontent.com/30430227/162110119-48d13a4f-059d-40a7-bf82-9a251054b112.png)
![image](https://user-images.githubusercontent.com/30430227/162110201-09b5d205-0ffd-4ad7-b1a9-7b772d5860be.png)

``Apply Modifier > Move Door``

![image](https://user-images.githubusercontent.com/30430227/162110305-3790d235-ac7c-4040-8373-858e75b97b28.png)
![image](https://user-images.githubusercontent.com/30430227/162110331-cf2c51d8-6d8a-4893-92d1-e2761f71afb1.png)

``Root bone > Custom Property> Door bone Y-Location(Driven)``

![image](https://user-images.githubusercontent.com/30430227/162117579-ad2ad113-06d0-4182-b442-96bfa9aca303.png)
![image](https://user-images.githubusercontent.com/30430227/162117635-43e564ac-10df-44c8-ad11-0364f57bdb04.png)

![image](https://user-images.githubusercontent.com/30430227/162117651-57667de3-3dd9-4822-826c-56358c7b04d7.png)
![image](https://user-images.githubusercontent.com/30430227/162117994-2c9679a9-9207-4086-b2cd-cea2665816dd.png)

**Door 2**

``시간 차 오픈 top,bottom door Z-Axis > Limits``

![image](https://user-images.githubusercontent.com/30430227/162120234-0b63497e-161f-4ea5-a8ac-d9f6c7ed1a06.png)

![image](https://user-images.githubusercontent.com/30430227/162120669-e533e9cc-dece-42ae-98b9-b45d8e56a8fe.png)

![image](https://user-images.githubusercontent.com/30430227/162121468-9759067a-2b09-4da9-892f-54ee692b5990.png)
![image](https://user-images.githubusercontent.com/30430227/162121537-0f8c9ed3-590a-4594-82e5-cbcbb5f6c80e.png)

![image](https://user-images.githubusercontent.com/30430227/162121703-94450114-a3ee-4662-9472-d1f94da0fa8c.png)
![image](https://user-images.githubusercontent.com/30430227/162121575-16c49428-87fc-4874-9b5c-c9fdf7c5cdc1.png)
![image](https://user-images.githubusercontent.com/30430227/162121676-f8b5f5cd-27e8-45b3-a210-8d7f25de9104.png)

**Shader Driven(Fac)**

![image](https://user-images.githubusercontent.com/30430227/162122688-d99d9b58-adbe-4ab7-978a-804343bebcfc.png)
![image](https://user-images.githubusercontent.com/30430227/162122702-020993fc-b15b-4ae7-91d4-029301a507aa.png)

![image](https://user-images.githubusercontent.com/30430227/162122655-f21a7710-65fe-4700-86d2-75159a09f408.png)
