Passport
========

1. app.js

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
    secret: "my Key",
    resave: true,
    saveUninitialized: true,
  })
);

app.use(passport.initialize());
app.use(passport.session());
app.use(flash());

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
      usernameField: "username",
      passwordField: "password",
      passReqToCallback: true,
    },
    (req, username, password, done) => {
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

passport.serializeUser((user, done) => {
  console.log("serializeUser() 호출됨");
  console.log(user);

  done(null, user);
});

passport.deserializeUser((user, done) => {
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
