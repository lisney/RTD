Flask
======

`라즈베리파이OS에 이미 설치되어 있음`


Hello World
----------------

```
from flask import Flask # 플라스크 모듈 호출

app = Flask(__name__) # 플라스크 앱 생성

@app.route('/') # 기본 경로('/')로 요청이 오면 hello 함수 실행
def hello():
    return 'Hello World'

if __name__ == '__main__': # 현재 파일이 main 이면 실행
    app.run(debug=True, port=80, host='0.0.0.0')
```

`서버 실행 - sudo python3 hello.py`


파이썬 가상환경
-----------------------

```
> python -m venv myproject

# 실행
myproject\script\activate.bat 실행

# 실행 배치파일 예 myproject.cmd - bat가 아니라 cmd

# 가상환경 나오기
> deactivate

# 플라스크 설치
> pip install flask
```


기본 앱 생성 
---------------

```
# pybo.py
from flask import Flask

app=Flask(__name__) # __name__ 모듈명

@app.route('/')
def hello_pybo():
    return 'Hello, Pybo!'
    
# 실행 
flask pybo
>> 플라스크는 기본 앱 명을 app.py로 한다. 기본 앱 명 수정
>> set FLASK_APP=pybo 실행 후 다시 실행한다

# 개발환경으로 실행하기 - 디버그 모드 활성
>> set FLASK_ENV=development 후 실행

# 환경파일 수정 myproject.cmd
@echo off
set FLASK_APP=pybo
set FLASK_ENV=development
.\scripts\activate

# 앱 팩토리-어플리케이션 팩토리(create_app함수) - 앱의 규모가 커질 때 발생하는 문제 예방
> mkdir pybo
> move pybo.py pybo\__init__.py #이름 바꿔 이동, __init__ 폴더를 패키지화, 패키지 초기화 기능

# __init__.py 파일 수정

from flask import Flask

def create_app():
    app = Flask(__name__)

    @app.route('/') # 애너테이션
    def hello_pybo(): # 애너테이션으로 URL '/'에 매핑되는 함수 = 라우팅 함수
        return 'Hello World!'

    return app
 
 
#블루프린트 - 라우팅 함수 체계적 관리
/pybo/views/main_views.py
form flask import Blueprint

bp = Blueprint('main',__name__,url_prefix='/')
# main 별칭, __name__ 현재 모듈명main_views, url_prefix 접두 URL - 해당 경로에서 pb URL 이어감

@bp.route('/')
def hello_pybo():
    return 'Hello World!'

## __init__.py 파일도 수정
def create_app():
    app = Flask(__name__)

    from .views import main_views
    app.register_blueprint(main_views.bp)

    return app
    
```


데이터 모델 생성 ORM -object relational mapping
--------------------------------

```
# SQLAlchemy 와 Flask-Migrate 라이브러리 설치(SQLAlchemy는 flask-migrate에 포함되 있음)
>pip install flask-migrate

# DB 설정파일 생성
/config.py
import os

BASE_DIR = os.path.dirname(__file__)

SQLALCHEMY_DATABASE_URI = 'sqlite:///{}'.format(os.path.join(BASE_DIR,'pybo.db'))
# DB 접속 주소 'URI' 다, 홈디렉토리에 pybo.db파일로 저장
SQLALCHEMY_TRACK_MODIFICATIONS = False
# sqlalchemy 의 이벤트를 처리하는 옵션, 현재 사용하지 않으므로 False

# __init__.py 파일 수정
from flask import Flask
from flask_migrate import Migrate
from flask_sqlalchemy import SQLAlchemy

import config

db = SQLAlchemy() # db 객체 생성
migrate = Migrate()

def create_app():
    app = Flask(__name__)
    app.config.from_object(config)

    # ORM
    db.init_app(app) # db 객체를 app에 등록
    migrate.init_app(app, db) # migrate 에 app과 db 등록

    # 블루프린트
    from .views import main_views
    app.register_blueprint(main_views.bp)

    return app

# 데이터 베이스 초기화 - /migrations(DB를 관리하는) 폴더가 생성
> flask db init

# flask db migrate - DB 모델 생성/변경, flask db upgrade - 실재 데이터베이스에 등록

# 데이터베이스 모델 생성
/pybo/models.py
from pybo import db

class Question(db.Model): # 생성된 테이블명은 'question'이 된다
    id = db.Column(db.Integer, primary_key=True)
    subject = db.Column(db.String(200), nullable=False)
    content = db.Column(db.Text(),nullable=False)
    create_data = db.Column(db.DateTime(), nullable=False)


class Answer(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    question_id = db.Column(db.Integer, db.ForeignKey('question.id', ondelete='CASCADE'))
    # foreign key 기존 모델과 연결된 속성 즉 외부키
    question = db.relationship('Question', backref=db.backref('answer_set'))
    # 답변 모델에서 질문 모델을 참조하기 위해 추가함, answer.question.subject처럼 참조 # backref 역참조, 질문의 답변들을 참조?
    content = db.Column(db.Text(), nullable=False)
    create_date = db.Column(db.DateTime(), nullable=False)

# __init__.py 추가
    # ORM
    db.init_app(app) # db 객체를 app에 등록
    migrate.init_app(app, db) # migrate 에 app과 db 등록
    from . import models
    
# 리비전 파일 생성
> flask db migrate

```

![image](https://user-images.githubusercontent.com/30430227/179382867-488c27f4-d25a-4190-b6d5-1aa9f1fd727e.png)
![image](https://user-images.githubusercontent.com/30430227/179382935-aedaaacf-2e19-40c7-a3c8-8194a92dd108.png)


```
# 리비전 파일 실행 - 실재 db가 생성된다
> flask db upgrade

```
