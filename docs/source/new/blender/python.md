Python
========


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

2. 애드온 설치

![image](https://user-images.githubusercontent.com/30430227/184315929-8a98eded-e65e-44f0-b98f-5f7bdbc3b03d.png)

3. 키맵 

![image](https://user-images.githubusercontent.com/30430227/184316927-606a7975-8416-4b79-986b-f7d99a3fd9fb.png)





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
