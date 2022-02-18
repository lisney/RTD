Passport
========

1. app.js

![image](https://user-images.githubusercontent.com/30430227/154609195-70360437-5383-404b-b61d-cb656ec0d78d.png)
![image](https://user-images.githubusercontent.com/30430227/154609224-f06ddeab-fe47-43d0-ba73-048835199b14.png)

```
import express from "express";
const app = express();
import { router } from "./router.js";

import expressSession from "express-session";
import passport from "./passport.js";
import flash from "express-flash";

import { engine } from "express-handlebars";
app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

const port = 3000;

app.set("view engine", "hbs");

app.use(express.urlencoded({ extended: true }));
app.use(express.json());

//expressSession 미들웨어는 passport.session미들웨어 앞에 있어야한다
app.use(
  expressSession({
    secret: "my Key",//필수옵션, 세션 암호화
    resave: true,//변경사항 없어도 요청마다 세션 다시 저장
    saveUninitialized: true,//저장할 내용이 없더라도 uninitialized 상태의 세션을 저장
  })
);

app.use(passport.initialize());
app.use(passport.session());
app.use(flash());// 내부적으로 session을 이용하기 때문에 session미들웨어 아래에 위치

app.use("/", router);

app.listen(port, () => {
  console.log(`The server is running on port ${port} `);
});
```

<br>

2. /passport.js, /router.js 

```
import passport from "passport";

import { Strategy as LocalStrategy } from "passport-local";

passport.use(
  "local-login",
  new LocalStrategy(
    {
      usernameField: "username",//요청정보를 req.body.username 대신 username 로 받는다
      passwordField: "password",
      passReqToCallback: true,
    },
    (req, username, password, done) => {
    //done() 함수를 이용해서 로그인 성공/실패 상태를 처리한다
      console.log("passport의 local-login :", username, password);

      if (username != "kang" || password != "12345") {
        console.log("입력정보 불일치!");
        return done(null, false, req.flash("loginMessage", "비밀번호 불일치!"));
      }
      console.log("로그인 성공!");
      return done(null, {
        username: username,
        password: password,
      });
    }
  )
);

// (2) - 로그인 인증 성공 시 한 번만 실행
passport.serializeUser((user, done) => {
  console.log("serializeUser() 호출됨");
  console.log(user);//세션에 사용자 정보인 user를 저장, 보통은 user.id를 사용한다

  done(null, user);
});

 // (3) - 로그인 인증이 되어있는 경우, 요청할 때마다 실행
passport.deserializeUser((user, done) => {
//로그인 한 사용자가 들어올 때마다 deserializeUser가 실행된다(반복), 사용자는 user 정보로 사용자 식별한다
  console.log("deserializeUser() 호출됨");
  console.log(user);

  done(null, user);
});

export default passport;
```
```
import express from "express";
export const router = express.Router();

import passport from "./passport.js";

router.get("/login", (req, res) => {
  res.render("login", { title: "인덱스" });
});

router.post(
  "/login",
  passport.authenticate("local-login", {
  //"local" - 로컬 전략을 쓰겠다.(페이스북/구글 전략...)
    successRedirect: "/loginSuccess",
    failureRedirect: "/loginFail",
    failureFlash: true,
  })
);

router.get("/loginSuccess", (req, res) => {
  res.render("loginsuccess");
});

router.get("/loginFail", (req, res) => {
  res.render("loginFail");
});
```

<br>

인증 
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

<br>

Session 인증
------------

[참고사이트](https://millo-l.github.io/Nodejs-passport-session-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/)

`npm install express-session memorystore session-file-store express-mysql-session`

1. Memory 세션

![image](https://user-images.githubusercontent.com/30430227/153786786-d2b858ad-61c2-47e6-a463-272763c11315.png)

```
import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import { createRequire } from "module";

const require = createRequire(import.meta.url);

const session = require("express-session"); 
const MemoryStore = require("memorystore")(session);

// ES6 방식
// import session from 'express-session' 해도 된다
// import memorystore from 'memorystore'; const memoryStore = memorystore(session) 해도 된다


const __dirname = path.resolve();
const port = 3000;

const app = express();

app.use(
  session({
    secret: "secret key",
    resave: false,
    saveUninitialized: true,
    store: new MemoryStore({
      checkPeriod: 86400000,
    }),
    cookie: { maxAge: 86400000 },
  })
);

app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

app.get("/", (req, res) => {
  console.log(req.session);
  if (req.session.num === undefined) {
    req.session.num = 1;
  } else {
    req.session.num += 1;
  }
  res.send(`View: ${req.session.num}`);
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});
```

<br>

2. File 세션

![image](https://user-images.githubusercontent.com/30430227/153786933-fb1d8456-4580-42d9-8ca5-21ff5c711e41.png)

```
- session의 데이터를 파일 형태로 디스크에 저장
- DB보다는 속도가 빠르지만 memory 방식보다는 속도가 느리다. memory에 비해 디스크가 저장 공간이 훨씬 여유롭다는 장점
- session.save() 세션이 저장된 후에 실행되는 함수(파일 저장 속도가 느려 반응이 늦을 경우)

const FileStore = require("session-file-store")(session);

app.use(
  session({
    secret: "secret key",
    resave: false,
    saveUninitialized: true,
    store: new FileStore(),
  })
);

// ES6 방식
// import filestore from "session-file-store";
// const FileStore = filestore(session);

```

<br>

`MySQL 세션`

```
import express from "express";
const app = express();

import { engine } from "express-handlebars";

import session from "express-session";

// import filestore from "session-file-store";
// const FileStore = filestore(session);

import mysqlstore from "express-mysql-session";
const MySQLStore = mysqlstore(session);

// import { createRequire } from "module";
// const require = createRequire(import.meta.url);

// const FileStore = require("session-file-store")(session);

import path from "path";
const __dirname = path.resolve();

const port = 3000;

import dotenv from "dotenv";
dotenv.config();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

const options = {
  host: "localhost",
  port: 3306,
  user: "root",
  password: "brush",
  database: "session_test",
};

app.set("view engine", "hbs");

app.use(express.urlencoded({ extended: false }));
app.use(express.json());

app.use(express.static(__dirname));

app.use(
  session({
    key: "session_cookie_name",
    secret: "283hehksfuse7@dfd", // 쿠기 정보, 알아보기 힘들게 작성한다
    resave: false, // true하면 변경사항이 없을 시에도 세션을 저장한다
    saveUninitialized: false, // 새로 생성된 세션에 아무 작업이 없을 경우도 저장한다
    store: new MySQLStore(options),
  })
);

app.get("/count", (req, res) => {
  if (req.session.count) {
    req.session.count++;
  } else {
    req.session.count = 1;
  }
  res.send(`count : ${req.session.count}`);
});

app.get("/welcome", (req, res) => {
  if (req.session.displayName) {
    res.send(`
    <h1>Hello, ${req.session.displayName} </h1>
    <a href='/logout'>logout</a>
    `);
  } else {
    res.render("home");
  }
});

app.get("/logout", (req, res) => {
  console.log(req.session.displayName);
  //delete req.session.displayName;
  req.session.destroy(); // delete 와 같은 기능
  res.redirect("welcome");
});

const users = [];

app.post("/register", (req, res) => {
  const user = {
    username: req.body.username,
    password: req.body.password,
    displayName: req.body.displayName,
  };
  users.push(user);
  req.session.displayName = req.body.username;
  req.session.save(() => {
    //session.save() 세션이 저장된 후에 실행되는 함수
    console.log(users);
    res.redirect("/welcome");
  });
});

app.get("/register", (req, res) => {
  res.render("register");
});

app.post("/login", (req, res) => {
  const uname = req.body.username;
  const pwd = req.body.password;
  for (let i = 0; i < users.length; i++) {
    if (uname === users[i].username && pwd === users[i].password) {
      req.session.displayName = users[i].displayName;
      return res.redirect("/welcome");
    }
  }
  res.send('Who are you? <a href ="/login">login</a>');
});

app.get("/login", (req, res) => {
  res.render("login");
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});

```

<br>


3. Passport 세션

`sequelize 시퀄라이즈- nodejs에서 mysql을 쉽게 다룰 수 있도록 도와주는 라이브러리,ORM(Object-relational Mapping)-SQL없이 DB사용`

```
특별한 점이 있다면 passport를 app.use(passport.initialize())해서 반드시 초기화를 해야 한다는 점이다. 물론 세션을 사용하기 때문에 app.use(passport.session())도 반드시 초기화해야 한다.
- serializeUser란 로그인을 성공한 user의 정보를 session에 저장하는 함수이고,
- deserializeUser는 페이지에 방문하는 모든 client에 대한 정보를 req.user 변수에 전달해주는 함수이다. 따라서, req.user로 해당 user가 로그인을 한 유저인지 또한 어떤 user인지에 대한 정보를 각각의 요청들에서 넘겨받을 수 있게 된다.
```

```
import express from "express";
const app = express();

import passport from "passport";
import localstrategy from "passport-local";
const LocalStrategy = localstrategy.Strategy;
import crypto from "crypto";

import { engine } from "express-handlebars";

import mysql from "mysql";
import session from "express-session";
import mysqlstore from "express-mysql-session";
const MySQLStore = mysqlstore(session);
//페이스북, 트위터 같은 소셜 로그인이 아니라 local에서 로그인 기능 구현을 위해 사용

// import { createRequire } from "module";
// const require = createRequire(import.meta.url);

import path from "path";
const __dirname = path.resolve();

const port = 3000;

import dotenv from "dotenv";
dotenv.config();

const connection = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: process.env.DB_NAME,
  multipleStatements: true,
});
connection.connect((err) => {
  if (!err) {
    console.log("Connected");
  } else {
    console.log("Connection Failed");
  }
});

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

app.set("view engine", "hbs");

// 사용자 쿠키 생성, 다음에 사용자가 사이트를 방문할 때 쿠키를 확인하고 세션ID와 유효한지 검사
app.use(
  session({
    key: "session_cookie_name",
    secret: "session_cookie_secret",
    store: new MySQLStore({
      host: process.env.DB_HOST,
      port: port,
      user: process.env.DB_USER,
      database: "cookie_user",
    }),
    resave: false,
    saveUninitialized: false,
    cookie: {
      maxAge: 1000 * 60 * 60 * 24,
    },
  })
);

// Passport  초기화 및 session 연결
app.use(passport.initialize());
app.use(passport.session());

app.use(express.urlencoded({ extended: true }));
app.use(express.json());

app.use(express.static(__dirname));

// passport.serializeUser((user, done) => done(null, user));

// passport.deserializeUser(function (id, done) {
//   done(null, id);
// });

const customFields = {
  usernameField: "uname",
  passwordField: "pw",
};

//사용자 유효성 판단(사용자 로그인 시 호출), validPassword메서드 사용 해 MySQL id/pass와 비교한다
const verifyCallback = (username, password, done) => {
  connection.query(
    "select * from users where username =?",
    [username],
    (err, results, fields) => {
      if (err) return done(err);

      if (results.length == 0) {
        return done(null, false);
      }
      const isValid = validPassword(password, results[0].hash, results[0].salt);
      user = {
        id: results[0].id,
        username: results[0].username,
        hash: results[0].hash,
        salt: results[0].salt,
      };
      if (isValid) {
        return done(null, user);
      } else {
        return done(null, false);
      }
    }
  );
};

const strategy = new LocalStrategy(customFields, verifyCallback);
passport.use(strategy);

// serializeUser - 사용자의 정보 객체를 세션에 아이디로 저장
passport.serializeUser((user, done) => {
  console.log("inside serialize");
  done(null, user.id);
});

// deserializeUser - 세션에 저장한 아이디를 통해 사용자 정보 객체를 불러옴
passport.deserializeUser(function (userId, done) {
  console.log("deserializeUser" + userId);
  connection.query(
    "select * from users where id =?",
    [userId],
    (err, results) => {
      done(null, results[0]);
    }
  );
});

//로그인 시 입력한 암호를 암호화하여 DB암호와 비교, 같으면 true 반환
function validPassword(password, hash, salt) {
  var hashVerify = crypto
    .pbkdf2Sync(password, salt, 10000, 60, "sha512")
    .toString("hex");
  return hash === hashVerify;
}

//암호화(사용자 등록 시 호출), 먼저 암호패키지를 사용해 암호 salt를 생성한다>암호salt를 사용해 암호에 대한 hash를 생성
function genPassword(password) {
  var salt = crypto.randomBytes(32).toString("hex");
  var genhash = crypto
    .pbkdf2Sync(password, salt, 10000, 60, "sha512")
    .toString("hex");
  return { salt: salt, hash: genhash };
}

// 사용자가 인증되었는지 여부 확인, false를 반환하면 '/notAuthorized' 경로로 리디렉션된다
function isAuth(req, res, next) {
  if (req.isAuthenticated()) {
    next();
  } else {
    res.redirect("/notAuthorized");
  }
}

// 사용자가 관리자인지 여부 확인
function isAdmin(req, res, next) {
  if (req.isAuthenticated() && req.user.isAdmin == 1) {
    next();
  } else {
    res.redirect("/notAuthorizedAdmin");
  }
}

// 사용자 이름이 이미 데이터베이스에 있는지 확인, 존재하면 '/userAlreadyExists'로 그렇지 않으면 사용자를 등록한 다음'/login' 경로로 리디렉션
function userExists(req, res, next) {
  connection.query(
    "select * from users where username=?",
    [req.body.uname],
    (err, results, fields) => {
      if (err) {
        console.log("Error");
      } else if (results.length > 0) {
        res.redirect("/userAlreadyExists");
      } else {
        next();
      }
    }
  );
}

app.get("/", (req, res, next) => {
  res.send("<h1>Home</h1><p>Please <a href='/register'>register</a>");
});

app.get("/login", (req, res, next) => {
  res.render("login");
});

app.get("/logout", (req, res, next) => {
  req.logout();
  res.redirect("/protected-route");
});

app.get("/login-success", (req, res, next) => {
  res.send(
    '<p>You successfully logged in. --> <a href="/protected-toute">Go to protected route</a></p>'
  );
});

app.get("/login-failure", (req, res) => {
  res.send("You entered the wrong id/password.");
});

app.get("/register", (req, res) => {
  console.log("inside get");
  res.render("register");
});

app.post("/register", userExists, (req, res, next) => {
  console.log("Inside post");
  console.log(req.body.pw);
  const saltHash = genPassword(req.body.pw);
  console.log(saltHash);
  const salt = saltHash.salt;
  const hash = saltHash.hash;

  connection.query(
    "insert into users(username,hash,salt,isAdmin) values(?,?,?,0)",
    [req.body.uname, hash, salt],
    (err, results, fields) => {
      if (err) {
        console.log("Error");
      } else {
        console.log("Successfully Entered");
      }
    }
  );
  res.redirect("/login");
});

app.post(
  "/login",
  passport.authenticate("local", {
    failureRedirect: "/login-failure",
    successRedirect: "/login-success",
  })
);

app.get("/protected-route", isAuth, (req, res, next) => {
  res.send(
    '<h1>You are authenticated</h1><p><a href="/logout">Logout and reload</a></p>'
  );
});

app.get("/admin-route", isAdmin, (req, res, next) => {
  res.send(
    '<h1>You are admin</h1><p><a href="/logout">Logout and reload</a></p>'
  );
});

app.get("/notAuthorized", (req, res, next) => {
  console.log("Inside get");
  res.send(
    '<h1>You are not authorized to view the resource</h1><p><a href="/login">Retry Login</a></p>'
  );
});

app.get("/notAuthorizedAdmin", (req, res, next) => {
  console.log("Inside get");
  res.send(
    '<h1>You are not authorized to view the resource as you are not the admin of the page </h1><p><a href="/login">Retry to Login as admin</a></p>'
  );
});

app.get("/userAlreadyExists", (req, res, next) => {
  console.log("Inside get");
  res.send(
    '<h1>Sorry This username is taken</h1><p><a href="/register">Register with different username</a></p>'
  );
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});

```

```
* register.hbs

<div class="login">
    <h1>Register</h1>
    <form action="/register" method="post">
        <label for="username">
            <i class="bi bi-alarm"></i>
        </label>
        <input type="text" name="uname" placeholder="UserID" id="id">
        <label for="password">
            <i class="bi bi-mailbox2"></i>
        </label>
        <input type="password" name="pw" placeholder="Password" id="password">
        <small>Already a member ? <a href="/login">Go and log in</a> </small>
        <input type="submit" value="Register">
    </form>
</div>

* login.hbs
<div class="login">
    <h1>Login</h1>
    <form action="/login" method="post">
        <label for="username">
            <i class="bi bi-alarm"></i>
        </label>
        <input type="text" name="uname" placeholder="UserID" id="id">
        <label for="password">
            <i class="bi bi-mailbox2"></i>
        </label>
        <input type="password" name="pw" placeholder="Password" id="password">
        <small>Not a member yet <a href="/register">Join us</a> </small>
        <input type="submit" value="Login">
    </form>
</div>
```

<br>

Egoing Session
---------------

1. MultiUser 세션

`app.js`

```
import express from "express";
const app = express();

import { engine } from "express-handlebars";

import session from "express-session";

// import filestore from "session-file-store";
// const FileStore = filestore(session);

import mysqlstore from "express-mysql-session";
const MySQLStore = mysqlstore(session);

// import { createRequire } from "module";
// const require = createRequire(import.meta.url);

// const FileStore = require("session-file-store")(session);

import path from "path";
const __dirname = path.resolve();

const port = 3000;

import dotenv from "dotenv";
dotenv.config();

app.engine(
  "hbs",
  engine({
    extname: "hbs",
  })
);

const options = {
  host: "localhost",
  port: 3306,
  user: "root",
  password: "brush",
  database: "session_test",
};

app.set("view engine", "hbs");

app.use(express.urlencoded({ extended: false }));
app.use(express.json());

app.use(express.static(__dirname));

app.use(
  session({
    key: "session_cookie_name",
    secret: "283hehksfuse7@dfd", // 쿠기 정보, 알아보기 힘들게 작성한다
    resave: false, // true하면 변경사항이 없을 시에도 세션을 저장한다
    saveUninitialized: false, // 새로 생성된 세션에 아무 작업이 없을 경우도 저장한다
    store: new MySQLStore(options),
  })
);

app.get("/count", (req, res) => {
  if (req.session.count) {
    req.session.count++;
  } else {
    req.session.count = 1;
  }
  res.send(`count : ${req.session.count}`);
});

app.get("/welcome", (req, res) => {
  if (req.session.displayName) {
    res.send(`
    <h1>Hello, ${req.session.displayName} </h1>
    <a href='/logout'>logout</a>
    `);
  } else {
    res.render("home");
  }
});

app.get("/logout", (req, res) => {
  console.log(req.session.displayName);
  delete req.session.displayName;
  // req.session.destroy();
  res.redirect("welcome");
});

const users = [];

app.post("/register", (req, res) => {
  const user = {
    username: req.body.username,
    password: req.body.password,
    displayName: req.body.displayName,
  };
  users.push(user);
  req.session.displayName = req.body.username;
  req.session.save(() => {
    //session.save() 세션이 저장된 후에 실행되는 함수
    console.log(users);
    res.redirect("/welcome");
  });
});

app.get("/register", (req, res) => {
  res.render("register");
});

app.post("/login", (req, res) => {
  const uname = req.body.username;
  const pwd = req.body.password;
  for (let i = 0; i < users.length; i++) {
    if (uname === users[i].username && pwd === users[i].password) {
      req.session.displayName = users[i].displayName;
      return res.redirect("/welcome");
    }
  }
  res.send('Who are you? <a href ="/login">login</a>');
});

app.get("/login", (req, res) => {
  res.render("login");
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});
```

`register.hbs, home.hbs`

```
<div class="login">
    <h1>Register</h1>
    <form action="/register" method="post">
        <label for="username">
            <i class="bi bi-alarm"></i>
        </label>
        <input type="text" name="username" placeholder="UserID" id="id">
        <label for="password">
            <i class="bi bi-mailbox2"></i>
        </label>
        <input type="password" name="password" placeholder="Password" id="password">
        <input type="text" name="displayName" placeholder="displayName">
        <small>Already a member ? <a href="/login">Go and log in</a> </small>
        <input type="submit" value="Register">
    </form>
</div>
```
```
    <h1>Welcome</h1>
    <ul>
    <li><a href='/login'>Login</a></li>
    <li><a href='/register'>Register</a></li>
    </ul>

  <a href="/logout">logout</a>
```

<br>
