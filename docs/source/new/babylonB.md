Babylon Basic
================


Basic Scene
---------------

![image](https://user-images.githubusercontent.com/30430227/173024992-7313dede-b2cb-4342-bec3-9907da6bbc79.png)

```
# css
body {
  width: 100%;
  height: 100%;
}

.box {
  margin: 0 auto;
  width: 70%;
  height: 70%;
}

#renderCanvas {
  width: 100%;
  height: 100%;
}


## babylonjs
const canvas = document.querySelector("#renderCanvas");
const engine = new BABYLON.Engine(canvas, true);

const scene = createScene();

engine.runRenderLoop(() => {
  scene.render();
});

function createScene() {
  const scene = new BABYLON.Scene(engine);

  const camera = new BABYLON.FreeCamera(
    "camera",
    new BABYLON.Vector3(0, 1, -5),
    scene
  );
  camera.attachControl(canvas, false);
  camera.speed = 0.25; // 키보드 방향키 감도
  // camera.wheelPrecision = 50;//FreeCamera는 줌이 안된다

  const hemiLight = new BABYLON.HemisphericLight(
    "hemiLight",
    new BABYLON.Vector3(0, 1, 0),
    scene
  );

  hemiLight.intensity = 0.5;

  // Mesh
  const ground = BABYLON.MeshBuilder.CreateGround(
    "ground",
    { width: 10, height: 10 },
    scene
  );
  ground.material = CreateGroundMaterial();

  const ball = BABYLON.MeshBuilder.CreateSphere("ball", { diameter: 1 }, scene);
  ball.position = new BABYLON.Vector3(0, 1, 0);

  // Material
  function CreateGroundMaterial() {
    const groundMat = new BABYLON.StandardMaterial("groundMat", scene);
    const uvScale = 4;
    const texArray = [];

    const difTexture = new BABYLON.Texture(
      "./images/cobblestone_05_diff_1k.jpg",
      scene
    );
    groundMat.diffuseTexture = difTexture;
    texArray.push(difTexture);

    const norTexture = new BABYLON.Texture(
      "./images/cobblestone_05_nor_gl_1.jpg",
      scene
    );
    groundMat.bumpTexture = norTexture;
    groundMat.invertNormalMapX = true;
    groundMat.invertNormalMapY = true;
    texArray.push(norTexture);

    const aoTexture = new BABYLON.Texture(
      "./images/cobblestone_05_rough_1k.jpg",
      scene
    );
    groundMat.ambientTexture = aoTexture;
    texArray.push(aoTexture);

    const spTexture = new BABYLON.Texture(
      "./images/cobblestone_05_rough_1k.jpg",
      scene
    );
    groundMat.specularTexture = spTexture;
    groundMat.specularPower = 10;
    texArray.push(spTexture);

    texArray.forEach((tex) => {
      tex.uScale = uvScale;
      tex.vScale = uvScale;
    });

    return groundMat;
  }

  return scene;
}
```

