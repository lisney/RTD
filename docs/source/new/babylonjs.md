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
Students.find(함수(student, index){return student.score===90} 
//data.scre가 90인 첫번째 요소에서 멈추고 해당 요소만 리턴(=>배열.filter 조건에 맞는 모든 요소 배열로 리턴)

Students.map(student=>student.score) //클래스 객체를 클래스 멤버변수로 매핑 즉 맴버 변수만 배열로 리턴

Students.reduce((prev, curr)=>{return prev + curr.score},0) // 중괄호 없어도 된다
//누적값 리턴, 초기값: 0, 순차적으로 return 한 값이 다음 번 prev의 값으로 들어간다.

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
# 프로미스로는
function fetchUser() {
  return new Promise((resolve, reject) => {
    resolve("ellie");
  });
}

const user = fetchUser();//사용자 데이터를 백앤드로 받아오는 함수

user.then(console.log);//user=>console.log(user) 의 축약형(전달 인수와 받는 함수의 인수가 같을 때 생략)

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

