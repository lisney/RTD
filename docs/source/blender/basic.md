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
//**텍스처의 Mapping:Coordinates->Generated 선택


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
//cycle 랜더 - **image node 생성> new image 연결 후 베이킹

`랜더링 시 firefiles(흰색 점들)제거`
//Render > Sampling : Clamp 값을 조정해본다


