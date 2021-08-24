기본
======

모델링
------
`LoopTools > space`
선택한 점들을 동일한 간격으로 정리해준다.

`Proportion Editing에서` Connected를 선택하면 연결된(Link) 면만 프로포션이 적용된다.(O Key)

`Edge>Unsubdivide` 꺼꾸로 디바이드

`선택을 상속하다(엣지->페이스)`
Edit 모드에서 엣지에서 선택한 후 ctrl + 페이스 버튼을 클릭하면 선택이 이어진다???

`섭디바이드 후` >프렉탈 파라미터 조절

`파티클을 메쉬로 변환`
Object>Make Duplicate Real  
파티클 오브젝트를 별도의 오브젝트로 변환한다  
Rigid Body Tools 탭에서 Copy form Active : 리지드바디 속성을 현재 액티브 되어있는 바디의 속성으로 전부 적용한다.한방에 전체 리지드바디의 속성을 변경할 수 있는 기능

`블랜더 백그라운드 이미지`
Numpad -1(FrontView) > Shift + A > Image > Background Image  
Ortho View에서만 확인 가능  

`라플라시안 디폼`
with후크..  후크>셀렉트 후크 한 다음 버텍스 그룹을 할당한다  
디폼을 적용한다

`메타볼 응용 모델링`
메시에 Parent 시킨 후 duplication 설정(Extrude 등을 적용해본다

`베지어 커브 도로 맵핑하기`
extrude는 z방향이니 로테이션 시키든지 아님 정면뷰에서 Align to View 생성한다  
또는 Tilt(ctrl + T) 값을 90도 준다  
Texture Space 에서 Use UV...체크한다  
Texture 콘텍스트에서 Mapping 패널을 연다 > Coordinates(좌표) >Generated 선택한다  
패턴을 줄려면 Size의 X,Y,Z 수치를 조절한다

`loopCut 시 맵 distortion 방지`
loopcut 후 옵션에서 Correct UVs를 체크한다  
Edge Slide에도 적용된다

`2.78 Draw Curve 단축키 생성`
//베지어 커브를 생성 후 에디터모드에서 버텍스를 지운다  
//커브옵션에서 Bevel을 준다음 좌측 옵션에서 TaperRadius 값을 조정한다  
//Create탭에서 DrawCurve 버튼을 누르고 그린다  
//UserPreferences에서 Curve에 새단축키를 생성한후  
// curve.draw 명령을 입력하고 Mouse : Action : Press를 선택한다(WaitforInput체크를 끈다), 조합키를 Shift를 체크한다  
//Shift + rightMouse 버튼으로 그린다

`Manipulate Center Point Mode`  
![image](https://user-images.githubusercontent.com/30430227/130587791-1b2f3b50-948e-45d8-a251-1559fc025adc.png)  
//여러 오브젝트를 선택후 Scale 명령 시 중심점을 중심으로 <이동>한다
<br>

스컬핑
-------
`Trim브러시`
//Strength를 1로, Area Plane를 LOck한다
//Curve를 평평한걸로

`스컬핑 시 Mesh Topology, 영역 주변만 영향을 받게`
//Front Faces Only를 체크한다

'Gravity'
//Options > Options > Gravity
<br>

리깅
-----
`블랜더 본 선택 시 Active(흰색테두리)되지 않고 비활성(하늘색)되는 경우`
//선택 시 해당 오브젝트를 바로 선택하지 말고 근처(살짝 옆부분)를 선택하면 된다

`Child OF의 단짝 Visual Transform` 현재 보여지는 위치로 이동시킨다
<br>

애니메이션
----------
`리버스 키프레임`
//도프시트에서 키프레임을 선택하고 스케일s키를 누른 후 -1을 입력한다.
//넌리니어에디트로 넘어간 후 리버스 키 한다...이후 도프시트에서 키프레임이 보이게 할려면 넌리니어에디트에서 TAB키를 누르면 키가 보인다.

`넌리니어클립으로 만들기`
//이름 옆의 //를 클릭하면 된다

`그래프에디터 타임라인 단축키 설정문제`
//마우스 오른키 : Set Cursor(타임라인 인디케이터 이동) 
///기존에 Handle Type로 설정되어 있는데..

`타임라인 표지 변경`
프레임 <> S:F   : ctrl + T

`Edit Mode에서 복사하여 공유된 키프레임 삭제방법 `
//키프레임을 오리지날과 공유하고 있으므로
//Outliner 에디터에서 Animation을 삭제하면 된다
<br>

협력작업 makeHuman
---------------------

`Link 오브젝트는 기본적으로 변형되지 않는다.`
ctrl + alt + P (프록시화) 하면 변형이 가능하다

`원본 오브젝트를 변형하고 결과를 보려면..`
File > Revert 한다

`Link 를 깨려면 `
Make Local 하면 된다

`MakeHuman Manipulator 나타나게`
//Transform > Lock을 푼다(잠금되어있다)
<br>

UV
-----
`UV 에디터에서 가운데 버튼 lasso 선택 기능 활성`
//User Preferences 에서 uv.slect_lasso 명령을 생성한다
//tweak 와 Middle 키를 선택하고 Any를 체크한다

`UV 릴리즈?`
//변형하지 않을 UV 버텍스들을 선택하고 Pin한 후
//Scale 명령 'R'을 실행하면 핀 되지않은 버텍스들이 자동릴리즈(완화)된다
//그 후 UV > Minimize Stretch 한다(값은 마우스 휠로 조절)

`UV 리셋`
//단축키 'U' > reset

`V회전`
//ctrl + 'F' > rotateUV
<br>


Cycle
---------
`사이클 노말맵 적용`
//ImageTexture에 이미지를 불러온다
//ImageFileColorSpace를 Color->Non-Conor Data롤 바꾼다
//Add > Vector > Normal Map 한 후 컬러를 링크한다
//Shader에 연결한다 

`추가로 광택을 주기위해`
//Glossy BSDF

`사이클 배경`
//TextureCoordinate(Generated)-Mapping-ImageTexture(Vector)

`사이클 Displacemap`
//렌더>Render:Feature Set->Experimental 선택
//머터리얼>Setting:Displacement->True로 바꿈
//노드에디터에서 재질을 적용한다
//노말텍스처를 MaterialOutput의 Displacement에 연결한다
//F12 1차 랜더링해야 뷰포트랜더에서도 반영된다
//참 메쉬는 어느정도 섭디해줘야하고, 모디파이>섭디바디이드서피스에서 Adaptive를 체크해준다

`사이클 Bump, Normal 맵`
//Vector > Bump 노드 사용
//Bump텍스처는 height에 Normal은 Normal 인풋에 연결한다
//쉐이더의 Normal 인풋에 연결한다

`스페큘러`
//MixColor에서 Color1에 인풋 Color2를 블랙으로 바꾸어 밝은부분만 선택
//Mix 쉐이더의 Factor에 연결한다

`이끼표현`
//두 텍스처를 섞기위해 MixColor을 사용한다. Noise텍스처를 Fac로 사용한다
//ColorRamp를 사용하여 적용정도를 조정한다

`노드그룹`
//진입 키 Tab

`Translucent BSDF 쉐이더`
//바로 Mix 쉐이더에 연결하지 않고
//Add Shader 노드에 연결(두 가닥 shader입력에 모두 연결한다)
//그리고 Color는 초록색(잎의 경우)으로 바꾼다


`Glossy Factor`
//ImageTexture - ColorRamp - MixShader(Fac)에 연결

`파티클 퐈이어`
//블렌더 버전업하면서 기본적으로 파티클에 재질이 들어가는데
//smoke 효과를 적용할 때는 꺼주어야한다
//Render:Emitter체크해제, Halo->None
//텍스처의 Mapping:Coordinates->Generated 선택


`파이어스모크도메인 블랙 제거?! 블렌더랜더의 경우`
//Material을 추가한 후 Shadow:Receive Transparent를 체크한다

`랜덤컬러(노드)`
//Input > ObjectInfo:Random->ColorRamp:Fac 연결

`텍스처 베이킹`
//UV/Image Editor(윈도우를 연다,UV에디터가 열린상태에서)
//새로운 UV와 Image를 만든 후
//랜더탭에서 베이킹한다(BakeMode : Textures)

`타일텍스처`
//uv맵을 2배로 스케일 조정한 후 페인팅한다

`Baking Texture`
//블렌더랜더 -UV에디터에서 UV, image 생성 후 베이킹
//cycle 랜더 - image node 생성> new image 연결 후 베이킹

`랜더링 시 firefiles(흰색 점들)제거`
//Render > Sampling : Clamp 값을 조정해본다
<br>

Nature
-------
`바다`
//ocean Modifier 적용 > scale(파도의크기)/choppiness(거친바다표현,끝이 날카롭다)

`포말`
//generate Foam 체크 >coverage(포말의 량)/bake Ocean>foam fade(폼이 사라지는 정도)
//Material>Mirror 적용
//Texture>Ocean Type 선택>Ocean>ModifierObject선택하고 output:Foam 선택한다 

`재질미러 사용하기(포말 사용할 시)`
//머티리얼 Mirror 값을 0로 하고
//texture>influence>shading>rayMirror(미러 재질설정) 한다


`다이내믹 페인트`
//표면은 Canvas, 물체는 Brush로 적용한다

`물체가 표면을 따라 이동`
//Date>VertexGroup 에서 그룹을 생성한다
//캔버스>다이내믹페인트어드벤스드>SurfaceType:weight선택>전에 만들어 둔 버텍스그룹 적용
//Fade체크한 후 Time을 1로 정한다
///표면을 따라 이동할 물체 생성한 후 Constraint>Copy Location/Rotate 두 개를 적용한 후 타겟을 오션모디파이어:버텍스 그룹으로 정한다

`다이내믹 페인트 추가`
//새로 만든 물체를 다이내믹 브러시로 정한다
//이전 브러시와 독립적으로 영향을 주기 위해 두 브러시를 각각 그룹화한다
//다이내믹브러시어드벤스드>브러시그룹에서 해당 서피스타입과 각각 연결한다

브러시옵션 Use object material 체크
//오브젝트의 재질로 페인트한다
//캔버스의 재질 옵션:VertexColorPaint를 체크한다
//캔버스의 다이내믹페인트아웃풋:Paintmap layer 메뉴의 + 를 눌러 생성한다

`캔버스옵션 SurfaceType:waves `
//물결을 생성

`돌 생성`
//Cell Fracture 에서 Noise 값을 높인다(내부에도 조각이 적용된다)

`연기`
//Domain>quickSmoke>Vorticity(소용돌이):터뷸런스 값
//Domain>Density(음수값으로 높일수록 억제력이 높다)
//Flow>FlowType:Fire+Smoke>FlameRate:Fire의 량

`풀 만들기`
//파티클(헤어)>그룹오브젝트>모디파이 파티클시스템:convert 클릭
//파티클 오브젝트에 Weight Paint 를 한다
//중요::DATA에서 숫자를 클릭(싱글화)한다음 join(Ctrl + j)한다

`파티클 시간에 따라 사이즈`
//Blender랜더모드
// : texture >New particleTexture
//type : Blend, colors : Ramp, Mapping>Coordinates : strand/particle , Influence : Size체크
//Cycle 랜더모드//Particle > Texture >New Texture 한 후 Texture을 위와같이 설정한다

`파티클 투명도`
//Cycle모드
//파티클오브젝트 > New Material
//노드에디터 
//New Transparent Shader->Mix Shader에 연결
//ParticleInfo노드의 Age(현재나이)/Lifetime(수명)->Math(Divide)->ColorRamp
//ColorRamp(Color)->MixShader의 Fac에 연결한다
<br>

애팩 합성
-----------
`OpenEXR multi 시 IndexOB 를 ID Mask 노드에 링크한 후 ID를 선택한다음`
//블랜더 File Output에 레이어를 만든 후 ID Mask 노드를 링크한다
//에팩에서는 3DChennel에서 EXtracter 효과에서 선택한다
<br>










기타 팁
-----------
`나무 Arbaro 실행방법`
//cd <arbaro directory> 
 java -jar arbaro_gui.jar

`Clipping Border 단면 보기  //Edit Mode에서 Alt +B`
View>Clipping Border 단면 보기

`Emulate 3 Button Mouse`
//2버튼 마우스 사용자를 위한 설정(중간 마우스 대신 좌측마우스키를 사용하게된다)

`카메라 회전 앵글 고정`  돌리다가 Alt키를 떼었다가 다시 누른다

`ctrl + L  (Modify)`
메이크링크...모디파이 속성을 복사

`F6` : 옵션 창 띄움

`카메라를 버텍스에 자식화 하기`
부모 오브젝트를 선택 하고 Edit 모드로 들어간 후 버텍스를 3개 선택한 후 shift 카메라 선택한다음 'p' 페어런트 한다.

`레이아웃 전환` ;  Ctrl + 화살표키 좌/우

`Shape Keys에서 두 오브젝트를 몰핑시키는 방법`
두 오브젝트를 선택한 후 역화살표를 클릭하면 나오는 메뉴에서 Join As Shape를 선택하면 된다

`stl파일 정리 팁`
//에디트모드에서 del
//limited Dissolve 선택
//3Dprint ToolBox에서 Make Manifold 한다

<br>
VertexPaint
---------------

///뷰포트에서 보려면 프로퍼티패널에서 Shading>TexturedSolid를 체크해준다
1.붓 선택
//Set Brush Number : 명령어 brush.active_index_set
//숫자를 정해준 후 Mode에 vertex_paint 를 넣어준다

2.Fill Color(paint.vertex_color_set)
//Shift + K

3.Color Picker(paint.sample_color)
//Sample Color 
//단축키 s

  
