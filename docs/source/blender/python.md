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
