BabylonJS
============

모듈 Export/Import
--------------------

```
* import {}

- ap.js
const a = 1;
const b = 2;
export { a }; //a와 c는 {}로 import해야한다. 변수명이 같게 써야한다.
export const c = 3; //선언과 동시에 할당한 한 변수는 import 시 {}안에 써야한다
export default b; // b는 기본 변수, {}없이 받으며...변수명이 달라도(d) 괜찮다 

- main.js
import d, { a, c as e } from "./ap.js";
console.log(a, d, e);
```


Handlebard 간단 서버
--------------

```
**app.js
import express from "express";
import { engine } from "express-handlebars";

const app = express();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);
app.set("view engine", "hbs");
app.set("views", "./views");

app.get("/", (req, res) => {
  res.render("home");
});

app.listen(3000);


**/views/home.hbs
<h1>방어력에 올인합니다!</h1>


**/views/layouts/main.hbs
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>
  {{{body}}}
</body>
</html>
```

자바스크립트 
---------------

1.문자열 3총사

```
userEmail.indexOf('@') //문자열에서 @문자가 있으면 그 위치의 Index 값 반환
phoneNum.substr(4,9) //빼내기, 4번째 인덱스부터 9번째까지 반환(인수 9가 없으면 4이후 전부 반환)
phoneNum.split('-') //문자 '-'를 기준으로 분리한 요소를 배열로 반환
```

2. HTML DOM Node

.nextElementSibling(형제), .firstElementChild, .childNodes.item(3)=childNodes[3]=children[1],
.nextElementSibling, .parentNode
ChildNode[] VS Children[] : childNodes[]는 줄바꿈 노드도 포함, children은 태그요소만
firstChild VS firstElementChild : 전자는 element,text,comment Node 반환, 후자는 element만 반환(style변경 시 사용) 

![image](https://user-images.githubusercontent.com/30430227/125756044-7e205db3-4663-4b4d-a1d2-7a36add79b8d.png)

```
    <section>
        <p>금쪽같은 내새끼</p>
        <div class="parent">
            <div class="child one"></div>
            <div class="child two" onclick="onParent()"></div>
            <div class="child three"></div>
        </div>
    </section>
```
```
 <style>
     section{
         margin: 0 auto;
         width: 200px;
         height: 150px;
         display: flex;
         flex-direction: column;
         justify-content: left;
         align-items: center;
         border: 1px solid #000;
         background: orange;
     }
     .parent{
         width: 150px;
         height: 80px;
         border: 1px solid #000;
         background: olive;
         display: flex;
         justify-content: space-around;
         align-items: center;
     }
     .child{
         width: 30px;
         height: 50px;
         background: gold;
     }
     

 </style>
```
```
    <script>
        document.querySelector('.parent').firstElementChild.style.background='white'
        document.querySelector('.parent').childNodes.item(3).style.cursor='pointer'
        function onParent(){
        //event.target
            event.target.parentNode.style.background = 'black' //event.target 함수 실행한 요소
            event.target.nextElementSibling.style.background = 'red'
        }
    </script>
```



