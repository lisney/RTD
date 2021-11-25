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

2. 패널 

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
        # row.operator('object.subdivision_set') # 상동 기능, F3 키 명령어 팝업에서 () 제거

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

4. 

