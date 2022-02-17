Ego-study
===========

MultiUser 세션
--------------

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

`register.hbs`

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

`home.hbs`

```
    <h1>Welcome</h1>
    <ul>
    <li><a href='/login'>Login</a></li>
    <li><a href='/register'>Register</a></li>
    </ul>

  <a href="/logout">logout</a>
```

<br>

Passport 인증
--------------

```
app.js

import express from "express";
const app = express();

import { engine } from "express-handlebars";

import session from "express-session";

// import filestore from "session-file-store";
// const FileStore = filestore(session);

import mysqlstore from "express-mysql-session";
const MySQLStore = mysqlstore(session);

import { createRequire } from "module";
const require = createRequire(import.meta.url);

var passport = require("passport");
var LocalStrategy = require("passport-local").Strategy;

// const FileStore = require("session-file-store")(session);

// import * as passport from "passport";
// import { Strategy as LocalStrategy } from "passport-local";

import path from "path";
const __dirname = path.resolve();

const port = 3000;

import dotenv from "dotenv";
import res from "express/lib/response";
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

app.use(passport.initialize());
app.use(passport.session());

passport.serializeUser((user, done) => {
  done(null, user.username); // 로그인한 사용자의 세션 식별자로 user.username 를 저장한다(초기), 보통은 user.id를 사용한다
});
passport.deserializeUser((id, done) => {
  //로그인 한 사용자가 들어올 때마다 deserializeUser가 실행된다(반복), 사용자는 id정보(user.username)로 사용자 식별한다
  for (let i = 0; i < users.length; i++) {
    let user = users[i];
    if (user.username === id) {
      return done(null, user);
    }
  }
});

passport.use(
  new LocalStrategy((username, password, done) => {
    const uname = username; //req.body.username 대신 username 바로 받는다
    const pwd = password;
    for (let i = 0; i < users.length; i++) {
      let user = users[i];
      if (uname === user.username && pwd === user.password) {
        done(null, user); // done() 로그인 성공/실패 처리함수
        //성공 시 passport.serializeUser 콜백함수 done(null,user.id)가 실행, 실패 시 deserializeUser
      } else {
        done(null, false); //id/pass 틀릴 경우
      }
    }
    done(null, false);
  })
);

app.post(
  "/login",
  passport.authenticate("local", {
    //"local" - 로컬 전략을 쓰겠다.(페이스북/구글 전략...)
    successRedirect: "/welcome",
    failureRedirect: "/login",
    failureFlash: false, //실패 처리, 메시지등...
  })
);

app.get("/welcome", (req, res) => {
  if (req.user && req.user.displayName) {
    //req.user는 passport에서 생성된 객체,passport.deserializeUser() 에서 리턴
    res.send(`
    <h1>Hello, ${req.user.displayName} </h1>
    <a href='/logout'>logout</a>
    `);
  } else {
    res.render("home");
  }
});

app.get("/logout", (req, res) => {
  req.logout(); //passport의 logout 함수
  // delete req.session.displayName;
  // req.session.destroy();
  req.session.save(() => {
    //.save 메소드는 세션의 저장이 끝나면 실행된다
    res.redirect("welcome");
  });
});

const users = [];

app.post("/register", (req, res) => {
  const user = {
    username: req.body.username,
    password: req.body.password,
    displayName: req.body.displayName,
  };
  users.push(user);
  req.login(user, (err) => {
    //passport 의 login 메소드를 사용하여 로그인 처리
    req.session.save(() => {
      res.redirect("/welcome");
    });
  });
});

app.get("/register", (req, res) => {
  res.render("register");
});

// app.post("/login", (req, res) => {
//   const uname = req.body.username;
//   const pwd = req.body.password;
//   for (let i = 0; i < users.length; i++) {
//     if (uname === users[i].username && pwd === users[i].password) {
//       req.session.displayName = users[i].displayName;
//       return res.redirect("/welcome");
//     }
//   }
//   res.send('Who are you? <a href ="/login">login</a>');
// });

app.get("/login", (req, res) => {
  res.render("login");
});

app.listen(port, () => {
  console.log(`The Server is Running on Port ${port}`);
});
```

```
/auth/passport.js

import * as passport from "passport";
import { Strategy as LocalStrategy } from "passport-local";
// import { Strategy as NaverStrategy } from "passport-naver";
// import { Strategy as KakaoStrategy } from "passport-kakao";

import { User } from "../db/models";

export default (app) => {
  app.use(passport.initialize());
  app.use(passport.session());

  // (2) - 로그인 인증 성공 시 한 번만 실행
  passport.serializeUser((user, done) => {
    done(null, user.id); // 세션에 사용자 정보인 id를 저장
  });
  // (3) - 로그인 인증이 되어있는 경우, 요청할 때마다 실행
  passport.deserializeUser(async (id, done) => {
    // 세션에 저장되어 있는 id를 인자 값으로 전달받음
    try {
      const user = await User.findOne({
        where: {
          id,
        },
        raw: true,
      });
      done(null, user); // req.user 객체 생성
    } catch {
      done(null, false, {
        message: "서버에 문제가 발생했습니다. 잠시 후 다시 시도해 주세요.",
      });
    }
  });

  // (1) new LocalStrategy를 통해 로컬 전략을 세움
  passport.use(
    new LocalStrategy(
      {
        session: true, // 세션 저장 여부
        usernameField: "id", // form > input name
        passwordField: "password",
      },
      async (id, password, done) => {
        try {
          // 회원정보 조회
          const user = await User.findOne({
            where: {
              email: id,
            },
            raw: true,
          });

          // 회원정보가 없거나 비밀번호가 일치하지 않는 경우
          if (!user || user.password !== password) {
            done(null, false, {
              message:
                "존재하지 않는 아이디이거나 비밀번호가 일치하지 않습니다.",
            });
          } else {
            done(null, user); // 요청 정보가 일치하면, serializeUser로 user 전달
          }
        } catch {
          done(null, false, {
            message: "서버에 문제가 발생했습니다. 잠시 후 다시 시도해 주세요.",
          });
        }
      }
    )
  );
};

```

```
/auth/session.js
import session from "express-session";
import dotenv from "dotenv";

dotenv.config();

export default (app) => {
  app.use(
    session({
      secret: process.env.SESSION_SECRET, //필수옵션, 세션 암호화
      cookie: { maxAge: 1000 * 60 * 60 }, // 1 hour, 쿠키 유효기간 설정
      resave: false, //변경사항 없어도 요청마다 세션 다시 저장
      saveUninitialized: false, //저장할 내용이 없더라도 uninitialized 상태의 세션을 저장
    })
  );
};

```

<br>

로그인,로그아웃 
--------------

```
# 로그인 인증여부 /middlewares/auth.js
-req.isAuthenticated() 함수는 로그인이 되어있는 경우, true를 반환

export const isLoggedIn = (req, res, next) => {
  if (req.isAuthenticated()) {
    next();
  } else {
    res.redirect("/auth/login");
  }
};

export const isNotLoggedIn = (req, res, next) => {
  if (!req.isAuthenticated()) {
    next();
  } else {
    res.redirect("/");
  }
};
```

```
# 로그인 및 로그아웃 구현 /routes/auth.js

- 로그인 인증 요청에 대한 라우팅은 passport.authenticate() 미들웨어 함수를 사용합니다. 이는 'local' 인자 값을 주어 앞에서 작성한 new LocalStrategy() 를 통해 세운 로컬 전략의 함수를 호출합니다.
- 'local'이 아닌 소셜 로그인 관련 전략을 세웠다면,'kakao', 'naver'를 인자 값으로 넘겨줍니다.

import express from "express";
import passport from "passport";

import authController from "../controllers/auth";
import { isLoggedIn, isNotLoggedIn } from "../middlewares/auth";

const router = express.Router();

/* /auth */
router.get("/login", isNotLoggedIn, authController.displayLogin);

router.post(
  "/login",
  isNotLoggedIn,
  passport.authenticate("local", {
    successRedirect: "/", //성공 시 redirect 경로
    failureRedirect: "/auth/login", //실패 시 redirect 경로
    failureFlash: false, //실패 시 flash 메시지 출력 여부
  })
);

router.get("/logout", isLoggedIn, authController.logout);

export default router;
```

```
# 비즈니스 로직을 구현하기 위해 /controllers/auth.js

import express from "express";

const displayLogin = (req, res) => {
  res.render("login", { message: req.flash("error") });
};

const logout = (req, res) => {
  req.session.destroy();
  res.redirect("/");
};

export default {
  displayLogin,
  logout,
};
```

