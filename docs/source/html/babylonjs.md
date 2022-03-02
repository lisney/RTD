Babylon JS
==============

Node Material Editor UI
---------------------------
1. Frame(Group)  
`Shift + Drag`  
2. Select  
`Ctrl + Drag`  



Method
---------
디버그  
`scene.debugLayer.show()`

<br>

첫번째 씬
---------

![image](https://user-images.githubusercontent.com/30430227/154913160-c1a90de8-f027-4330-bf58-e547485c4a3c.png)

```
import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import { createRequire } from "module";

const app = express();
app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);
const __dirname = path.resolve();
const require = createRequire(import.meta.url);
const port = 3000;

app.set("view engine", "hbs");
app.set("views", "./views");

app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

app.get("/", (req, res) => {
  res.render("home");
});

app.listen(port, ["192.168.0.21"], () => {
  console.log(`The server is running on port ${port}`);
});



-----------------------------
body,
#renderCanvas {
  width: 100%;
  height: 100%;
}
----------------------------
<canvas id="renderCanvas"></canvas>

<script src="https://cdn.babylonjs.com/babylon.js"></script>

<script>
  const canvas = document.querySelector('#renderCanvas')
  const engine = new BABYLON.Engine(canvas, true)

  const createScene =()=>{
    const scene = new BABYLON.Scene(engine)
    scene.clearColor = new BABYLON.Color3.Black

    const alpha = Math.PI/4
    const beta = Math.PI/3
    const radius = 8
    const target = new BABYLON.Vector3(0,0,0)

    const camera = new BABYLON.ArcRotateCamera('Camera', alpha, beta, radius,target, scene)
    camera.attachControl(canvas, true)
    camera.wheelPrecision = 100 //숫자값 낮으면 민감, 높으면 둔감

    const light = new BABYLON.HemisphericLight('Light', new BABYLON.Vector3(1,1,0))

    const box = BABYLON.MeshBuilder.CreateBox('box',{})
    box.position.x = 0.5
    box.position.y = 1

    return scene
  }

  const sceneToRender = createScene()

  engine.runRenderLoop(()=>{
    sceneToRender.render()
  })
</script>
```