BabylonJS
============

모듈 Export/Import
--------------------

```
* import {}

- ap.js
const a = 1;
const b = 2;
export { a }; //a와 c는 {}로 import해야한다. 변수명이 같게 써야한다.
export const c = 3; //선언과 동시에 할당한 한 변수는 import 시 {}안에 써야한다
export default b; // b는 기본 변수, {}없이 받으며...변수명이 달라도(d) 괜찮다 

- main.js
import d, { a, c as e } from "./ap.js";
console.log(a, d, e);
```


Handlebard 간단 서버
--------------

```
**app.js
import express from "express";
import { engine } from "express-handlebars";

const app = express();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);
app.set("view engine", "hbs");
app.set("views", "./views");

app.get("/", (req, res) => {
  res.render("home");
});

app.listen(3000);


**/views/home.hbs
<h1>방어력에 올인합니다!</h1>


**/views/layouts/main.hbs
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  {{{body}}}
</body>
</html>
```

자바스크립트 
---------------

1.문자열, 배열

```
userEmail.indexOf('@') //문자열에서 @문자가 있으면 그 위치의 Index 값 반환
문자열.substr(4,9) //빼내기, 4번째 인덱스부터 9번째까지 반환(인수 9가 없으면 4이후 전부 반환)
문자열.split('-') //문자 '-'를 기준으로 분리한 요소를 배열로 반환(<=> 배열.join('--')
배열.splice(0,1) : 배열에서 0~1번째 인덱스 요소를 삭제하고 삭제한 요소를 리턴=> 객체.slice 배열 원본은 보존/리턴

클래스 객체 배열의 경우...
Students.find(함수(student){return student.score===90} 
//data.scre가 90인 첫번째 요소에서 멈추고 해당 요소만 리턴(=>배열.filter 조건에 맞는 모든 요소 배열로 리턴)

const scores = Students.map(student=>student.score) //클래스 객체를 클래스 멤버변수로 매핑 즉 맴버 변수만 배열로 리턴

Students.reduce((prev, curr)=>{return prev + curr.score},0) // 중괄호 없어도 된다
//누적값 리턴, 초기값: 0, 순차적으로 return 한 값이 다음 번 prev의 값으로 들어간다.
//scores.reduce((prev,curr)=>prev+curr,0)와 같은 결과

```

2. HTML DOM Node

.nextElementSibling(형제), .firstElementChild, .childNodes.item(3)=childNodes[3]=children[1],
.nextElementSibling, .parentNode
ChildNode[] VS Children[] : childNodes[]는 줄바꿈 노드도 포함, children은 태그요소만
firstChild VS firstElementChild : 전자는 element,text,comment Node 반환, 후자는 element만 반환(style변경 시 사용) 

![image](https://user-images.githubusercontent.com/30430227/125756044-7e205db3-4663-4b4d-a1d2-7a36add79b8d.png)

```
    <section>
        <p>금쪽같은 내새끼</p>
        <div class="parent">
            <div class="child one"></div>
            <div class="child two" onclick="onParent()"></div>
            <div class="child three"></div>
        </div>
    </section>
```
```
 <style>
     section{
         margin: 0 auto;
         width: 200px;
         height: 150px;
         display: flex;
         flex-direction: column;
         justify-content: left;
         align-items: center;
         border: 1px solid #000;
         background: orange;
     }
     .parent{
         width: 150px;
         height: 80px;
         border: 1px solid #000;
         background: olive;
         display: flex;
         justify-content: space-around;
         align-items: center;
     }
     .child{
         width: 30px;
         height: 50px;
         background: gold;
     }
     

 </style>
```
```
    <script>
        document.querySelector('.parent').firstElementChild.style.background='white'
        document.querySelector('.parent').childNodes.item(3).style.cursor='pointer'
        function onParent(){
        //event.target
            event.target.parentNode.style.background = 'black' //event.target 함수 실행한 요소
            event.target.nextElementSibling.style.background = 'red'
        }
    </script>
```

3. Element 생성과 추가

![image](https://user-images.githubusercontent.com/30430227/168986844-7c8992e5-9f9b-4075-b2e5-2663e5c8dc65.png)

```
*innerHTML-HTML String, appendChild-Node Object

<ul></ul>

<script>
    const list = document.querySelector('ul');

    let data =['인디자인','자바스크립트','블렌더']

    data.forEach(i=>{
        const li = document.createElement('li')
        li.innerHTML=`${i}`
        list.appendChild(li)
    })
</script>
```

4. Promise 

```
상태 : Pending, Fulfill-다하다, 완료, reject

# 프로미스는 자바스크립트 기본 클래스이자 객체 생성 시 바로 실행된다. 비동기적으로..결과는 res, rej
const promise = new Promise((res, rej) => {
  setTimeout(() => {
    console.log("ellie");
  }, 2000);
});


# 프로미스 실행 결과(resolve 혹은 reject)를 사용하는 방법
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("ellie");
  }, 2000);
});

promise.then((value) => {
  console.log(value);
});


# 프로미스 사용하기 chaining
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(1);
  }, 2000);
});

promise
  .then((num) => num * 2)
  .then((num) => num * 3)
  .then((num) => {
    console.log(num);
    return new Promise((resolve, reject) => {
      setTimeout(() => resolve(num - 1), 2000);
    });
  })
  .then((num) => console.log(num));

```

5. 프로미스를 깔끔하게 사용하기 async, await

```
# 프로미스로 리턴 - 함수 실행 시 프로미스 스타토
function fetchUser() {
  return new Promise((resolve, reject) => {
    resolve("ellie");
  });
}

const user = fetchUser();//사용자 데이터를 백앤드로 받아오는 함수
user.then(console.log);//user=>console.log(user) 의 축약형(전달 인수와 받는 함수의 인수가 같을 때 생략)
//fetchUser().then(console.log) - 변수 user 대신 바로 실행해도 같은 결과

// console.log(user);//프로미스 실행 상태를 볼 수 있다(pending, fulfilled, reject)


# async로 바꾸면
async function fetchUser() {
  return "ellie";
}

const user = fetchUser();

user.then(console.log);


# await


```

첫번째 Scene 
-------------

![image](https://user-images.githubusercontent.com/30430227/154913160-c1a90de8-f027-4330-bf58-e547485c4a3c.png)

```
# router.mjs
import express from "express";

export const router = express.Router();
//const router = express.Router(); export {router};

router.get("/", async (req, res) => {
  res.render("home");
});


# app.js
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
    defaultLayout: "main",
  })
);

app.set("view engine", "hbs");
app.set("views", "./views");

app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

import { router } from "./router.mjs";
app.use("/", router);

app.listen(port, ["192,168.0.21"], () => {
  console.log(`The server is running on port ${port}`);
});


# style.css
body,
#renderCanvas {
  width: 100%;
  height: 100%;
}


# main.hbs
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <script src="https://cdn.babylonjs.com/babylon.js"></script>
  <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
  <script src="https://unpkg.com/earcut@2.2.3/dist/earcut.min.js"></script>//ExtrudePolygon은 Earcut라이브러리 필요
  <script src="https://preview.babylonjs.com/gui/babylon.gui.min.js"></script>
  
  <script defer src="https://preview.babylonjs.com/gui/babylon.gui.min.js"></script>//defer연기하다. 일단 다운로드 받기시작 HTML로딩 후에 순차적으로 실행

  {{{body}}}
</body>
</html>


# home.hbs
  <canvas id="renderCanvas"></canvas>


# babylon.js
    const canvas = document.querySelector('#renderCanvas')
    const engine = new BABYLON.Engine(canvas, true)//antialis true

    function createScene(){
        const scene = new BABYLON.Scene(engine)
        scene.clearColor = new BABYLON.Color3.Black

        const radius = 5
        const target = new BABYLON.Vector3(0,0,0)

        const camera  = new BABYLON.ArcRotateCamera('Cam', Math.PI/4, Math.PI/3, radius, target, scene)
        camera.attachControl(canvas, true)
        camera.wheelPrecision = 100//숫자 낮으면 민감

        const light = new BABYLON.HemisphericLight('Light', new BABYLON.Vector3(4,3,2))

        const box = BABYLON.MeshBuilder.CreateBox('Box', {})
        //box.position.x = 0.5
        box.position = new BABYLON.Vector3(0.5,1,0)

        return scene
    }

    const sceneToRender= createScene()

    engine.runRenderLoop(()=>{
        sceneToRender.render()
    })
```


GLTF 로더 
-------------

![image](https://user-images.githubusercontent.com/30430227/169491561-9cec2c04-11ac-4553-a4f5-764cb86f2b9c.png)

```
const canvas = document.querySelector("#renderCanvas");
const engine = new BABYLON.Engine(canvas, true);

function createScene() {
  const scene = new BABYLON.Scene(engine);

  const camera = new BABYLON.ArcRotateCamera(
    "Cam",
    Math.PI / 4,
    Math.PI / 3,
    10,
    new BABYLON.Vector3(0, 0, 0)
  );
  camera.attachControl(canvas, true);
  camera.wheelPrecision = 100;

  const light = new BABYLON.HemisphericLight(
    "Light",
    new BABYLON.Vector3(1, 1, 0)
  );

  BABYLON.SceneLoader.ImportMeshAsync("", "./gltfs/", "afo.gltf");

  const ground = BABYLON.MeshBuilder.CreateGround("Ground", {
    width: 10,
    height: 10,
  });

  return scene;
}

const sceneToRender = createScene();

engine.runRenderLoop(() => {
  sceneToRender.render();
});

```


비동기적 실행과 기본 버튼 생성
-------------------------------

![image](https://user-images.githubusercontent.com/30430227/169730870-00f92c36-45d3-42e7-9de1-6d947ece9b2a.png)

```
const canvas = document.querySelector("#renderCanvas");

const engine = new BABYLON.Engine(canvas, true);

async function startRenderLoop(sceneToRender) {
  engine.runRenderLoop(() => {
    sceneToRender.render();
  });
}

createScene().then(startRenderLoop);

async function createScene() {
  const scene = new BABYLON.Scene(engine);

  const light = new BABYLON.PointLight(
    "Light",
    new BABYLON.Vector3(0, 100, 100),
    scene
  );
  const camera = new BABYLON.ArcRotateCamera(
    "Camera",
    0,
    1,
    5,
    new BABYLON.Vector3.Zero(),
    scene
  );
  camera.attachControl(canvas, true);
  camera.wheelPrecision = 100;

  const box1 = BABYLON.Mesh.CreateBox("Box1", 1, scene);
  box1.position.y = 1;

  const matBox = new BABYLON.StandardMaterial("MatBox", scene);
  matBox.diffuseColor = new BABYLON.Color3(0, 1, 0);

  box1.material = matBox;

  const advancedTexture =
    BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI");

  const btn1 = BABYLON.GUI.Button.CreateSimpleButton("Btn1", "클릭클릭");
  btn1.width = "150px";
  btn1.height = "40px";
  btn1.onPointerUpObservable.add(() => [alert("니주글래!")]);

  advancedTexture.addControl(btn1);

  return scene;
}

```


블랜더 GLTF Animation 
-----------------------

![image](https://user-images.githubusercontent.com/30430227/169786317-7133f653-0df1-437d-9845-645050b4971d.png)

```
dispose 폐기하다, 처분하다//메모리에서 제거

키프레임 그룹 : 움직이지 않는 Act 그룹을 먼저 만든다(Default 액팅그룹, 별아이콘 같은 이름 = 그룹이 된다)

Export 시 Punctual Lights 체크 - 블랜더 조명 사용
```

![image](https://user-images.githubusercontent.com/30430227/169786222-5c86bc86-c795-4a2d-97f8-a7290def13fa.png)

![image](https://user-images.githubusercontent.com/30430227/169786658-05583dd9-61e8-4d0e-baba-3853a459f074.png)


```
const canvas = document.querySelector("#renderCanvas");

const engine = new BABYLON.Engine(canvas, true);

async function startRenderLoop(sceneToRender) {
  engine.runRenderLoop(() => {
    sceneToRender.render();
  });
}

createScene().then(startRenderLoop);

async function createScene() {
  const scene = new BABYLON.Scene(engine);

  const light = new BABYLON.PointLight(
    "Light",
    new BABYLON.Vector3(0, 100, 100),
    scene
  );
  const camera = new BABYLON.ArcRotateCamera(
    "Camera",
    0,
    1,
    5,
    new BABYLON.Vector3.Zero(),
    scene
  );
  camera.attachControl(canvas, true);
  camera.wheelPrecision = 100;

  BABYLON.SceneLoader.ImportMeshAsync("", "./gltfs/", "minami.glb", scene);

  const advancedTexture =
    BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI");

  const btn1 = BABYLON.GUI.Button.CreateSimpleButton("Btn1", "클릭클릭");
  btn1.width = "150px";
  btn1.height = "40px";
  btn1.left = "-200px";
  btn1.top = "100px";
  btn1.color = "white";
  btn1.onPointerUpObservable.add(() => {
    scene.stopAllAnimations();
    scene.animationGroups[2].play(true);
  });

  advancedTexture.addControl(btn1);

  const btn2 = BABYLON.GUI.Button.CreateImageOnlyButton(
    "Btn2",
    "images/4g2.jpg"
  );
  btn2.width = "150px";
  btn2.height = "150px";
  btn2.top = "100px";
  btn2.hoverCursor = "pointer";
  btn2.onPointerUpObservable.add(() => {
    scene.stopAllAnimations();
    scene.animationGroups[1].play(true);
  });

  advancedTexture.addControl(btn2);

  return scene;
}

```

SkyBox Stack UI
-----------------

![image](https://user-images.githubusercontent.com/30430227/169964778-d331c338-f5bb-4bbf-8fe7-37012446bdb7.png)

```
# dds : directDrawSurface 바빌론 Skybox 용 HDRI 이미지보다 작은 용량이라는데...


const canvas = document.querySelector("#renderCanvas");

const engine = new BABYLON.Engine(canvas, true);

async function startRenderLoop(sceneToRender) {
  engine.runRenderLoop(() => {
    sceneToRender.render();
  });
}

createScene().then(startRenderLoop);

async function createScene() {
  const scene = new BABYLON.Scene(engine);

  const camera = new BABYLON.ArcRotateCamera(
    "Camera",
    0,
    1,
    5,
    new BABYLON.Vector3.Zero(),
    scene
  );
  camera.attachControl(canvas, false);//true: Canvas 이벤트를 받는다(마우스휠 영향) 
  camera.wheelPrecision = 100;

  BABYLON.SceneLoader.ImportMeshAsync(
    "",
    "./gltfs/",
    "minami.glb",
    scene,
    function () {
      const advancedTexture =
        BABYLON.GUI.AdvancedDynamicTexture.CreateFullscreenUI("UI");

      const UiPanel = new BABYLON.GUI.StackPanel();
      UiPanel.width = "220px";
      UiPanel.fontSize = "14px";
      UiPanel.horizontalAlignment =
        BABYLON.GUI.Control.HORIZONTAL_ALIGNMENT_RIGHT;
      advancedTexture.addControl(UiPanel);

      let nbButtons = 1;

      const addButton = function (text, parent, onPointerUpObservable) {
        const button = BABYLON.GUI.Button.CreateSimpleButton(
          "but" + nbButtons++,
          text
        );
        button.paddingTop = "10px";
        button.width = "100px";
        button.height = "50px";
        button.color = "white";
        button.background = "green";
        button.hoverCursor = "pointer";
        button.onPointerUpObservable.add(onPointerUpObservable);
        parent.addControl(button);
      };

      addButton("Clean Animations", UiPanel, () => {
        scene.stopAllAnimations();
      });

      addButton("Minami", UiPanel, () => {
        scene.animationGroups[1].play(true);
      });

      const button = BABYLON.GUI.Button.CreateImageOnlyButton(
        "4G2",
        "images/4g2.jpg"
      );
      button.paddingTop = "10px";
      button.width = "100px";
      button.height = "100px";
      button.onPointerUpObservable.add(() => {
        scene.stopAllAnimations();
        scene.animationGroups[1].play(true);
      });

      UiPanel.addControl(button);
    }
  );

  const hdrTexture = BABYLON.CubeTexture.CreateFromPrefilteredData(
    "images/environment.dds", 
    scene
  );
  const currentSkybox = scene.createDefaultSkybox(hdrTexture, true);

  return scene;
}

```

Skybox 용 .env 파일 만들기 
--------------------

![image](https://user-images.githubusercontent.com/30430227/169996866-9e82cd27-2c61-4b36-9efe-9591df06de7a.png)

```
# dds대신 env 텍스쳐로 대체

  const hdrTexture = new BABYLON.CubeTexture("images/environment.env", scene);

  const currentSkybox = scene.createDefaultSkybox(hdrTexture, true);

# 바빌론 SANDBOX에 아무 씬이나 넣은 후 HDR 텍스쳐를 드랙해서 넣으면 메뉴가 생성된다
```

![image](https://user-images.githubusercontent.com/30430227/169995070-345f3e2d-21c3-4506-9ab6-4659ad9737c2.png)


백그라운드 머티리얼 -  Environment에 사용되는 재질
-----------------------------------------

![image](https://user-images.githubusercontent.com/30430227/170226120-1dbef7f1-42d9-4001-b6fe-21201fdd35da.png)

```
# .createInstance 인스턴스 복사
# mesh.parent mesh의 원점이 부모의 원점으로 이동

const canvas = document.querySelector("#renderCanvas");

const engine = new BABYLON.Engine(canvas, true);

var createScene = function () {
  // This creates a basic Babylon Scene object (non-mesh)
  var scene = new BABYLON.Scene(engine);
  
  // glTF Files use right handed system 
  scene.useRightHandedSystem = true;
  BABYLON.SceneLoader.ImportMesh(
    "",
    "gltfs/",
    "minami.glb",
    scene,
    function (meshes) {
      const parent = new BABYLON.TransformNode("parent");

      // Original mesh
      const mesh = scene.getMeshByName("Cube");
      mesh.parent = parent;
      // mesh.position = new BABYLON.Vector3(0, 2, 0);
      parent.position = new BABYLON.Vector3(0, -1, 0);

      // Instance
      const meshInstance = scene.meshes[3].createInstance("meshInstance");
      meshInstance.position = new BABYLON.Vector3(5, 0, 0);

      // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
      var light = new BABYLON.DirectionalLight(
        "light",
        new BABYLON.Vector3(2, -2, -2),
        scene
      );

      // Our built-in 'ground' shape.
      var ground = BABYLON.MeshBuilder.CreateGround(
        "ground",
        { width: 40, height: 40 },
        scene
      );
      ground.position = new BABYLON.Vector3(0, -1, 0);

      const backgroundMaterial = new BABYLON.BackgroundMaterial(
        "BackgroundMaterial",
        scene
      );
      backgroundMaterial.shadowOnly = true;
      ground.material = backgroundMaterial;

      var shadowGenerator = new BABYLON.ShadowGenerator(1024, light);
      shadowGenerator.bias = 0;
      // shadowGenerator.addShadowCaster(meshInstance, true);
      scene.meshes.forEach((mesh) => {
        shadowGenerator.addShadowCaster(mesh, true);
      });
      ground.receiveShadows = true;
    }
  );

  var camera = new BABYLON.ArcRotateCamera(
    "camera",
    Math.PI / 2,
    0.9,
    50,
    new BABYLON.Vector3(0, 2, 0),
    scene
  );
  camera.attachControl(canvas, true);

  return scene;
};

const sceneToRender = createScene();

engine.runRenderLoop(() => {
  sceneToRender.render();
});

```


백그라운드 머티리얼,비디오,스프라이트 
-----------------------

![image](https://user-images.githubusercontent.com/30430227/170646510-de0569f2-c947-4d70-a68e-9b30a3d8d83e.png)

```
const canvas = document.querySelector("#renderCanvas");

const engine = new BABYLON.Engine(canvas, true);

function createScene() {
  const scene = new BABYLON.Scene(engine);

  const camera = new BABYLON.ArcRotateCamera(
    "Camera",
    Math.PI / 4,
    Math.PI / 3,
    5,
    new BABYLON.Vector3.Zero(),
    scene
  );
  camera.attachControl(canvas, false); // 마우스 휠 시 브라우저 스크롤 false
  camera.wheelPrecision = 100;

  const light = new BABYLON.DirectionalLight(
    "Light",
    new BABYLON.Vector3(-1, -3, 1),
    scene
  );
  light.position = new BABYLON.Vector3(3, 9, 3);
  light.intensity = 0.7;

  const sphere = BABYLON.MeshBuilder.CreateSphere(
    "Sphere",
    { segments: 6, diameter: 2 },
    scene
  );
  sphere.position = new BABYLON.Vector3(0, 1, 0);

  // Click Action Manager
  sphere.isPickable = true;
  sphere.actionManager = new BABYLON.ActionManager(scene);
  sphere.actionManager.registerAction(
    new BABYLON.ExecuteCodeAction(
      BABYLON.ActionManager.OnPickTrigger,
      function () {
        sphere.position.y += 0.1;
      }
    )
  );

  const hi = new BABYLON.HighlightLayer("hi", scene, { isStroke: true }); // 하이라이트효과, blur대신 선으로 true

  scene.registerBeforeRender(() => {
    hi.blurHorizontalSize = 0.1;
    hi.blurVerticalSize = 0.1;
  });

  sphere.actionManager.hoverCursor = "pointer";

  sphere.actionManager.registerAction(
    new BABYLON.ExecuteCodeAction(
      BABYLON.ActionManager.OnPointerOverTrigger,
      function () {
        scene.hoverCursor = "pointer";
        hi.addMesh(sphere, BABYLON.Color3.Green());
      }
    )
  );
  sphere.actionManager.registerAction(
    new BABYLON.ExecuteCodeAction(
      BABYLON.ActionManager.OnPointerOutTrigger,
      function () {
        hi.removeMesh(sphere, BABYLON.Color3.Green());
      }
    )
  );

  const ground = BABYLON.MeshBuilder.CreateGround(
    "Ground",
    { width: 6, height: 6, subdivisions: 32 },
    scene
  );

  // Video
  const video = BABYLON.MeshBuilder.CreatePlane(
    "Video",
    {
      width: 1,
      height: 2,
      sideOrientation: BABYLON.Mesh.DOUBLESIDE,
    },
    scene
  );
  video.position = new BABYLON.Vector3(2, 1, 0);

  const matVideo = new BABYLON.StandardMaterial("MatVideo", scene);
  const texVideo = new BABYLON.VideoTexture(
    "TexVideo",
    "images/packing.mp4",
    scene
  );
  matVideo.diffuseTexture = texVideo;
  matVideo.roughness = 1;
  matVideo.emissiveColor = new BABYLON.Color3.White();
  video.material = matVideo;

  video.actionManager = new BABYLON.ActionManager(scene);
  video.actionManager.registerAction(
    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, () => {
      console.log("hu");
    })
  );
  video.actionManager.hoverCursor = "help";

  scene.onPointerObservable.add(function (event) {
    if (event.pickInfo.pickedMesh === video) {
      if (texVideo.video.paused) {
        texVideo.video.play();
      } else {
        texVideo.video.pause();
      }
    }
  }, BABYLON.PointerEventTypes.POINTERPICK);

  // Add Shadow
  const generator = new BABYLON.ShadowGenerator(512, light);
  generator.addShadowCaster(sphere);
  generator.useBlurExponentialShadowMap = true; // true t-소문자, 그림자 가장자리 부드럽게
  generator.blurScale = 1;
  generator.blurKernel = 64; // blur에 사용되는 작은 행렬, Blur 확장
  generator.useKernelBlur = true;
  generator.depthScale = 0;

  ground.receiveShadows = true; // receiveShadows -복수형

  const backgroundMaterial = new BABYLON.BackgroundMaterial(
    "BackgroundMaterial",
    scene
  );

  // BackgroundMaterial Texture
  backgroundMaterial.diffuseTexture = new BABYLON.Texture(
    "images/backgroundGround.png",
    scene
  );
  backgroundMaterial.diffuseTexture.hasAlpha = true; // hasAlpha
  // backgroundMaterial.diffuseTexture.uScale = 2.0;
  // backgroundMaterial.diffuseTexture.vScale = 3.0;
  backgroundMaterial.shadowLevel = 0.1; // shadow Transparent(0 black, 1 no shadow)
  backgroundMaterial.opacityFresnel = false; // 각도에 따른 불투명도 효과 제거, 수평일 때도 선명하게 보인다

  // 미러 텍스처
  const mirror = new BABYLON.MirrorTexture("mirror", 512, scene);
  mirror.mirrorPlane = new BABYLON.Plane(0, -1, 0, 0);
  mirror.renderList.push(sphere);
  backgroundMaterial.reflectionTexture = mirror;
  backgroundMaterial.reflectionFresnel = true; // fresnel 보는 각도에 따라 반사량이 다른
  backgroundMaterial.reflectionStandardFresnelWeight = 0.9;

  // BackgroundMaterial Shadow Only
  // backgroundMaterial.primaryColor = new BABYLON.Color4(0.6, 0.6, 0, 1);
  // backgroundMaterial.shadowOnly = true;
  // backgroundMaterial.wireframe = true;
  ground.material = backgroundMaterial;

  //sprite
  const spriteManager4G2 = new BABYLON.SpriteManager(
    "4G2Manager",
    "images/4g2.jpg",
    1000,
    { width: 100, height: 100 } // 300X300 spriteSheet, 가로 세로가 같은 경우 100만 써도 된다
  );
  const sprite = new BABYLON.Sprite("4G2", spriteManager4G2);
  sprite.width = 1;
  sprite.height = 1.2;
  sprite.position = new BABYLON.Vector3(0, 1, 2);

  sprite.playAnimation(0, 8, true, 1000); // loop true, frame delay 100

  return scene;
}

const sceneToRender = createScene();

engine.runRenderLoop(() => {
  sceneToRender.render();
});

```

Node Editor
--------------

![image](https://user-images.githubusercontent.com/30430227/171119668-d3d1d9dd-3bb0-4fe5-807b-edec5660e841.png)

```
# 생성 
  const nodeMaterial = new BABYLON.NodeMaterial("node material", scene, {
    emitComments: true,
  });
  nodeMaterial.setToDefault();  // 기본 노드들 생성

# 디버거 활성
  scene.debugLayer.show();
  // scene.debugLayer.select(nodeMaterial);
  
## 박스선택 단축키 : Ctrl hold
## 노드 에러 시 기존 노드를 지운 후 인풋 포인트를 클릭하면 새로 생성된다. 
```

![image](https://user-images.githubusercontent.com/30430227/171120012-04502fbe-c796-46a0-941b-105bf69dfcba.png)

![image](https://user-images.githubusercontent.com/30430227/171120111-8ac3b15c-a368-48ea-a1f9-4e93a798e458.png)

**PBRMatallicRoughness**

![image](https://user-images.githubusercontent.com/30430227/171123988-0cbf0cb7-6463-44cc-89fa-d63c56e1ab11.png)





