NodeJs 3
==========

[부트스트랩](https://getbootstrap.com/docs/5.1/getting-started/introduction/)

[부트스트랩 아이콘CDN](https://icons.getbootstrap.com/#usage)

<br>

Dependencies Installation
----------------------

```
npm install express dotenv express-handlebars body-parser mysql
//dotenv - 단일 상황에 대한 보안값을 담은 단일 파일 .env
npm install --save-dev nodemon //nodemon start 로 실행한다 하지만
//노드몬을 npm start로 실행하기 위해 package.json를 다음과 같이 설정할 수 있다.
  "scripts": {
    "start": "nodemon app.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```
```
* package.json
  "type": "module"
```

<br>

![image](https://user-images.githubusercontent.com/30430227/153152900-0ce070ab-1a32-410b-b1a4-dfa5a1a4c2a4.png)

![image](https://user-images.githubusercontent.com/30430227/153152957-b7a1fd98-a780-41e2-80cc-4b261c47a6eb.png)

<br>

전체코드 
--------

```
*  .env
DB_HOST = localhost
DB_NAME = express_db
DB_USER = root
DB_PASS = brush
```

```
* app.js

import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import mysql from "mysql";
import dotenv from "dotenv";
dotenv.config();

import { createRequire } from "module";
const require = createRequire(import.meta.url);
const db_config = require("./db-config.json");

const con = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: process.env.DB_NAME,
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
    res.render("home", { result });
  });
});

app.get("/adduser", (req, res) => {
  res.render("add-user");
});

app.get("/viewuser/:id", (req, res) => {
  const sql = "select * from users where id = ?";
  con.query(sql, [req.params.id], (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.render("view-user", { result });
  });
});

app.post("/adduser", (req, res) => {
  const sql = "insert into users set ?";
  con.query(sql, req.body, (err, result, fields) => {
    if (err) throw err;
    console.log(result);
    res.redirect("/");
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

```
* views/layouts/main.hbs
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css">
</head>
<body>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <a href="/" class="navbar-brand">User Management system</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" area-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a href="/" class="nav-link active" aria-current="page" >Home</a>
          </li>
        </ul>

        <form action="/" class="d-flex" method="POST" novalidate>
          <input type="search" class="from-control me-2" placeholder="Search" name="search" aria-label="Search">
          <button class="btn btn-outline-light" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>

  <div class="container pt-5 pb-5">
    {{{body}}}
  </div>
</body>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
</html>

* views/partials/user-form.hbs
<div class="col-6">
    <div class="form-floating mb-3">
      <input type="text" class="form-control" id="floatingInput" value="{{this.id}}" placeholder="Id" name="id">
      <label for="floatingInput">아이디</label>
    </div>
  </div>
  <div class="col-6">
    <div class="form-floating mb-3">
      <input type="text" class="form-control" id="floatingInput" value="{{this.name}}" placeholder="Name" name="name">
      <label for="floatingInput">이름</label>
    </div>
  </div>
  <div class="col-6">
    <div class="form-floating mb-3">
      <input type="email" class="form-control" id="floatingInput" value="{{this.email}}" placeholder="email@email.com" name="email">
      <label for="floatingInput">이메일</label>
    </div>
  </div>

  <div class="col-12 d-grid">
    <button class="btn btn-primary" type="submit">Submit</button>
  </div>
  
* views/home.hbs
{{#if removedUser}}
<div class="alert alert-success alert-dismissible fade show" role="alert">
    User has been removed.
    <button class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
</div>
{{/if}}

<div class="row">
    <div class="col-6">
        <h1>Users</h1>
    </div>
    <div class="col-6 d-flex justify-content-end">
        <a href="/adduser" class="btn btn-primary align-self-center" type="button">+add user</a>
    </div>
</div>

<table class="table table-bordered">
    <thead class="thead-dark">
        <tr>
            <th scope="col">#</th>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col" class="text-end">Action</th>
        </tr>
    </thead>
    <tbody>
        {{#each result}}
        <tr>
            <th scope="row">{{this.id}}</th>
            <td>{{this.name}} </td>
            <td>{{this.email}} </td>
            <td class="text-end">
                <a href="/viewuser/{{this.id}} " type="button" class="btn btn-light btn-small">
                    <i class="bi bi-eye"></i>View
                </a>
                <a href="/edit/{{this.id}} " type="button" class="btn btn-light btn-small">
                    <i class="bi bi-pencil"></i>Edit
                </a>
                <a href="/delete/{{this.id}}" type="button" class="btn btn-light btn-small">
                <i class="bi bi-person-x"></i>Delete</a>
            </td>
        </tr>
        {{/each}}
    </tbody>
</table>

* views/add-user.hbs
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="/">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">New User</li>
  </ol>
</nav>

{{#if alert}}
<div class="alert alert-success alert-dismissible fade show" role="alert">
  {{alert}}
  <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
</div>
{{/if}}

<form class="row g-3 needs-validation" method="POST" action="/adduser" novalidate>
  {{> user-form}}
</form>

* views/edit-user.hbs
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="/">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">Edit User</li>
  </ol>
</nav>

{{#if alert}}
  <div class="alert alert-success alert-dismissible fade show" role="alert">
    {{alert}}
    <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
  </div>
{{/if}}

{{#each result}}
<form class="row g-3 needs-validation" method="POST" action="/update/{{this.id}}" novalidate> 
  {{> user-form}}
</form>
{{/each}}

* views/view-user.hbs
<nav aria-label="breadcrumb">
  <ol class="breadcrumb">
    <li class="breadcrumb-item"><a href="/">Home</a></li>
    <li class="breadcrumb-item active" aria-current="page">View User</li>
  </ol>
</nav>

<div class="view-user p-5">
  {{#each result}}
  <div class="row mb-5">
    <div class="col text-center">
      <h3>{{this.id}} {{this.name}}</h3>
    </div>
  </div>
  <div class="row">
    <div class="col">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">{{this.id}}</th>
            <td>{{this.name}}</td>
            <td>{{this.email}}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="row">
      <div class="col">
        <b>Comments</b>
      </div>
    </div>
    <div class="row">
      <div class="col">
        {{this.comments}}
      </div>
    </div>
  </div>
  {{/each}}
</div>

```

<br>

Nodejs-UserManagement-Express-Hbs-MySQL-main 샘플 사용법
------------------------------------------

[깃허브](https://github.com/RaddyTheBrand/Nodejs-UserManagement-Express-Hbs-MySQL)

[튜토](https://www.raddy.dev/blog/simple-user-management-system-nodejs-express-mysql-handlebards/)

```
* a.env
DB_HOST = localhost
DB_NAME = usermanagement_tut
DB_USER = root
DB_PASS = password

* install
$ npm install
$ npm start
```

<br>

회원가입, 로그인
--------------

[참조사이트](https://codeshack.io/basic-login-system-nodejs-express-mysql/)

![image](https://user-images.githubusercontent.com/30430227/153364585-74bccbce-b8a4-4a73-a321-1bedfa33bf71.png)

1. SQL

![image](https://user-images.githubusercontent.com/30430227/153357837-07dc307a-7902-4327-bdb5-23bdc246a530.png)

```
CREATE DATABASE IF NOT EXISTS `nodelogin` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
USE `nodelogin`;

CREATE TABLE IF NOT EXISTS `accounts` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `username` varchar(50) NOT NULL,
  `password` varchar(255) NOT NULL,
  `email` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

INSERT INTO `accounts` (`id`, `username`, `password`, `email`) VALUES (1, 'test', 'test', 'test@test.com');
```

<br>

2. .env

```
DB_HOST = localhost
DB_NAME = nodelogin
DB_USER = root
DB_PASS = brush
```

<br>

3. app.js, router.js(/routers/router.js)

```
import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import { createRequire } from "module";

const require = createRequire(import.meta.url);
const __dirname = path.resolve();
const port = 3000;

const app = express();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

app.set("view engine", "hbs");

app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

import { router } from "./routers/router.js";
app.use("/", router);

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});
```

```
import mysql from "mysql";
import session from "express-session";
import dotenv from "dotenv";
import express from "express";
export const router = express.Router();

dotenv.config();

const connect = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: process.env.DB_NAME,
});

router.use(
  session({
    secret: "secret",
    resave: true,
    saveUninitialized: true,
  })
);

router.use(express.urlencoded({ extended: true }));
router.use(express.json());

router.get("/", async (req, res) => {
  res.render("login");
});

router.post("/auth", (req, res) => {
  let username = req.body.username;
  let password = req.body.password;
  if (username && password) {
    connect.query(
      "select * from accounts where username = ? and password = ?",
      [username, password],
      (err, results, fields) => {
        if (err) throw error;
        if (results.length > 0) {
          req.session.loggedin = true;
          req.session.username = username;
          res.redirect("/home");
        } else {
          res.send("Incorrect Username and/or Password!");
        }
        res.end();
      }
    );
  } else {
    res.send("Please enter Username and Password!");
    res.end();
  }
});

router.get("/home", (req, res) => {
  if (req.session.loggedin) {
    res.send("Welcome back, " + req.session.username + "!");
  } else {
    res.send("Please login to view this page!");
  }
  res.end();
});

```

<br>

4. login.hbs

```
<div class="login">
    <h1>Login</h1>
    <form action="/auth" method="post">
        <label for="username">
            <i class="bi bi-alarm"></i>
        </label>
        <input type="text" name="username" placeholder="Username" id="username" required>
        <label for="password">
            <i class="bi bi-mailbox2"></i>
        </label>
        <input type="password" name="password" placeholder="Password" id="password" required>
        <input type="submit" value="Login">
    </form>
</div>
```

<br>

5. style.css

```
* {
  box-sizing: border-box;
}

body {
  background: slategray;
}

.login {
  width: 400px;
  background: white;
  box-shadow: 0 0 9px 0 rgba(0, 0, 0, 0.3);
  margin: 100px auto;
}
.login h1 {
  text-align: center;
  color: slategray;
  font-size: 24px;
  padding: 20px 0;
  border-bottom: 1px solid lightblue;
}
.login form {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding-top: 20px;
}
.login form label {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  background: dodgerblue;
  color: white;
}
.login form input[type="password"],
.login form input[type="text"] {
  width: 310px;
  height: 50px;
  margin-bottom: 20px;
  padding: 0 15px;
}

.login form input[type="submit"] {
  width: 100%;
  padding: 15px;
  margin-top: 30px;
  background: dodgerblue;
  border: 0;
  cursor: pointer;
  font-weight: bold;
  color: white;
  transition: 0.2s;
}
.login form input[type="submit"]:hover {
  background: deepskyblue;
}
```

<br>

회원가입
--------

1. MySQL Workbench

![image](https://user-images.githubusercontent.com/30430227/153522325-099819f6-a94d-41f8-9f1f-c07fc5ad69f1.png)
![image](https://user-images.githubusercontent.com/30430227/153522344-c095c648-e92a-4e6d-ab0e-ce57e79a18a8.png)

![image](https://user-images.githubusercontent.com/30430227/153522392-db35f09a-72c8-4c99-8131-12c8b1df0b59.png)
![image](https://user-images.githubusercontent.com/30430227/153522436-b9746fd8-0b1e-41ad-9777-4d19bf531452.png)

![image](https://user-images.githubusercontent.com/30430227/153522531-c5e747ec-fb1d-4ae0-8ae4-70b295606cca.png)
![image](https://user-images.githubusercontent.com/30430227/153522583-54084354-b543-4624-abe6-56f358a69356.png)

2. Session 기반 인증 방식

```
- 일반적으로 웹 서버는 HTTP. 즉, stateless 프로토콜을 사용하기 때문에 웹사이트에서 사용자가 로그인한 회원인지에 대한 인증을 관리하는 방안이 필요하다.
- 세션이란 일정 시간 동안 같은 사용자(정확하게 브라우저를 말한다)로 부터 들어오는 일련의 요구를 하나의 상태로 보고 그 상태를 일정하게 유지시키는 기술이라고 한다.
즉, 방문자가 웹서버에 접속해 있는 상태를 하나의 단위로 보고 세션이라고 칭한다.
```

```
* Session과 Cookie의 차이점
- 쿠키의 경우는 방문자의 정보를 방문자 컴퓨터의 메모리에 저장
- 정보를 방문자 메모리에 저장하는 것이 아닌 웹 서버가 세션 아이디 파일을 만들어 서비스가 돌아가고 있는 서버에 저장
- 세션은 Stateful 서버이다.
- Session 저장 위치는 Memory, File, DB 다(Memory가 속도가 가장 빠르다..)
```

```
* 작동방식
브라우저. 사용자가 로그인을 요청하고(id, pw 전달)
서   버. 유효하다면, 세션이 서버의 메모리 상에 저장(SessionId 저장), sessionId를 cookie에 담아 브라우저로 전달
브라우저.  모든 request에 cookie(sessionId)를 함께 전송
서   버. 브라우저가 보낸 sessionId를 키로 session 정보를 식별하고 유효하다면, 원하는 응답을 제공
```

```
* 장점
- 서버에서 클라이언트의 상태 확인이 용이, 클라이언트가 임의로 정보 변경 불가
* 단점
- 서버에서 클라이언트의 상태를 모두 유지하고 있어야 하므로 클라이언트 수에 따른 부하가 심하다.(확장성 떨어짐)
- 사용자가 많아지는 경우 세션의 관리가 어려워진다
- 멀티 디바이스 환경(모바일, 브라우저 공동 사용 등)에서 로그인 시 중복 로그인 처리가 되지 않음
```

<br>

3. JWT - Javascript Web Token

```
* 작동방식
- 서버는 클라이언트의 정보를 저장하지 않고, JWT의 발급과 매 요청마다 header에 넘어오는 access token의 유효성 검사만 진행한다.
- 클라이언트는 JWT를 local storage에 저장
- 서버가 클라이언트의 정보를 저장하지 않으므로 Stateless 서버이다.
```

<br>

4. OAuth 2.0

`OAuth 2.0은 로그인하지 않고도 제삼자에게 서비스를 제공할 수 있도록 하는 표준 사용자 인증 프로토콜이다.`

```
- google, facebook 등과 같은 서비스의 계정으로 제3의 서비스에 로그인하여 등록되어 있는 정보나 해당 사이트들(google, facebook 등)의 기능을 사용할 권한을 부여받는 표준 프로토콜이다.
- OAuth 2.0은 HTTPS 환경에서만 작동한다.
- token 인증 방식을 사용
```


