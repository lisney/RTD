FlaskUP
========

시작 
-----

1. 가상환경

```
$ python -m venv env
$ source env/bin/activate

$ pip install flask

$ mkdir core
$ cd core

* 빈파일 만들기
$ touch __init__.py  $ touch views.py

```

2. __init__.py

```
* __name__ 생성한 모듈명 즉 'core'
from flask import Flask

app = Flask(__name__)

from core import views


* views.py
from core import app

@app.route('/')
def index():
    return 'Hello Ace'
    

$ cd ..
$ touch base.py

$ export FLASK_APP=base.py
$ flask run

```

3. python-dotenv 생성 - 실행환경 만들기

```
$ pip install python-dotenv

$ touch .flaskenv //생성 후 환경변수 입력
FLASK_APP=base.py
FLASK_ENV=development

```


4. Template - 플라스크는 jinja2 신사 템플릿을 기본으로 사용한다

![image](https://user-images.githubusercontent.com/30430227/180363701-9bc0971f-5be9-4f56-ad2f-c190d6a35a93.png)

```
$ cd core
$ mkdir templates
$ touch index.html

\views.py 수정
from flask import render_template
from core import app

@app.route('/')
def index():
    greeting = 'Hello there, Ace'
    return render_template('index.html', greet=greeting)


\templates\index.html 작성
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jinja2</title>
</head>

<body>
    <h1>{{greet}}</h1>
</body>

</html>
```


To Do List
----------------




파일업로드 
-------------

```
** <form>태그의 속성인 method는 전송 방식, action은 전송 목적지, enctype은 전송되는 데이터 형식을 설정

** enctype 속성은 세가지의 값으로 지정될 수 있음
1. application/www-form-urlencoded 디폴트값이다. 폼데이터는 서버로 전송되기 전에 URL-Encode 됨
2. multipart/form-data 파일이나 이미지를 서버로 전송할 경우 이 방식을 사용
3. text/plain 이 형식은 인코딩을 하지 않은 문자 상태로 전송

