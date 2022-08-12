Python
========


애드온 제작
--------------

![image](https://user-images.githubusercontent.com/30430227/184336436-e6ffe6a3-bc51-4f3b-aa14-482754d6e4bb.png)


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



시퀀서 메뉴 
--------------

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
