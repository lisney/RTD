NodeJs 2
========

1. Nodemon 설치

`npm i -g nodemon(글로벌로 설치)`

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

4. 



