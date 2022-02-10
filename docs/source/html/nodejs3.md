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
