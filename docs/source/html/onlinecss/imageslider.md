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

<br>

버튼 슬라이드 
-------------

```
  user-select: none - 텍스트 마우스 드랙 선택 금지
  border-radius: 3px 0 0 3px; - 왼쪽 위에서 시계방향

```

![image](https://user-images.githubusercontent.com/30430227/151287377-35cba6b6-5e78-48a9-ac75-fb448bbe7ae8.png)

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    *{
      box-sizing: border-box;
    }
    .slider{
      max-width: 1000px;
      position: relative;
      margin: auto;
      border: 1px solid #000;
    }
    .slider .slide{
      display: none;
      animation: fade 1.5s;
    }
    @keyframes fade{
      from{opacity: .4;}to{opacity:1}
    }
    .prev, .next{
      cursor: pointer;
      position: absolute;
      top: 50%;
      width: auto;
      margin-top: -22px;
      padding: 16px;
      font-size: 18px;
      transition: 0.6s ease;
      border-radius: 0 3px 3px 0;
      user-select: none;
    }
    .next{
      right: 0;
      border-radius: 3px 0 0 3px;
    }
    .prev:hover, .next:hover{
      background: rgba(0,0,0,0.8);
    }
    .slide p{
      width: 100%;
      padding: 8px 12px;
      position: absolute;
      bottom: 8px;
      color: white;
      font-size: 15px;
      text-align: center;
    }
    .slide .num{
      padding: 8px 12px;
      position: absolute;
      top: 0;
      color: white;
      font-size: 12px;
    }
    nav{
      text-align: center;
    }
    nav .dot{
      display: inline-block;
      cursor: pointer;
      height: 15px;
      width: 15px;
      margin: 0 2px;
      background: lightgray;
      border-radius: 50%;
    }
    nav .dot:hover, span.active{
      background: slategray;
    }
    
  </style>
</head>
<body>
  <section class="slider">
    <div class="slide">
      <img src="./images/4g2.jpg" alt="">
      <div class="num">1 / 3</div>
      <p>Caption Text</p>
    </div>
    <div class="slide">
      <div class="num">1 / 3</div>
      <img src="./images/4g3.png" alt="">
      <p>Caption Text</p>
    </div>
    <div class="slide">
      <div class="num">1 / 3</div>
      <img src="./images/4g2.jpg" alt="">
      <p>Caption Text</p>
    </div>
    <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
    <a class="next" onclick="plusSlides(1)">&#10095;</a>
  </section>
  <nav>
    <span class="dot" onclick="currentSlide(1)"></span>
    <span class="dot" onclick="currentSlide(2)"></span>
    <span class="dot" onclick="currentSlide(3)"></span>
  </nav>
</body>
<script>
  let slideIndex =1;
  showSlides(slideIndex)
  //Next/previous controls
  function plusSlides(n){
    showSlides(slideIndex += n);
  }
  //thumbnail image controls
  function currentSlide(n){
    showSlides(slideIndex=n)
  }
  function showSlides(n){
    let i;
    const slides = document.querySelectorAll('.slide');
    const dots = document.querySelectorAll('.dot')
    if(n>slides.length){slideIndex =1}
    if(n<1){slideIndex=slides.length}
    for(const slide of slides){
      slide.style.display='none';
    }
    slides[slideIndex-1].style.display="block";

    for(const dot of dots){
      dot.classList.remove('active')
    }
    dots[slideIndex-1].classList.add('active')
  }
</script>
</html>
```

```
- 자동 슬라이드
<script>
  let slideIndex =0;
  showSlides()
 
  function showSlides(){
    let i;
    const slides = document.querySelectorAll('.slide');
    for(const slide of slides){
      slide.style.display="none";
    }
    slideIndex++;
    if(slideIndex > slides.length){slideIndex = 1}
    slides[slideIndex-1].style.display='block';
    setTimeout(showSlides, 2000);
  }
</script>
```
