Button
==========

Button Ripple Effect
--------------------

![image](https://user-images.githubusercontent.com/30430227/150300838-0b02da89-1c1f-4e81-a863-ff685e1878f4.png)

```
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


