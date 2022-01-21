Button
==========

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
