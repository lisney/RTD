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
const __dirname = path.resolve();
const require = createRequire(import.meta.url);
const port = 3000;

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

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
  const engine = new BABYLON.Engine(canvas, true)//Antialias:true

  function createScene(){
    const scene = new BABYLON.Scene(engine)
    scene.clearColor = new BABYLON.Color3.Black

    const alpha = Math.PI/4
    const beta = Math.PI/3
    const radius = 5
    const target = new BABYLON.Vector3(0,0,0)

    const camera = new BABYLON.ArcRotateCamera('Camera', alpha, beta, radius,target, scene)//target, scene없어도 실행된다
    camera.attachControl(canvas, true)
    camera.wheelPrecision = 100 //숫자값 낮으면 민감, 높으면 둔감

    const light = new BABYLON.HemisphericLight('Light', new BABYLON.Vector3(4,3,2))

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

<br>

바빌론 Web Viewer
-----------------

![image](https://user-images.githubusercontent.com/30430227/156299539-6560d396-ada4-44d3-a17b-8441f96ee23f.png)

```
<script src="https://cdn.babylonjs.com/viewer/babylon.viewer.js"></script>

<babylon model="./gltfs/afo.gltf"></babylon>
```

`불러온 GLTF 바닥이 깜빡일 때`

```
<babylon extends="minimal" model="path to model file"></babylon> //기본 Ground 제거, 하지만 카메라 위치가 가깝다

//카메라 거리를 조절하기위해 ID 생성
<babylon id="myViewer" extends="minimal"></babylon>

<script>
    BabylonViewer.viewerManager.getViewerPromiseById('myViewer').then((viewer) => {
        viewer.onSceneInitObservable.add(() => {
            viewer.sceneManager.camera.radius = 15; //set camera radius
            viewer.sceneManager.camera.beta = Math.PI / 2.2; //angle of depression
        });
        viewer.onEngineInitObservable.add((scene) => {
            viewer.loadModel({
                url: "path to model file"
            });
        });
    });
</script>
```

<br>

GLTF 로더
-----------

```
<script src="https://cdn.babylonjs.com/babylon.js"></script>
<script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>

<canvas id="renderCanvas"></canvas>

<script>
  const canvas = document.querySelector('#renderCanvas')  
  const engine = new BABYLON.Engine(canvas, true)

  function createScene(){
    const scene = new BABYLON.Scene(engine)

    const camera = new BABYLON.ArcRotateCamera('camera',Math.PI/4,Math.PI/3,10, new BABYLON.Vector3(0,0,0))
    camera.attachControl(canvas,true)
    camera.wheelPrecision =100

    const light = new BABYLON.HemisphericLight('light',new BABYLON.Vector3(1,1,0))

    BABYLON.SceneLoader.ImportMeshAsync('','./gltfs/','afo.gltf') //''- 모든 메쉬 불러옴,
---------------------------------------------------------------------------
    BABYLON.SceneLoader.ImportMeshAsync('Test','./gltfs/','afo01.glb').then(result=>{//'Test'메쉬만 불러옴
      result.meshes[1].position.y=3//첫 번째 메쉬 선택
      result.meshes[2].scaling.x=2//바닥판 스케일, meshes[0]는 전체에 영향을 주는 것 같다
      const afo = scene.getMeshByName('Test')//이름으로 선택
      afo.position.y=1
    })
     const sound = new BABYLON.Sound('love','./gltfs/true.mp3',scene,null,{loop:true, autoplay:true})//소리꾼
     BABYLON.MeshBuilder.CreateBox("box", {width: 2, height: 1.5, depth: 3})
     box.scaling = new BABYLON.Vector3(2, 1.5, 3);
------------------------------------------------------------------------------

    const ground = BABYLON.MeshBuilder.CreateGround('ground',{width:10, height:10})
    
    return scene
  }

const sceneToRender = createScene()

engine.runRenderLoop(()=>{
  sceneToRender.render()
})

</script>
```

![image](https://user-images.githubusercontent.com/30430227/156319898-5980261e-43ac-48a0-bfff-2a6da77b6ce7.png)

```
    const roofMat = new BABYLON.StandardMaterial('roofM',scene)
    roofMat.diffuseColor = new BABYLON.Color3(0,1,0)
    
    const floorMat = new BABYLON.StandardMaterial('floorM')
    floorMat.diffuseTexture = new BABYLON.Texture('./images/4g2.jpg',scene)

    BABYLON.SceneLoader.ImportMeshAsync('','./gltfs/','afo01.glb').then(result=>{
      const afo = scene.getMeshByName('Test')
      afo.position.y=1
      afo.material = roofMat
      result.meshes[2].scaling.x=2
      result.meshes[2].material=floorMat
    })
```

![image](https://user-images.githubusercontent.com/30430227/156322917-5e3015ba-f0e3-4077-944b-d68dae2fe92f.png)

```
    /*** 하우스 UV맵 ***/
    const boxMat = new BABYLON.StandardMaterial('boxM')
    boxMat.diffuseTexture = new BABYLON.Texture('/images/cubehouse.png')
    const faceUV =[]
    faceUV[0]=new BABYLON.Vector4(0.25,0.0,0.5,1.0)//rear face
    faceUV[1]=new BABYLON.Vector4(0.75,0.0,1.0,1.0)//front face
    faceUV[2]=new BABYLON.Vector4(0.5,0.0,0.75,1.0)//right side
    faceUV[3]=new BABYLON.Vector4(0.0,0.0,0.25,1.0)//left side

    const box = BABYLON.MeshBuilder.CreateBox('box',{width:2,height:1.5,depth:2.5,faceUV:faceUV, wrap:true})
    box.material = boxMat
```

![image](https://user-images.githubusercontent.com/30430227/156323917-12475163-38a8-4be2-9db5-3525c4467cf8.png)
![image](https://user-images.githubusercontent.com/30430227/156324958-07e833c1-5c4e-44dd-b280-19354b421129.png)

```
    /*** 메쉬 합치기 ***/
    const house = BABYLON.Mesh.MergeMeshes([box,roof])
    const house = BABYLON.Mesh.MergeMeshes([box,roof],true,false,null,false,true)//합치고, 개별 재질,마지막 매개변수true
```

![image](https://user-images.githubusercontent.com/30430227/156329039-e9e60b95-deac-4444-b1f5-a6501f116a63.png)

```
    /*** 복사 Clone ***/
    const house1 = house.clone('cloneH') //Copy
    house1.position.x=3
    
    const house2 = house.createInstance('instanceH')//instance Copy
    house2.position.x =-3
```

![image](https://user-images.githubusercontent.com/30430227/156479753-74923597-0581-415a-aff0-c695af35a374.png)
![image](https://user-images.githubusercontent.com/30430227/156491013-de37d33e-1657-406a-9a1c-b19cda779c24.png)

![image](https://user-images.githubusercontent.com/30430227/156497135-6fae3b5a-cab3-412b-93cf-5226dce0caf6.png)
![image](https://user-images.githubusercontent.com/30430227/156497156-65fa9f8f-51a0-4763-93f3-9661147d4500.png)

```
<script src="https://unpkg.com/earcut@2.2.3/dist/earcut.min.js"></script>//ExtrudePolygon은 Earcut라이브러리 필요

    /*** 자동차 ***/
    const outline =[
      new BABYLON.Vector3(-3,0,-1),
      new BABYLON.Vector3(2,0,-1)
    ]
    for(let i =0;i<5;i++){
      outline.push(
        new BABYLON.Vector3(2*Math.cos(i*Math.PI/10), 0, 2*Math.sin(i*Math.PI/10)-1)
      )
    }
    outline.push(new BABYLON.Vector3(0,0,1))
    outline.push(new BABYLON.Vector3(-3,0,1))

    //const car = BABYLON.MeshBuilder.ExtrudePolygon('car',{shape:outline,depth:2})

    const carUV =[]
    carUV[0] = new BABYLON.Vector4(0,0.5,0.38,1)//Bottom
    carUV[1] = new BABYLON.Vector4(0,0,1,0.5)//Side
    carUV[2] = new BABYLON.Vector4(0.38,1,0,0.5)//Top

    const carMat = new BABYLON.StandardMaterial('carM')
    carMat.diffuseTexture = new BABYLON.Texture('./images/car.png')
    
    const car = BABYLON.MeshBuilder.ExtrudePolygon('car',{shape:outline,depth:2, faceUV:carUV,wrap:true})
    car.material = carMat

    /*** 바퀴 ***/
    const wheelUV =[]
    wheelUV[0]= new BABYLON.Vector4(0,0,1,1)//Bottom
    wheelUV[1]= new BABYLON.Vector4(0,0.5,0,0.5)//Side
    wheelUV[2]= new BABYLON.Vector4(0,0,1,1)//Top

    const wheelMat = new BABYLON.StandardMaterial('wheelM')
    wheelMat.diffuseTexture = new BABYLON.Texture('/images/wheel.png')

    const wheelRB = BABYLON.MeshBuilder.CreateCylinder('wheelRB',{diameter:1, height:0.5,faceUV:wheelUV})
    wheelRB.material = wheelMat
    wheelRB.parent = car
    wheelRB.position = new BABYLON.Vector3(-2,0,-1)

    const wheelRF=wheelRB.clone('wheelRF')
    wheelRF.position.x=1

    const wheelLB=wheelRB.clone('wheelLB')
    wheelLB.position.y =-2

    const wheelLF=wheelRF.clone('wheelLF')
    wheelLF.position.y=-2
  
    return scene
  }
```

![image](https://user-images.githubusercontent.com/30430227/156513971-a411a2e7-f138-425b-b93f-0c54cbfd3226.png)

```
    /*** 애니메이션 ***/
    const animWheel = new BABYLON.Animation('animW', 'rotation.y',10, BABYLON.Animation.ANIMATIONTYPE_FLOAT,BABYLON.Animation.ANIMATIONLOOPMODE_CYCLE) //이름, 회전축, 초당프레임,애니메이션타입,Loop모드

    const wheelKeys=[]//키프레임 객체 배열
    wheelKeys.push({frame:0,value:0})
    wheelKeys.push({frame:30,value:2*Math.PI})

    animWheel.setKeys(wheelKeys)//애니메이션 객체를 키프레임 방식으로 세팅,키프레임 배열 인수
    //wheelRB.animations=[]//이 라인 없어도 실행됨
    wheelRB.animations.push(animWheel)
    
    //wheelRF.animations=[]//바퀴에 애니메이션 연결(배열...)
    wheelRF.animations.push(animWheel)
    //wheelLB.animations=[]
    wheelLB.animations.push(animWheel)
    //wheelLF.animations=[]
    wheelLF.animations.push(animWheel)

    scene.beginAnimation(wheelRB,0,3,true)//씬 애니메이션, 움직일 객체, 시작 프레임, 끝 프레임, 반복
    scene.beginAnimation(wheelRF,0,30,true)
    scene.beginAnimation(wheelLB,0,30,true)
    scene.beginAnimation(wheelLF,0,30,true)
  
    return scene
```

<br>

애니메이션 JSON - Promise
----------------

![image](https://user-images.githubusercontent.com/30430227/156721241-25a22ffe-6b99-44b4-8c64-b0ab7fab9e36.png)


```
        <!-- Babylon.js -->
        <script src="https://preview.babylonjs.com/babylon.js"></script>

    <canvas id="renderCanvas"></canvas>
    <script>
        const canvas = document.querySelector("#renderCanvas");

        const engine = new BABYLON.Engine(canvas, true);

        async function startRenderLoop(sceneToRender) {
            engine.runRenderLoop(()=> {
                sceneToRender.render();
            });
        }

    //initFunction().then(() => {scene.then(returnedScene => { sceneToRender = returnedScene; }); });   
    createScene().then(startRenderLoop)

        async function createScene() {
    // This creates a basic Babylon Scene object (non-mesh)
    var scene = new BABYLON.Scene(engine);

    // This creates and positions a free camera (non-mesh)
    var camera = new BABYLON.FreeCamera("camera1", new BABYLON.Vector3(0, 5, -10), scene);

    // This targets the camera to scene origin
    camera.setTarget(BABYLON.Vector3.Zero());

    // This attaches the camera to the canvas
    camera.attachControl(canvas, true);

    // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
    var light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);

    // Default intensity is 1. Let's dim the light a small amount
    //light.intensity = 0.1;

    // Our built-in 'sphere' shape.
    var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", {diameter: 2, segments: 32}, scene);

    let animations = await BABYLON.Animation.ParseFromFileAsync(null, "./gltfs/animations.json");
    sphere.animations = animations;
    scene.beginAnimation(sphere, 0, 100, true);
    
    // Our built-in 'ground' shape.
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 6, height: 6}, scene);

    return scene;
    };

    </script>
```
