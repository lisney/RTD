Rigging
-------

**커스텀 프로퍼티 - 회전값 Expression**

``Copy New Driver > Paste Driver(Rotate) > to Radian(radians(prop))`` 

![image](https://user-images.githubusercontent.com/30430227/161925933-d7cbf67c-0a12-449b-95ae-298750baa68c.png)
![image](https://user-images.githubusercontent.com/30430227/161926179-6717b206-60de-412e-b2f5-5b7f1af2b283.png)

**또는 Python 사용 회전**

``bpy.context.scene.frame_current/10``

![image](https://user-images.githubusercontent.com/30430227/162128564-cb397160-0cae-4283-9758-707285d972c5.png)

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

**Multi Piston**

![image](https://user-images.githubusercontent.com/30430227/162127861-6278b54a-11eb-4f05-ba84-770518d6bec3.png)
![image](https://user-images.githubusercontent.com/30430227/162127896-732480b5-4351-422b-836b-7cba08c185f5.png)


``Root parent > Damped Track > Parent > Copy Transforms``
 
![image](https://user-images.githubusercontent.com/30430227/162126459-ae8d6100-1ae0-4f63-98f8-02e244c6cb86.png)
![image](https://user-images.githubusercontent.com/30430227/162126833-e942e6df-8a29-44b6-9f80-295c0cff3609.png)

![image](https://user-images.githubusercontent.com/30430227/162127010-73f2a175-ed70-4de3-bcbb-249e6cccd58b.png)
![image](https://user-images.githubusercontent.com/30430227/162127064-34615542-2652-4c5a-878d-fa2fd5c9f3cc.png)

![image](https://user-images.githubusercontent.com/30430227/162127776-0f59dee5-be73-4609-80c5-dc0e4bc0406e.png)
![image](https://user-images.githubusercontent.com/30430227/162127820-d8e96374-895b-42f0-b3a7-fac3d9846ba4.png)

**Eye Rig**

``Shape Keys > New Shape from Mix > UP, Down Vertex Group``

![image](https://user-images.githubusercontent.com/30430227/162130749-6cae8b83-8297-42f2-81bd-a63294bc0f3e.png)
![image](https://user-images.githubusercontent.com/30430227/162130968-24341306-3f78-4ac8-8b57-14c7afd52824.png)

![image](https://user-images.githubusercontent.com/30430227/162131228-a5e66046-beee-4025-b336-fa128f4b0ce6.png)

![image](https://user-images.githubusercontent.com/30430227/162131357-23fb2a5e-8bd7-4f2d-b048-d0d5620425a3.png)

``Shape Key Driver``

![image](https://user-images.githubusercontent.com/30430227/162131964-e5b5d387-e310-4348-b5da-101b6dbfc716.png)
![image](https://user-images.githubusercontent.com/30430227/162131854-6a80143a-3e6d-45ba-a38a-0522c6d8b532.png)

![image](https://user-images.githubusercontent.com/30430227/162131824-3139d7b0-d5ff-4ce7-aeeb-24d92ed957f5.png)



