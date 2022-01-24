Button
==========

컬러 
----
steelblue, dodgerblue, olive, navy, tomato, teal, violet, whitesmoke, azure, Midnightblue

Button Ripple Effect
--------------------

![image](https://user-images.githubusercontent.com/30430227/150300838-0b02da89-1c1f-4e81-a863-ff685e1878f4.png)

```
버튼 내부의 위치 찾기
addEventListener('click', e=>{
let x = e.clientX - e.target.offsetLeft
}
clientX: 좌측 벽에서 찍은 점까지의 X거리
target.offsetLeft: 좌측 벽에서 찍은 대상의 왼쪽까지 X거리

```

```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        *{
            text-decoration: none;
            box-sizing: border-box;
        }
        body{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            flex-direction: column;
            background: teal;
        }
        a{
            position: relative;
            display: inline-block;
            padding: 12px 100px;
            margin: 10px 0;
            border: 1px solid #000;
            color: white;
            font-size: 20px;
            letter-spacing: 2px;
            border-radius: 40px;
            background: linear-gradient(90deg, tomato, dodgerblue);
            overflow: hidden;
        }
        
        a:nth-child(2){
            background: linear-gradient(90deg, dodgerblue, tomato);
        }

        span{
            position: absolute;
            background: white;
            transform: translate(-50%,-50%);
            pointer-events: none;
            border-radius: 50%;
            animation: animate 1s linear infinite;
        }

        @keyframes animate{
            0%{
                width: 0;
                height: 0;
                opacity: 0.5;
            }
            100%{
                width: 500px;
                height: 500px;
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <a href="#">버어튼</a>
    <a href="#">버어튼</a>
</body>
<script>
    const buttons = document.querySelectorAll('a')
    buttons.forEach(btn=>{
        btn.addEventListener('click', function(e){
            let x = e.clientX - e.target.offsetLeft
            let y = e.clientY - e.target.offsetTop

            let ripples = document.createElement('span')
            ripples.style.left = x + 'px'
            ripples.style.top = y + 'px'
            this.appendChild(ripples)

            setTimeout(()=>{
                ripples.remove()
            },1000)
        })
    })
</script>
</html>
```

<br>

커서 Hover Event
----------------

![image](https://user-images.githubusercontent.com/30430227/150450583-f2474bfc-909f-40c7-9912-698d85d8ecb6.png)

```
커서 중심에 원을 두는 다른 방법
cursor.style.left = (e.pageX - cursor.clientWidth/2) + 'px'

pointer-events: none;
기본값: auto, none - 애니효과 X
```

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
            list-style-type: none;
            text-decoration: none;
        }

        body{
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        ul{
            position:relative;
            display: flex;
            flex-direction: column;
        }

        ul li a{
            position: relative;
            display: inline-block;
            margin: 10px 0;
            font-size: 4em;
            color: white;
            transition: 0.2s;
        }

        .cursor{
            position: fixed;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: white;
            transition: .2s;
            transform: translate(-50%, -50%);
            pointer-events: none;
            mix-blend-mode: difference;
        }

        ul li:hover ~ .cursor{
            transform: scale(6);
        }

    </style>
</head>
<body>
    <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Portfolio</a></li>
        <li><a href="#">Team</a></li>
        <li><a href="#">Contact</a></li>
        <div class="cursor"></div>
    </ul>
</body>
<script>
    const cursor = document.querySelector('.cursor')
    document.addEventListener('mousemove', (e)=>{
        cursor.style.left = e.pageX + 'px'
        cursor.style.top = e.pageY + 'px'
    })
</script>

</html>
```

<br>

색상 바꾸기 hue
-------------

![image](https://user-images.githubusercontent.com/30430227/150453781-5379e448-cc37-4166-912e-d3ad1326508d.png)

``
+ : 함수 반환값
    bg.style.backgroundColor = 'rgba('+randomColor()+','+randomColor()+','+randomColor()+','+randomColor()+')'
    bg.style.backgroundColor = `rgba( ${randomColor()},${randomColor()},${randomColor()},${randomColor()})` - `백틱 사용(=파이썬)
CSS - hue
    mix-blend-mode: hue;
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

        }

        body{
            overflow: hidden;
        }

        img{
            width: 100%;
        }

        #bg{
            position: absolute;
            top: 0;
            width: 100%;
            height: 100vh;
            mix-blend-mode: hue;
        }
    </style>
</head>
<body>
    <img src="./images/testhand.jpg" alt="">
    <div id="bg"></div>
</body>
<script>
    const bg = document.querySelector('#bg')
    function randomColor(){
        return Math.floor(Math.random()*255)
    }
    bg.addEventListener('click', ()=>{
        bg.style.backgroundColor = 'rgba('+randomColor()+','+randomColor()+','+randomColor()+','+randomColor()+')'
    })
</script>
</html>
```

<br>

Animate Sliding 메뉴
----------------------

![image](https://user-images.githubusercontent.com/30430227/150458394-32b49ea4-9985-4260-b02a-086c9fdc3c97.png)

```
width, top 이 없음을 확인!
        #marker{
            position: absolute;
            height: 50px;
            background: dodgerblue;
            border-radius: 5px;
            transition: 0.5s;
        }
```


![image](https://user-images.githubusercontent.com/30430227/150458151-fe8c4ec0-6c1e-4902-9b23-727829dba46d.png)
![image](https://user-images.githubusercontent.com/30430227/150458160-d8ff1b0f-3abe-4bb1-a9f3-232fbc6e6c0a.png)

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
            list-style: none;
            text-decoration: none;
        }

        body{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: midnightblue;
        }
        ul{
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        ul li a{
            position: relative;
            font-size: 2em;
            color: white;
            display: inline-block;
            padding: 0 20px;
        }
        #marker{
            position: absolute;
            height: 50px;
            background: dodgerblue;
            border-radius: 5px;
            transition: 0.5s;
        }
    </style>
</head>
<body>
    <ul>
        <div id="marker"></div>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Service</a></li>
        <li><a href="#">Portfolio</a></li>
        <li><a href="#">Team</a></li>
    </ul>
</body>
<script>
    const marker = document.querySelector('#marker')
    const items = document.querySelectorAll('ul li a')

    function indicator(e){
        marker.style.top = e.offsetTop+'px'
        marker.style.width = e.offsetWidth+'px'
    }

    items.forEach(item=>{
        item.addEventListener('mousemove', event=>{
            indicator(event.target)
        })
    })


</script>
</html>
```

<br>

온오프 
------

![image](https://user-images.githubusercontent.com/30430227/150486669-75008549-c7c5-4d76-955e-b984f31a2cf8.png)

```
옴푹 홈
box-shadow: inset 0 8px 60px rgba(0,0,0,0.5),inset 0 8px 8px rgba(0,0,0,0.5), inset 0 -4px 4px rgba(0,0,0,0.1);

원형 버튼
box-shadow: 0 8px 40px rgba(0,0,0,0.5), inset 0 4px 4px rgba(255,255,255,0.2), inset 0 -4px 4px rgba(255,255,255,0.2);
```

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
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: mue;
            transition: 0.5s;
            background: deepskyblue;
        }

        body.active{
            background: snow;
        }

        #toggle{
            position: relative;
            display: block;
            width: 320px;
            height: 160px;
            border-radius: 160px;
            background: darkslategray ;
            transition: 0.5s;
            box-shadow: inset 0 8px 60px rgba(0,0,0,0.5),inset 0 8px 8px rgba(0,0,0,0.5), inset 0 -4px 4px rgba(0,0,0,0.1);
            cursor: pointer;
        }

        #toggle.active{
            background: snow;
        }

        #toggle.active .indicator{
            left: 160px;
        }

        #toggle .indicator{
            position: absolute;
            width: 160px;
            height: 160px;
            top: 0;
            left: 0;
            background: linear-gradient(to bottom, dodgerblue, midnightblue);
            border-radius: 50%;
            transform: scale(0.9);
            box-shadow: 0 8px 40px rgba(0,0,0,0.5), inset 0 4px 4px rgba(255,255,255,0.2), inset 0 -4px 4px rgba(255,255,255,0.2);
            transition: 0.5s;
        }
    </style>
</head>
<body>
    <div id="toggle">
        <i class="indicator"></i>
    </div>
</body>
<script>
    const body = document.querySelector('body')
    const toggle = document.querySelector('#toggle')
    toggle.onclick = function(){
        toggle.classList.toggle('active')
        body.classList.toggle('active')
    }
</script>
</html>
```

<br>

3D Flip 카드 
------------

![image](https://user-images.githubusercontent.com/30430227/150494329-fccb7bc6-4f62-448a-995c-9bee7a634135.png)

```
3D 효과
transform-style: preserve-3d;
transform: perspective(2000px);
transform-origin: left;
transform: rotateY(-180deg);
z-index: 2;
```

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
            text-decoration: none;
        }
        body{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: teal;
        }
        .card{
            position: relative;
            width: 300px;
            height: 400px;
            background: white;
            transform-style: preserve-3d;
            transform: perspective(2000px);
            transition: 1s;
            box-shadow: inset 300px 0 50px rgba(0,0,0,0.15), 0 20px 20px rgba(0,0,0,0.15);
        }
        
        .card:hover{
            transform: perspective(2000px) translateX(50%);
            box-shadow: inset 300px 0 50px rgba(0,0,0,0.15), 0 10px 10px rgba(0,0,0,0.15);
            
        }
        
        .card:hover .cover{
            transform: rotateY(-180deg);
        }
        
        .card .cover{
            position: relative;
            width: 100%;
            height: 100%;
            background: white;
            z-index: 2;
            display: flex;
            justify-content: center;
            align-items: center;
            transform-style: preserve-3d;
            overflow: hidden;
            transition: 1s ease-in-out;
            transform-origin: left;
        }

        .card .cover::before{
            content: "";
            position: absolute;
            width: 10px;
            height: 150%;
            background: white;
            transform: rotate(36.5deg);
            box-shadow: 0 0 0 20px tomato;
            transition: 0.5s;
        }

        .card:hover .cover{
            transform: rotateY(-180deg);
        }

        .card:hover .cover::before{
            width: 0;
            box-shadow: 0 0 0 250px tomato;
            transform: rotate(143.5deg);
        }

        .card .cover img{
            max-width: 100%;
            z-index: 1;
        }

        .card .details{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            <!-- align-items: center; -->
            overflow: hidden;
            text-align: center;
        }

        .card .details h3{
            font-weight: 200;
            margin: 5px 0;
        }

        .card .details h2{
            font-size: 1.5em;
            color: tomato;
            font-weight: 600;
        }

        .card .details a{
            display: inline-block;
            padding: 8px 20px;
            background: dodgerblue;
            margin-top: 5px;
            letter-spacing: 1px;
            border-radius: 25px;
            font-weight: 500;
            color: white;
            font-weight: 600;
        }

        .card .cover img

    </style>
</head>
<body>
    <div class="card">
        <div class="cover">
            <img src="./images/4g3.png" alt="">
        </div>
        <div class="details">
            <div>
                <img src="./images/4g2.jpg" width="250" alt="">
                <h3>그런 나마에노 히또 시라나이</h3>
                <h2><sup>$</sup>4G2</h2>
                <a href="">Buy Now</a>
            </div>
        </div>
    </div>
</body>
</html>
```

<br>

Social Media Hover - with VanillaTilt.js
-----------------------------------

[font Awesome](https://fontawesome.com/)

![image](https://user-images.githubusercontent.com/30430227/150636018-007c76eb-fd8a-4252-b6fd-cf2b88afade4.png)

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
            box-sizing: border-box;
            list-style: none;
            text-decoration: none;
        }
        .socialMedia{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .sci{
            position: relative;
            display: flex;
        }
        .sci li a{
            position: relative;
            display: inline-block;
            width: 120px;
            height: 120px;
            background: snow;
            display: flex;
            justify-content: center;
            align-items: center;
            color: black;
            border-radius: 10px;
            margin: 24px;
            font-size: 4em;
            transform-style: preserve-3d;
            perspective: 500px;
            box-shadow: 0 25px 35px rgba(0,0,0, 0.2);
            transition: background 0.2s;
        }
        .sci li::before{
            content: attr(data-text);
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,calc(-50% + 120px));
            font-size: 14vw;
            pointer-events: none;
            font-weight: 700;
            transition: 0.5s;
            opacity: 0;
        }
        .sci li:hover::before{
            opacity: 0.1;
            transform: translate(-50%,calc(-50% + 150px));
        }
        .sci li a:hover{
            background: dodgerblue;
        }

    </style>
</head>
<body>
    <section class="socialMedia">
        <ul class="sci">
            <li data-text="Facebook" data-color="tomato"><a href="#">A</a>
            <li data-text="Youtube" data-color="olive"><a href="#">B</a>
            <li data-text="Naver" data-color="dodgerblue"><a href="#">C</a>
            <li data-color="teal"><a href="#">D</a>
            <li data-color="green"><a href="#">E</a>
        </ul>
    </section>
</body>
<script src="./vanilla-tilt.min.js"></script>
<script>
    let list =document.querySelectorAll('.sci li')
    let bg =document.querySelector('.socialMedia')
    list.forEach(elements=>{
        elements.addEventListener('mouseenter',event=>{
            let color = event.target.getAttribute('data-color')
            bg.style.backgroundColor = color
        })
    })
    VanillaTilt.init(document.querySelectorAll(".sci li a"),{
        max:25,
        speed:400,
        glare:true,
        "max-glare":1
    })
</script>
</html>
```

<br>

육각형 
------

![image](https://user-images.githubusercontent.com/30430227/150638190-6b5ceb11-dba8-4c45-94d5-70177ffd39d8.png)

[css-clip-path-generatot](https://www.cssportal.com/css-clip-path-generator/)

```
background: radial-gradient(rgba(0,0,0,0.5),transparent,transparent);
background: linear-gradient(45deg, dodgerblue, rgba(3,169,244,0.5));
clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
```

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
            box-sizing: border-box;
        }
        body{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container{
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }
        .container .hexagon{
            position: relative;
            width: 350px;
            height: 400px;
            margin: 50px 20px 70px;
        }
        .container .hexagon::before{
            content: '';
            position: absolute;
            bottom: -70px;
            width: 100%;
            height: 60px;
            background: radial-gradient(rgba(0,0,0,0.5),transparent,transparent);
            border-radius: 50%;
            transition: 0.5s;
        }

        .container .hexagon:hover::before{
            opacity: .5;
            transform: scale(0.8);
        }
        .container .hexagon .shape{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000;
            clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
        }
        .container .hexagon:hover .shape{
            transform: translateY(-30px);
        }
        .container .hexagon .shape img{
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
        }
        .container .hexagon .shape .content{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            text-align: center;
            background: linear-gradient(45deg, dodgerblue, rgba(3,169,244,0.5));
            color: white;
            opacity: 0;
            transition: 0.5s;
        }
        .container .hexagon:hover .shape .content{
            opacity: 1;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="hexagon">
            <div class="shape">
                <img src="./p01.jpg" alt="">
                <div class="content">
                    <div>
                        <h2>someone Famouse</h2>
                        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Laboriosam dicta debitis aperiam dolores libero saepe ullam id animi nemo voluptatibus.</p>
                    </div>
                </div>
            </div>
        </div>
        <div class="hexagon">
            <div class="shape">
                <img src="./p02.jpg" alt="">
            </div>
        </div>
        <div class="hexagon">
            <div class="shape">
                <img src="./p03.jpg" alt="">
            </div>
        </div>
    </div>
</body>
</html>
```

<br>

Icon Hover Effects
--------------------

[ionicons](https://ionic.io/ionicons)

![image](https://user-images.githubusercontent.com/30430227/150639475-e4691c48-a2ec-44f5-bb88-61acc999ffc5.png)

```
전체 클래스를 지우고 현재 요소에 클래스 추가
        list.forEach(item=>{
            item.classList.remove('active')
            this.classList.add('active')
```  


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
            box-sizing: border-box;
            list-style: none;
            text-decoration: none;
        }
        body{
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: midnightblue;
        }
        .navigation{
            position: relative;
            width: 350px;
            height: 70px;
        }
        .navigation ul{
            display: flex;
        }
        .navigation ul li{
            position: relative;
            width: 70px;
            height: 70px;
            z-index: 1;
            /* indicator 위로 */
        }
        .navigation ul li a{
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            text-align: center;
        }
        .navigation ul li a .icon{
            position: relative;
            line-height: 75px;
            transition: 0.5s;
            font-size: 30px;
        }
        .navigation ul li.active a .icon{
            font-size: 20px;
            transform: translateY(-6px);
        }
        .navigation ul li a .text{
            position: absolute;
            font-size: 12px;
            color: white;
            bottom: 20px;
            font-weight: 400;
            transition: 0.25s;
            transform: scale(0);
        }
        .navigation ul li.active a .text{
            transform: scale(1);
        }
        .indicator{
            position: absolute;
            left: 0;
            width: 70px;
            height: 70px;
            border-radius: 10px;
            transition: 0.5s;
        }
        .navigation ul li:nth-child(1).active ~ .indicator{
            background: tomato;
            box-shadow: 0 15px 25px tomato;
            transform: translateX(calc(70px*0));
        }
        .navigation ul li:nth-child(2).active ~ .indicator{
            background: tomato;
            box-shadow: 0 15px 25px tomato;
            transform: translateX(calc(70px*1));
        }
        .navigation ul li:nth-child(3).active ~ .indicator{
            background: tomato;
            box-shadow: 0 15px 25px tomato;
            transform: translateX(calc(70px*2));
        }
    </style>
</head>
<body>
    <div class="navigation">
        <ul>
            <li class="list active">
                <a href="#">
                    <span class="icon">
                        <ion-icon name="airplane-outline"></ion-icon>
                    </span>
                    <span class="text">About</span>
                </a>
            </li>
            <li class="list">
                <a href="#">
                    <span class="icon">
                        <ion-icon name="bicycle-outline"></ion-icon>
                    </span>
                    <span class="text">Home</span>
                </a>
            </li>
            <li class="list">
                <a href="#">
                    <span class="icon">
                        <ion-icon name="balloon-outline"></ion-icon>
                    </span>
                    <span class="text">Message</span>
                </a>
            </li>
            <div class="indicator"></div>
        </ul>
    </div>
</body>
<script>
    let list = document.querySelectorAll('.list')
    function setActiveClass(){
        list.forEach(item=>{
            item.classList.remove('active')
            this.classList.add('active')
        })
    }
    list.forEach(item=>{
        item.addEventListener('mouseover',setActiveClass)
    })
</script>
<script type="module" src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.esm.js"></script>
<script nomodule src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.js"></script>
</html>
```

<br>

Card Hover - Product
----------------------

![image](https://user-images.githubusercontent.com/30430227/150665588-194a5833-c259-461f-9b45-ee8593d0347b.png)
![image](https://user-images.githubusercontent.com/30430227/150665595-ec933ecd-22b3-4a8b-b334-b2185a748ff0.png)

```
clip-path: circle(65% at 0 100%); - 크기 at 위치xy
backdrop-filter: blur(15px) ;
transition: 0.5s ease-in-out;
visibility: visible; -반대 hidden
text-transform: uppercase;
```

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
            box-sizing: border-box;
            text-decoration: none;
        }
        section{
            padding: 100px 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: teal;
            overflow: hidden;
            border: 1px solid #000;
        }
        section::before{
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: red;
            clip-path: circle(65% at 100% -20%);
        }
        section::after{
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: dodgerblue;
            clip-path: circle(65% at 0 100%);
        }
        .container{
            position: relative;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            z-index: 1;
        }
        .container .card{
            position: relative;
            width: 300px;
            height: 400px;
            margin: 20px 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2); 
            backdrop-filter: blur(15px) ;
        }
        .container .card .imgBx{
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            transition: 0.5s ease-in-out;
            color: white;
        }
        .container .card:hover .imgBx{
            transform: translateY(-50px);
        }
        .container .card .imgBx img{
            max-width: 70%;
            margin: 0 0 20px;
            transition: 0.5s ease-in-out;
        }
        .container .card:hover .imgBx img{
            transform: translate(-20px,-40px) rotate(-25deg) scale(1.4);
        }
        .container .card .content{
            position: absolute;
            bottom: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            transition: 0.3s ease-in-out;
            opacity: 0;
            visibility: hidden;
        }
        .container .card:hover .content{
            opacity: 1;
            visibility: visible;
            transform: translateY(-30px);
        }
        .container .card .content .size,
        .container .card .content .color{
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 8px 20px;
        }
        .container .card .content h3{
            color: white;
            font-weight: 300;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-right: 10px;
        }
        .container .card .content .size span{
            display: inline-block;
            width: 20px;
            height: 25px;
            text-align: center;
            color: black;
            background: white;
            border-radius: 4px;
            margin: 0 5px;
            box-sizing: content-box;
            padding: 2px;
            transition: 0.5s;
            cursor: pointer;
        }
        .container .card .content .color span{
            width: 20px;
            height: 20px;
            background: red;
            border-radius: 50%;
            margin: 0 5px;
            border: 2px solid white;
            cursor: pointer;
        }
        .container .card .content .color span:last-child{
            background: green;
        }
        .container .card .content a{
            position: relative;
            top: 10px;
            display: inline-block;
            padding: 12px 30px;
            background: white;
            border-radius: 40px;
            text-transform: uppercase;
        }

    </style>
</head>
<body>
    <section>
        <div class="container">
            <div class="card">
                <div class="imgBx">
                    <img src="./kanna.png" alt="">
                    <h2>Kanna</h2>
                </div>
                <div class="content">
                    <div class="size">
                        <h3>Size :</h3>
                        <span>7</span>
                        <span>7</span>
                        <span>7</span>
                    </div>
                    <div class="color">
                        <h3>Color :</h3>
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>
                    <a href="#">Buy Now</a>
                </div>
            </div>
        </div>
    </section>
</body>
</html>
```
