Python
========

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
