Menu
======

Dropdwon 
---------

![image](https://user-images.githubusercontent.com/30430227/150658665-047fe6d1-903f-4961-84f2-4dfe9c61bf02.png)

```
<div onclick="show('ReactJS')">ReactJS</div>
function show(anything){
        document.querySelector('.textBox').value=anything
    }
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
            color: 0;
            box-sizing: border-box;
        }
        body{
            display: flex;
            justify-content: center;
            min-height: 100vh;
            background: beige;
        }
        .dropdown{
            position: relative;
            margin-top: 100px;
            width: 300px;
            height: 50px;
        }
        .dropdown::before{
            content: '';
            position: absolute;
            right: 20px;
            top: 15px;
            width: 8px;
            height: 8px;
            border: 2px solid black;
            border-top: 2px solid white;
            border-right: 2px solid white;
            transform: rotate(-45deg);
            z-index: 100;
        }
        .dropdown.active::before{
            opacity: 22px;
            transform: rotate(-225deg);
        }
        .dropdown input{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
            background: white;
            border: none;
            border-radius: 10px;
            padding: 12px 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }
        .dropdown .option{
            position: absolute;
            top: 70px;
            width: 100%;
            border-radius: 10px;
            overflow: hidden;
            background: white;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            display: none;
        }
        .dropdown.active .option{
            display: block;
        }
        .dropdown .option div{
            padding: 12px 20px;
            cursor: pointer;
        }
        .dropdown .option div:hover{
            background: dodgerblue;
            color: white;
        }
    </style>
</head>
<body>
    <div class="dropdown">
        <input type="text" class="textBox" placeholder="Dropdown Menu">
        <div class="option">
            <div onclick="show('HTML')">HTML</div>
            <div onclick="show('CSS')">CSS</div>
            <div onclick="show('Javascript')">Javascript</div>
            <div onclick="show('ReactJS')">ReactJS</div>
        </div>
    </div>
</body>
<script>
    function show(anything){
        document.querySelector('.textBox').value=anything
    }
    let dropdown = document.querySelector('.dropdown')
    dropdown.onclick =()=>{
        dropdown.classList.toggle('active')
    }

</script>
</html>
```

<br>

Dropdown Profile
-------------------

![image](https://user-images.githubusercontent.com/30430227/150660316-8fd249e8-1aeb-4634-bad5-ce2d7410a820.png)
![image](https://user-images.githubusercontent.com/30430227/150660343-b74d3992-8b7b-45f2-a836-0efa02fa69c5.png)

```
min-height: 100vh; - 기본값을 정의(기본값은 0, min-width 기본값 100%)
border-radius: 50%; overflow: hidden; - overflow가 없으면 이미지 경계를 벗어난다
object-fit: cover; - 배경 채움 - fit(영역에 가득), cover(비율에따라 일부 짤림), fill(비율무시)
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
            background: teal;
        }
        .card{
            position: relative;
            width: 350px;
            height: 120px;
            padding: 20px;
            background: white;
            box-shadow: 0 50px 50px rgba(0, 0, 0, 0.2);
            overflow: hidden;
            transition: height 0.5s ease-in-out;
        }
        .card.active{
            height: 350px;
        }
        .card .content{
            display: flex;
            align-items: center;
        }
        .card .content .imgBx{
            position: relative;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            overflow: hidden;
        }
        .card .content .imgBx img{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .card .content h2{
            margin-left: 15px;
            font-size: 1.3em;
            color: midnightblue;
        }
        .card .content h2 span{
            font-size: 0.8em;
            font-weight: 400;
            color: gray;
        }
        .navigation{
            position: relative;
            top: 25px;
            border-top: 1px solid rgba(0, 0, 0, 0.2);
            padding: 20px 0;
            text-transform: uppercase;
        }
        .navigation li{
            margin: 15px 0;
        }
        .navigation li a{
            display: flex;
            align-items: center;
            color: darkcyan;
            font-size: 1.1em;
            transition: 0.2s;
        }
        .navigation li a:hover{
            color: midnightblue;
        }
        .toggle{
            position: absolute;
            right: 0;
            bottom: 0;
            width: 40px;
            height: 40px;
            background: slategray;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            z-index: 100;
        }
        .toggle p{
            color: white;
            transition: ease-in-out 0.5s;
        }
        .card.active .toggle p{
            transform: rotate(180deg);
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="content">
            <div class="imgBx">
                <img src="./p02.jpg" alt="">
            </div>
            <h2>Sagiri<br><span>MangaSense</span></h2>
        </div>
        <ul class="navigation">
            <li>
                <a href="#">🧨 Edit Profile</a>
            </li>
            <li>
                <a href="#">🎈 Inbox</a>
            </li>
            <li>
                <a href="#">🥽 Settings</a>
            </li>
        </ul>
        <div class="toggle">
            <p>▽</p>
        </div>
    </div>
</body>
<script>
    const card = document.querySelector('.card')
    const cardToggle = document.querySelector('.toggle')
    cardToggle.onclick = ()=>{
        card.classList.toggle('active')
    }
</script>
</html>
```

<br>

Accordion 메뉴 
-------------

![image](https://user-images.githubusercontent.com/30430227/150667456-86e0f886-9c88-463c-8eef-0eec63965fd1.png)

```
top: 50%;(부모 박스센터)  transform: translateY(-50%);(박스센터) - 세로 센터 위치 
overflow: hidden; overflow-y: auo;  - auto: Y방향 컨텐츠가 많을 경우 스크롤바 생성
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
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: skyblue;
        }
        .accordion{
            max-width: 400px;
        }
        .accordion .contentBx{
            position: relative;
            margin: 10px 20px;
        }
        .accordion .contentBx .label{
            position: relative;
            padding: 10px;
            background: teal;
            color: white;
            cursor: pointer;
        }
        .accordion .contentBx .label::before{
            content: '+';
            position: absolute;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
        }
        .accordion .contentBx.active .label::before{
            content: '-';
        }
        .accordion .contentBx .content{
            position: relative;
            background: white;
            height: 0;
            overflow: hidden;
            overflow-y: auo;
            transition: 0.5s;
            padding: 0 10px;
        }
        .accordion .contentBx.active .content{
            height: 150px;
            padding: 10px;
        }
    </style>
</head>
<body>
    <div class="accordion">
        <div class="contentBx">
            <div class="label">List One</div>
            <div class="content">
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur commodi eius nesciunt soluta dicta maiores quam aut dolore qui numquam.</p>
            </div>
        </div>
        <div class="contentBx">
            <div class="label">List Two</div>
            <div class="content">
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur commodi eius nesciunt soluta dicta maiores quam aut dolore qui numquam.</p>
            </div>
        </div>
        <div class="contentBx">
            <div class="label">List Three</div>
            <div class="content">
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur commodi eius nesciunt soluta dicta maiores quam aut dolore qui numquam.</p>
            </div>
        </div>
    </div>
</body>
<script>
    const contentBxs = document.querySelectorAll('.contentBx')
    contentBxs.forEach(contentBx=>{
        contentBx.addEventListener('click', ()=>{
            contentBx.classList.toggle('active')
        })
    })
</script>
</html>
```
