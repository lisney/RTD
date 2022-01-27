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

<br>

Accordion 자동닫힘 
-------------------

![image](https://user-images.githubusercontent.com/30430227/151134191-660680d6-f927-4096-b38d-2128cdcb1050.png)

```
<html>
  <head>
    <meta charset="utf-8" />
    <title>Example App</title>
    <link rel="stylesheet" href="./style.css" />
    <style>
      *{
        margin: 0;
        padding: 0;
        list-style: none;
        text-decoration: none;
      }
      section{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%) ;
      }
      .menu{
        width: 300px;
        border-radius: 8px;
        overflow: hidden;
      }
      .item{
        border-top: 1px solid teal;
        overflow: hidden;
      }

      .btn{
        display: block;
        padding: 16px 20px;
        background: dodgerblue;
        color: white;
        position: relative;
      }
      .btn:before{
        content: '';
        position: absolute;
        width: 14px;
        height: 14px;
        background: dodgerblue;
        left: 20px;
        bottom: -7px;
        transform: rotate(45deg);
      }
      .smenu{
        background: darkslategray;
        overflow: hidden;
        transition: max-height 0.3s;
        max-height: 0;
      }
      .smenu a{
        display: block;
        padding: 16px 26px;
        color: white;
        margin: 4px 0;
        position: relative;
      }
      .smenu a:before{
        content: '';
        position: absolute;
        width: 6px;
        height: 100%;
        left: 0;
        top: 0;
        background: dodgerblue;
        transition: 0.3s;
        opacity: 0;
      }
      .smenu a:hover:before{
        opacity: 1;
      }

      .item:target .smenu{
        max-height: 10em;
      }


    </style>
  </head>
  <body>
    <section>
      <ul class="menu">
        <li class="item" id="profile">
          <a href="#profile" class="btn">🤍Profile</a>
          <div class="smenu">
            <a href="#">Posts</a>
            <a href="#">Picture</a>
          </div>
        </li>
        <li class="item" id="message">
          <a href="#message" class="btn">💌Messages</a>
          <div class="smenu">
            <a href="#">New</a>
            <a href="#">Sent</a>
            <a href="#">Spam</a>
          </div>
        </li>
        <li class="item" id="settings">
          <a href="#settings" class="btn">🔅Settings</a>
          <div class="smenu">
            <a href="#">Password</a>
            <a href="#">Language</a>
          </div>
        </li>
        <li class="item">
          <a href="#l" class="btn">💨Logout</a>
        </li>
      </div>
    </section>

  </body>
</html>
```



Modal Popup Box
------------------

![image](https://user-images.githubusercontent.com/30430227/150738040-2c17ee89-e247-4ea3-8e55-5189bac90a12.png)
![image](https://user-images.githubusercontent.com/30430227/150738075-9f09f2eb-e236-4a4e-b8f5-884a34c21fa0.png)

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
            background: dodgerblue;
        }
        .btn{
            position: relative;
            padding: 15px 20px;
            background: white;
            color: dodgerblue;
            cursor: pointer;
            letter-spacing: 2px;
            text-transform: uppercase;
            transition: 0.5s;
        }
        .btn:hover{
            letter-spacing: 4px;
        }
        #popup{
            position: fixed;
            top: -100%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 1000;
            background: white;
            width: 450px;
            padding: 80px 50px 50px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
            transition: 0.5s;
            visibility: hidden;
        }
        #popup.active{
            visibility: visible;
            top: 50%;
        }
        #popup .content{
            position: relative;
            width: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        #popup .content img{
            max-width: 80px;
        }
        #popup .content .inputBox{
            position: relative;
            width: 100%;
            margin-top: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        #popup .content .inputBox input{
            width: 100%;
            padding: 15px;
            outline: none;
            font-size: 18px;
            border: 1px solid rgba(0,0,0,0.2);
        }
        #popup .content .inputBox input[type="submit"]{
            max-width: 150px;
            background: dodgerblue;
            color: white;
            border: none;
        }
        .close{
            position: absolute;
            top: 30px;
            right: 30px;
            cursor: pointer;
        }

    </style>
</head>
<body>
    <a class="btn" onclick="popupToggle();">Subscribe Us</a>
    <div id="popup">
        <div class="content">
            <img src="./images/4g3.png" alt="">
            <h2>Join Our Newletter</h2>
    "editor.quickSuggestionsDelay": 1000,
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Totam blanditiis voluptatem repellendus aliquid, necessitatibus error dolore recusandae atque quam iste.</p>
            <div class="inputBox">
                <input type="email" placeholder="Enter Email">
            </div>
            <div class="inputBox">
                <input type="submit" value="Sign Up">
            </div>
        </div>
        <a class="close" onclick="popupToggle()">✖</a>
    </div>
</body>
<script>
    function popupToggle(){
        const popup = document.querySelector('#popup')
        popup.classList.toggle('active')
    }
</script>
</html>
```

<br>

Modal Popup - :target 방식
-----------------------

![image](https://user-images.githubusercontent.com/30430227/150750383-3493c3b2-eff8-41fb-af9f-b6dffc490741.png)
![image](https://user-images.githubusercontent.com/30430227/150750448-fd36a5cf-25e6-4ae8-8c34-0a63270258b8.png)

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
        .container{
            position: relative;
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            background: skyblue;
            transition: 0.5s;
            padding: 20px;
            z-index: 1;
        }
        .container .content{
            position: relative;
            max-width: 500px;
            background: white;
            padding: 10px;
        }
        .container .content img{
            margin: 0 auto;
            display: block;
        }
        .container .content a{
            position: relative;
            display: block;
            width: 100px;
            margin-top: 20px;
            background: #000;
            color: white;
        }

        .layer{
            position: absolute;
            top: 0;
            width: 100%;
            min-height: 100vh;
            background: rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(15px);
            z-index: 100;
            visibility: hidden;
            opacity: 0;
            transition: 0.5s;
        }
        .layer .box{
            position: absolute;
            top: 40%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 600px;
            padding: 50px;
            box-shadow: 0 5px 30px rgba(0,0,0,.3);
            background: white;
        }
        .layer:target{
            visibility: visible;
            opacity: 1;
        }


    </style>
</head>
<body>
    <section class="container">
        <div class="content">
            <h2>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Esse, molestias!</h2>
            <img src="./images/4g2.jpg" alt="">
            <a href="#popup">Read More</a>
        </div>
    </section>
    <section class="layer" id="popup">
        <div class="box">
            <h2>Lorem ipsum dolor sit amet consectetur adipisicing elit. Sint, expedita?</h2>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Eaque, sint!</p>
            <a href="#">Close</a>
        </div>
    </section>
</body>

</html>
```

<br>

Smooth Scroll
----------------

![image](https://user-images.githubusercontent.com/30430227/151125794-bfe9bc27-bdcf-405d-9e3a-dbba0392c90d.png)

```
ul>li*5>a[href="#sec$"]{Section $}
section#sec$[data-text="Section $"]{내용}*5

- data 속성, data-text="1"
        javascript 에서 접근 data-text
        css 에서 접근 attr(data-text)-내용, article[data-text='1']{ ... } -선택자
        
- 크롬에서 scroll-behavior 안먹힐 때 chrome://flags/#smooth-scrolling  하거나 Javascript
    <script>
      const links = document.querySelectorAll("ul a");

      for (const link of links) {
        link.addEventListener("click", clickHandler);
      }

      function clickHandler(e) {
        e.preventDefault();
        const href = this.getAttribute("href");

        document.querySelector(href).scrollIntoView({ behavior: "smooth" });
      }
    </script>
```

```
<html>
  <head>
    <meta charset="utf-8" />
    <title>Example App</title>
    <link rel="stylesheet" href="./style.css" />
    <style>
      *{
        margin: 0;
        box-sizing: border-box;
        text-decoration: none;
        list-style: none;
        scroll-behavior: smooth;
      }
     
      section{
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
      }
      section:nth-child(odd){
        background: tomato;
      }
      section:before{
        content: attr(data-text)
      }
      ul{
        width: 100%;
        height: 50px;
        background: slategray;
        position: fixed;
        top: 0;
        display: flex;
        justify-content: space-around;
      }
      ul a{
        color: white;
        line-height: 50px;
        font-weight: 800;
        text-transform: uppercase;
      }
    </style>
  </head>
  <body>
    <ul>
      <li><a href="#sec1">Section 1</a></li>
      <li><a href="#sec2">Section 2</a></li>
      <li><a href="#sec3">Section 3</a></li>
      <li><a href="#sec4">Section 4</a></li>
      <li><a href="#sec5">Section 5</a></li>
    </ul>

    <section id="sec1" data-text="Section 1">내용</section>
    <section id="sec2" data-text="Section 2">내용</section>
    <section id="sec3" data-text="Section 3">내용</section>
    <section id="sec4" data-text="Section 4">내용</section>
    <section id="sec5" data-text="Section 5">내용</section>

    <script>
    </script>
  </body>
</html>
```

Mega Menu
-----------

![image](https://user-images.githubusercontent.com/30430227/151158477-7d20b6b4-cd31-4ed3-9b27-7a3059f21685.png)

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
      box-sizing: border-box;
    }
    body{
      background: slategray;
    }
    nav{
      width: 100%;
    }
    .megaMenu{
      width: 100%;
      height: 60px;
    }
    .megaMenu ul{
      width: 100%;
      height: 100%;
      background: #000;
      text-align: center;
      line-height: 60px;
      position: relative;
    }
    .megaMenu ul li{
      display: inline-block;
      margin: 0 15px;
      padding: 0 15px;
    }
    .megaMenu ul li:hover{
      background: olive;
    }
    .megaMenu ul li a{
      color: white;
      text-transform: uppercase;
      font-weight: 800;
      letter-spacing: 5px;
      display: block;
    }
    .megaMenu ul li:hover a{
      color: gold;
    }
    .megaMenu ul li .subMenu{
      position: absolute;
      background: tomato;
      width: 100%;
      left: 0;
      top: 60px;
      padding: 25px 15px;
      display: flex;
      justify-content: space-around;
      line-height: 24px;
      visibility: hidden;
    }
    .megaMenu ul li:hover .subMenu{
      visibility: visible;
    }
    .megaMenu ul li .subMenu .col img{
      width: 250px;
      display: block;
    }
    .megaMenu ul li .subMenu p{
      color: white;
      margin-top: 15px;
    }
  </style>
</head>
<body>
  <nav>
    <div class="megaMenu">
      <ul>
        <li><a href="#">popular</a></li>
        <li>
          <a href="#">sports</a>
          <div class="subMenu">
            <div class="col">
              <img src="./images/4g2.jpg" alt="">
              <p>football is unconditional love</p>
            </div>
            <div class="col">
              <img src="./images/4g2.jpg" alt="">
              <p>football is unconditional love</p>
            </div>
            <div class="col">
              <img src="./images/4g2.jpg" alt="">
              <p>football is unconditional love</p>
            </div>
          </div>
        </li>
        <li><a href="#">tv shows</a></li>
        <li><a href="#">movies</a></li>
        <li>
          <a href="#">music</a>
          <div class="subMenu">
            <div class="col">
              <h4>the best way to predict the future is to invent it.</h4>
              <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Porro fugiat saepe exercitationem ducimus, tempore officia!</p>
            </div>
            <div class="col">
              <h4>the best way to predict the future is to invent it.</h4>
              <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Porro fugiat saepe exercitationem ducimus, tempore officia!</p>
            </div>
            <div class="col">
              <h4>the best way to predict the future is to invent it.</h4>
              <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Porro fugiat saepe exercitationem ducimus, tempore officia!</p>
            </div>
          </div>
        
        </li>
      </ul>
    </div>
  </nav>
    
</body>
</html>
```

<br>

Sign In 폼 
------------

```
      background: url(./images/minami.jpg) 50% 50% no-repeat; // 위치 50%
      display: table;
      outline: none; / Input
      border: 0; // 버튼
```

![image](https://user-images.githubusercontent.com/30430227/151346161-890792d2-38ef-4a86-b0fa-da1c314ff043.png)

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
      width: 100%;
      min-height: 100vh;
      background: url(./images/minami.jpg) 50% 50% no-repeat;
      background-size: cover;
      display: table;
    }
    .signin{
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);
      border: 1px solid rgba(255,255,255,0.3);
      border-radius: 5px;
      padding: 30px;
    }
    h2{
      margin: 30px 0;
      font-weight: lighter;
      color: white;
      font-size: 50px;
      text-align: center;
    }
    input{
      display: block;
      width: 320px;
      height: 50px;
      background: rgba(0,0,0,0.3);
      outline: none;
      border: 1px solid rgba(0,0,0,0.5);
      border-radius: 5px;
      font-weight: lighter;
      font-size: 14px;
      margin-bottom: 10px;
      padding-left: 10px;
    }
    button{
      width: 332px;
      height: 50px;
      font-size: 16px;
      background: #000;
      color: white;
      border: 0;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <section class="signin">
    <form action="">
      <h2>Sign In</h2>
      <input type="text" placeholder="Enter Username">
      <input type="text" placeholder="Enter Password">
      <button class="btn">Sign In</button>
    </form>
  </section>
</body>
</html>
```

