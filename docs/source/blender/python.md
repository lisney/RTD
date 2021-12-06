Python
==========

VSCode
-----------------------

1. 개발자 Extension 설치 

![image](https://user-images.githubusercontent.com/30430227/143177111-c9d7668f-26ae-4932-96b4-cf51fb679de7.png)

2. Ctrl - Shift - P

`Blender: New Addon 실행`

![image](https://user-images.githubusercontent.com/30430227/143177427-37f0aef2-babf-4d45-bc3e-4479abd1da35.png)

`블렌더 Addon/Script 폴더에 새폴더를 생성하고 선택한다`

3. VSCode 에서 생성한 폴더를 연다

![image](https://user-images.githubusercontent.com/30430227/143178015-b7293fca-e93f-4ab6-9fdd-11df9df93d2e.png)

`__init__.py`

![image](https://user-images.githubusercontent.com/30430227/143178095-5b29430d-8f22-49d8-bd78-e97a6b1aa092.png)

4. Blender Start

![image](https://user-images.githubusercontent.com/30430227/143178232-c0eddc37-3f5d-4240-b084-213a6062ffd2.png)

---------

5. 그냥 블렌더 실행시키고 .py파일 연다

`VSCode에서 편집하고 블렌더에서 파일 갱신하면 된다`

<br>

자동완성 세팅 
-------------

`blender_autocomplete-master.zip 다운`

![image](https://user-images.githubusercontent.com/30430227/143220970-d00f75ca-2ba7-4aee-af20-517c394d0e1e.png)

`작업 폴더 생성 > 라이브러리 풀기 > VSCode 에서 Open Folder`

![image](https://user-images.githubusercontent.com/30430227/143221230-38deef53-99f6-4aa1-bcf0-b9dce1303404.png)
![image](https://user-images.githubusercontent.com/30430227/143221196-739b449e-6e88-4bd8-a474-597eece0de0d.png)

`추가 - 파이썬 맞춤법 검사기? > Shift - Ctrl - P > Pyline 선택 > .Vscode 폴더 자동으로 생긴다`

![image](https://user-images.githubusercontent.com/30430227/143222173-f50c90af-b4b3-44b7-8ff5-9b2b63c6959f.png)

`.Vscode/setting.json`

![image](https://user-images.githubusercontent.com/30430227/143221398-c7b95e44-a405-4e23-894f-8fa0e300e31c.png)

![image](https://user-images.githubusercontent.com/30430227/143221654-f4b0cc43-2b37-418d-a4d1-c05b4a11b2a7.png)

```
"python.autoComplete.extraPaths": [
     "d:\\my_project\\blender_autocomplete\\2.90",
     "_PATH_TO_BLENDER_\\2.90\\scripts\\modules",
]

_PATH_TO_BLENDER_ 블렌더 설치 패스
```

-------------

코딩
-------

1. 랜덤 생성 

`context 변할 수 있는 설정 prop- 속성값(Context의 하위개념?)`

![image](https://user-images.githubusercontent.com/30430227/143227607-87f0feb0-9a2e-4d71-83a3-b51b12828d33.png)

```
import bpy

from random import randint

for i in range(5):
    x = randint(-3, 3)
    y = randint(-3, 3)
    z = randint(-3, 3)
    bpy.ops.mesh.primitive_monkey_add(location=(x,y,z))
    bpy.ops.object.modifier_add(type='SUBSURF')
    bpy.context.object.modifiers['Subdivision'].render_levels = 3
    bpy.context.object.modifiers['Subdivision'].levels = 3
```

<br>

2. 패널 - bpy.types.Panel

![image](https://user-images.githubusercontent.com/30430227/143232485-320921ac-fcdc-4c8f-ac40-f73da7189ed5.png)

```
import bpy

class CrayPanel(bpy.types.Panel):
    bl_label = "블랜더 패널"
    bl_space_type = 'PROPERTIES' 
    bl_region_type ='WINDOW'   # properties창 그룹의
    bl_context = 'collection'  # collection 탭(콘텐스트)에 생긴다
 
    def draw(self, context):
        self.layout.row().label(text='블렌더의 세계', icon='WORLD_DATA')

bpy.utils.register_class(CrayPanel)
```

----
- @ 데코레이션

`@ 데코함수명 - 다음에 오는 함수를 데코함수로 장식`
```
import datetime

def datetime_decorator(func):
    def decorated():
        print(datetime.datetime.now())
        func()
        print(datetime.datetime.now())
    return decorated

@datetime_decorator
def main_function_1():
    print("MAIN FUNCTION 1 START")

@datetime_decorator
def main_function_2():
    print("MAIN FUNCTION 2 START")
    
main_function_1()
main_function_2()
```

`*args, **kwargs 여러 개의 인수`

```
def full_name(*names):
    for name in names:
        print(name[0],name[1:3], end=' ')
    print('\n')
    
full_name('이천수','안정환')
full_name('이천수')
```

`클래스 사용`
```
import datetime

class DatetimeDecorator:
    def __init__(self,f):
        self.func = f
        
    def __call__(self,*args,**kwargs):
        print(datetime.datetime.now())
        self.func(*args, **kwargs)
        print(datetime.datetime.now())

class MainClass:
    @DatetimeDecorator
    def main_function_10():
        print('Function 1 start')
        
    @DatetimeDecorator
    def main_function_20():
        print('Function 2 start')

my = MainClass()
    
my.main_function_10()
my.main_function_20()
```

-----

3. 오브젝트 패널 

```
import bpy

class HelloWorld(bpy.types.Panel):
    bl_label = '헬로월드'
    bl_idname = 'OBJECT_PT_hello'
    bl_space_type = 'PROPERTIES'
    bl_region_type = 'WINDOW'
    bl_context = 'object'
    
    def draw(self, context):
        layout = self.layout
        obj = context.object
        row = self.layout.row() 
        
        row.label(text='Hello World!', icon='WORLD_DATA')
        row = layout.row() #\n 개행

        row.label(text='Active object is:'+obj.name) #  현재 선택한 오브젝트 이름
        row = layout.row()

        row.operator('mesh.primitive_cube_add') # 명령 실행 버튼
        row = layout.row()
        
        row.operator('object.modifier_add').type="SUBSURF"   
        # row.operator('object.subdivision_set') # 상동 기능, F3 키 명령어 팝업에서 .ops, () 뺀 이름

def register():
    bpy.utils.register_class(HelloWorld)

def unregister():
    bpy.utils.unregister_class(HelloWorld)

if __name__ == '__main__':
    register()
```

> 블렌더 시작 스크립트 파일 폴더

![image](https://user-images.githubusercontent.com/30430227/143384264-ed749f53-57bd-49d7-ae9c-140d8ac77f8c.png)

![image](https://user-images.githubusercontent.com/30430227/143384308-126525a0-ff3a-4c26-86ea-9249a643ed5e.png)

<br>

4. 실행 - bpy.types.Operator

![image](https://user-images.githubusercontent.com/30430227/143427068-a6ebeb88-692e-44d0-be04-0aab17ff7ff3.png)

```
import bpy

# print 내장 콘솔 출력 - 한글 지원
# def print(data):
#     window=bpy.context.window_manager.windows[0]
#     screen = window.screen
#     for area in screen.areas:
#         if area.type == 'CONSOLE':
#             bpy.ops.console.scrollback_append(
#                 {'window': window, 'screen': screen, 'area': area},
#                 text=str(data))

class CustomArrayOperator(bpy.types.Operator):
    # 오퍼레이터 아이디값[
    bl_idname = "object.custom_draw"
    # 팝업창 이름
    bl_label = "Arr 배열 복사"

    # 속성 정의
    x_repeat : bpy.props.IntProperty(name="갯수")

    def invoke(self, context, event):
        wm = context.window_manager
        return wm.invoke_props_dialog(self)

    def draw(self, context):
        layout = self.layout
        
        # 행 추가
        row = layout.row()
        # 입력 항목 - 속성 매칭
        row.prop(self, "x_repeat")
        
    def execute(self, context):    
        
        selected_objects=bpy.context.selected_objects
        if len(selected_objects) == 0:
            self.report({'ERROR'}, "오브젝트를 선택하세요")
            return {'FINISHED'}

        org_name=selected_objects[0].name;

        for x in range(1, self.x_repeat + 1):
            bpy.data.objects[org_name].select_set(True)
            bpy.ops.object.duplicate_move(
                OBJECT_OT_duplicate={"mode":'TRANSLATION'},
                TRANSFORM_OT_translate={"value":(x * 4, 0, 0)})
            bpy.ops.object.select_all(action='DESELECT')

        self.report({'INFO'}, "오브젝트가 복사되었습니다.")
        
        return {'FINISHED'}

bpy.utils.register_class(CustomArrayOperator)

# test call
bpy.ops.object.custom_draw('INVOKE_DEFAULT')
```
```
- bpy.data.objects[org_name].select_set(True)
오브젝트는 복사를 하고 나면 복사한 오브젝트로 선택이 옮겨져 버립니다.
그래서 복사전 항상 원본을 선택

- bpy.ops.object.select_all(action='DESELECT')
복사 후에는 선택이 마지막 오브젝트로 가 있을 겁니다. 선택을 취소

- bpy.ops.object.custom_draw('INVOKE_DEFAULT')
클래스의 invoke 함수가 실행되고 invoke 는 draw 를 실행해서 다이얼로그를 보여준 다음,
OK 버튼을 누르면 execute() 함수가 실행되는 거지요.
```

<br>

5. 프로퍼티, 패널, 오퍼레이터 클래스 복합 

![image](https://user-images.githubusercontent.com/30430227/143569098-54cdcfb2-b183-46e3-b80c-82f8194ad475.png)

```
import bpy

class C_PROP(bpy.types.PropertyGroup):
    x_repeat: bpy.props.IntProperty(name="X반복", default=0)
    y_repeat: bpy.props.IntProperty(name="Y반복", default=0)

class C_PANEL(bpy.types.Panel):
    bl_label = "VIEW 3D"
    bl_category = "브러시"
    bl_space_type = "VIEW_3D"
    bl_region_type = "UI"

    def draw(self, context):
        row = self.layout.row()
        row.label(text="오브젝트 : ", icon='OBJECT_DATA')
        box = self.layout.box()
        obj = context.object
        if obj is not None:
          box.label(text=obj.name, icon='KEYFRAME')
          
        row = self.layout.row()
        row.prop(context.scene.c_prop, "x_repeat")
        row = self.layout.row()
        row.prop(context.scene.c_prop, "y_repeat")
        
        row = self.layout.row()
        row.operator("cray.spin", text="복사")
    
class C_OPER(bpy.types.Operator):
    bl_idname = 'cray.spin'
    bl_label = 'cray.spinoperator'

    def execute(self, context):        
        print(context.scene.c_property.x_repeat, context.scene.c_property.y_repeat)
        
        selected_objects=bpy.context.selected_objects
        if len(selected_objects) == 0:
            self.report({'ERROR'}, "오브젝트를 선택하세요")
            return {'FINISHED'}

        org_name=selected_objects[0].name;
                
        for x in range(context.scene.c_prop.x_repeat + 1):
            for y in range(context.scene.c_prop.y_repeat + 1):
                if x==0 and y==0:
                    continue
                bpy.data.objects[org_name].select_set(True)
                bpy.ops.object.duplicate_move(
                    OBJECT_OT_duplicate={"mode":'TRANSLATION'},
                    TRANSFORM_OT_translate={"value":(x * 4, y * 4, 0)})
                bpy.ops.object.select_all(action='DESELECT')

        self.report({'INFO'}, "오브젝트가 복사되었습니다.")
        
        return {'FINISHED'}
    
bpy.utils.register_class(C_PROP)
bpy.types.Scene.c_prop = bpy.props.PointerProperty(type=C_PROP)
bpy.utils.register_class(C_OPER)
bpy.utils.register_class(C_PANEL)
```

<br>

6. 애드온

```
# bl_info - 애드온을 위한 변수

bl_info = {
    "name": "CraySpin",
    "author": "Cray",
    "version": (0, 1, 0),
    "blender": (2, 80, 0),
    "location": "View3D > Sidebar > cray",
    "description": "오브젝트 배열 복사 애드온 샘플코드",
    "category": "CrayTool",
}

###################
import bpy

def print(*datas):
    window=bpy.context.window_manager.windows[0]
    screen = window.screen
    for area in screen.areas:
        if area.type == 'CONSOLE':
            for data in datas:
                bpy.ops.console.scrollback_append(
                    {'window': window, 'screen': screen, 'area': area},
                    text=str(data))

class CRAYSPIN_PROPERTY(bpy.types.PropertyGroup):
    x_repeat: bpy.props.IntProperty(name="X반복", default=0)
    y_repeat: bpy.props.IntProperty(name="Y반복", default=0)

class CRAYSPIN_PT_panel(bpy.types.Panel):
    bl_label = "크레이 스핀 도구창"
    bl_category = "크레이"
    bl_space_type = "VIEW_3D"
    bl_region_type = "UI"

    def draw(self, context):
        row = self.layout.row()
        row.label(text="선택 오브젝트 : ", icon='OBJECT_DATA')
        box = self.layout.box()
        obj = context.object
        if obj is not None:
          box.label(text=obj.name, icon='KEYFRAME')
          
        row = self.layout.row()
        row.prop(context.scene.crayspin_property, "x_repeat")
        row = self.layout.row()
        row.prop(context.scene.crayspin_property, "y_repeat")
        
        row = self.layout.row()
        row.operator("cray.spinoperator", text="복사")
    
class CRAYSPIN_Operator(bpy.types.Operator):
    bl_idname = 'cray.spinoperator'
    bl_label = 'cray.spinoperator'

    def execute(self, context):        
        print(context.scene.crayspin_property.x_repeat, context.scene.crayspin_property.y_repeat)
        
        selected_objects=bpy.context.selected_objects
        if len(selected_objects) == 0:
            self.report({'ERROR'}, "오브젝트를 선택하세요")
            return {'FINISHED'}

        org_name=selected_objects[0].name;
                
        for x in range(0, context.scene.crayspin_property.x_repeat + 1):
            for y in range(0, context.scene.crayspin_property.y_repeat + 1):
                if x==0 and y==0:        continue
                bpy.data.objects[org_name].select_set(True)
                bpy.ops.object.duplicate_move(
                    OBJECT_OT_duplicate={"mode":'TRANSLATION'},
                    TRANSFORM_OT_translate={"value":(x * 4, y * 4, 0)})
                bpy.ops.object.select_all(action='DESELECT')

        self.report({'INFO'}, "오브젝트가 복사되었습니다.")
        
        return {'FINISHED'}
    
classes = (
   CRAYSPIN_PROPERTY,
   CRAYSPIN_PT_panel,
   CRAYSPIN_Operator,
)


def register():
    for cls in classes:
        bpy.utils.register_class(cls)
    bpy.types.Scene.crayspin_property = bpy.props.PointerProperty(type=CRAYSPIN_PROPERTY)

# unregister함수 - 애드온 체크해제 할 때 실행
def unregister():
    for cls in classes:
        bpy.utils.unregister_class(cls)
    del bpy.types.Scene.crayspin_property

# 블렌더 실행할 때 해당 스크립트 실행을 막는다.(main이 아니므로) 자체적으로 실행해야 실행된다.(실행할 때 main이다) 
if __name__ == "__main__":
    register()
```

<br>

UI 배끼기
---------

`기존 UI요소 오른클릭 > Edit Source`

![image](https://user-images.githubusercontent.com/30430227/144031741-baba0d90-a098-466a-8104-f22ae1709866.png)

`해당 스크립트 명령줄을 가리킨다`

![image](https://user-images.githubusercontent.com/30430227/144031808-5bffcf54-9afe-4759-adbf-925e41ce96ad.png)

`복사해서 자신의 Py에 붙여넣기 - 변수도 같이 복사한다`

![image](https://user-images.githubusercontent.com/30430227/144032096-dbcb5815-82d8-4579-91f0-3ba499eb8286.png)

![image](https://user-images.githubusercontent.com/30430227/144032290-ff18a6bf-cc74-47a7-88ad-a591eccdca90.png)

<br>

CSV 그래프 
-----------

1. import csv

```
import csv

with open('c:/users/3dprinter/desktop/sample.csv') as f:
    readout = list(csv.reader(f))
    print(readout)  #  시스템 콘솔에서 확인
```

2. 바 생성 > Cube 생성 후 info 창에서 파이썬 명령 복사

![image](https://user-images.githubusercontent.com/30430227/144152726-ac4bfe53-54ad-4348-b55a-87741fd42f2d.png)

```
import csv
import bpy

bar_space = 1.5
bar_width = 1

with open('c:/users/3dprinter/desktop/sample.csv') as f:
    readout = list(csv.reader(f))
    # print(readout)
    
for i in readout:
    placement = readout.index(i) # 인덱스
    bpy.ops.mesh.primitive_cube_add(size=1)
    new_bar = bpy.context.object # 현재 선택된 오브젝트
    
    for vert in new_bar.data.vertices:
        vert.co[1] += 0.5 # y방향으로, co[0]- X 방향 # Y 축 원점 -> 바닥
        vert.co[0] += placement*bar_space + 0.5 # X 축 원점 -> 좌측
        
    new_bar.scale = (bar_width, float(i[1]), 1)
```

3. 텍스트 생성 

![image](https://user-images.githubusercontent.com/30430227/144155031-a5f63b3c-f8d4-4c86-9b76-5a3589cb04f3.png)

```
for i in readout:
    placement = readout.index(i)
    bpy.ops.mesh.primitive_cube_add(size=1)
    new_bar = bpy.context.object
    
    for vert in new_bar.data.vertices:
        vert.co[1] += 0.5 # y방향으로, co[0]- X 방향
        vert.co[0] += placement*bar_space + 0.5
        
    new_bar.scale = (bar_width, float(i[1]), 1)
    
    bpy.ops.object.text_add()
    bpy.context.object.data.align_x = 'RIGHT'
    bpy.context.object.data.align_y = 'CENTER'
    bpy.ops.transform.rotate(value=-1.5708)
    bpy.ops.transform.translate(value=(placement*bar_space + 0.5, -0.4, 0))
    bpy.context.object.data.body = i[0]
```

<br>

모델링
------

`URBANBASE TECH BLOG 참조`

1. 모듈 

```
-bpy.data –블렌더 프로그램에서 모델링한 것을 저장할 때, .blend 파일에 저장되는 데이터들을 다루는 모듈 –점/선/면으로 정의된 mesh, 색/거칠기/매끄러움 등 물체의 재질을 표현하는 material, mesh/material/texture 등의 정보를 포함하는 하나의 물체 자체를 표현하는 object 등을 포함

-bpy.context –현재 블렌더의 컨텍스트에 대한 데이터들(활성화된 창에 대한 데이터들)을 다루는 모듈 –선택된 object들이나 현재 scene과 같은 데이터

-bpy.ops –사용자가 GUI 상에서 블렌더와 상호작용하는 모든 행위에 대한 operation을 다루는 모듈 –object를 조작하는 행위들을 bpy.ops를 통해 스크립트에서 구현이 가능

import bpy
from mathutils import Vector
from math import inf, radians
import os
# bpy, mathutils 블렌더 모듈
```

2. 함수 생성

```
reset_blender_data – 스크립트 실행 전에 불필요한 데이터들을 삭제하는 함수
create_cube – 인자로 받은 위치와 사이즈를 통해 직육면체를 생성하고 배치하는 함수
set_object_color_rgba – 블렌더 object의 색을 설정하는 함수
get_boundary_info – 블렌더 object를 감싸는 bounding box의 정보를 계산하여 반환하는 함수
create_floor_plane – 블렌더 object 밑에 바닥면을 생성하는 함수
create_camera – 특정 물체를 바라보는 카메라 object를 생성하는 함수
create_sunlight – 태양광에 해당하는 조명 object를 생성하는 함수
save_image_with_gpu – 렌더링에 사용할 엔진 설정 – 해상도 설정 – 인자로 받은 경로에 렌더링 결과 사진을 저장
```

`코딩`

```
def reset_blender_data():
    for bpy_data_iter in (
            bpy.data.objects,
            bpy.data.meshes,
            bpy.data.lights,
            bpy.data.cameras,
            bpy.data.materials
    ):
        for id_data in bpy_data_iter:
            bpy_data_iter.remove(id_data)
            
def create_cube(location, scale):
    bpy.ops.mesh.primitive_cube_add(size=1.0)
    cube_object = bpy.context.active_object
    cube_object.name = "cube"
    cube_object.location = location
    cube_object.scale = scale
    return cube_object        
    
def set_object_color_rgba(blender_object, color):
    material = bpy.data.materials.new(name=blender_object.name)
    material.use_nodes = True

    principled_bsdf_node = material.node_tree.nodes['Principled BSDF']
    principled_bsdf_node.inputs['Base Color'].default_value = color

    blender_object.data.materials.append(material)
    
    
def get_boundary_info(blender_object):
    bpy.context.view_layer.update()

    min_point = [inf, inf, inf]
    max_point = [-inf, -inf, -inf]

    boundary_points = [blender_object.matrix_world @
                       Vector(point) for point in blender_object.bound_box]
    for point in boundary_points:
        for i in range(3):
            if point[i] > max_point[i]:
                max_point[i] = point[i]
            if point[i] < min_point[i]:
                min_point[i] = point[i]

    center_point = []
    boundary_length = []
    for i in range(3):
        center_point.append((min_point[i]+max_point[i])/2)
        boundary_length.append(max_point[i]-min_point[i])

    boundary_info = {
        "min_point": min_point,
        "max_point": max_point,
        "center_point": center_point,
        "boundary_length": boundary_length
    }

    return boundary_info
# 생성한 큐브 밑에 바닥면을 생성할 때 필요한 정보를 구하기 위해 만든 함수입니다. 
# 블렌더는 object의 bound_box 속성에서 해당 object를 감싸는 bounding box의 8개 정점에 대한 정보를 제공합니다. 하지만 이 정보들은 모델 좌표계 기준의 좌표이기 때문에 이를 월드 좌표계로의 변환이 필요합니다.

모델 좌표계를 월드 좌표계로 변환해주는 월드 변환 행결은 object의 matrix_world 속성을 통해 알 수 있습니다. 블렌더에서는 효율성을 위해 object의 transform이 변경되어도 바로 matrix_world 속성을 다시 계산하여 갱신하지 않습니다. 따라서 사용자는 bpy.context.view_layer.update()를 호출하여 갱신을 요청해야 matrix_world 속성이 갱신됩니다.

갱신한 matrix_world에 bounding box의 각 정점을 곱하면 해당 정점의 월드 좌표계를 구할 수 있습니다. @는 mathutils에서 제공하는 연산으로 행렬 및 벡터의 곱하기 연산을 의미합니다. 정점들의 월드 좌표계를 이용하여 최소값, 최대값, 중점, 길이를 계산하면 해당 정보들을 딕셔너리로 반환해줍니다.  

def create_floor_plane(blender_object):
    boundary_info = get_boundary_info(blender_object)
    min_point = boundary_info["min_point"]
    center_point = boundary_info["center_point"]

    plane_position = (center_point[0], center_point[1], min_point[2])
    plane_scale = (20, 20, 1)

    bpy.ops.mesh.primitive_plane_add()
    plane_object = bpy.context.active_object
    plane_object.name = "floor plane"
    plane_object.location = plane_position
    plane_object.scale = plane_scale
    
# 바닥면의 x,y좌표는 object의 중심의 x,y좌표와 일치시켜주고, z좌표는 object의 z좌표 중 가장 작은 값으로 설정해 줍니다. scale의 경우 카메라 화면에 꽉 차도록 제가 임의로 설정

def create_camera(location, target_vector):
    camera_data = bpy.data.cameras.new("Main Camera")
    camera_data.lens = 50

    camera_object = bpy.data.objects.new("Main Camera", camera_data)
    camera_object.location = location

    scene = bpy.context.scene
    scene.collection.objects.link(camera_object)
    scene.camera = camera_object

    # lookAt the target point
    if not isinstance(target_vector, Vector):
        target_vector = Vector(target_vector)
	
	camera_location = camera_object.location
    direction = target_vector - location
    quat = direction.to_track_quat('-Z', 'Y')
    camera_object.rotation_euler = quat.to_euler()

    return camera_object
    
# 우선 bpy.data.cameras.new 함수를 사용하여 카메라 데이터를 생성합니다. 카메라 데이터는 카메라 시점에 대한 데이터들을 가지고 있는데, 투영 방법(평행, 원근)이나 가시 부피과 관련된 데이터들이 있습니다.

bpy.data.objects.new 함수를 사용하여 생성한 카메라 데이터를 지니는 blender object를 생성합니다. 이 object를 카메라 객체라고 부르겠습니다.

카메라 객체의 location 속성을 인자로 받은 location으로 설정하여 카메라 객체의 위치를 설정합니다. 생성한 카메라 객체를 현재 씬에 추가하고 씬의 메인 카메라로 설정해야 합니다.

bpy.context.scene는 현재 씬을 가리키는데, 현재 씬에 대해서 collection.objects.link 메소드를 통해 생성한 카메라 객체를 추가해줍니다. 그리고 현재 씬의 camera 속성을 카메라 객체로 설정해주면 씬의 메인 카메라가 설정됩니다.

마지막으로 카메라가 target_vector를 향하도록 회전을 해주어야 합니다. 카메라가 바라 보는 방향인 direction을 계산해야 하는데, mathutils의 Vector를 사용하기 위해 튜플형의 location 변수를 그대로 사용하지 않고, camera_object.location를 direction 계산 시에 사용합니다.

카메라가 생성되면 디폴트 값으로 -Z축을 바라보며 up-vector는 Y축 방향이 됩니다. 그래서 카메라가 바라보아야 하는 direction에 대해서 to_track_quat(‘-Z’, ‘Y’) 함수를 이용하면 카메라 transform의 회전값을 구할 수 있습니다.

이 회전값은 쿼터니안 각이기 때문에, 오일러 각을 사용하여 카메라의 회전값을 설정하기 위하여 to_euler()를 통해 쿼터니안을 오일러로 변환해 각도를 설정합니다.

def create_sunlight():
    light_data = bpy.data.lights.new(name="sun", type="SUN")
    light_data.energy = 4.5

    light_object = bpy.data.objects.new(
        name="sun", object_data=light_data
    )
    light_object.rotation_euler = (radians(20), radians(30), radians(-20))

    scene = bpy.context.scene
    scene.collection.objects.link(light_object)

    return light_object
    
# 여기서는 간단하게 빛의 세기만을 설정합니다.광원 object를 만드는 과정은 카메라 object를를 만드는 것과 똑같습니다. 다만 방향성 광원의 경우 광원의 방향만 중요하기 때문에 위치 대신 회전값을 설정하였습니다.

def save_image_with_gpu(resolution, file_path, file_name):
    scene = bpy.context.scene

    scene.render.resolution_x = resolution
    scene.render.resolution_y = resolution

    scene.render.engine = 'CYCLES'
    scene.cycles.device = 'GPU'
    scene.cycles.denoiser = 'NLM'
    scene.cycles.use_denoising = True

    # set Cycles add-on
    cycles_preferences = bpy.context.preferences.addons['cycles'].preferences
    cycles_preferences.compute_device_type = "CUDA"

    for devices in cycles_preferences.get_devices():
        for device in devices:
            if device.type == "CUDA":
                device.use = True
            else:
                device.use = False

    if not os.path.exists(file_path):
        os.makedirs(file_path)
	
	# output setting
    scene.render.image_settings.file_format='PNG'
    scene.render.filepath = os.path.join(file_path, file_name)
	
	# rendering
    bpy.ops.render.render(write_still=True)
    
 # 여기서는 Cycles 엔진을 사용하여 렌더링하며, Nvidia GPU가 있다는 가정하에 gpu를 이용하여 렌더링 속도를 빠르게 하였습니다.
 해상도에 해당하는 x축 픽셀수와 y축 픽셀수는 scene.render에서 설정하는데 여기서는 정사각형 형태로 설정하였습니다.
 scene.cycles에서는 GPU 설정 및 잡음 제거를 위한 설정을 해줍니다.
그리고 GPU 사용 설정을 위해서는 추가적으로 Cycles 애드온도 설정이 필요하기 때문에, bpy.context.preferences.addons[‘cycles’].preferences를 통해 애드온 설정을 따로 해주었습니다.
scene.render.image_settings 에서는 저장할 아웃풋 이미지의 포멧 및 압축률과 같은 설정을 할 수 있는데 여기서는 단순히 png 형식으로 저장하도록 설정하였습니다.
scene.render에서 저장할 디렉토리를 설정하고, 마지막으로 bpy.ops.render.render를 통해 렌더링 및 위에서 설정한 형식으로 결과물을 저장합니다.   
      
```

<br>

3. Main 함수 

```
if __name__ == "__main__":
    reset_blender_data()

    cube_loc = (0, 0, 0)
    cube_size = (2, 1, 3)
    cube_color = (0.8, 0.35, 0.29, 1.0)
    cube_obj = create_cube(cube_loc, cube_size)
    set_object_color_rgba(cube_obj, cube_color)

    create_floor_plane(cube_obj)

    camera_loc = (4.5, 6, 5)
    create_camera(camera_loc, cube_loc)

    create_sunlight()

    save_image_with_gpu(1024, "D://", "Test")
```

<br>

4. 실행

```
blender --background --python <스크립트 절대 경로>
blender --background --python D:\test.py
```

<br>

테스트
------

```
import bpy
from mathutils import Vector
from math import inf, radians
import os

def reset_blender_data():
    for bpy_data_iter in (bpy.data.objects, bpy.data.meshes, bpy.data.cameras):
        for id_data in bpy_data_iter:
            bpy_data_iter.remove(id_data)
            
 
def create_cube(location,scale):
    bpy.ops.mesh.primitive_cube_add() 
    cube_object = bpy.context.active_object
    cube_object.name = 'cube'
    cube_object.location = location
    cube_object.scale = scale
    bpy.context.view_layer.update() # 매트릭스 갱신
    boundary_points = [cube_object.matrix_world @ Vector(point) for point in cube_object.bound_box] # 바운딩박스 8개 점 리스트
    
    # create_floor
    center_point = []
    for i in range(3):
        center_point.append((boundary_points[0][i] + boundary_points[6][i])/2)
    
    plane_position = (center_point[0], center_point[1], boundary_points[0][2])
    plane_scale = (20,20,1)
    
    bpy.ops.mesh.primitive_plane_add(location=plane_position)
    plane_object = bpy.context.active_object
    plane_object.name = 'floor plane'
    # plane_object.locaton = plane_position
    plane_object.scale=plane_scale # location은 적용되나 scale은 생성 시 적용되지 않는다?
    bpy.context.view_layer.update() # 매트릭스 갱신
        
    print(center_point)
    
    return cube_object

def set_object_color_rgba(blender_object, color):
    material = bpy.data.materials.new(name=blender_object.name)
    material.use_nodes = True

    principled_bsdf_node = material.node_tree.nodes['Principled BSDF']
    principled_bsdf_node.inputs['Base Color'].default_value = color

    blender_object.data.materials.append(material)

def get_boundary_info(blender_object):
    bpy.context.view_layer.update()
           
if __name__ == '__main__':
    reset_blender_data()
    
    cube_obj = create_cube((2,2,0),(2,1,3))
    set_object_color_rgba(cube_obj, (0.8,0.35,0.29,1.0))
```
