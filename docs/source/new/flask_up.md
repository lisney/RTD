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


```

파일업로드 
-------------

```
** <form>태그의 속성인 method는 전송 방식, action은 전송 목적지, enctype은 전송되는 데이터 형식을 설정

** enctype 속성은 세가지의 값으로 지정될 수 있음
1. application/www-form-urlencoded 디폴트값이다. 폼데이터는 서버로 전송되기 전에 URL-Encode 됨
2. multipart/form-data 파일이나 이미지를 서버로 전송할 경우 이 방식을 사용
3. text/plain 이 형식은 인코딩을 하지 않은 문자 상태로 전송

