NodeJs 2
========

1. Nodemon 설치

`npm i -g nodemon(글로벌로 설치), 실행 'nodemon start' - package.json main에 등록한 js파일 `

2. VScode Autocomplition
 
`npm install --save-dev @types/node`

3. package.json 

`npm init -y`

4. express - NodeJs 서버 프레임워크, handlebars - 템플릿엔진

`설치 - npm install express-handlebars`

5. express 가 bodyParser 모듈 내장 urlencoded, json 파서

```
    // app.use(bodyParser.urlencoded({extended:true})) bodyParser 모듈 불러올 필요없이
    app.use(express.urlencoded({extended:true}))
    app.use(express.json())
```

6. ES6 이상 문법 사용 - require 대신 import

```
   require 대신 ES6 import 사용하기 package.json 에  "type":"module" 추가
   기존 require 방식 사용 시 "type": "commonjs"로 명기할 수 있다.

  'babel-node' 에러시 - npm i @babel/node -g 설치
  
   ES6에는 __dirname 변수가 없다
    import path from 'path';
    const __dirname = path.resolve();
    
* Require 사용하기 
import { createRequire } from "module";
const require = createRequire(import.meta.url);
const db_config = require("./db-config.json");

* __dirname 사용하기
import path from 'path';
const __dirname = path.resolve();

* dotenv
import "dotenv/config.js";
또는
// loadEnv.js
import dotenv from 'dotenv';
dotenv.config()

// index.js
import './loadEnv';
import express from 'express';
let x = process.env.David;
console.log(x);

* import router file
export const myRouteHandler = async (req, res) => {
   ...
};
import { myRouteHandler } from "./myModule";
app.post('/exampleroute', myRouteHandler)
----------------------------------------
또는
//router.js
import express from 'express';
export const router = express.Router();

router.get("/", async (req, res) => {
  res.render("login");
});
//app.js
import { router } from "./router.js"; // .js 붙여줘야 인식?
app.use("/", router);

```




7. handldbars 신버전 데이터 전달

```
- 구버전을 사용하던가 Original JSON을 반환하는 '.lean()'옵션을 추가한다

router.get('/list',(req,res)=>{
    Employee.find((err,docs)=>{
        if(!err){
            res.render('employee/list',{
                list: docs
            })
        }
    }).lean() //lean 옵션 추가
})
```

8. Prettier Handlebars 파일에 적용하지 않기

```
  "[handlebars]": {
    "editor.formatOnSave": false,
    "editor.formatOnPaste": false
  }
  
 -특정 파일에 적용하지 않기 
  "prettier.disableLanguages": [
    "css"
]
```



<br>

손잡이 기초
----------

![image](https://user-images.githubusercontent.com/30430227/150886419-134eed43-46d9-4789-9fe2-4fb7dafe8488.png)

1. app.js 

```
import express from 'express';
import { engine } from 'express-handlebars';

const app = express();

app.engine('handlebars', engine());
app.set('view engine', 'handlebars');
app.set('views', './views');

app.get('/', (req, res) => {
    res.render('home');
});

app.listen(3000);
```

<br>

2. main.handlebars

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Example App</title>
</head>
<body>

    {{{body}}}

</body>
</html>
```

<br>

3. home.handlebars

```
<h1>Example App: Home</h1>
```

<br>

이전 버전 갱신
--------------

![image](https://user-images.githubusercontent.com/30430227/150892194-3f63963c-acc6-4715-b7ff-2d417762262a.png)

`app.js`

```
import express from 'express';
import { engine } from 'express-handlebars';
import path from 'path'

const __dirname = path.resolve()
//ES6부터는 __dirname 변수가 없다. path.resolve()는 현재 경로의 절대경로 반환, path.join()은 상대경로
const port = 3000

const app = express();

app.engine('hbs', engine({
    extname: 'hbs',
    defaultLayout:'layout', //기본 레이아웃인 main.hbs 대신 사용할 레이아웃명 
}));
app.set('view engine', 'hbs');
app.set('views', './views'); //기본 views폴더 대신 사용할 경로 지정시 사용

app.use(express.static(__dirname))
app.use((req,res,next)=>{
    next()
})

app.get('/', (req, res) => {
    res.render('index',{
        name:'Brush'
    });
});

app.listen(port, ()=>{
    console.log(`The server is running on Port ${port}`)
});
```

`index.hbs`

```
<h1>Example App: {{name}} </h1>
```

<br>

MySQL
------

1. 설치

`npm i mysql`

2. 연결하기 

```
import mysql from "mysql";

const con = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "brush",
});

con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
});

* 암호보안
//db-config.json
{"host":"localhost", "user":"root", "password":"brush","database":"express_db"}

//require 사용하기 - JSON 파일 import 지원안한다(assert 로 잘 안된다)
import { createRequire } from "module";
const require = createRequire(import.meta.url);

const db_config = require("./db-config.json");

//사용하기 - 2.연결하기 내용 수정 
const con = mysql.createConnection({ //con = connection
  host: db_config.host,
  user: db_config.user,
  password: db_config.password,
});
```

3. 쿼리 사용하기 - .query 메소드

```
* db 생성 - 생성 후 생성코드는 삭제
con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
  con.query("create database express_db", (err, result) => {
    if (err) throw err; //throw - 강제 예외처리
    console.log("database created");
  });
});

* db 연결
const con = mysql.createConnection({
  host: db_config.host,
  user: db_config.user,
  password: db_config.password,
  database: "express_db",
});

* 테이블 생성 
con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
  const sql =
    "create table users (id int not null primary key auto_increment, name varchar(255) not null, email varchar(255) not null)";
  con.query(sql, (err, result) => {
    if (err) throw err;
    console.log("table created");
  });
});

* MySQL 워크벤치를 이용해 데이터 입력

* 데이터 추출
con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
  const sql = "select * from users";
  con.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);//인덱스 0의 email만 보기 > console.log(result[0].email);
  });
});

* 브라우저로 보내기 
app.get("/", (req, res) => {
  const sql = "select * from users";
  con.query(sql, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.send(result);
  });
  
* 데이터 입력해보기
con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
  const sql = "insert into users(name,email) values('Kevin','k@ke.com')";
  con.query(sql, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
  });
});

```

<br>

4. 입력폼 작성

```
* index.hbs
<h1>입력폼</h1>
<form action="/" method="POST">
    <label for="">이름</label>
    <input type="text" name="name"><br>
    <label for="">메일</label>
    <input type="text" name="email"><br>
    <button type="submit">보내기</button>
</form>


* 브라우저에서 들어온 데이터 처리 미들웨어 - body-parser 기능 내장
app.use(express.urlencoded({extended:true}));
// app.js 이렇게 수정
app.get("/", (req, res) => {
  res.render("index", {});
});

app.post("/", (req, res) => {
  res.send(req.body);
});


* 데이터베이스에 Insert하기
//INSERT INTO table (a, b, c) VALUES (1,2,3)를 INSERT INTO table SET a=1, b=2, c=3 로 대체할 수 있다

app.post("/", (req, res) => {
  const sql = "insert into users set ?";//물음표 (?) 삽입하면 값 배열로 대체됨
  con.query(sql, req.body, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.send("등록이 완료"); //res.redirect("/") 해당 경로로 되돌아감
  });
});



* 템플릿 엔진 사용 - lean() 안써도 에러안난다^^
app.get("/", (req, res) => {
  const sql = 'select * from users';
  con.query(sql, (err,result,fields)=>{
    if(err) throw err;
    res.render('index',{users:result})
  })
});


//index.hbs
<table>
    <tr>
        <th>이름</th>
        <th>이메일</th>
        <th>수정</th>
        <th>삭제</th>
    </tr>
    {{#each users}}
    <tr>
        <td>{{this.name}} </td>
        <td>{{this.email}} </td>
        <td><a href="/edit/{{this.id}}">수정</a> </td>
        <td><a href="/delete/{{this.id}}">삭제</a> </td>
    </tr>
    {{/each}}
</table>
```

![image](https://user-images.githubusercontent.com/30430227/152928825-c5306584-89e0-4af3-8b5b-8bd0f5a20053.png)

<br>

5. 수정과 삭제

```
app.get("/delete/:id", (req, res) => {
  const sql = "delete from users where id = ?";
  con.query(sql, [req.params.id], (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.redirect("/");
  });
});

* edit.hbs
<h1>업데이트 폼</h1>

<form action="/update/{{user.0.id}}" method="POST">
    <label for="">이름</label>
    <input type="text" name="name" value="{{user.0.name}}"><br>
    <label for="">메일</label>
    <input type="text" name="name" value="{{user.0.email}}"><br>
    <button type="submit">업데이트</button>
</form>
```

6. 전체 코드

```
import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import mysql from "mysql";

import { createRequire } from "module";
const require = createRequire(import.meta.url);
const db_config = require("./db-config.json");

const con = mysql.createConnection({
  host: db_config.host,
  user: db_config.user,
  password: db_config.password,
  database: "express_db",
});

con.connect((err) => {
  if (err) throw err;
  console.log("Connected");
});

const __dirname = path.resolve();

const port = 3000;

const app = express();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
    defaultLayout: "main",
  })
);

app.set("view engine", "hbs");
app.set("views", "./views");

app.use(express.urlencoded({ extended: true }));
app.use(express.json());
app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

app.get("/", (req, res) => {
  const sql = "select * from users";
  con.query(sql, (err, result, fields) => {
    if (err) throw err;
    res.render("index", { users: result });
  });
});

app.get("/delete/:id", (req, res) => {
  const sql = "delete from users where id = ?";
  con.query(sql, [req.params.id], (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.redirect("/");
  });
});

app.get("/edit/:id", (req, res) => {
  const sql = "select * from users where id = ?";
  con.query(sql, [req.params.id], (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.render("edit-user", { result });
  });
});

app.post("/update/:id", (req, res) => {
  const sql = `update users set ? where id = ${req.params.id}`;
  con.query(sql, req.body, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.redirect("/");
  });
});

app.post("/", (req, res) => {
  const sql = "insert into users set ?";
  con.query(sql, req.body, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.redirect("/");
  });
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});



```




