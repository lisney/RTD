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

/** JSON 방식 애니메이션Promise**/
    //let animations = await BABYLON.Animation.ParseFromFileAsync(null, "./gltfs/animations.json");
    //sphere.animations = animations

/** 기본 키프레임 방식 push**/
    const xSlide = new BABYLON.Animation('xSlide', 'position.x', 10,BABYLON.Animation.ANIMATIONTYPE_FLOAT,BABYLON.Animation.ANIMATIONLOOPMODE_CYCLE)
    const keyFrames =[]

    keyFrames.push.apply(keyFrames,[
        {frame:0,value:2},
        {frame:10,value:-2},
        {frame:20,value:2}]
        )

    xSlide.setKeys(keyFrames)

    sphere.animations.push(xSlide)

/* 애니메이션 시작   **/
    scene.beginAnimation(sphere, 0, 100, true);
    
    // Our built-in 'ground' shape.
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 6, height: 6}, scene);

    return scene;
    };

    </script>
```

![image](https://user-images.githubusercontent.com/30430227/156955656-7faed452-583e-4bce-add6-55d1652481cf.png)

```
/** GUI **/
  <script src="https://preview.babylonjs.com/gui/babylon.gui.min.js"></script>
  
    const advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI('UI')
    const button1 = BABYLON.GUI.Button.CreateSimpleButton('btn1','Click Me')
    button1.width='150px';
    button1.height='40px';   
    button1.color='white';
    button1.cornerRadius=20;
    button1.background='green';
    button1.onPointerUpObservable.add(()=>{
        alert('You did it!')
    })
    advancedTexture.addControl(button1)
    
# 삼차원 버튼
    const advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateForMesh(btnPlane)
    const btnPlane = BABYLON.Mesh.CreatePlane('btnPlane',20)
    btnPlane.parent = sphere
    btnPlane.position.y = 2
    
    const advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateForMesh(btnPlane)
    const button1 = BABYLON.GUI.Button.CreateSimpleButton('btn1','Click Me')
    button1.background='green';
    button1.hoverCursor='pointer'
    button1.top='150px';
    button1.left='-150px';
    let clicks =0
    button1.onPointerUpObservable.add(()=>{
        clicks++
        clicks%2==0?button1.background='#eb4d4b':button1.background='#007900'
        alert('You did it!')
    })
    //btnPlane.billboardMode = BABYLON.Mesh.BILLBOARDMODE_ALL;//항상 카메라 방향 향함
    
# 이미지 GUI
    const image = new BABYLON.GUI.Image('4g2','./images/4g2.jpg')
```

![image](https://user-images.githubusercontent.com/30430227/156979510-833b11a4-5ae5-428c-b002-dabcfce112eb.png)

```

<script src="https://preview.babylonjs.com/babylon.js"></script>
<script src="https://preview.babylonjs.com/gui/babylon.gui.min.js"></script>

<canvas id="renderCanvas"></canvas>

<script>
    const canvas = document.querySelector('#renderCanvas')

    const engine = new BABYLON.Engine(canvas, true)

    async function startRenderLoop(sceneToRender){
        engine.runRenderLoop(()=>{
            sceneToRender.render()
        })
    }

    createScene().then(startRenderLoop)

    async function createScene(){
        const scene = new BABYLON.Scene(engine)

        const light = new BABYLON.PointLight('Light', new BABYLON.Vector3(0,100,100),scene)
        const camera = new BABYLON.ArcRotateCamera('Camera',0,1,50,new BABYLON.Vector3.Zero(),scene)
        camera.attachControl(canvas,true)
        camera.wheelPreciion=100

        const box1 = BABYLON.Mesh.CreateBox('Box1',10,scene)
        box1.position.x = -20

        const matBox= new BABYLON.StandardMaterial('MatBox',scene)
        matBox.diffuseColor = new BABYLON.Color3(0,1,0)//new BABYLON.Color3.Green()
        
        box1.material = matBox

        const anim1= new BABYLON.Animation('Anim1','scaling.x',30,BABYLON.Animation.ANIMATIONTYPE_FLOAT,
            BABYLON.Animation.ANIMATIONLOOPMODE_CYCLE)
        
        let keys =[]

        keys.push.apply(keys,[
            {frame:0,value:1},
            {frame:20,value:0.2},
            {frame:100,value:1}
        ]
        )

        anim1.setKeys(keys)

        const anim2= new BABYLON.Animation('Anim2','rotation.y',30,BABYLON.Animation.ANIMATIONTYPE_FLOAT,
            BABYLON.Animation.ANIMATIONLOOPMODE_CYCLE)
        
        keys =[]

        keys.push.apply(keys,[
            {frame:0,value:0},
            {frame:40,value:Math.PI},
            {frame:80,value:0}
        ]
        )

        anim2.setKeys(keys)

        const animationGroup = new BABYLON.AnimationGroup('myGroup')
        animationGroup.addTargetedAnimation(anim1,box1)
        animationGroup.addTargetedAnimation(anim2,box1)

        animationGroup.normalize(0,100)

        const advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI('UI')
        const panel = new BABYLON.GUI.StackPanel()
        panel.isVertical=false
        panel.verticalAlignment= BABYLON.GUI.Control.VERTICAL_ALIGNMENT_BOTTOM
        advancedTexture.addControl(panel)

        function addButton(text,callback){
            const button = BABYLON.GUI.Button.CreateSimpleButton('button',text)
            button.width ='140px';
            button.height='40px';
            button.background='green'
            button.paddingLeft='10px';
            button.paddingRight='10px';
            button.onPointerUpObservable.add(()=>{
                callback()
            })
            panel.addControl(button)
        }
        
        //box1.animations.push(anim1)
        //scene.beginAnimation(box1,0,100,true)

        addButton('Play',()=>animationGroup.play(true))
        addButton('Pause',()=>animationGroup.pause())
        addButton('Stop',()=>{
            animationGroup.reset()
            animationGroup.stop()
        })

        return scene

    }
</script>
```

![image](https://user-images.githubusercontent.com/30430227/157173530-5a13b6b3-a5e3-4011-ae9f-61aec211d5af.png)
마우스 드래그
```
<script src="https://preview.babylonjs.com/babylon.js"></script>

<canvas id="renderCanvas"></canvas>

<script>
    const canvas = document.querySelector('#renderCanvas')
    const engine = new BABYLON.Engine(canvas,true)

    async function startRenderLoop(sceneToRender){
        engine.runRenderLoop(()=>{
            sceneToRender.render()
        })
    }

    createScene().then(startRenderLoop)

    async function createScene(){
        const scene = new BABYLON.Scene(engine)

        const light = new BABYLON.PointLight('Light',new BABYLON.Vector3(50,200,0),scene) 
        const camera = new BABYLON.ArcRotateCamera('Camera',0,0,10,new BABYLON.Vector3.Zero(),scene)
        camera.attachControl(canvas, true)
        camera.wheelPrecision=100
        camera.setPosition(new BABYLON.Vector3(20,200,400))

        const groundMat= new BABYLON.StandardMaterial('GroundMat',scene)
        groundMat.specularColor=BABYLON.Color3.Black()

        const ground = BABYLON.MeshBuilder.CreateGround('Ground',{width:1000,height:1000})
        ground.material = groundMat

        const redMat = new BABYLON.StandardMaterial('RedMat',scene)
        redMat.diffuseColor = new BABYLON.Color3(0.4,0.4,0.4)
        redMat.emissiveColor=BABYLON.Color3.Red()

        const box1 = BABYLON.MeshBuilder.CreateBox('Box1',{size:20},scene)
        box1.position.z-=100
        box1.position.y =10
        box1.material = redMat

        const box2 = BABYLON.MeshBuilder.CreateBox('Box2',{size:20},scene)
        box2.position.z=100
        box2.position.y =10

        let startingPoint
        let currentMesh

        function getGroundPosition(){
            let pickInfo = scene.pick(scene.pointerX, scene.pointerY, (mesh)=> mesh == ground)
                if(pickInfo.hit){
                    return pickInfo.pickedPoint
                }
                return null
        }

        function pointerDown(mesh){
            currentMesh = mesh
            startingPoint = getGroundPosition()
            if(startingPoint){
                setTimeout(()=>{
                    camera.detachControl(canvas)
                },0)
            }
        }

        function pointerUp(){
            if(startingPoint){
                camera.attachControl(canvas,true)
                startingPoint=null
                return
            }
        }

        function pointerMove(){
            if(!startingPoint){
                return
            }
            let current = getGroundPosition()
            if(!current){
                return
            }

            let diff = current.subtract(startingPoint)
            currentMesh.position.addInPlace(diff)

            startingPoint = current
        }

        scene.onPointerObservable.add((pointerInfo)=>{
            switch(pointerInfo.type){
                case BABYLON.PointerEventTypes.POINTERDOWN:
                    if(pointerInfo.pickInfo.hit && pointerInfo.pickInfo.pickedMesh != ground){
                        pointerDown(pointerInfo.pickInfo.pickedMesh)
                    }
                    break;
                case BABYLON.PointerEventTypes.POINTERUP:
                    pointerUp()
                    break;
                case BABYLON.PointerEventTypes.POINTERMOVE:
                    pointerMove();
                    break;
            }
        })

        return scene
    }

</script>
```

![image](https://user-images.githubusercontent.com/30430227/157575785-f7d797c5-abfe-4fb5-8a84-917c44e3adab.png)

```
//씬 이동은 하나 카메라 컨트롤이 되지 않음
<script src="https://preview.babylonjs.com/babylon.js"></script>
<script src="https://preview.babylonjs.com/gui/babylon.gui.min.js"></script>

<canvas id="renderCanvas"></canvas>

<script>
    const canvas = document.querySelector('#renderCanvas')
    const engine = new BABYLON.Engine(canvas,true)

    async function renderLoop(sceneToRender){
        engine.runRenderLoop(()=>{
            sceneToRender.render()
        })
    }

    createScene().then(renderLoop)


    async function createScene(){
        const scene1 = new BABYLON.Scene(engine)
        scene1.clearColor = new BABYLON.Color3(.1,.1,0)
        
        const light1 = new BABYLON.HemisphericLight('Light1',new BABYLON.Vector3(1,0,0),scene1)
        light1.intensity = 0.75
        light1.specular = new BABYLON.Color3(0.9,0.9,0.5)

        const camera1 = new BABYLON.ArcRotateCamera('Camera1',0,0,0,new BABYLON.Vector3.Zero(), scene1)
        camera1.setPosition(new BABYLON.Vector3(0,20,-100))
        camera1.attachControl(canvas, true)
        camera1.wheelPrecision=100

        let nbBuildings = 800
        let fact = 60
        let scaleX = 0
        let scaleY = 0
        let scaleZ =0
        let grey = 0
        let uvSize = 0

        ///SCENE1///
        const ground1Mat=new BABYLON.StandardMaterial('Ground1Mat',scene1)
        //ground1Mat.diffuseColor = new BABYLON.Color3(0.4,0.4,0.4)
        ground1Mat.backFaceCulling = false

        const ground1 = BABYLON.MeshBuilder.CreatePlane('Ground1',{size:fact},scene1)
        ground1.rotation.x = Math.PI/2
        ground1.material = ground1Mat

        const girlTxt = new BABYLON.Texture('/images/4g2.jpg', scene1)
        const girlMat = new BABYLON.StandardMaterial('GirlMat',scene1)
        girlMat.diffuseTexture = girlTxt

        // custom position function
        function myPositionFunction(particle, i, s){
            scaleX = Math.random()*2+0.8;
            scaleY = Math.random()*6+0.8
            scaleZ = Math.random()*2+0.8
            uvSize = Math.random()*0.9
            particle.scale.x = scaleX
            particle.scale.y = scaleY
            particle.scale.z = scaleZ
            particle.position.x=(Math.random()-0.5)*fact
            particle.position.y = particle.scale.y/2+0.01
            particle.position.z = (Math.random()-0.5)*fact
            particle.rotation.y = Math.random()*3.5
            grey = 1.0 - Math.random()*0.5
            particle.color= new BABYLON.Color4(grey+0.1, grey+0.1,grey, 1)
            particle.uvs.x = Math.random()*0.1
            particle.uvs.y = Math.random()*0.1
            particle.uvs.z= particle.uvs.x+uvSize
            particle.uvs.w=particle.uvs.y+uvSize
        }

        //Particle system creation:immutable
        const SPS = new BABYLON.SolidParticleSystem('SPS', scene1,{updatable:false})
        const model = BABYLON.MeshBuilder.CreateBox('m',{},scene1)
        SPS.addShape(model, nbBuildings,{positionFunction:myPositionFunction})
        const mesh = SPS.buildMesh()
        mesh.material = girlMat
        model.dispose()

        //////SCENE2///////
        const scene2 = new BABYLON.Scene(engine)

        const light2 = new BABYLON.HemisphericLight('Light2',new BABYLON.Vector3(1,0.5,0), scene2)
        light2.intensity=0.8

        const camera2 = new BABYLON.ArcRotateCamera('Camera2',-Math.PI/2,Math.PI/2,5,BABYLON.Vector3.Zero(),scene2)
        camera2.attachControl(canvas,true)
        camera2.wheelPrecision = 100

        const sphere1 = BABYLON.MeshBuilder.CreateSphere('Sphere1',{segments:3},scene2)
        sphere1.material = new BABYLON.StandardMaterial('Sphere1Mat',scene2)
        sphere1.material.wireframe=true
        showNormals(sphere1, 0.25, new BABYLON.Color3.Red(),scene2)

        function showNormals(mesh, size, color, sc){
            const normals = mesh.getVerticesData(BABYLON.VertexBuffer.NormalKind)
            const positions = mesh.getVerticesData(BABYLON.VertexBuffer.PositionKind)
            color=color||BABYLON.Color3.White()
            sc=sc||scene
            size=size||1

            const lines=[]
            for(let i=0;i<normals.length;i+=3){
                let v1=BABYLON.Vector3.FromArray(positions,i)
                let v2=v1.add(BABYLON.Vector3.FromArray(normals,i).scaleInPlace(size))
                lines.push([v1.add(mesh.position),v2.add(mesh.position)])
            }
            const normalLines=BABYLON.MeshBuilder.CreateLineSystem('normalLines',{lines:lines},sc)
            normalLines.color=color
            return normalLines
        }

        ///GUI BOTH SCENES///

        let clicks =0
        let showScene=0
        let advancedTexture

        function createGUI(scene, showScene){
            switch(showScene){
                case 0:
                    advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI",true,scene1)
                    break
                case 1:
                    advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI",true,scene2)
                    break
            }
            const button = BABYLON.GUI.Button.CreateSimpleButton('btn','Scene '+((clicks+1)%2))
            button.width=0.2
            button.height='40px'
            button.color='white'
            button.background='green';
            button.verticalAlignment= BABYLON.GUI.Control.VERTICAL_ALIGNMENT_TOP;
            advancedTexture.addControl(button);

            button.onPointerUpObservable.add(()=>{
                clicks++
            })
        }

        createGUI(scene1,showScene)

        setTimeout(()=>{

            engine.stopRenderLoop()
            engine.runRenderLoop(()=>{
                if(showScene !=(clicks%2)){
                    showScene=clicks%2
                    switch(showScene){
                        case 0:
                            advancedTexture.dispose();
                            createGUI(scene1,showScene);
                            scene1.render();
                            break
                        case 1:
                            advancedTexture.dispose();
                            createGUI(scene2,showScene);
                            scene2.render();
                            break
                    }
                }
            })
        },500)

        return scene1

    }
</script>
```
