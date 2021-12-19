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

