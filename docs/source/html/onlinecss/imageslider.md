Image Slider
===============

1. 반응형

![image](https://user-images.githubusercontent.com/30430227/151275995-894432f9-cc54-4df7-90f5-38bfd53acf3c.png)

```
  section.slider>.slide*4>p{Slide $}
  animation: slide 8s infinite; // 8초
  animation-delay: -1s; //슬라이드 각각 시간 차 -1s/1s/3s/5s(총 8초)
  
```
![image](https://user-images.githubusercontent.com/30430227/151276157-541e3481-9937-46f1-b91c-08617d412b59.png)

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body{
      width: 100%;
      min-height: 100vh;
      background: slategray;
    }
    .slider{
      width: 100%;
      height: 50%;
      background: olive;
      position: absolute;
      overflow: hidden;
    }
    .slider .slide{
      position: absolute;
      width: 100%;
      height: 100%;
      background: olive;
      animation: slide 8s infinite;
      overflow: hidden;
    }
    .slide:nth-child(1){
      animation-delay: -1s;
      background: url(./images/4g2.jpg);
      background-size:cover;
      background-position: center;
    }
    .slide:nth-child(2){
      animation-delay: 1s;
      background: url(./images/4g3.png);
      background-size:cover;
      background-position: center;
    }
    .slide:nth-child(3){
      animation-delay: 3s;
      background: url(./images/4g2.jpg);
      background-size:cover;
      background-position: center;
    }
    .slide:nth-child(4){
      animation-delay: 5s;
      background: url(./images/4g3.png);
      background-size:cover;
      background-position: center;
    }

    .slide p{
      font-size: 70px;
      min-height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
    }

    @keyframes slide{
      0% {left:100%; width: 100%}
      5% {left: 0%;}
      25% {left: 0;}
      30% {left: -100%; width: 100%}
      30.0001% {left: -100%; width: 0}
      100% { left:100%; width:0}
    }
    
  </style>
</head>
<body>
  <section class="slider">
    <div class="slide">
      <p>Slide 1</p>
    </div>
    <div class="slide">
      <p>Slide 2</p>
    </div>
    <div class="slide">
      <p>Slide 3</p>
    </div>
    <div class="slide">
      <p>Slide 4</p>
    </div>
  </section>
</body>
</html>
```
