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
