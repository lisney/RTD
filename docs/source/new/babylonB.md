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
  camera.setTarget(BABYLON.Vector3.Zero());
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



PBR Material 
-------------------

![image](https://user-images.githubusercontent.com/30430227/173498961-c6db96cb-34fe-466b-93bc-2e899e231cf9.png)

```
const canvas = document.querySelector("#renderCanvas");
const engine = new BABYLON.Engine(canvas, true);

const scene = createScene();

engine.runRenderLoop(() => {
  scene.render();
});

function createScene() {
  const scene = new BABYLON.Scene(engine);
  // scene.environmentIntensity = 0.1;//씬 환경 텍스처 Intensity

  const camera = new BABYLON.ArcRotateCamera(
    "camera",
    Math.PI / 4,
    Math.PI / 3,
    5,
    new BABYLON.Vector3(0, 0, 0),
    scene
  );
  // camera.setTarget(BABYLON.Vector3.Zero());//freeCamera용 타깃
  camera.attachControl(canvas, false);
  // camera.speed = 0.25; // 키보드 방향키 감도
  camera.wheelPrecision = 50; //FreeCamera는 줌이 안된다

  const hemiLight = new BABYLON.HemisphericLight(
    "hemiLight",
    new BABYLON.Vector3(0, 1, 1),
    scene
  );

  hemiLight.intensity = 0.5;

  // Mesh
  const ground = BABYLON.MeshBuilder.CreateGround(
    "ground",
    { width: 5, height: 5 },
    scene
  );

  const ball = BABYLON.MeshBuilder.CreateSphere("ball", { diameter: 2 }, scene);
  ball.position = new BABYLON.Vector3(0, 1, 0);

  // Material
  function CreateGroundMaterial() {
    const pbr = new BABYLON.PBRMaterial("pbr", scene);
    pbr.roughness = 1; //값이 0 면 거울
    pbr.albedoTexture = new BABYLON.Texture("./images/adiffuse.jpg", scene);
    pbr.albedoTexture.vScale = 4;
    pbr.albedoTexture.uScale = 4;
    pbr.bumpTexture = new BABYLON.Texture("./images/anormal.jpg", scene);
    pbr.bumpTexture.vScale = 4;
    pbr.bumpTexture.uScale = 4;
    pbr.invertNormalMapX = true;
    pbr.invertNormalMapY = true;
    pbr.emissiveTexture = new BABYLON.Texture("./images/aambientt.jpg", scene); //흰색이 Emissive, 검정은 투명
    pbr.emissiveColor = new BABYLON.Color3(1, 1, 1);
    // pbr.emissiveIntensity = 3;

    const glowLayer = new BABYLON.GlowLayer("glow", scene);
    glowLayer.intensity = 1;

    // pbr.useAmbientOcclusionFromMetallicTextureRed = true;
    // pbr.useRoughnessFromMetallicTextureGreen = true;
    // pbr.useMetallinessFromMetallicTextureBlue = true;

    return pbr;
  }
  ground.material = CreateGroundMaterial();

  function CreateBallMaterial() {
    const pbr = new BABYLON.PBRMetallicRoughnessMaterial("pbr", scene);
    pbr.baseColor = new BABYLON.Color3(1, 0.7, 0.3);
    pbr.metallic = 1;
    pbr.roughness = 0;
    pbr.environmentTexture = BABYLON.CubeTexture.CreateFromPrefilteredData(
      "images/environment.dds",
      scene
    );
    return pbr;
  }

  ball.material = CreateBallMaterial();

  const envTexture = new BABYLON.CubeTexture("images/environment.env", scene);
  scene.createDefaultSkybox(envTexture, true);

  return scene;
}

```


import GLB(GLTF)
-------------------

![image](https://user-images.githubusercontent.com/30430227/173505758-a0ff0ed1-7246-4bd0-8390-3f5ce88a9470.png)

```
  BABYLON.SceneLoader.ImportMesh(
    "",
    "./gltfs/",
    "afo.gltf",
    scene,
    (meshes) => {
      scene.meshes[0].position = new BABYLON.Vector3(0, -1, 0);
    }
  );
```


그림자와 Gizmo
--------------

![image](https://user-images.githubusercontent.com/30430227/173759157-b837b499-1e32-4dcd-b6a4-40875e3aae41.png)

`블랜더에서 라이트 제거하고 export`

```
  const camera = new BABYLON.FreeCamera(
    "camera",
    new BABYLON.Vector3(5, 5, -5),
    scene
  );
  camera.setTarget(BABYLON.Vector3.Zero()); //freeCamera용 타깃
  camera.attachControl(canvas, false);
  camera.speed = 0.25; // 키보드 방향키 감도

  //조명

  // const hemiLight = new BABYLON.HemisphericLight(
  //   "hemiLight",
  //   new BABYLON.Vector3(0, 1, 0),
  //   scene
  // );
  // hemiLight.intensity = 0.5;
  // hemiLight.diffuse = new BABYLON.Color3(1, 0, 0);
  // hemiLight.groundColor = new BABYLON.Color3(0, 0, 1);
  // hemiLight.specular = new BABYLON.Color3(0, 1, 0);

  const spotLight = new BABYLON.SpotLight(
    "spotLight",
    new BABYLON.Vector3(-3, 3, -5), //위치
    new BABYLON.Vector3(3, -2, 3), //방향-위치가 아니라 방향이다
    Math.PI / 2, //조명 각도
    10, //Exponent
    scene
  );
  spotLight.intensity = 10;
  spotLight.shadowEnabled = true;
  spotLight.shadowMinZ = 1;//shadow clipping minimum
  spotLight.shadowMaxZ = 10;

  //shadow 제너레이터
  const shadowGen = new BABYLON.ShadowGenerator(1024, spotLight);
  shadowGen.useBlurCloseExponentialShadowMap = true;//부드러운 가장자리

  CreateGizmos(spotLight);

  // Light Gizmo
  function CreateGizmos(customLight) {
    const lightGizmo = new BABYLON.LightGizmo(); //라이트 메쉬
    lightGizmo.scaleRatio = 3;
    lightGizmo.light = customLight;

    const gizmoManager = new BABYLON.GizmoManager(scene); //컨트롤러
    gizmoManager.positionGizmoEnabled = true;
    gizmoManager.rotationGizmoEnabled = true;
    gizmoManager.usePointerToAttachGizmos = false;
    gizmoManager.scaleRatio = 2;
    gizmoManager.attachToMesh(lightGizmo.attachedMesh);
  }

  // Import GLB file
  BABYLON.SceneLoader.ImportMesh(
    "",
    "./gltfs/",
    "nolight.glb",
    scene,
    (meshes) => {
      meshes.map((mesh) => {
        mesh.receiveShadows = true;
        shadowGen.addShadowCaster(mesh);
      });
    }
  );
```



