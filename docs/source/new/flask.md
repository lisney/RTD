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
    create_date = db.Column(db.DateTime(), nullable=False)


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
![image](https://user-images.githubusercontent.com/30430227/179383238-a7199536-5ca4-4c2d-9913-a93e312e9585.png)

# DB 브라우저

[사이트](https://sqlitebrowser.org/dl/)

![image](https://user-images.githubusercontent.com/30430227/179383421-a99729f3-aecd-4e50-933b-9c55c828f0e1.png)
![image](https://user-images.githubusercontent.com/30430227/179383463-4552a0c3-f81f-4b66-a195-bfe0c0922606.png)

`alembic_version 은 migrate가 관리`


질문 목록 Template
-----------------------

```
# main_views.py 변경
from flask import Blueprint, render_template

from pybo.models import Question

bp = Blueprint('main',__name__,url_prefix='/')
# main 별칭, __name__ 현재 모듈명main_views, url_prefix 접두 URL - 해당 경로에서 pb URL 이어감

@bp.route('/')
def index():
    question_list = Question.query.order_by(Question.create_date.desc())
    return render_template('question/question_list.html', question_list=question_list)
    # render_template 템플릿 파일을 화면으로 랜더링하는 함수, templates폴더를 기본으로 인식, question_list 데이터를 전달한다
    
# 질문 리스트 HTML
\pybo\templates\question\question_list.html
{% if question_list %}
<ul>
    {% for question in question_list %}
    <li><a href="/detail/{{ question.id }}">{{ question.subject }}</a></li>
    {% endfor %}
</ul>
{% else %}
<p>질문이 없습니다</p>

{% endif %}

# 질문 라우팅 함수 추가 main_views.py
@bp.route('/detail/<int:question_id>/')
def detail(question_id):
    # question = Question.query.get(question_id)
    question = Question.query.get_or_404(question_id) # 페이지 없음 메시지 표시
    return render_template('question/question_detail.html', question=question)
    
# 질문 상세 HTML
\pybo\templates\question\question_detail.html
<h1>{{ question.subject}}</h1>
<div>
    {{ question.content}}
</div>
```

![image](https://user-images.githubusercontent.com/30430227/179385299-1152ee5b-07b4-42f4-90dc-cc87fa7475b2.png)
![image](https://user-images.githubusercontent.com/30430227/179385295-69d32683-0ebc-426d-a127-264a0bca0d66.png)

![image](https://user-images.githubusercontent.com/30430227/179385402-20e149ee-11c1-438e-aecf-0dfe42975c2c.png)

```
* 블루프린트로 질문 템플릿들 분리
\views\question_views.py
from flask import Blueprint, render_template

from pybo.models import Question

bp = Blueprint('question',__name__,url_prefix='/question')
# bp 객체 생성 시 url_prefix 에 /question 을 붙여 구분한다

@bp.route('/list/') # URL 매핑을 /list/ 로 한다
def _list(): # 함수명은 _list(list는 파이썬 예약어)
    question_list = Question.query.order_by(Question.create_date.desc())
    return render_template('question/question_list.html', question_list=question_list)

@bp.route('/detail/<int:question_id>/')
def detail(question_id):
    question = Question.query.get_or_404(question_id)
    return render_template('question/question_detail.html', question=question)


* main_views.py 수정
from flask import Blueprint, render_template, url_for
from werkzeug.utils import redirect

from pybo.models import Question

bp = Blueprint('main',__name__,url_prefix='/')
# main 별칭, __name__ 현재 모듈명main_views, url_prefix 접두 URL - 해당 경로에서 pb URL 이어감

@bp.route('/')
def index():
    return redirect(url_for('question._list'))
    # 함수 redirect(URL) - URL로 페이지 이동(리다이렉트), 함수 url_for(라우팅 함수) -라우팅 함수에 매핑돼 있는 URL 리턴
    

* __init__.py에 블루프린트 추가
    # 블루프린트
    from .views import main_views, question_views
    app.register_blueprint(main_views.bp)
    app.register_blueprint(question_views.bp)


* url_for 사용 'question_list.html' 수정, url_for(함수명, 매개변수) - 함수 detail(quesion_id)
    <!-- <li><a href="/detail/{{ question.id }}">{{ question.subject }}</a></li> -->
    <li><a href="{{ url_for('question.detail', question_id=question.id)}}">{{ question.subject }}</a></li>
```


답변 등록
--------------

![image](https://user-images.githubusercontent.com/30430227/179387879-f6f1ca95-3bef-44b8-80ef-4d1f194bcb28.png)

```
# question_detail.html 내용 수정 - '|length' 개수를 출력하는 필터
<h1>{{ question.subject}}</h1>
<div>
    {{ question.content}}
</div>

<h5>{{ question.answer_set|length}}개의 답변이 있습니다</h5>
<div>
    <ul>
        {% for answer in question.answer_set %}
        <li>{{ answer.content }}</li>
        {% endfor %}
    </ul>
</div>

<form action="{{ url_for('answer.create', question_id=question.id)}}" method="post">
    <textarea name="content" id="content" rows="15"></textarea>
    <input type="submit" value="답변등록">
</form>

* 답변 관리 블루프린트 생성 
\pybo\views\answer_views.py
from datetime import datetime

from flask import Blueprint, url_for, request
from werkzeug.utils import redirect

from pybo import db
from pybo.models import Question, Answer

bp = Blueprint('answer',__name__, url_prefix='/answer')

@bp.route('/create/<int:question_id>', methods=['POST',])
def create(question_id):
    question = Question.query.get_or_404(question_id)
    content = request.form['content'] # post 로 전달받은 form의 요소 중 content의 내용을 받는다
    answer = Answer(content=content, create_date=datetime.now())
    question.answer_set.append(answer)
    db.session.commit()
    return redirect(url_for('question.detail',question_id=question.id))
   
* __init__.py 에 블루프린트 추가
    # 블루프린트
    from .views import main_views, question_views, answer_views
    app.register_blueprint(main_views.bp)
    app.register_blueprint(question_views.bp)
    app.register_blueprint(answer_views.bp)
    
```




