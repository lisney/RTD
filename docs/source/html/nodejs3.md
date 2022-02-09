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

전체코드 
--------

```
import express from "express";
import { engine } from "express-handlebars";
import path from "path";
import mysql from "mysql";
import dotenv from "dotenv";
import { createRequire } from "module";
const require = createRequire(import.meta.url);

dotenv.config();
// import 'dotenv/config.js';

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

app.use(express.urlencoded({ extended: true }));
app.use(express.json());
app.use(express.static(__dirname));
app.use((req, res, next) => {
  next();
});

const routes = require("./server/routes/user");
app.use("/", routes);

app.listen(port, () => {
  console.log(`Listening on port ${port}`);
});

nodnode;

```
