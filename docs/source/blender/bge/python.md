Python
======

1. 회전 

`Logic Brick Editor > Text Editor`

![image](https://user-images.githubusercontent.com/30430227/146662575-1a3c334e-dde5-4357-9d94-d1369d4c3374.png)

```
import bge

controller = bge.logic.getCurrentController()

owner = controller.owner

#owner.worldPosition.z += 0.1
owner.applyRotation([0,0,0.1])
```

<br>

2. 스페이스바 회전 

![image](https://user-images.githubusercontent.com/30430227/147081433-fd2dacfd-fe60-4149-bd73-1bae3c48d43e.png)

```
from bge import logic

cont = logic.getCurrentController()
owner = cont.owner

scene = logic.getCurrentScene()
objects = scene.objects

text_obj = objects['Text']

sens = cont.sensors['my_sensor']
act = cont.actuators['my_actuator']

if sens.positive:
    cont.activate(act)
    text_obj['Text'] = 'CADABRA'

else:
    cont.deactivate(act)
    text_obj['Text'] = 'ABRA'
```

![image](https://user-images.githubusercontent.com/30430227/147081544-c4e7c772-771b-4961-aff0-746e83292d34.png)

<br>

3. 파이썬 모듈

![image](https://user-images.githubusercontent.com/30430227/147171359-1a7fb51a-c97e-47df-97e7-fa2887fafb6b.png)

![image](https://user-images.githubusercontent.com/30430227/147171375-371a59d2-5105-461c-a822-ea769109c029.png)

```
def move(cont):
    own = cont.owner
    own.applyMovement([0,0.01,0], False) # [x,y,z], local(bool)
```

<br>

4. 카 속도 

`세팅 - 카 Mess:1, Force: Y5, Collision bounds(Box) - 박스는 메시의 센터를 기준으로 생긴다`

![image](https://user-images.githubusercontent.com/30430227/147172830-a27701ea-7722-42b7-9085-dec0bfaab4e2.png)

![image](https://user-images.githubusercontent.com/30430227/147172869-e7fbc04e-5db0-4f53-8f1e-22dad986110b.png)

![image](https://user-images.githubusercontent.com/30430227/147172918-f10b84ee-5cc6-4620-ade2-d88bd7e4bafc.png)

`카메라 - 카 따라다니는 카메라`

![image](https://user-images.githubusercontent.com/30430227/147173038-78a3991f-0eb0-4447-b909-84254e19cf0b.png)

![image](https://user-images.githubusercontent.com/30430227/147173113-1b2f7d1d-ed46-4ed6-ac59-64a2fa977a56.png)

`파이썬`

```
from bge import logic

gd = logic.globalDict

def getSpeed(cont):
    own = cont.owner
    gd['speed'] = own.localLinearVelocity.y
    
def setSpeedMeter(cont):
    own = cont.owner
    own['Text'] = gd.get('speed')
```

![image](https://user-images.githubusercontent.com/30430227/147175699-4bb1ac8a-1405-44bc-be24-0e152a892175.png)

`HUD; New Camera > New Collection`

![image](https://user-images.githubusercontent.com/30430227/147175947-5c2ce323-f217-4981-bf92-068d207be2c0.png)

![image](https://user-images.githubusercontent.com/30430227/147177579-5ff88c9d-481a-43f8-9fa6-104cbb42c85e.png)

`Camera`

![image](https://user-images.githubusercontent.com/30430227/147177622-658ed004-b1dc-4e52-8dd8-9be79a317623.png)

<br>

5. 이동 Physical, 회전

![image](https://user-images.githubusercontent.com/30430227/147186095-4e1609c4-4b65-4197-9477-11294095e116.png)

![image](https://user-images.githubusercontent.com/30430227/147186124-cb4dcc89-b101-4f12-bc85-4eb4dbd96c4d.png)

```
import math

def move(cont):
    own = cont.owner
    
    own.applyForce([0,3,0], False)
    
def rotation(cont):
    own = cont.owner
    
    # own.applyRotation([0,math.radians(3.14),0], False) #제자리 돌기
    # own.setAngularVelocity([0,math.radians(90),0], True) #구르기
    # own.localAngularVelocity = [0,math.radians(45),0] #앞과 같은 구르기
    own.applyTorque([0,math.radians(90),0], True) #더 잘 구른다?
    
```

<br>

6. 키보드 

`Reflection Plane/CubeMap > Bake - CubeMap은 삭제해도 되더라`

![image](https://user-images.githubusercontent.com/30430227/147197170-2fb6128c-d408-459c-a098-f16ee9148828.png)

```
from bge import logic, events

keyboard = logic.keyboard

def function(cont):
    own = cont.owner
    
    if key_space(events.SPACEKEY):
        own.applyForce([0,0,20], False)
        
    if key_w(events.WKEY):
        own.applyForce([0,0,200], True)
    
def key_space(key):
    return keyboard.events[key] == logic.KX_INPUT_ACTIVE # 누르고 있는 동안

def key_w(key):
    return keyboard.events[key] == logic.KX_INPUT_JUST_ACTIVATED # 한 번에 한 번
```

![image](https://user-images.githubusercontent.com/30430227/147197221-ee5852d0-b42f-4dd1-9998-ca291660ab82.png)

<br>

7. 구슬이 몇 개 있는지 거리 기준으로 찾기- getDistanceTo(obj)

![image](https://user-images.githubusercontent.com/30430227/147204950-11da7b31-325e-4248-9a9e-a63d71d90a59.png)
![image](https://user-images.githubusercontent.com/30430227/147204180-70b26002-8acc-43bb-9f47-53f14aea30ab.png)

`Debug Properties 체크 > Add Game Property 'items_around' - 느낌표버튼 체크해야 뷰포트에 표시된다`

![image](https://user-images.githubusercontent.com/30430227/147204331-41c06e3b-426c-49cc-a95d-f8c259337ea2.png)
![image](https://user-images.githubusercontent.com/30430227/147204208-36979f33-40de-4a45-a59b-9c4f13e07784.png)

```
추가 함수
def count_close_objects(obj, property, distance):
    scene = obj.scene
    count = 0
    for o in scene.objects:
        dist = obj.getDistanceTo(o)
        if dist <= distance and property in o: # property는 대상의 Game Property다
            count += 1
    return count
```

`구슬 > Add Game Property > function 함수 수정`

![image](https://user-images.githubusercontent.com/30430227/147204646-0228f3f3-225c-4d18-868e-05cfc31b79cc.png)

```
def function(cont):
    own = cont.owner
    
    own['items_around'] = count_close_objects(own, 'item', 4) # 이 라인 추가 
    ...
  
```

<br>

8. 총 빼고/넣기 - 애니메이션

![image](https://user-images.githubusercontent.com/30430227/147207138-a93177ac-ba36-4f97-a2dc-6703e5eb2961.png)

`Action Editor > Physics: No Collision> Parent(기존 큐브)`

![image](https://user-images.githubusercontent.com/30430227/147207180-384b026c-4ccd-44cb-9e49-3eb8c410ee4a.png)

![image](https://user-images.githubusercontent.com/30430227/147207578-e32adeef-2d00-4073-8187-c41a510333a4.png)

![image](https://user-images.githubusercontent.com/30430227/147208952-43968405-cd24-476f-bc96-35f36d44255a.png)


```
def draw_gun(obj, gunname, length, input):
    scene = obj.scene
    gun = scene.objects[gunname]
    if input:
        if gun['draw'] < length:
            gun['draw'] += 1
    else:
        if gun['draw'] > 0:
            gun['draw'] -= 1
            
function함수 수정
    aim = key_space(events.SPACEKEY)    
    draw_gun(own, 'Gun', 30, aim) #스페이스 누르고 있는 동안 +, 손 떼면 -(역)애니메이션
```

![image](https://user-images.githubusercontent.com/30430227/147210111-d43593ba-32cb-433f-b0d4-47fcf99c2773.png)


















