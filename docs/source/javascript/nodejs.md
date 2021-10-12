NodeJS
=========

직원관리
---------

1. 'nondmon start'로 실행`

![image](https://user-images.githubusercontent.com/30430227/127253400-28e54c2e-1f4a-455d-8ec5-01dd8e5adbbf.png)
- "main":"server.js" 실행할 파일명 지정


2. express 신버전은 body-parser 내장되어 있어
```
    // app.use(bodyParser.urlencoded({extended:true})) bodyParser 모듈 불러올 필요없이
    app.use(express.urlencoded({extended:true}))
    app.use(express.json())
```

3. mongoose 매서드 기능 확장 문제 - handlebars 에러

` 구버전을 사용하던가 Original JSON을 반환하는 '.lean()'옵션을 추가한다 `
```
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

### 코딩 시작
![image](https://user-images.githubusercontent.com/30430227/127324134-a99b4f9f-fd67-4099-85e1-e0ec74b545c3.png)  
![image](https://user-images.githubusercontent.com/30430227/127324201-f6ebddc5-6a2a-44e5-97eb-b83f193aa940.png)

<br>
서버, 라우터 분리, DB 분리

` server.js `  

```
const express = require('express')

const path = require('path')

// const bodyParser = require('body-parser')

const hbs = require('express-handlebars')

const app = express()

require('./models/db')

app.get('/',(req,res)=>{
    res.send('Hello world')
})

//bodyParser
    // app.use(bodyParser.urlencoded({extended:true}))
    app.use(express.urlencoded({extended:true}))
    app.use(express.json())
    
    //handlebars
    app.set('views', path.join(__dirname,'/views/'))
    
    app.engine('hbs',hbs({
        extname:'hbs',
        defaultLayout:'layout',
        layoutsdir:__dirname+'/views/layouts/'
    }))
    
    app.set('view engine', 'hbs')
    
    
    app.listen(3000,()=>{
        console.log('Server is listening Port 3000')
    })
    
    //별도 라우터 사용하기
    const employeeRouter =require('./routers/employeeRouter')
    app.use('/employee', employeeRouter) // '/employee' 경로
```
<br>
라우터

`employeeController.js`
```
const express = require('express')
const mongoose = require('mongoose')
const Employee = mongoose.model('Employee')


const router = express.Router()
// router.use(express.urlencoded({extended:true}))
// router.use(express.json())

router.get('/',(req,res)=>{
    res.render('employee/addOrEdit',{
        viewTitle:"Insert Employee"
    })
})

// 직원 입력
router.post('/',(req,res)=>{
    if(req.body._id==""){
        insertRecord(req, res)
    }else{
        updateRecord(req, res)
    }
})

// 직원 리스트 보기
router.get('/list',(req,res)=>{
    Employee.find((err,docs)=>{
        if(!err){
            res.render('employee/list',{
                list: docs
            })
        }
    }).lean()
})

function insertRecord(req,res)
{
    let employee = new Employee()
    employee.fullName = req.body.fullName
    employee.email = req.body.email
    employee.mobile = req.body.mobile

    employee.save((err, doc)=>{
        if(!err){
            res.redirect('employee/list')
        }else{
            if(err.name=='ValidationError'){
                handleValidationError(err, req.body)
                res.render('employee/addOrEdit',{
                    viewTitle:'Insert Employee',
                    employee:req.body
                })
            }
            console.log('Error occured during record insertion'+ err)
        }
    })
}

router.get('/:id',(req,res)=>{
    Employee.findById(req.params.id,(err,doc)=>{
        if(!err){
            res.render('employee/addOrEdit',{
                viewTitle:'Update Employee',
                employee:doc
            })
        }
    }).lean()
})

router.get('/delete/:id',(req,res)=>{
    Employee.findByIdAndRemove(req.params.id,(err,doc)=>{
        if(!err){
            res.redirect('/employee/list')
        }else{
            console.log("An error occured during the Delete Process"+ err)
        }
    }).lean()
})

function handleValidationError(err,body){
    for(field in err.errors)
    {
        switch(err.errors[field].path){
            case 'fullName':
                body['fullNameError']=err.errors[field].message
                break

            case 'email':
                body['emailError'] = err.errors[field].message
                break

                default:
                    break
        }
    }
}

function updateRecord(req,res)
{
// new:true 업데이트 후 문서를 반환한다(doc), runValidators: ValidationError 에러 체크(구문에러)
    Employee.findOneAndUpdate({_id:req.body._id}, req.body,{new:true, runValidators:true},(err,doc)=>{
        if(!err){
            res.redirect('employee/list')
        }else{
            if(err.name=="ValidationError"){
                handleValidationError(err, req.body)
                res.render("employee/addOrEdit",{
                    viewTitle:"Uddate Employee",
                    employee:req.body
                })
                console.log('Error occured in Updating the records'+err)
            }
    })
}

module.exports = router
```
<br>
DB

`db.js, employee.model.js`
```
const mongoose = require('mongoose')

require('dotenv').config({path:'variables.env'})

// const url = "mongodb+srv://root:1234@education.8nfen.mongodb.net/myFirstDatabase?retryWrites=true&w=majority";

mongoose.connect(process.env.MONGODB_URL,{useNewUrlParser:true, useUnifiedTopology: true},(err) => {
    if(!err){ console.log("MongoDB Connection Succeeded");}
    else{
        console.log("An Error Occured");
    } 
})

require('./employee.model');
```
```
const mongoose = require('mongoose')
const validator = require('email-validator')

const employeeSchema = new mongoose.Schema({
    fullName:{
        type:String,
        required:'This field is required'
    },
    email:{
        type:String
    },
    mobile:{
        type:String
    }
})

// custom validation for email

employeeSchema.path('email').validate((val)=>{
    return validator.validate(val)
},'Invalid Email')


mongoose.model('Employee', employeeSchema)

```
<br>
hbs  layout, addOrEdit, list

```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        *{
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            text-decoration: none;
        }
        html, body{
            height: 100%;
            background: rgb(211, 240, 255);
        }
        section{
            width: 60%;
            margin: 20px auto;
            padding: 50px 20px;
            background: white;
        }
        label{
            display: block;

        }
        form{
            margin: 10px 5px;
        }
        input[type='text']{
            width: 60%;
            border-radius: 5px;
            border: 1px solid gray;
            padding: 5px;
        }
        input[type='submit'], .viewAll{
            display: inline-block;
            margin: 10px 5px;
            background: firebrick;
            border: none;
            width: 100px;
            height: 30px;
            text-align: center;
            font-size: 12px;
            color: white;
            line-height: 30px;
            font-weight: bold;
            border-radius: 5px;
        }

        table{
            margin: 30px 10px;
            width: 100%;
            padding: 10px;
            background: white;
            border-top: 1px solid gray ;
            border-style: none;
            border-collapse: collapse;
        }
        th,td{
            border-bottom: 1px solid gray;
            padding: 10px 0;
        }
        tr:nth-child(even){
            background: rgb(238, 238, 238);
        }
        td{
            text-indent: 2em;
        }
        .createNew{
            display: inline-block;
            width: 130px;
            height: 40px;
            background: chocolate;
            color: white;
            line-height: 40px;
            border-radius: 5px;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <section>
    {{{body}}}
    </section>
</body>
</html>
```
```
<h3>{{viewTitle}}</h3>

<form action="/employee" method="post" autocomplete="off">
    <input type="hidden" name="_id" value="{{employee._id}}">
    <div>
        <label for="">Full Name</label>
        <input type="text" name="fullName" value="{{employee.fullName}}" placeholder="Full Name">
        <div class="textDanger">
        {{employee.fullNameError}}
        </div>
    </div>
    <div>
        <label for="">Email</label>
        <input type="text" name="email" value="{{employee.email}}" placeholder="Email">
        <div class="textDanger">
        {{employee.emailError}}
        </div>
    </div>
    <div>
        <label for="">Mobile</label>
        <input type="text" name="mobile" value="{{employee.mobile}}" placeholder="Mobile">
    </div>
    <div>
        <input type="submit" value="🚀쿨쿨">
        {{!-- <span class="viewAll"><a href="#">View All</a></span> --}}
        <a href="/employee/list" class="viewAll">🛒View All</a>
    </div>
</form>
```
```
    <h2>
    <a href="/employee" class="createNew">➕Create New</a>
        Employee List</h2>
{{!-- {{list}} --}}
<table>
    <thead>
        <tr>
            <th>Full Name</th>
            <th>Email</th>
            <th>Mobile</th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        {{#each list}}
        <tr>
            <td>{{this.fullName}}</td>
            <td>{{this.email}}</td>
            <td>{{this.mobile}}</td>
            <td><a href="/employee/{{this._id}}">🚀</a>
            <a href="/employee/delete/{{this._id}}" onclick="return confirm('정말로?')">♨</a>
            
            </td>
        </tr>
        {{/each}}

        
    </tbody>
</table>
```

서버
-----------

### 서버 기초

`request.url/ response.write, response.end`

```
const http = require('http') // http 모듈을 불러온다

const server = http.createServer((request, response)=>{
    console.log(request.url) // '/xxx' 주소
    console.log(request.method) 
    if(request.url ==='/'){ 
        res.writeHead(200, {'Content-Type': 'text/html; charset=utf-8'}) //브라우저 한글 깨질 시
                                 // 주소가 '/'이면
        response.write('Hello') // 서버의 응답, express에선 response.send('text')하면 된다
        response.end()  // 응답 끝
    }else{
        response.write('hi')
        response.end()
    }
})

server.listen(3000) // 서버에서 요청받기(port: 3000)
```

###  서버에서 html 파일 보내기( fs 모듈)

```
const http = require('http')
const fs = require('fs') // 노드js 파일시스템 모듈

const server = http.createServer((request, response)=>{
    console.log(request.url)
    console.log(request.method)
    fs.readFile('./index.html',null, (err, data)=>{
        response.writeHead(200,{ // 200 상태 코드 양호
            'Content-Type':'text/html'
        })
        response.write(data)
        response.end()
    })
})

server.listen(3000)
```

` nodemon 설치`
> npm i -g nodemon

```
실행방법 > nodemon server.js
```
<br>
편한 서버 express 모듈
-----------------------

1. package.json 생성 // 코드 배포를 편하게  
` npm init `

2. express 모듈 설치  
` npm install express  
> node_modules 폴더가 생성되어 여기에 설치가 된다

3. 서버 생성

```
const express = require('express')

const server = express()

server.get('/',(req,res)=>{
    res.status(200).sendFile(__dirname+'/index.html') // __dirname 현재 경로
})

server.listen(3000, ()=>{
    console.log('The server is running on Port 3000') //서버 실행 문구
})
```

4. static 파일 사용(express.static 미들웨어) server.use

```
const express = require('express')

const server = express()

server.use(express.static(__dirname)) // express.static 미들웨어 사용

server.use((req,res,next)=>{ //미들웨어 이어서
    //config
    next()
})

server.get('/',(req,res)=>{
    res.status(200).sendFile(__dirname+'/index.html') // __dirname 현재 경로
})

server.listen(3000, ()=>{
    console.log('The server is running on Port 3000!')
})

(추가) 서버 ip 주소
server.listen(3000,'192.168.0.33',()=>{}
```

html랜더링 Template Engine 'handlebars' /{{}} 컬리브라켓
---------------------------------------------------------

1. handlebars 설치  
` npm i express-handlebars`

2. 서버 파일

```
const express = require('express')
const hbs = require('express-handlebars')

const server = express()

server.engine('hbs', hbs({
    extname:'hbs',
    defaultLayout:'layout',
    layoutDir:__dirname+'/views/layouts', // views 템플릿 폴더
    partialsDir:__dirname+'/views/partials'
}))

server.set('view engine', 'hbs') // view engine 세팅

server.use(express.static(__dirname+'/statics')) // express.static 미들웨어 사용

server.use((req,res,next)=>{
    //config
    next()
})

server.get('/',(req,res)=>{
    res.status(200).render('index.hbs') // 템플릿 랜더
})

server.listen(3000, ()=>{
    console.log('The server is running on Port 3000!')
})
```

3. layout.hbs  
views/layouts 폴더

```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <img src="./4g2.jpg" style="width: 200px;" alt="">
    {{{ body }}} //이 부분에 index.hbs 내용이 들어간다
</body>
</html>
```

4. index.hbs

views 폴더

```
<h1>안녕</h1>
```
![image](https://user-images.githubusercontent.com/30430227/126600391-15ab168d-5b2c-4df0-823a-8af006ff2f8d.png)

5. 서버에서 index.hbs 로 객체 보내기

서버 내용 변경
```
server.get('/',(req,res)=>{
    res.status(200).render('index.hbs',{  //{name:   } 객체 전달
        name:'DannyTWLC'
    }) 
})
```
> index.hbs 내용 변경

```
<h1>안녕</h1>
<h2>{{name}} 안녕 </h2>
```

### nodemon 변경 감시 확장자 설정 방법

` nodemon server.js --ext .js,.hbs `

### handlebars 실습

![image](https://user-images.githubusercontent.com/30430227/126608100-5d13d6de-1753-408b-acae-fbed45c8d493.png)

1. layout.hbs

```
    <style>
        .active{
            color:white;
            background: #000;
        }
    </style>
</head>
<body>
    <img src="./4g2.jpg" style="width: 200px;" alt="">
    <nav>
        <a class="{{#if home}}active{{/if}}" href="/">Home</a>
        <a class="{{#if features}}active{{/if}}" href="/features">Features</a>
        <a class="{{#if contact}}active{{/if}}" href="/contact">Contact</a>
    </nav>
    {{{ body }}}
```

2. server.js

```
server.get('/',(req,res)=>{
    res.status(200).render('index.hbs',{  //{name:   } 객체 전달
        home: true
    }) 
})
server.get('/features',(req,res)=>{
    res.status(200).render('index.hbs',{  //{name:   } 객체 전달
        features: true
    }) 
})
server.get('/contact',(req,res)=>{
    res.status(200).render('index.hbs',{  //{name:   } 객체 전달
        contact: true
    }) 
})
```

3. partials(layout 분리)

![image](https://user-images.githubusercontent.com/30430227/126608655-cf6d2ae4-a7f9-407e-949a-4d38782d3e69.png)

```
<body>
    <img src="./4g2.jpg" style="width: 200px;" alt="">
    {{>nav}}

    {{{ body }}}
    
</body>
```

4. #each 반복

![image](https://user-images.githubusercontent.com/30430227/126609548-a83b2faf-8498-46c1-822a-550068a1fe9d.png)

` server.js`

```
server.get('/contact',(req,res)=>{
    res.status(200).render('index.hbs',{  //{name:   } 객체 전달
        contact: true,
        list:[
            'Danny','Jenny','boy'
        ]
    }) 
})
```

` index.hbs`

```
<h1>반갑</h1>
<ul>
    {{#each list}}
    <li>{{this}}</li>
    {{/each}}
</ul>
```

### REST API 1) GET method
![image](https://user-images.githubusercontent.com/30430227/126629970-a22d1be7-7c01-4152-8615-f95d4bb06843.png)

 /api/user 주소를 입력하면(요청하면) json데이터로 응답한다

`Chrome JSON Viewer 애드온 설치`  
![image](https://user-images.githubusercontent.com/30430227/134854171-c1ab9dcf-ae85-4877-88ea-aab598e67381.png)  

![image](https://user-images.githubusercontent.com/30430227/134854089-0624ae63-2b17-44d2-8e09-7b5391ec0c6f.png)  


```
const express = require('express')

const server = express()

const users =[
    {
    id:'Dan',
    name:'Danny',
    email:'d@dan.com'
    },
    {
    id:'lisney',
    name:'Lee',
    email:'lisney@namver.com'
    }

]

server.get('/api/user',(req, res)=>{
    res.json(users)
})


server.listen(3000,()=>{
    console.log('The server is running')
})
```

### REST POST  body-parser 요청 데이터 파싱 미들웨어

```
const express = require('express')

const bodyParser = require('body-parser') //body-parser

const server = express()

server.use(bodyParser.json()) // JSON 파싱

const users =[
    {
    id:'Dan',
    name:'Danny',
    email:'d@dan.com'
    },
    {
    id:'lisney',
    name:'Lee',
    email:'lisney@namver.com'
    }

]

server.get('/api/user',(req, res)=>{
    res.json(users)
})

server.post('/api/user',(req, res)=>{
    console.log(req.body) // 요청 데이터 표시
    users.push(req.body) // 요청 데이터 users에 추가
    res.json(users)
})

server.listen(3000,()=>{
    console.log('The server is running')
})
```

![image](https://user-images.githubusercontent.com/30430227/126738802-6d986bc2-7ea4-4fea-93bd-8c8ca5649804.png)

헤더에 보내는 데이터 타입 JSON

![image](https://user-images.githubusercontent.com/30430227/126738842-11d72ce2-d94b-4e1e-8610-65d6c5c15c51.png)

바디에 JSON 문 작성 ("쌍따옴표)


### REST ID를 통해 데이터 불러오기 params(params.id)

```
server.get("/api/user/:id",(req, res)=>{
    const user = users.find(u=>{
        return u.id === req.params.id // 요청 : 파라미터 id 와 같은게 있는지 찾기, 있으면 true 리턴
    })
    if(user){
        res.json(user)
    }else{
        res.status(404).json({errorMessage:"User was not found"})
    }
})
```

![image](https://user-images.githubusercontent.com/30430227/126742307-03f57ab0-0fde-49ba-99f8-e28047460665.png)

응답!

### REST  put, delete 데이터 업데이트, 삭제

```
server.put('/api/user/:id',(req, res)=>{
    let foundIndex = users.findIndex(u=>u.id===req.params.id)
    if(foundIndex === -1){
        res.status(404).json({errorMessage:'User was not found'})
    }else{
        users[foundIndex] = {...users[foundIndex], ...req.body} // ... Rest Operator 똑같은 프로퍼티가 있다면 뒤에 쓴걸로 덮어쓰기
        res.json(users[foundIndex])
    }
})
```
`... 확산연산자(spread operator)`  
```
# 배열 분해
const [apple, ...notApple] = ['🍎', '🙌', '♨', '🚀']
console.log(notApple)  //  ['🙌', '♨', '🚀']

# 배열의 중복값 제거
const fruit = ['🍎', '🙌', '♨', '🙌', '🚀', '🙌', '🚀']
const uFruit = [...new Set(fruit)]
console.log(uFruit) // ['🍎', '🙌', '♨', '🚀']

# 배열의 합집합 - 병합 후 중복제거(set)
fruitA = ['🍎', '🙌', '♨']
fruitB = ['🙌', '♨', '🚀']

union = [...new Set([...fruitA + ...fruitB])]
console.log(union) // ['🍎', '🙌', '♨', '🚀']

# 다른 '배열'의 요소를 앞에 추가(push는 뒤에 추가)
fruit.unshift(['🙌', '♨']
console.log(fruit) // ['🙌', '♨','🍎', '🙌', '♨', '🙌', '🚀', '🙌', '🚀']

## slice를 사용하여 배열을 복사하는 방법
fruitC = fruit.slice()

# 배열에서 최대/최소값 찾기
const price = [23,54,33,77]

minPrice = Math.min(...price)
minPrice = Math.max(...price)

## 숫자배열 정렬
price.sort((a,b)=>a-b) //오름차순
price.sort((a,b)=>b-a) //내림차순

## 문자배열 정렬
fruit.sort((a,b)=>a>b?1:a<b?-1:0) //오름차순
fruit.sort((a,b)=>a>b?-1:a<b?1:0) //내림차순

```


> server.put > ... Rest Operator 사용

```
server.delete('/api/user/:id', (req, res)=>{
    let foundIndex = users.findIndex(u=> u.id === req.params.id)
    if(foundIndex === -1){
        res.status(404).json({errorMessage:"User was not found"})
    }else{
        let foundUser = users.splice(foundIndex, 1)
        res.json(foundUser[0])
    }
})
```
> server.delete > splice(접합, 결혼)
```
A = B.splice(i,N)
배열 B에서 인덱스 i부터 N개만큼 잘라낸 후 붙여서 배열 B에 저장하고, 잘라낸 요소를 A에 저장한다

```

### 파일업로드 multer 미들웨어

` npm i multer`

```
const multer = require('multer')

const upload = multer({
    storage: multer.diskStorage({
        destination:(req, file, cb)=>{
            cb(null,'uploads/') // cb 콜백함수를 통해 전송된 파일 저장 디렉토리 설정
        },
        filename: (req, file, cb)=>{
            cb(null, file.originalname) // cb 콜백함수를 통해 전송된 파일 이름 설정
        }
    })
})
```
```
server.post('/upload',upload.single('img'), (req, res)=>{
    res.send('업로드 성공!'+req.file)
})
```

### 서버 코딩 연습

![image](https://user-images.githubusercontent.com/30430227/126763279-d7efa93a-89df-49da-994f-c6e36c6c8f00.png)

> upload.hbs 파일 위치 '/views/'

```
<form action="upload" method='post' enctype="multipart/form-data"> // action 해당경로 '/upload'로 이동
    <input type="file" name="img">
    <input type="submit">
</form>
```

>layout.hbs 파일 위치 '/views/layouts/'

```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .active{
            color:white;
            background: #000;
        }
    </style>
</head>
<body>
    <img src="./4g2.jpg" style="width: 200px;" alt="">
    {{>nav}}

    {{{ body }}}
    
</body>
</html>
```

> nav.hbs '/views/partials/'

```
    <nav>
        <a class="{{#if home}}active{{/if}}" href="/">Home</a>
        <a class="{{#if features}}active{{/if}}" href="/features">Features</a>
        <a class="{{#if contact}}active{{/if}}" href="/contact">Contact</a>
    </nav>
```

```
const express = require('express')
const hbs = require('express-handlebars')
const bodyParser = require('body-parser')
//파일업로드
const multer = require('multer')

const upload = multer({
    storage: multer.diskStorage({
        destination:(req, file, cb)=>{
            cb(null,'uploads/') // cb 콜백함수를 통해 전송된 파일 저장 디렉토리 설정
        },
        filename: (req, file, cb)=>{
            cb(null, file.originalname) // cb 콜백함수를 통해 전송된 파일 이름 설정
        }
    })
})

//서버 생성
const server = express()

//hbs 엔진
server.engine(
    'hbs',
    hbs({
        extname:'hbs',
        defaultLayout:'layout',
        layoutsDir:__dirname+'/views/layouts',
        partialsDir:__dirname+'/views/partials'
    })
)

server.set('view engine', 'hbs')

//미들웨어
server.use(express.static(__dirname+'/statics')) // statics 가 루트경로로 지정된다

server.use(bodyParser.json())

server.use('/users', express.static(__dirname+'/statics'))// statics 가상경로 지정하기

server.get('/',(req,res)=>{
    res.status(200).sendFile(__dirname+'/index.html') // __dirname 현재 경로
})

server.get('/login', (req, res)=>{
    res.send('<h1>login please Goo!</h1>')
})

// 파일업로드
server.get('/upload', (req, res)=>{
    res.render('upload.hbs',{contact:true}) // '/views' 폴더, contact 변수 전달
})
server.post('/upload',upload.single('img'), (req, res)=>{  //.single() 이미지를 받아서 req.file 에 저장
    res.send('업로드 성공!'+req.file)  
})

////////////////////
const users =[
    {
    id:'Dan',
    name:'Danny',
    email:'d@dan.com'
    },
    {
    id:'lisney',
    name:'Lee',
    email:'lisney@namver.com'
    }

]
////////GET///////////
server.get('/api/user',(req, res)=>{
    res.json(users)
})

////////POST/////////
server.post('/api/user',(req, res)=>{
    console.log(req.body) // 요청 데이터 표시
    users.push(req.body) // 요청 데이터 users에 추가
    res.json(users)
})

////////PUT/////////////
server.put('/api/user/:id',(req, res)=>{
    let foundIndex = users.findIndex(u=>u.id===req.params.id)
    if(foundIndex === -1){
        res.status(404).json({errorMessage:'User was not found'})
    }else{
        users[foundIndex] = {...users[foundIndex], ...req.body} // ... Rest Operator 똑같은 프로퍼티가 있다면 뒤에 쓴걸로 덮어쓰기
        res.json(users[foundIndex])
    }
})

/////////DELETE/////////////
server.delete('/api/user/:id', (req, res)=>{
    let foundIndex = users.findIndex(u=> u.id === req.params.id)
    if(foundIndex === -1){
        res.status(404).json({errorMessage:"User was not found"})
    }else{
        let foundUser = users.splice(foundIndex, 1) //splice 접합, 결혼
        res.json(foundUser[0])
    }
})


server.listen(3000, ['192.168.0.33'], ()=>{
    console.log('The server is running...')
})
```

### 몽고db

![image](https://user-images.githubusercontent.com/30430227/126935220-f2819c3a-83f2-48ed-8400-86a9c010a3d6.png)
![image](https://user-images.githubusercontent.com/30430227/126935275-8985f2ba-2d1e-413b-9e5f-4492d886b56a.png)

모든ip 주소를 허용하기 위해 두번 쩨 Add Different Ip 버튼을 클릭 후 '0.0.0.0'을 입력, 사용자 root/1234 입력

![image](https://user-images.githubusercontent.com/30430227/126935628-105cc6f5-76c6-40a6-8414-20dfe75d5612.png)

두 번째 'Connect your Application' 클릭
<br>
1. pagkage.json 생성

npm init --y 한방에 생성
<br>
2. 모듈 설치

npm i express mongoose dotenv //dotenv 보안을 위해 환경변수를 관리하는 모듈  
variables.env 파일 생성

```
MONGODB_URL=mongodb+srv://root:1234@education.8nfen.mongodb.net/myFirstDatabase?retryWrites=true&w=majority
```

` server.js`

```
const express = require('express')
const mongoose = require('mongoose')
require('dotenv').config({path:'variables.env'})

// console.log(process.env.MONGODB_URL) // dotenv 내 변수 'process.env.변수명'

//몽고db접속 URL
// const MONGODB_URL ='mongodb+srv://root:1234@education.8nfen.mongodb.net/myFirstDatabase?retryWrites=true&w=majority'

mongoose.connect(process.env.MONGODB_URL, {useUnifiedTopology:true, useNewUrlParser: true},(err=>{
    if(err){
        console.log(err)
    }else{
        console.log('Connected to database succefully')
    }
}))
```
<br>
3. 데이터베이스 모델 생성

models 폴더 생성 > User.js 모델 파일(대문자로 시작)

```
const mongoose = require('mongoose')
const {Schema} = mongoose   // const Schema = mongoose.Schema 와 같다

const userSchema = new Schema({
    email:{
        type:String,
        required:true //email이 있어야 데이터 생성
    },
    name:String,
    age:{
        type:Number,
        min:18,
        max:50
    },
    //가입 일시 저장
    // enrolled:{
    //     type:Date,
    //     default:Date.now
    // }
},
//가입일 업데이트 일시 자동저장 enrolled 필요없음
{
    timestamps: true
})

module.exports = mongoose.model('User', userSchema)
```

server.js 수정

```
const express = require('express')
const mongoose = require('mongoose')
require('dotenv').config({path:'variables.env'})

const User = require('./models/User')

const server = express()

server.get('/',(req, res)=>{
    const newUser = new User()
    newUser.email = "danny@1.com"
    newUser.name = 'Danny'
    newUser.age = 25
    newUser.save().then((user)=>{
        console.log(user)
        res.json({
            message:'User Created Successfully'
        })
    }).catch((err)=>{
        res.json({
            message:"User was not successfully created"
        })
    })
})

server.listen(3000,err=>{
    if(err){
        return console.log(err)
    }else{
        mongoose.connect(process.env.MONGODB_URL, {useUnifiedTopology:true, useNewUrlParser: true},(err=>{
            if(err){
                console.log(err)
            }else{
                console.log('Connected to database succefully')
            }
        }))

    }
})
// console.log(process.env.MONGODB_URL)

//몽고db접속 URL
// const MONGODB_URL ='mongodb+srv://root:1234@education.8nfen.mongodb.net/myFirstDatabase?retryWrites=true&w=majority'
```

<br>
### 몽구스
<br>
 데이터베이스 연결
 
```
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/goormdb', { useNewUrlParser });
// 위에서처럼 데이터베이스가 연결되면, connection 인스턴스가 생성되며 연결되는 순간에는 open 이벤트가 발생합니다. 이때 인스턴스는 mongoose.connection입니다. goormdb라는 데이터베이스가 없다면 mongoDB는 이를 자동으로 생성합니다.
```

<br>
 여러개의 데이터베이스를 연결할 때

```
var mongoose = require('mongoose');
var connection1 = mongoose.createConnection('mongodb://localhost/mydb1');
var connection2 = mongoose.createConnection('mongodb://localhost/mydb2');
```

<br>

스키마 생성

```
var Schema = mongoose.Schema, ObjectId = Schema.ObjectId;
var ArticleSchema = new Schema({
    author: ObjectId,
    title: String,
    body: String,
    date: Date
});
```

<br>

스키마를 이용 모델 생성

```
var ArticleModel = mongoose.model('Article', ArticleScheme);
```
<br>

## 주소록
----------------
![image](https://user-images.githubusercontent.com/30430227/127465755-fb9bcd20-091d-47c2-8d79-8b982629eb35.png)

` server.js`

```
const express = require('express')
const path = require('path')
const hbs = require('express-handlebars')
const { Server } = require('http')
const mongoose = require('mongoose')

const methodOverride = require('method-override')// HTML에 없는 put, delete 를 받는다


const app = express()

// DB
require('./models/db')

// Set
app.engine('hbs',hbs({
    extname:'hbs',
    defaultLayout:'layout',
    layoutsDir:__dirname+'/views/layouts/',
    partialsDir:__dirname+'/views/partials/'
}))
app.set('views', path.join(__dirname+'/views/'))

app.set('view engine','hbs')

// Middleware
app.use(express.static(__dirname+'/statics'))
app.use(express.urlencoded({extended: true})) //bodyParser
app.use(express.json())
app.use(methodOverride('_method')) // New

app.listen(3000,['192.168.0.33'],()=>{
    console.log('Server is running...')
})

// Router
const router = require('./controller/router')
app.use('/user', router)


```
<br>

` db.js`

```
const mongoose = require('mongoose')

require('dotenv').config({path:'variables.env'})

mongoose.connect(process.env.MONGODB_URL, {useNewUrlParser:true, useUnifiedTopology:true},(err)=>{
    if(!err){console.log('MongoDB Connection succeeded')}
    else{
        console.log("An Error Occured")
    }
})

require('./user.model')

```
<br>

` user.model.js`
```
const express = require('express')
const path = require('path')
const hbs = require('express-handlebars')
const { Server } = require('http')
const mongoose = require('mongoose')

const methodOverride = require('method-override')// HTML에 없는 put, delete 를 받는다


const app = express()

// DB
require('./models/db')

// Set
app.engine('hbs',hbs({
    extname:'hbs',
    defaultLayout:'layout',
    layoutsDir:__dirname+'/views/layouts/',
    partialsDir:__dirname+'/views/partials/'
}))
app.set('views', path.join(__dirname+'/views/'))

app.set('view engine','hbs')

// Middleware
app.use(express.static(__dirname+'/statics'))
app.use(express.urlencoded({extended: true})) //bodyParser
app.use(express.json())
app.use(methodOverride('_method')) // New

app.listen(3000,['192.168.0.33'],()=>{
    console.log('Server is running...')
})

// Router
const router = require('./controller/router')
app.use('/user', router)

```
<br>

` router.js`
```
const express = require('express')
const mongoose = require('mongoose')


const User = mongoose.model('User')

const router = express.Router()

router.get('/',(req,res)=>{
    res.redirect('/user/contacts') // router redirect는 앞에 '/user/'가 붙는다
})

router.get('/contacts',(req,res)=>{
    User.find({},(err,docs)=>{ //  모든 데이터 받음, {}는 생략가능
        if(!err){
            res.render('contacts/index',{list:docs})
        }
    }).lean()
})

router.get('/contacts/new',(req,res)=>{
    res.render('contacts/new')
})

router.post('/contacts/new',(req,res)=>{
    User.create(req.body,(err,contact)=>{
        if(!err){res.redirect('/user')}
        else{
            return res.json(err)
        }
    })
    }
)

// Show
router.get('/contacts/:id',(req,res)=>{
    User.findOne({_id:req.params.id}, (err, doc)=>{ // findById(req.params.id 참고
        if(!err){
            res.render('contacts/show',{contact: doc})
        }else{
            return res.json(err)
        }
    }).lean()
})

// Edit
router.get('/contacts/:id/edit', (req, res)=>{
    User.findById(req.params.id, (err, doc)=>{
        if(!err){
            res.render('contacts/edit',{contact:doc})
        }
    }).lean()
})
router.put('/contacts/:id', (req,res)=>{
    User.findOneAndUpdate({_id:req.params.id},req.body,(err, doc)=>{
        if(!err){
            res.redirect('/user')
        }
    })
})

// Delete
router.delete('/contacts/:id',(req,res)=>{
    User.deleteOne({_id:req.params.id},(err)=>{ // findByIdAndRemove(req.params.id 참고
        if(err) return res.json(err)
        res.redirect('/user/contacts')
    })
})

module.exports = router
```
<br>

`layout.hbs`
```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" href="http://localhost:3000/style.css"> 
    {{!-- router 사용 시 절대경로 사용해야 오류가 없다 부모 경로가 루트, '/user' 현재 경로, --}}
</head>
<body>
    <nav>
        <div><h3>Contact Book</h3></div>
        <div><a href="/user/contacts">Index</a></div>
        <div><a href="/user/contacts/new">New</a></div>
    </nav>
    {{{body}}}
</body>
</html>
```
<br>

` new.hbs`
```
<h2>New</h2>
<form action="/user/contacts/new" method="post">
    <div>
    <label for="name">Name</label>
    <input type="text" id="name" name="name">
    </div>
    <div>
    <label for="email">Email</label>
    <input type="text" id="email" name="email">
    </div>
    <div>
    <label for="phone">Phone</label>
    <input type="text" id="phone" name="phone">
    </div>

    <input type="submit" value="등록">
</form>
```
<br>

` show.hbs`
```
<h2>Show</h2>
<ul>
    <li>
        이름은 : {{contact.name}}
    </li>
    <li>
        메일은 : {{contact.email}}
    </li>
    <li>
        전화 : {{contact.phone}}
    </li>
</ul>
<a href="/user/contacts/{{contact._id}}/edit">Edit</a>
<form action="/user/contacts/{{contact._id}}?_method=delete" method="post">
    <input type="submit" onclick="return confirm('정말?')" value="Delete">
</form>
```
<br>

`edit.hbs`
```
<h2>Edit</h2>
<form action="/user/contacts/{{contact._id}}?_method=put" method="post">
    <div>
        <label for="name">Name</label>
        <input type="text" id="name" name="name" value="{{contact.name}}">
    </div>
    <div>
        <label for="email">Email</label>
        <input type="text" id="email" name="email" value="{{contact.email}}">
    </div>
    <div>
        <label for="phone">Phone</label>
        <input type="text" id="phone" name="phone" value="{{contact.phone}}">
    </div>
    <div>
        <input type="submit" value="쿨쿨">
    </div>
</form>
```
<br>

` style.css`
```
*{
    margin: 0;
    padding: 0;
    text-decoration: none;
    list-style: none;
}

nav{
    color: lightgray;
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 50px;
    align-items: center;
    background: ghostwhite;
}

nav div a{
    padding: 10px;
    color: gray;
    font-size: 12px;
    font-weight: bolder;
}
section{
    margin: 0 auto;
    width: 70%;
}
h2{
    color: tomato;
    margin-bottom: 20px;
}

ul{
    width: 100%;
    border: 1px solid lightgray;
    padding: 15px 10px;
}

label{
    display: inline-block;
    width: 80px;
    text-align: right;
}
input[type=submit]{
    border-style: none;
    width: 100px;
    margin-left: 100px;
}
```


