Responsive 1
=============

![image](https://user-images.githubusercontent.com/30430227/151502178-0d27c579-0dff-40ed-acc9-8b571f09b3e1.png)
![image](https://user-images.githubusercontent.com/30430227/151502248-718c0cf3-96d4-43f8-ae8b-97628ec94c13.png)

[Font Awesome](https://www.bootstrapcdn.com/fontawesome/)

```
<i class="fas fa-bars"></i> // 삼선이미지

Font Awesome 박스로 보일 때 CSS
    @import url("//use.fontawesome.com/releases/v5.15.3/css/all.css");

   background-attachment:fixed;
   background-position: center;
```

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <style>
    @import url("//use.fontawesome.com/releases/v5.15.3/css/all.css");
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      list-style: none;
      text-decoration: none;
    }
    body{
      background: url(./images/minami.jpg) no-repeat;
      background-attachment:fixed;
      background-position: center;
      background-size:cover;
    }
    header{
      position: absolute;
      top: 0;
      left: 0;
      padding: 0 100px;
      background: black;
      width: 100%;
    }
    header .logo{
      height: 50px;
      line-height: 50px;
      float: left;
      color: white;
      font-size: 24px;
      font-weight: bold;
    }
    header nav{
      float: right;
    }
    header nav ul{
      display: flex;
    }
    header nav li{
      display: block;
    }
    header nav a{
      display: block;
      height: 50px;
      line-height: 50px;
      padding: 0 20px;
      color:  white;
    }
    header nav a:hover,
    header nav a.active
    {
      background: dodgerblue;
    }
    .menu-toggle{
      line-height: 50px;
      color: white;
      float: right;
      font-size: 24px;
      cursor: pointer;
      display: none;
    }
    @media(max-width: 991px){
      header{
        padding: 0 20px;
      }
      .menu-toggle{
        display: block;
      }
      header nav{
        position: absolute;
        width: 100%;
        height: 100vh;
        background: #333;
        top: 50px;
        left: -100%;
        transition: 0.5s;
      }
      header nav.active{
        left: 0;
      }
      header nav ul{
        display: block;
        text-align: center;
      }
      header nav ul li a{
        border-bottom: 1px solid rgba(0,0,0,.2);
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">LOGO</div>
    <nav>
      <ul>
        <li><a href="#" class="active">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Team</a></li>
        <li><a href="#">Portfolio</a></li>
        <li><a href="#">contact</a></li>
      </ul>
    </nav>
    <div class="menu-toggle"><i class="fas fa-bars"></i></div>
    
  </header>
</body>
<script>
  const menuToggle = document.querySelector('.menu-toggle');
  menuToggle.addEventListener('click',()=>{
    document.querySelector('nav').classList.toggle('active')
  })
</script>
</html>
```

<br>

