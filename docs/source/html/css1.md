
CSS
========

[Flex Froggy](https://flexboxfroggy.com/#ko)

[CSS레이아웃 입문서](https://developer.mozilla.org/ko/docs/Learn/CSS/CSS_layout/Introduction)

[Particle.js](https://github.com/VincentGarreau/particles.js/)

[Chart.js](https://www.chartjs.org/)

1. 가상요소 `:before`, `after`

```
.tab_type1 ul li a:before{
    content:"맛있는";
    width: 40px;
    padding: 3px 6px;
    margin: 0 5px;
    border-radius: 4px;
    background:red;
    text-align:center;
    color: white;
}

```
<img src="https://user-images.githubusercontent.com/30430227/73346127-b1142000-42c8-11ea-8db1-9b214669e73e.jpg">
<br>

2. list-style: none
```
리스트 스타일
*{
    padding:0;
    list-style: none;
}
```
<br>

3. margin-left: auto

```
왼 쪽 마진을 공유한다 
```
<img src="https://d2.naver.com/content/images/2018/12/helloworld-201811-flex_13.png">

https://d2.naver.com/helloworld/8540176#ch2

<br>

4. flex border collapse Tip

```
ul      { border-width: 2px  0   0  2px }
ul > li { border-width:  0  2px 2px  0  }
```
`border 속성 다음에 border-width가 놓어야 한다`
<br>

5. Div 속성 

`기본적으로 div는 가로너비(width)가 100% 지만, width 속성을 지정하지 않고 margin과 padding을 지정했을 때 이를 포함한 너비가 100%`

![image](https://user-images.githubusercontent.com/30430227/150628505-3902efed-b557-4714-8bc4-22686d9f771f.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box{
            width: 500px;
            border: 1px solid #000;
        }
        .box div{
            width: 100%;
            margin: 20px;
            padding: 20px;
            background: dodgerblue;
        }
    </style>
</head>
<body>
    <div class="box">
        <div>width 를 지정하지 않고 margin 과 padding  을 지정하면</div>
    </div>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/30430227/150628533-5e22c5e7-6734-43d2-b4a5-2cd91e7fc104.png)

<br>

6. Inline 속성

`width, height 적용 불가, inline 요소 하위에 block 요소를 가질 수 없음, `

<br>

7. Float 속성

```
어울림 효과 해지 - clear:both(left,right)
before와 :after에는 무조건 content:""; 속성이 들어가야 합니다.
그리고 display:block을 해줘야 clear:both가 작동합니다.
float은 "어울림" 이고 inline-block은 "글자처럼취급" 입니다. 
```

> http://placeimg.com/640/480/any

<img src="http://placeimg.com/640/480/any">

<br>

8. Modal Popup - target 선택자

![image](https://user-images.githubusercontent.com/30430227/150629353-a99c5d02-5952-446b-b59e-c4445d5fc1ff.png)
![image](https://user-images.githubusercontent.com/30430227/150629348-afcb37e5-9368-472b-a4ad-bdc4c9b88c19.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
            text-decoration: none;
        }
        #popup{
            display: none;
        }
        #popup:target{
            display: block;
        }
    </style>
</head>
<body>
    <a href="#popup" class="opener">클릭하세요</a>
    <div id="popup" class="layer">
        <h2>열려라</h2>
        <a href="#">닫혀라</a>
    </div>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/30430227/150629777-45e4399b-d176-48f0-a131-4859ddd1455c.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            list-style: none;
            text-decoration: none;
        }
        .layer{
            display: none;
            justify-content: center;
            align-items: center;
            background: dodgerblue;
            position: fixed;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
        }
        .layer .box{
            padding: 20px 20px 60px;
            width: 500px;
            background: white;
            position: relative;
        }
        .layer .close{
            position: absolute;
            right: 20px;
            bottom: 20px;
            display: block;
            background:#09F;
            color:#fff;text-align:center;
            padding:5px 20px;
            font-size:13px;
        }

        .layer:target{
            display: flex;
            animation: open 0.5s;
        }

        @keyframes open{
            from{opacity:0;} to {opacity:1;}
        }
    </style>
</head>
<body>
    <a href="#popup" class="opener">클릭하세요</a>
    <div id="popup" class="layer">
        <div class="box">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Inventore quibusdam nihil deserunt ratione optio nemo rem provident dicta facilis magni minima saepe,obcaecati eaque? Laudantium voluptatum iusto est beatae adipisci aliquam ex, doloribus blanditiis!
            <a href="#" class="close">닫혀라</a>
        </div>
    </div>
</body>
</html>
```

Pure CSS Parallax
-------------------
<br>

[`출처` https://www.hyungjoo.me/parallax-scroll원리](https://www.hyungjoo.me/parallax-scroll-%EC%9B%90%EB%A6%AC/)

1. HTML

```
<div id="title" class="slide header">
  <h1>Pure CSS Parallax</h1>
</div>

<div id="slide1" class="slide">
  <div class="title">
    <h1>Slide 1</h1>
    <p>Lorem ipsum dolor sit amet, in velit iudico mandamus sit, persius dolorum in per, postulant mnesarchum cu nam. Malis movet ornatus id vim, feugait detracto est ea, eam eruditi conceptam in. Ne sit explicari interesset. Labores perpetua cum at. Id viris docendi denique vim.</p>
  </div>
</div>

<div id="slide2" class="slide">
  <div class="title">
    <h1>Slide 2</h1>
    <p>Lorem ipsum dolor sit amet, in velit iudico mandamus sit, persius dolorum in per, postulant mnesarchum cu nam. Malis movet ornatus id vim, feugait detracto est ea, eam eruditi conceptam in. Ne sit explicari interesset. Labores perpetua cum at. Id viris docendi denique vim.</p>
  </div>
  <img src="https://lorempixel.com/640/480/abstract/6/">
  <img src="https://lorempixel.com/640/480/abstract/4/"> 
</div>

<div id="slide3" class="slide">
  <div class="title">
    <h1>Slide 3</h1>
    <p>Lorem ipsum dolor sit amet, in velit iudico mandamus sit, persius dolorum in per, postulant mnesarchum cu nam. Malis movet ornatus id vim, feugait detracto est ea, eam eruditi conceptam in. Ne sit explicari interesset. Labores perpetua cum at. Id viris docendi denique vim.</p>
  </div>
</div>

<div id="slide4" class="slide header">
    <h1>The End</h1>
</div>
```
<br>

2. CSS

```
@import url(https://fonts.googleapis.com/css?family=Nunito);

html {
  height: 100%;
  overflow: hidden;
}

body { 
  margin:0;
  padding:0;
	perspective: 1px;
	transform-style: preserve-3d;
  height: 100%;
  overflow-y: scroll;
  overflow-x: hidden;
  font-family: Nunito;
}

h1 {
   font-size: 250%
}

p {
  font-size: 140%;
  line-height: 150%;
  color: #333;
}

.slide {
  position: relative;
  padding: 25vh 10%;
  min-height: 100vh;
  width: 100vw;
  box-sizing: border-box;
  box-shadow: 0 -1px 10px rgba(0, 0, 0, .7);
	transform-style: inherit;
}

img {
  position: absolute;
  top: 50%;
  left: 35%;
  width: 320px;
  height: 240px;
  transform: translateZ(.25px) scale(.75) translateX(-94%) translateY(-100%) rotate(2deg);
  padding: 10px;
  border-radius: 5px;
  background: rgba(240,230,220, .7);
  box-shadow: 0 0 8px rgba(0, 0, 0, .7);
}

img:last-of-type {
  transform: translateZ(.4px) scale(.6) translateX(-104%) translateY(-40%) rotate(-5deg);
}

.slide:before {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  box-shadow: 0 0 8px 1px rgba(0, 0, 0, .7);
}

.title {
  width: 50%;
  padding: 5%;
  border-radius: 5px;
  background: rgba(240,230,220, .7);
  box-shadow: 0 0 8px rgba(0, 0, 0, .7);
}

.slide:nth-child(2n) .title {
  margin-left: 0;
  margin-right: auto;
}

.slide:nth-child(2n+1) .title {
  margin-left: auto;
  margin-right: 0;
}

.slide, .slide:before {
  background: 50% 50% / cover;  
}

.header {
  text-align: center;
  font-size: 175%;
  color: #fff;
  text-shadow: 0 2px 2px #000;
}

#title {
  background-image: url("https://placeimg.com/640/480/abstract/6/");
  z-index:2;
}

#title h1 {
 transform: translateZ(.25px) scale(.75);
 transform-origin: 50% 100%;

}

#slide1:before {
  background-image: url("https://placeimg.com/640/480/abstract/4/");
  transform: translateZ(-1px) scale(2);
}

#slide2 {
  background-image: url("https://lorempixel.com/640/480/abstract/3/");
  z-index:2;
}

#slide3:before {
  background-image: url("https://placeimg.com/640/480/abstract/5/");
  transform: translateZ(-1px) scale(2);
}

#slide4 {
  background: #222;
}
```
<br>

Animation 축약
---------------

```
   div {
        animation-name: myShorthand;
        animation-duration: 3s;
        animation-timing-function: ease-in-out;
        animation-delay: 1s;
        animation-iteration-count: 3;
        animation-direction: alternate;
    }
```

> div { animation: myShorthand 3s ease-in-out 1s 3 alternate; }

	@keyframes movingPara {
        from { margin-left: 100%; }
        to { margin-left: 0%; }

<br>


이어서 메뉴
----------

```
	<ul class="one">
    <li>메뉴1
        <ul class="two">
            <li>메뉴1-1</li>
            <li>메뉴1-2</li>
            <li>메뉴1-3</li>
        </ul>
    </li>
    <li>메뉴2
        <ul class="two">
            <li>메뉴2-1</li>
            <li>메뉴2-2</li>
            <li>메뉴2-3</li>
        </ul>
    </li>
    <li>메뉴3
        <ul class="two">
            <li>메뉴3-1</li>
            <li>메뉴3-2</li>
            <li>메뉴3-3</li>
        </ul>
    </li>
	</ul>
	
```
<br>

```
function handler(event){
    // 2단계. handler 의 함수를 작성. handler 함수가 호출이 되면 아래와 같은 행동을 하라.
    var $target = $(event.target);
        // 현재 클릭했던 요소가 뭔 요소인지 변수 $target 에 담는다.
    if($target.is("li")){
        // 만약에 $target 이 담고있었던 요소가 li 가 맞다면!
        $target.children().toggle();
            // 클릭했던 바로 그 li 의 자식 요소(.one li .two) 을 토글 시켜라.
    }
``` 
<br>

```
  *{margin:0;padding:0;}
li{list-style-type:none;text-align:center;}
.one{background-color:#ffddd6;padding:10px;*zoom:1;}
.one:after{content:'';display:block;clear:both;}
.one>li{float:left;background-color:#ffffd6;margin-right:10px;cursor:pointer;}
.two{background-color:#d6ffd9;padding:10px;}
.two>li{background-color:#dad6ff;}
}
```
<br>

```
$(".one").click(handler).find("ul").hide();
    // 1단계. one 라는 클래스를 가진 요소를 클릭하게 되면 handler 라는 함수를 동작하게 하라
    // .one 가 자식으로 가지고 있는 요소들 중에 ul 을 찾아 숨겨라 <- 브라우저가 시작하마자 동작
 ```
<br>

팁 2
----------

1. border-radius 찌그러짐
` border-radius: 3%/10% //가로가 긴 경우 가로 % 값을 작게준다`
<br>

2. Fieldset
 
```
<form> <fieldset> <legend>개인정보:</legend>
    <label>이름: <input type="text"></label><br> 
    <label>주소: <input type="text">
    </label><br> <input type="submit"> </fieldset> </form>

출처: https://webdir.tistory.com/318 [WEBDIR]
```
<br>

3. Input Type 선택

` input[type=text] `

<br>

4. clear both

```
div 블럭은 넓이를 얼마를 주던간에 아래로만 깔린다.//좌우 공간을 다 차지
float 속성을 주면 옆으로 나란히 배열된다.//텍스트의 경우는 블럭을 둘러싸게된다
블럭 줄바꿈(?)을 하는 기능이 clear이다// left clear는 왼쪽에 붙는 것을 제거(안 붙는다)
#slide ul:after{content:"";display:block;clear:both;} //이렇게하면 ul 다음 블럭부터는 줄을 바꾸어 시작한다
```
<br>
5. radio 버튼

```
name은 같고 id(채널)은 다르게한다
<input type="radio" name="pos" id="pos1" checked>
<input type="radio" name="pos" id="pos2">
<input type="radio" name="pos" id="pos3">
Label과 연동하기1 -for 사용
<label for="pos1">일번 선택</label>

Lable과 연동하기2 -라벨에 포함
<label><input...>일번 선택</label>

#pos1 :checked ~ ul // 라디오 채널(id) pos1이 선택되었을 때 뒤의 태그 ul을 선택하여 속성 변경//이미지 슬라이드로
```

6. 전체 코드
```
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <title>Document</title>
    </head>
    <body>
    <style>
      *{margin:0;padding:0;}
      ul,li{list-style:none;}
      #slide{height:300px;position:relative;overflow:hidden;}
      #slide ul{width:400%;height:100%;transition:1s;}
      #slide ul:after{content:"";display:block;clear:both;}
      #slide li{float:left;width:25%;height:100%;}
      #slide li:nth-child(1){background:#faa;}
      #slide li:nth-child(2){background:#ffa;}
      #slide li:nth-child(3){background:#faF;}
      #slide li:nth-child(4){background:#aaf;}
      #slide input{display:none;}
      #slide label{display:inline-block;vertical-align:middle;width:10px;height:10px;border:2px solid #666;background:#fff;transition:0.3s;border-radius:50%;cursor:pointer;}
      #slide .pos{text-align:center;position:absolute;bottom:10px;left:0;width:100%;text-align:center;}
      #pos1:checked~ul{margin-left:0%;}
      #pos2:checked~ul{margin-left:-100%;}
      #pos3:checked~ul{margin-left:-200%;}
      #pos4:checked~ul{margin-left:-300%;}
      #pos1:checked~.pos>label:nth-child(1){background:#666;}
      #pos2:checked~.pos>label:nth-child(2){background:#666;}
      #pos3:checked~.pos>label:nth-child(3){background:#666;}
      #pos4:checked~.pos>label:nth-child(4){background:#666;}
    </style>
    <div id="slide">
      <input type="radio" name="pos" id="pos1" checked>
      <input type="radio" name="pos" id="pos2">
      <input type="radio" name="pos" id="pos3">
      <input type="radio" name="pos" id="pos4">
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <p class="pos">
        <label for="pos1"></label>
        <label for="pos2"></label>
        <label for="pos3"></label>
        <label for="pos4"></label>
      </p>
    </div>
    </body>
    </html>
```
<br>

7. 자동슬라이드

```
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
        *{margin:0;padding:0;}
        ul,li{list-style:none;}
        .slide{height:300px;overflow:hidden;}
        .slide ul{width:calc(100% * 4);display:flex;animation:slide 8s infinite;} /* slide를 8초동안 진행하며 무한반복 함 */
        .slide li{width:calc(100% / 4);height:300px;}
        .slide li:nth-child(1){background:#ffa;}
        .slide li:nth-child(2){background:#faa;}
        .slide li:nth-child(3){background:#afa;}
        .slide li:nth-child(4){background:#aaf;}
        @keyframes slide {
          0% {margin-left:0;} /* 0 ~ 10  : 정지 */
          10% {margin-left:0;} /* 10 ~ 25 : 변이 */
          25% {margin-left:-100%;} /* 25 ~ 35 : 정지 */
          35% {margin-left:-100%;} /* 35 ~ 50 : 변이 */
          50% {margin-left:-200%;}
          60% {margin-left:-200%;}
          75% {margin-left:-300%;}
          85% {margin-left:-300%;}
          100% {margin-left:0;}
        }
      </style>
    </head>
    <body>
      <div class="slide">
        <ul>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
      </div>
    </body>
    </html>
```
<br>

8. Flex를 사용하는 방법

```
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Document</title>
      <style>
        *{margin:0;padding:0;}
        ul,li{list-style:none;}
        .slide{height:300px;overflow:hidden;position:relative;}
        .slide ul{width:calc(100% * 4);display:flex;transition:1s;}
        .slide li{width:calc(100% / 4);height:300px;}
        .slide li:nth-child(1){background:#ffa;}
        .slide li:nth-child(2){background:#faa;}
        .slide li:nth-child(3){background:#afa;}
        .slide li:nth-child(4){background:#aaf;}
        .slide input{display:none;}
        .slide .bullet{position:absolute;bottom:20px;left:0;right:0;text-align:center;z-index:10;}
        .slide .bullet label{width:10px;height:10px;border-radius:10px;border:2px solid #666;display:inline-block;background:#fff;font-size:0;transition:0.5s;cursor:pointer;}
        /* 슬라이드 조작 */
        #pos1:checked ~ ul{margin-left:0;}
        #pos2:checked ~ ul{margin-left:-100%;}
        #pos3:checked ~ ul{margin-left:-200%;}
        #pos4:checked ~ ul{margin-left:-300%;}
        /* bullet 조작 */
        #pos1:checked ~ .bullet label:nth-child(1),
        #pos2:checked ~ .bullet label:nth-child(2),
        #pos3:checked ~ .bullet label:nth-child(3),
        #pos4:checked ~ .bullet label:nth-child(4){background:#666;}
      </style>
    </head>
    <body>
      <div class="slide">
        <input type="radio" name="pos" id="pos1" checked>
        <input type="radio" name="pos" id="pos2">
        <input type="radio" name="pos" id="pos3">
        <input type="radio" name="pos" id="pos4">
        <ul>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
        <p class="bullet">
          <label for="pos1">1</label>
          <label for="pos2">2</label>
          <label for="pos3">3</label>
          <label for="pos4">4</label>
        </p>
      </div>
    </body>
    </html>
 ```
 <br>
 
9. float:left 대신 요소 나란히 배열하고 화면 센터에 놓는 방법

```
   .pagination a {
-    display: block;
+    display: inline-block;
     width: 30px;
     height: 30px;
-    float: left;
     margin-left: 3px;
     background: url(/images/structure/pagination-button.png);
 }
 -대신 + 라인을 사용한다
 ```
 <br>
 비교 슬라이더
 -------------
 
 ![image](https://user-images.githubusercontent.com/30430227/120735395-8291ff00-c525-11eb-8920-3865cbf69f4e.png)
```
 <style>
     *{
         margin: 0;
         padding: 0;
         box-sizing: border-box;
     }
     body{
         display: flex;
         justify-content: center;
         align-items: center;
         min-height: 100vh;
         background: #000;
     }
     .imgBox{
         position: relative;
         width: 442px;
         height: 500px;
         border: 3px solid white;
     }

     .imgBox textarea{
         position: absolute;
         top: 0;
         left: 0;
         width: 100%;
         max-width: 100%;
         height: 100%;
         background: url(../4g2.jpg) ;
         background-size: cover;
         resize: none;
         opacity: 0.4;
         filter: grayscale(1) blur(5px);
         outline: none;
     }

     .imgBox textarea:nth-child(2){
         opacity: 1;
         filter: grayscale(0) blur(0);
         width: 150px;
         border-right: 2px solid yellow;
         resize: horizontal;
     }
 </style>
</head>
<body>

    <div class="imgBox">
        <textarea readonly></textarea>
        <textarea readonly></textarea>
    </div>
```
