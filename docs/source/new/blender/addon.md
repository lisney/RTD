Python
========


파이썬 스크립트 자동실행 토글 
---------------------------

![image](https://user-images.githubusercontent.com/30430227/184476159-e61a59ec-1d75-43eb-b9d7-f3fe3b81fc1f.png)



X 축 방향으로 1 이동
--------------

![image](https://user-images.githubusercontent.com/30430227/184336436-e6ffe6a3-bc51-4f3b-aa14-482754d6e4bb.png)

```
bl_info = {
    "name": "Move X Axis",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy


class ObjectMoveX(bpy.types.Operator):
    """My Object Moving Script"""      # Use this as a tooltip for menu items and buttons.
    bl_idname = "object.move_x"        # Unique identifier for buttons and menu items to reference.
    bl_label = "Move X by One"         # Display name in the interface.
    bl_options = {'REGISTER', 'UNDO'}  # Enable undo for the operator.

    def execute(self, context):        # execute() is called when running the operator.

        # The original script
        scene = context.scene
        for obj in scene.objects:
            obj.location.x += 1.0

        return {'FINISHED'}            # Lets Blender know the operator finished successfully.

def menu_func(self, context):
    self.layout.operator(ObjectMoveX.bl_idname)

def register():
    bpy.utils.register_class(ObjectMoveX)
    bpy.types.VIEW3D_MT_object.append(menu_func)  # Adds the new operator to an existing menu.

def unregister():
    bpy.utils.unregister_class(ObjectMoveX)


# This allows you to run the script directly from Blender's Text editor
# to test the add-on without having to install it.
if __name__ == "__main__":
    register()
```

`텍스트 에디터에서 스크립트 실행 Alt-P > 메뉴로 등록된다`

![image](https://user-images.githubusercontent.com/30430227/184477835-7472c085-ff4b-475f-990a-3b7c0ec37605.png)
![image](https://user-images.githubusercontent.com/30430227/184477779-b45b9507-81de-4c03-a733-aceef4da0dde.png)


현재 커서 위치로 복사한다
------------------------

![image](https://user-images.githubusercontent.com/30430227/184478001-250be0ac-10c5-4e73-8be3-df71f8276516.png)
![image](https://user-images.githubusercontent.com/30430227/184478009-a1b6ca9d-4181-4036-b7ef-84fb0b141416.png)

```
import bpy
from bpy import context

# Get the current scene
scene = context.scene

# Get the 3D cursor location
cursor = scene.cursor.location

# Get the active object (assume we have one)
obj = context.active_object

# Now make a copy of the object
obj_new = obj.copy()

# The new object has to be added to a collection in the scene
scene.collection.objects.link(obj_new)

# Now we can place the object
obj_new.location = cursor
```

`10회 복사`

![image](https://user-images.githubusercontent.com/30430227/184478453-186ae1d5-1259-4e77-8979-057a9a54c3b8.png)
![image](https://user-images.githubusercontent.com/30430227/184478457-209efa0d-11ef-4e36-b59d-14987f82b9b5.png)

```
import bpy
from bpy import context

scene = context.scene
cursor = scene.cursor.location
obj = context.active_object

total = 10

for i in range(total):
    obj_new = obj.copy()
    scene.collection.objects.link(obj_new)
    
    factor = i / total
    obj_new.location = (obj.location*factor) + (cursor*(1.0 -factor))
```

![image](https://user-images.githubusercontent.com/30430227/184478713-c01de7c5-cdd4-4f64-b5f5-27d0c5bc5de2.png)


`애드온으로 작성 > 'F3'으로 실행`

```
bl_info = {
    "name": "Cursor Array",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy


class ObjectCursorArray(bpy.types.Operator):
    """Object Cursor Array"""
    bl_idname = "object.cursor_array"
    bl_label = "Cursor Array"
    bl_options = {'REGISTER', 'UNDO'}

    def execute(self, context):
        scene = context.scene
        cursor = scene.cursor.location
        obj = context.active_object

        total = 10

        for i in range(total):
            obj_new = obj.copy()
            scene.collection.objects.link(obj_new)

            factor = i / total
            obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

        return {'FINISHED'}

def register():
    bpy.utils.register_class(ObjectCursorArray)


def unregister():
    bpy.utils.unregister_class(ObjectCursorArray)


if __name__ == "__main__":
    register()
```



1. 텍스트에디터 slow_speed,py 생성

```
bl_info ={
        "name":"Slow Speed",
        "category":"3D View",
        "author":"Brush"
        }


import bpy

class slowSpeed(bpy.types.Menu):
    bl_label = "Slow Speed"
    bl_idname ="view3D.slow_speed"
    
    def draw(self, context):
        layout = self.layout
        layout.operator("mesh.primitive_cube_add")
        layout.operator("object.duplicate_move")
    
    
def register():
    bpy.utils.register_class(slowSpeed)
//  bpy.ops.wm.call_menu(name=slowSpeed.bl_idname) //이 라인은 테스트용(Alt-P 파이썬 실행)으로 나중에 키맵으로 적용하니 없어도됨
    
def unregister():
    bpy.utils.unregister_class(slowSpeed)
    
    
if __name__ =="__main__":
    register()
```

`함수의 total 변수를 클래스로 옮김`

```
# moved assignment from execute() to the body of the class...
total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

# and this is accessed on the class
# instance within the execute() function as...
self.total
```

`메뉴에 설치`

![image](https://user-images.githubusercontent.com/30430227/184478921-e4d10616-b313-4d7c-a58d-87cb8c81a14e.png)

```
def menu_func(self, context):
    self.layout.operator(ObjectCursorArray.bl_idname)

def register():
    bpy.utils.register_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.append(menu_func)
```

`단축키 설정`

```
# store keymaps here to access after registration
addon_keymaps = []


def register():
    bpy.utils.register_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.append(menu_func)

    # handle the keymap
    wm = bpy.context.window_manager
    # Note that in background mode (no GUI available), keyconfigs are not available either,
    # so we have to check this to avoid nasty errors in background case.
    kc = wm.keyconfigs.addon
    if kc:
        km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
        kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
        kmi.properties.total = 4
        addon_keymaps.append((km, kmi))

def unregister():
    # Note: when unregistering, it's usually good practice to do it in reverse order you registered.
    # Can avoid strange issues like keymap still referring to operators already unregistered...
    # handle the keymap
    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()

    bpy.utils.unregister_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.remove(menu_func)
```

`메뉴와 단축키 포함`

```
bl_info = {
    "name": "Cursor Array",
    "blender": (2, 80, 0),
    "category": "Object",
}

import bpy


class ObjectCursorArray(bpy.types.Operator):
    """Object Cursor Array"""
    bl_idname = "object.cursor_array"
    bl_label = "Cursor Array"
    bl_options = {'REGISTER', 'UNDO'}

    total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

    def execute(self, context):
        scene = context.scene
        cursor = scene.cursor.location
        obj = context.active_object

        for i in range(self.total):
            obj_new = obj.copy()
            scene.collection.objects.link(obj_new)

            factor = i / self.total
            obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

        return {'FINISHED'}


def menu_func(self, context):
    self.layout.operator(ObjectCursorArray.bl_idname)

# store keymaps here to access after registration
addon_keymaps = []


def register():
    bpy.utils.register_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.append(menu_func)

    # handle the keymap
    wm = bpy.context.window_manager
    # Note that in background mode (no GUI available), keyconfigs are not available either,
    # so we have to check this to avoid nasty errors in background case.
    kc = wm.keyconfigs.addon
    if kc:
        km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
        kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
        kmi.properties.total = 4
        addon_keymaps.append((km, kmi))

def unregister():
    # Note: when unregistering, it's usually good practice to do it in reverse order you registered.
    # Can avoid strange issues like keymap still referring to operators already unregistered...
    # handle the keymap
    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()

    bpy.utils.unregister_class(ObjectCursorArray)
    bpy.types.VIEW3D_MT_object.remove(menu_func)


if __name__ == "__main__":
    register()
```


2. 애드온 설치

![image](https://user-images.githubusercontent.com/30430227/184315929-8a98eded-e65e-44f0-b98f-5f7bdbc3b03d.png)

3. 키맵 

![image](https://user-images.githubusercontent.com/30430227/184316927-606a7975-8416-4b79-986b-f7d99a3fd9fb.png)



시퀀서 Slow Speed 메뉴 
--------------

![image](https://user-images.githubusercontent.com/30430227/184494608-4ee72284-fd3f-4e75-a5bd-f668f160e609.png)
![image](https://user-images.githubusercontent.com/30430227/184494652-5821b923-c8fc-4b20-8fc4-d902d6543c6e.png)
![image](https://user-images.githubusercontent.com/30430227/184494621-e5997b4c-6493-4476-939b-95ecf3c9f613.png)

```
bl_info = {
    "name": "Cursor Array",
    "blender": (2, 80, 0),
    "category": "Sequencer",
}

import bpy


class SlowSpeed(bpy.types.Operator):
    """Slow Speed"""
    bl_idname = "sequencer.slow_speed"
    bl_label = "Slow Speed"
    bl_options = {'REGISTER', 'UNDO'}

    def execute(self, context):

        bpy.ops.sequencer.meta_make()
        bpy.ops.sequencer.effect_strip_add(type='SPEED')
        bpy.context.active_sequence_strip.speed_control = 'MULTIPLY'
        bpy.context.active_sequence_strip.speed_factor = 0.5

        return {'FINISHED'}


def menu_func(self, context):
    self.layout.operator(SlowSpeed.bl_idname)

# store keymaps here to access after registration
addon_keymaps = []


def register():
    bpy.utils.register_class(SlowSpeed)
    bpy.types.SEQUENCER_MT_strip.append(menu_func)

    # handle the keymap
    wm = bpy.context.window_manager
    # Note that in background mode (no GUI available), keyconfigs are not available either,
    # so we have to check this to avoid nasty errors in background case.
    kc = wm.keyconfigs.addon
    if kc:
        km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
        kmi = km.keymap_items.new(SlowSpeed.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
        addon_keymaps.append((km, kmi))

def unregister():
    # Note: when unregistering, it's usually good practice to do it in reverse order you registered.
    # Can avoid strange issues like keymap still referring to operators already unregistered...
    # handle the keymap
    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()

    bpy.utils.unregister_class(SlowSpeed)
    bpy.types.SEQUENCER_MT_strip.remove(menu_func)


if __name__ == "__main__":
    register()
```

```
bl_info ={
        "name":"Slow Speed",
        "category":"Sequencer",
        "author":"Brush"
        }


import bpy

class slowSpeed(bpy.types.Menu):
    bl_label = "Slow Speed"
    bl_idname ="Sequencer.slow_speed"
    
    def draw(self, context):
        layout = self.layout
        layout.operator("sequencer.meta_make")
        layout.operator("sequencer.effect_strip_add").type='SPEED'
    
        bpy.context.active_sequence_strip.speed_factor = 0.5
    
def register():
    bpy.utils.register_class(slowSpeed)

    
def unregister():
    bpy.utils.unregister_class(slowSpeed)
    
    
if __name__ =="__main__":
    register()
```



```
import bpy

class SequencerEditMenu(bpy.types.Menu):
    bl_label = "Specials"
    bl_idname = "SEQUENCER_OT_sequencer_edit_menu"

    def draw(self, context):

        if context.space_data.type == 'SEQUENCE_EDITOR':

            layout = self.layout
            layout.operator("sequencer.gap_remove").all = False
            layout.operator("sequencer.gap_insert")
            layout.separator()
            props = layout.operator("sequencer.strip_jump", text="Jump to Previous Strip")
            props.next = False
            props.center = False
            props = layout.operator("sequencer.strip_jump", text="Jump to Next Strip")
            props.next = True
            props.center = False            
            layout.separator()            
            layout.operator("transform.transform", text="Grab/Move").mode = 'TRANSLATION'
            layout.operator("transform.transform", text="Grab/Extend from Frame").mode = 'TIME_EXTEND'
            layout.operator("sequencer.slip", text="Slip Strip Contents")            
            layout.separator()
            layout.operator("sequencer.cut", text="Cut (Hard) at frame").type = 'HARD'
            layout.operator("sequencer.cut", text="Cut (Soft) at frame").type = 'SOFT'           

addon_keymaps = []
def register():
    bpy.utils.register_class(SequencerEditMenu)

    # handle the keymap
    wm = bpy.context.window_manager
    kc = wm.keyconfigs.addon
    if kc:    
        km = wm.keyconfigs.addon.keymaps.new(name='Sequencer', space_type='SEQUENCE_EDITOR')
        kmi = km.keymap_items.new('wm.call_menu', 'W', 'PRESS')
        kmi.properties.name = "SEQUENCER_OT_sequencer_edit_menu"    
        addon_keymaps.append((km, kmi))

def unregister():
    bpy.utils.unregister_class(SequencerEditMenu)

    for km, kmi in addon_keymaps:
        km.keymap_items.remove(kmi)
    addon_keymaps.clear()

if __name__ == "__main__":
    register()
```

```
import bpy

currentFrame = bpy.data.scenes['Scene'].frame_current

#@classmethod
#def poll(cls, context):
#    if context.scene and context.scene.sequence_editor:
#        bpy.ops.sequencer.effect_strip_add(type='SPEED', frame_start=cFrame, frame_end=1cFrame+25)


def main():
    bpy.ops.sequencer.meta_make()
    bpy.ops.sequencer.effect_strip_add(type='SPEED', frame_start=cFrame, frame_end=1cFrame+25)
    bpy.context.active_sequence_strip.speed_factor = 0.5



class MyOperator(bpy.types.Operator):
    """Tooltip"""
    bl_idname = "slow_Speed"
    bl_label = "slow_Speed"

    @classmethod
    def poll(cls, context):
        return context.active_object is not None

    def execute(self, context):
        main(context)
        return {'FINISHED'}


def register():
    bpy.utils.register_class(MyOperator)


def unregister():
    bpy.utils.unregister_class(MyOperator)


if __name__ == "__main__":
    register()
```
