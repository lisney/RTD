2D스타일
==========

물/불
------

### Basic

![image](https://user-images.githubusercontent.com/30430227/126256294-48ffeace-b998-4ad3-8063-bb26f7b836e3.png)

![image](https://user-images.githubusercontent.com/30430227/126256277-0b175de7-e776-4ec7-b7a9-eaaac2df7c35.png)

1. Voronoi
2. Gradient 생성 후 Color>MixRGB(SoftLight)
3. Texture Coordinate
4. MixShader Fac(검정부분 투명)

### 화염, 연기

![image](https://user-images.githubusercontent.com/30430227/126415400-0fd3f6e6-0041-4ad4-af19-6c665f245ad8.png)

![image](https://user-images.githubusercontent.com/30430227/126415438-f2087d0e-314c-4b35-9032-bbd20810981b.png)

> IcoSphere(Torus) > Subdivision > Displace 1~2회(Strength: 음수, Voronoi: DistanceSquared)

### 물결 1

![image](https://user-images.githubusercontent.com/30430227/126417036-d7ed6855-73ab-4e3b-9238-44719f9da560.png)

![image](https://user-images.githubusercontent.com/30430227/126417060-c2d4a67c-144b-4239-8a15-b3e1b1efdc12.png)

### 물결 2

![image](https://user-images.githubusercontent.com/30430227/126417586-0065f415-b4e6-4d24-a4dc-8316131ff260.png)

![image](https://user-images.githubusercontent.com/30430227/126417717-3991507c-8421-476b-9796-bb8d2a1e993c.png)

![image](https://user-images.githubusercontent.com/30430227/126417627-1533f8b5-2f86-4a37-a84f-439be02133a3.png)

> SeparateXYZ, MUsgraveTexture

### 물결 3

![image](https://user-images.githubusercontent.com/30430227/126418078-a78fd6cc-3a09-4539-888d-4c4ee6498f12.png)

![image](https://user-images.githubusercontent.com/30430227/126418129-3be017b0-0c97-49bd-b931-8e28157d3632.png)

> 잔물결 추가

### 파장 1 Voronoi

![image](https://user-images.githubusercontent.com/30430227/126263463-eef5000d-2244-4947-8fb3-4ebcf66c9fc9.png)

![image](https://user-images.githubusercontent.com/30430227/126263294-71e064eb-57fa-401e-900a-3255a8061ec5.png)

![image](https://user-images.githubusercontent.com/30430227/126263309-6538cbf5-0290-4b55-8021-a87c57391850.png)

### 파장 2 Wave

![image](https://user-images.githubusercontent.com/30430227/126264267-dd171e3f-7cab-42bd-8ec9-8bcba9825fa7.png)

![image](https://user-images.githubusercontent.com/30430227/126264306-7c09799a-59b9-421a-a46a-da1144199845.png)

### 파장 3 Gradient

![image](https://user-images.githubusercontent.com/30430227/126265471-37f6d06a-76a0-4926-8095-e36365a908b3.png)

![image](https://user-images.githubusercontent.com/30430227/126265561-d9b97a68-54c7-40ff-93b1-ec43f42936d6.png)


### 물결 반짝이 추가

![image](https://user-images.githubusercontent.com/30430227/126418841-199b47b3-437c-4eb7-a798-4e59205c47e7.png)

![image](https://user-images.githubusercontent.com/30430227/126418818-daade5f2-1bcc-453c-a60f-e75a07cf4d19.png)

### 물결 반짝이 애니 추가

![image](https://user-images.githubusercontent.com/30430227/126419076-aa8610d8-ca1f-4de4-ba39-060e85814d73.png)


![image](https://user-images.githubusercontent.com/30430227/126415613-26629353-7c2b-494b-bb34-1acab2fbbcaf.png)

> Fresnel, Gamma

![image](https://user-images.githubusercontent.com/30430227/126415787-70c11cbc-396b-40bd-81c3-b5c2c9a639d7.png)

> Animate

기초 이팩트
--------------

### 좌우 흔들림

![image](https://user-images.githubusercontent.com/30430227/126256235-db9a552e-65af-4879-9897-0b82c0857d3f.png)

![image](https://user-images.githubusercontent.com/30430227/126256205-d018d38d-8c75-4a7a-86dc-a8996ee73cbb.png)

1. Checker Texture
2. Separate - Combine
3. Wave, Gradient Texture Mix(Screen)


### Outline(Solidify)

![image](https://user-images.githubusercontent.com/30430227/126270984-602d99bc-c7d7-4d21-b669-164f207b55e7.png)

![image](https://user-images.githubusercontent.com/30430227/126271007-5c320315-9bde-414d-8ced-777a3f54bb50.png)

> solidify > Normal:flip, Material Offset: 1

![image](https://user-images.githubusercontent.com/30430227/126271121-843b957c-b8f6-4f08-a1cc-186f99d64aaa.png)

![image](https://user-images.githubusercontent.com/30430227/126271176-fd8241e1-420c-4f4f-8a1e-4cff5077cc7a.png)

> AlphaClip

![image](https://user-images.githubusercontent.com/30430227/126271256-dd4da045-9e40-48ab-bc05-504da4e155e6.png)

>BackfaceCulling

### 평면 얼굴
![image](https://user-images.githubusercontent.com/30430227/130608808-a6f88753-8e52-4a7a-8619-49ade63942c7.png)  
![image](https://user-images.githubusercontent.com/30430227/130609121-e5a3e172-fee6-4e24-84b7-ed3c98d79aec.png)

![image](https://user-images.githubusercontent.com/30430227/130608889-118fd5c8-ef3c-40c5-8741-138e278b813c.png)  
`복사할 면 선택`

![image](https://user-images.githubusercontent.com/30430227/130609029-21b01a6e-4c2f-4016-899c-1b8982462323.png)  
`붙여넣을 면 선택`



Water Ripple
-------------
![image](https://user-images.githubusercontent.com/30430227/133927833-f182b002-b082-438c-8958-066ea2642950.png)
![image](https://user-images.githubusercontent.com/30430227/133927846-f0f1ff1a-a6d4-4d2a-9da5-3294a1807b49.png)  

![image](https://user-images.githubusercontent.com/30430227/133927864-93932063-3fcc-4e94-9d4d-b8381857b41c.png)
![image](https://user-images.githubusercontent.com/30430227/133927870-a35e49ef-6454-48b3-bc82-d92424805928.png)  


심플 구름  
-----------
`Musgrave`  
![image](https://user-images.githubusercontent.com/30430227/133928242-f07ab0f6-b752-4039-a32e-73dcb0f98c39.png)  
![image](https://user-images.githubusercontent.com/30430227/133928261-fb442e79-4be5-43d9-99bc-43ffae94c651.png)  

![image](https://user-images.githubusercontent.com/30430227/133928318-3f25e256-92d7-43ef-a5b3-dac33031e573.png)
![image](https://user-images.githubusercontent.com/30430227/133928338-21cdd49a-571b-4da8-a503-af207e62a8f3.png)  

<br>

Ghibli Style 구름
---------------









