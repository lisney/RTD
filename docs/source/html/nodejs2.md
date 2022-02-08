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

  'babel-node' 에러시 - npm i @babel/node -g 설치
  
   ES6에는 __dirname 변수가 없다
    import path from 'path';
    const __dirname = path.resolve();
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
{"host":"localhost", "user","root", "password":"brush","database":"express_db"}

//require 사용하기 - JSON 파일 import 지원안한다(assert 로 잘 안된다)
import { createRequire } from "module";
const require = createRequire(import.meta.url);

const db_config = require("./db-config.json");

//사용하기 - 2.연결하기 내용 수정
const con = mysql.createConnection({
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






