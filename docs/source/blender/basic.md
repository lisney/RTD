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
```
//cd <arbaro directory> 
//java -jar arbaro_gui.jar
```

`Clipping Border 단면 보기 Edit Mode에서 Alt +B`
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
3Dprint ToolBox에서 Make Manifold 한다  
<br>

VertexPaint
------------  
뷰포트에서 보려면 프로퍼티패널에서 Shading>TexturedSolid를 체크해준다  
1.붓 선택  
//Set Brush Number : 명령어 brush.active_index_set
//숫자를 정해준 후 Mode에 vertex_paint 를 넣어준다

2.Fill Color(paint.vertex_color_set)  
//Shift + K

3.Color Picker(paint.sample_color)  
//Sample Color 
//단축키 s

단축키 세팅
------------

`⓿Interface `: Auto Depth(줌 억제기능 해제,&&Fly Mode Shift + F 해제시 버그) 체크/Auto Perspective 체크

`메뉴사이즈 조정(Alt + R-Mouse)` //View2D->명령어 view2d.zoom->단축키 설정

`input : UserPreferences77/Select With : Left / zoomStyle : Horizontal`
//Select Shortest Path :with Ctrl Key
//6 : MATERIAL - RENDERED 단축키 설정
//Inset face : i 단축키 설정
//Curve : Set Handle Typee 단축키 v로 설정(기존 오른 마우스키)

`외부 Addon` : blender-sculpt-tools-master-1 > 현재 bool tool 기본 애드온이다

`Carver Addon` : 뉴커팅툴

`Wrangler` : Ctrl + Shift +클릭, Ctrl + R클릭 , Ctrl + T

```
⓵3Dview>mesh 카테고리 mesh.select_mode 명령어
//edit 모드에서 vertex, edge, face 전환(단축키 1,2,3)
//image 카테고리에도 같은 방식으로 생성한다(UV에디터에서도 적용시키기 위함)

//View > Top :넘패드 7, front : 넘패드 1, right : 3, left : 9 
ortho : 7, Align view>Align Active Camera to view(ctrl + alt + 0), Align view to Active : shift + Numpad 7
```

`Hide 단축키 설정` ; 오브젝트, 메쉬(에디트)모드에 'h', 'shift + h', 'alt + h'

```
⓶Transform 단축키 설정
//메뉴의 transform > tralslate 단축키를 Alt + w로설정한다
//Preferences>Input에서 key-binding에서 ‘alt w’로 검색하여 기존의 Alt +w를(Clear Translate) Ctrl + w로 바꾼다)
//나머지 rotate, scale도 같은 방법으로 바꾼다
```

`Extrude : 기본 alt x` 
//메뉴설정 ; wm.call_menu 명령어>Name: VIEW3D_MT_edit_mesh_extrude(ctl +alt + x)

```
⓷mesh.knife_tool -> 단축키 k 
**블랜더 Knife 자동으로 잘라내는 에러
--Knife Tool Modal Map > Add New, Add Cut 선택 한 후 'Any'를 선택한다.(Left,아래 모든 기능이 체크되어있다)

⓸선택한 면만 잘림 단축키 추가 -> shift + k
//명령어:mesh.knife_tool -> only select 체크

⓹숏컷 만들기//오른클릭으로 안되는 메뉴의 숏컷
//Add New > wm.call_menu 입력하면 우측하단에 나오는 입력란에 메뉴를 써넣는다
(예 Hooks : VIEW3D_MT_hook)
**참고
//enum 배열 선택 토글은 wm.context_toggle_enum
//명령어 space_data.XXX  이후에 값을 입력한다
//pivot Point 전환
//command;wm.context_toggle_enum
///context Attributes;space_data.pivot_point/value1;CURSOR, value2;BOUNDING_BOX_CENTER

⓺블랜더WeightPaintMode_ShiftSelect
Short description of error
 In order to select a bone during weight paint mode, the "maya" shortcut is SHIFT+Click on the bone.
 But in order for this to work, I have to first unchecked the :
File/user preferences/input/3D view/Weight Paint/WeightPaintSampleGroup
 (Because it uses the same short cut)
And then, I have to add the following shortcut (like for blender shortcut):
- File/user preferences/input/3D view/3D view (global)/Add new => view3d.select + case shift + Click left + center + object
Because this initial shortcut does'nt seem to work :
File/user preferences/input/3D view/3D view (global)/Select or Deselect All (Shift Select Mouse)
//////////////////////////////////////////////////
셋드라이버 지정 시 Error:Python auto-exection disabled에러
// 이건 임시방편이고 아래 방법이 좋다///일단 파일로 저장한 후>Update Dependencies 버튼을 클릭하면 상단에 Auto-run disabled에서 Reload Trusted를 클릭하면 된다
////아래방법>>..User Preferences에서 이전버전에서는 System에 있었던 Auto Run Python Scripts가 File 탭에 존재하니..이걸 체크해주면 된다.

⓻mesh.shortest_path_pick 단축키 Mesh 카테고리에 추가한다음

⓼엣지 루프/링 선택 ctrl + alt + right/left M클릭

```
<br>

기타단축키
----------
```
Edge Crease 단축키 설정하기 -> '.'
타이어 만들기/link Dupe & Mirror 적용 > Ctrl + M

View All 단축키 'A' 3D커서 센터로 리셋 설정
//Preperence 에서 'Center' 체크한다

**Slide 단축키
//alt + W(무브)단축키 후 'G'키를 누르면 슬라이딩한다

Rip (Fill)
//단축키로 설정해 놓는다 'v', 립필 ->Alt + v
// Path 셀렉트>> 립필 >> G키 조합 GOOD

오클루드 지오메트리 버튼 토글 (뒤 쪽 버텍스 선택)
//Open preferences and under Input > 3d View > Mesh section click on the “Add” button.
 Enter " wm.context_toggle" into first empty input box.
 Map a key you wish to use instead of occlude geometry button.
 In the second input box bellow (Contex Attrib) add a line: space_data.use_occlude_geometry

Snap ; shift + s
Set origin ; shift + ctrl + alt + c 로(블렌더 단축키와 같게) 설정한다

Ctrl + B
//view3d.render_border
//Camera Only 체크 시 카메라뷰(ctrl + 0)에서만 박스렌더 지원

Weight Paint 모드 시 shift + 본 선택 토글(선택 시 토글 해제되지 않는 문제)
//3D View > Activate/Select 에서 Extend 체크를 풀고, Toggle Selection 체크한다

와콤설정 Circle Select Mode
//Brush Size : 마우스 휠 ->태블릿 휠 설정
//Left 버튼 : 선택, Middle 버튼 선택 : 해제

Maya Shift 선택 기능 에러
//Blender 기본 셀렉터 명령 view3d.select 으로 바꾼다(바꾸기보단 추가하는게 더 낫다^^)
//3D View의 Select or Deselect All 메뉴에서 Shift Select Mouse에
//기존 명령을 view3d.select 로 바꾼 후 Toggle Selection 체크한다

UV Editor 에서 3D커서(2D커서) 세팅
//Set 2D Cursor 설정을 바꾼다(기존 C + rightMouse) : uv.cursor_set   -Mouse : Action Mouse
UV Editor 에서 Lassor Select 방법 : Ctrl,Shift등 아무 조합키와 함께 가운데 버튼

F5 (마우스 커서 위치) 순간이동키^^
//properties Region/Tool Shelf/Header를 오른쪽(위)과 왼쪽(아래)으로 이동

Shading 모드 단축키 바꾸기(5,6)
첫번째 항목 Value : wm.context_toggle_enum(토글키 만들기)
Value : MATERIAL, TEXTURED(대문자)
Context Attribute : space_data.viewport_shade(반영할 속성은)

⓽스컬핑 브러시 단축키 설정
**Draw Curve(커브의 EditMode에서 베벨값, Shift+Right(ActionMouse)로 드랙. curve.draw, WaitForInput 체크X 
//paint.brush_select  
//가령 키보드 M에 마스크브러시를 설정한다면.
//Sculp Tool에서 마스크를 선택한다.
//Toggle 은 키를 반복해서 누르면 이전 브러시로 돌아간다.

스컬핑브러시 라소 마스크 단축키 설정
//paint.mask_lasso_gesture
//shift+ctrl+레프트마우스

//Dynatopo 와 Symmetry XYZ 단축키 설정하기
//sculpt.dynamic_topology_toggle(ctrl + D)//wm.context_toggle//tool_settings.sculpt.use_symmetry_x
Edge Crease 단축키 설정하기 -> '.'
타이어 만들기/link Dupe & Mirror 적용 > Ctrl + M

View All 단축키 'A' 3D커서 센터로 리셋 설정
//Preperence 에서 'Center' 체크한다

**Slide 단축키
//alt + W(무브)단축키 후 'G'키를 누르면 슬라이딩한다

Rip (Fill)
//단축키로 설정해 놓는다 'v', 립필 ->Alt + v
// Path 셀렉트>> 립필 >> G키 조합 GOOD

오클루드 지오메트리 버튼 토글 (뒤 쪽 버텍스 선택)
//Open preferences and under Input > 3d View > Mesh section click on the “Add” button.
 Enter " wm.context_toggle" into first empty input box.
 Map a key you wish to use instead of occlude geometry button.
 In the second input box bellow (Contex Attrib) add a line: space_data.use_occlude_geometry

Snap ; shift + s
Set origin ; shift + ctrl + alt + c 로(블렌더 단축키와 같게) 설정한다

Ctrl + B
//view3d.render_border
//Camera Only 체크 시 카메라뷰(ctrl + 0)에서만 박스렌더 지원

Weight Paint 모드 시 shift + 본 선택 토글(선택 시 토글 해제되지 않는 문제)
//3D View > Activate/Select 에서 Extend 체크를 풀고, Toggle Selection 체크한다

와콤설정 Circle Select Mode
//Brush Size : 마우스 휠 ->태블릿 휠 설정
//Left 버튼 : 선택, Middle 버튼 선택 : 해제

Maya Shift 선택 기능 에러
//Blender 기본 셀렉터 명령 view3d.select 으로 바꾼다(바꾸기보단 추가하는게 더 낫다^^)
//3D View의 Select or Deselect All 메뉴에서 Shift Select Mouse에
//기존 명령을 view3d.select 로 바꾼 후 Toggle Selection 체크한다

UV Editor 에서 3D커서(2D커서) 세팅
//Set 2D Cursor 설정을 바꾼다(기존 C + rightMouse) : uv.cursor_set   -Mouse : Action Mouse
UV Editor 에서 Lassor Select 방법 : Ctrl,Shift등 아무 조합키와 함께 가운데 버튼

F5 (마우스 커서 위치) 순간이동키^^
//properties Region/Tool Shelf/Header를 오른쪽(위)과 왼쪽(아래)으로 이동

Shading 모드 단축키 바꾸기(5,6)
첫번째 항목 Value : wm.context_toggle_enum(토글키 만들기)
Value : MATERIAL, TEXTURED(대문자)
Context Attribute : space_data.viewport_shade(반영할 속성은)

⓽스컬핑 브러시 단축키 설정
**Draw Curve(커브의 EditMode에서 베벨값, Shift+Right(ActionMouse)로 드랙. curve.draw, WaitForInput 체크X 
//paint.brush_select  
//가령 키보드 M에 마스크브러시를 설정한다면.
//Sculp Tool에서 마스크를 선택한다.
//Toggle 은 키를 반복해서 누르면 이전 브러시로 돌아간다.

스컬핑브러시 라소 마스크 단축키 설정
//paint.mask_lasso_gesture
//shift+ctrl+레프트마우스

//Dynatopo 와 Symmetry XYZ 단축키 설정하기
//sculpt.dynamic_topology_toggle(ctrl + D)//wm.context_toggle//tool_settings.sculpt.use_symmetry_x

```
![image](https://user-images.githubusercontent.com/30430227/130591252-a5b39f6e-0918-49b3-8dd0-9af8ab73b24e.png)

```
⓾Mesh Select Mode::
Edit 모드에서 마우스 오른버튼으로 3D커서를 사용하기 위해서는
Mesh>Call Menu 중에
Name 'VIEW3D_MT_edit_mesh_select_mode'를 비활성하거나 단축키를 바꾸면 된다
(블랜더 기본 단축키 Ctrl + Tab)

⓫Grease Pencil
//Sculpt strokes 단축키 설정한다 Shift + E

⓬노드 
연결 선 끊기
//Ctrl 홀드 상태에서 자른다
//Compositing Node에서 Ctrl +Shift 클릭 View 노드가 생기며 (랜더)이미지가 배경에 드롭한다
BackDrop 무브
//Node Editor(Global) > Background Image Move에서 Alt를 Ctrl로 바꾼다
//node.backimage_move

Node 자동연결
//연결할 노드들을 선택한 후 'F'

⓭텍스처페인트
텍스처페인트 Stroke MethodMode 단축키 설정 (블렌더 기본 e->)
//imagePaint 하위메뉴 생성
//wm.context_menu_enum, tool_settings.image_paint.brush.stroke_method

텍스처페인트 아이드로퍼 단축키(블렌더 기본 s; 마야기본 right Mouse)
//image Panit 하위메뉴
//paint.sample_color

텍스처페인트 시 Shadeless//display Mode : texture
//오른쪽 프로퍼티 메뉴에서 Shading탭에서 Shadeless체크

텍스처페인트 양방향 칠하기
//Option > Ccclude, Normal 체크를 푼다

특정영역만(마스킹) 칠하기
//Edit 모드 : 페이스 선택 > Texture Paint 모드에서 
```
![image](https://user-images.githubusercontent.com/30430227/130591345-cb9252ab-24df-4d11-9518-82ad2431eb89.png)

```
⓮Node Wrangler
//ctrl + shift + 클릭 : output
//ctrl + right Mouse Drag - 연결
//ctrl + t : 텍스처 맵 생성
//alt + right Drag : Node Mix(블렌더 단축키모드에서만 된다)

⓯트래킹 Solve : Create Plane Track 마커 이동단축키 R-마우스 설정
Clip>Clip Editor>Add New 후 
clip.slide_plane_marker 명령 입력 Mouse : Action 선택

⓰Grease Pencil
//Border Select - 기존 b -> 드랙
//Border Select >Type : Tweak/left/Any로 바꾼다
//브러쉬 사이즈 단축키
//Radial Control : B와 shift + B로 바꾼다
구리스펜 에티트모드 시 단축키
//스컬프트 툴 단축키 설정(shift + R-mouse)
//wm.context_menu_enum
//Context Attribute : tool_settings.gpencil_sculpt.tool(파이썬 명령라인)

구리스펜 Alt키 기능(전체선택) 해제
//Alt + L-Mouse키가 전체선택으로 기본설정되어 있다

⓱인터페이스 팁
//패널 드래그 : 패널 한번에 닫기
//Ctrl + 패널 클릭 :해당 패널만 열기
//Shift + 패널 클릭 : 패널 핀
//머티리얼 아이콘 드랙 : 머티리얼 적용
//여러 오브젝트를 동시에 조작 : 여러 오브젝트 선택 > Alt + 슬라이드 드랙, 모디파이 값 입력

⓲Video Sequence Editor에서 화면 프리징
//Speed Contrrol ; Multiply Speed : 0 ; Stretch to input strip length 체크 해제
//Strip : Slip Strip Control (블렌더 단축키 :s, 단축키 설정해준다)
클립 해상도로 세팅
//Video Sequence Editor > Strip > Set Render Size

다양한 사이즈 이미지 편집하기
//클립 선택 프로퍼티 > Image offset 체크 > Add > Effect Strip : Transform

Proxy
//타임라인 속성 탭에서 Proxy 체크 : 25%등 선택
//Strip > Rebuild Proxy
//비디오시퀀스에디터 속성 택에서 View Setting > Proxy render size에서 선택한다
```
<br>

문제해결
----------

`툴쉘프에서 생성 시 세팅 패널이 그레이로 비활성일 때`
//Globla Undo 체크

`IME를 사용하지 않습니다 문제..`
--제어판>시계,언어 및 국가별 옵션>언어>고급설정  바로가기 키 변경
입력언어간 ctrl + shift 설정을 '없음'으로 바꾼다

`UnDo 키가 안먹힐 때`..Preference 에서 Global Undo를 체크한다.

`Display Only Render 체크 시 물체가 사라지는 현상`
//실수로 Duplication 을 누르면 사라진다 -None로 바꾼다

`오토스무스 안먹히는 현상`
//Go to Properties editor > Data panel > Geometry Data and click on Clear Custom Split Normals Data to re-enable the angle setting.

`PreStyle 안먹힐 때`
//씬에 카메라가 없을 경우 카메라를 생성하면 된다

### blender2.79

```
# shift 조절자 드래그 XZ축 고정 이동(내 프리셋은 되지 않는다)
//view3d.manipulator > Planar Constraint 기능이다 ;; 기존 Manipulator에서 shift 조합키를 빼고, 
//새로운 Maniplator에서 Confirm on Release 와 Planar constraint를 체크한다
# Ctrl + Alt + C : 전체 데이터 셋 복사 xyz 복사
# Interface > Display : Scale
# UV tools 
# Cycle 프로젝트 라이트
# Cut Knife
# Particle Copy to other Object
```

`Armature`
//Recalculator 본의 축방향을 바꿈

`Vertex > ConnectVertex`
//더이상 나이프툴로 고생할 필요없다..나이프는 나이프로

`Node Wrangler Mix 안될 때`
//단축키 Node Editor > Mix Nodes 에서 Alt 체크를 풀면 Right 마우스로 기능하게된다지요

`Weight Transform`
//Source Layers : By Name

![image](https://user-images.githubusercontent.com/30430227/130591652-a191c48e-383d-4d4e-88cf-e1b744f3ae74.png)

`Bone 숨기기(Armature) 설정 바꿀 것`
//armature.hide
//단축키 설정 바꾸기(Pose 모드에서도 설정을 바꾼다)

`DopeSheet에서 색상 적용`
//Pose Mode Pose모양(Data) 탭에서 Bone Group 설정

![image](https://user-images.githubusercontent.com/30430227/130591729-c532924a-40bc-4074-873a-5409187b17e0.png)

`Driver>Expression`
radians(sin(frame/30))*180// 시간이 지남에 따라 +-180로 주기 회전한다



