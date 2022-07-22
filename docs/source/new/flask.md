Flask
======

`라즈베리파이OS에 이미 설치되어 있음`

```
# 파이썬3을 기본으로 설정하기

> 파이썬 버전 확인 > python -V(대문자)
> update-alternatives --config python(상태 확인, 처음에는 아무것도 설정되어 있지 않다)
> sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1
> sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.9 2
> update-alternatives --config python(설정 확인)
> python -V
```

![image](https://user-images.githubusercontent.com/30430227/179646088-3284240c-45e4-40d1-8a88-7c2b048f83ff.png)

```
# 라즈베리파이 가상환경
> sudo apt install virtualenv(설치)
> virtualenv myproject(생성)
> source myproject/bin/activate(실행,source 쉘스크립트를 실행)
> deactivate(나오기)

# 라즈베리파이 배치파일 -쉘 스크립트 .sh
> sudo chmod +x myproject.sh(sh을 실행되도록 만듬)
> ./myproject.sh('./' - 앞에 붙이면 실행명령=sh, bash)


```

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
flask run
>> 플라스크는 기본 앱 명을 app.py로 한다. 기본 앱 명 수정
>> set FLASK_APP=pybo 실행 후 다시 실행한다(리눅스 $ export FLASK_APP=pybo)

# 개발환경으로 실행하기 - 디버그 모드 활성
>> set FLASK_ENV=development 후 실행

# 환경파일 수정 myproject.cmd
@echo off
set FLASK_APP=pybo
set FLASK_ENV=development
.\scripts\activate

# 앱 팩토리-어플리케이션 팩토리(create_app함수) - 앱의 규모가 커질 때 발생하는 문제 예방
> mkdir pybo
> move pybo.py pybo\__init__.py #이름 바꿔 이동, __init__ 폴더를 패키지화, 패키지 초기화 기능(리눅스 $ mv)

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

![image](https://user-images.githubusercontent.com/30430227/179385299-1152ee5b-07b4-42f4-90dc-cc87fa7475b2.png)
![image](https://user-images.githubusercontent.com/30430227/179385295-69d32683-0ebc-426d-a127-264a0bca0d66.png)

`.get_or_404`

![image](https://user-images.githubusercontent.com/30430227/179385402-20e149ee-11c1-438e-aecf-0dfe42975c2c.png)

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


템플릿 상속 extends 
------------------

```
# style.css
\pybo\static\style.css
textarea {
  width: 100%;
}

input[type="submit"] {
  margin-top: 10px;
  color: teal;
}


# 기본 HTML 생성 - url_for('폴더',filename='파일명)
\pybo\templates\base.html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello, Pybot</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css')}}">
</head>

<body>
    {% block content %}
    {% endblock %}
</body>

</html>


# question_detail.html
{% extends 'base.html' %}
{% block content %}

...내용

{% endblock %}

```


폼 모듈 사용 질문 등록 생성
-----------------------

![image](https://user-images.githubusercontent.com/30430227/179438177-1b55f470-481f-47c9-9396-fe2aea220ad1.png)

```
# 모듈 설치
> pip install flask-wtf

# secret key 등록 -config.py
...내용추가
SECRET_KEY='dev'
# 편의상 문자열 'dev' 를 사용했지만 실제 서비스를 운영에는 다르다


# question_list.html 에 질문등록
<h1>플라스크 연습</h1>
<a href="{{ url_for('question.create') }}">질문등록</a>
<hr>
<table>
    <thead>
        <tr>
            <th>번호</th>
            <th>제목</th>
            <th>작성일시</th>
        </tr>
    </thead>
    <tbody>
        {% if question_list %}
        {% for question in question_list %}
        <tr>
            <td>{{ loop.index }}</td>
            <td>
                <a href="{{ url_for('question.detail', question_id=question.id) }}">{{ question.subject }}</a>
            </td>
            <td>{{ question.create_date }}</td>
        </tr>
        {% endfor %}
        {% else %}
        <tr>
            <td>질문이 없습니다</td>
        </tr>
        {%endif%}
    </tbody>
</table>


## 질문 폼 만들기
\pybo\forms.py
from flask_wtf import FlaskForm
from wtforms import StringField, TextAreaField
from wtforms.validators import DataRequired

class QuestionForm(FlaskForm):
    subject = StringField('제목', validators=[DataRequired()])
    # validators 검증, DataREquired-필수항목인지 체크, Email-이메일인지 체크, Length-길이 체크 등
    content = TextAreaFiedl('내용', validators=[DataRequired()])
    

# 질문등록 라우팅함수 변경
\pybo\question_views.py
...
from datetime import datetime
from flask import Blueprint, render_template, request, url_for
from werkzeug.utils import redirect

from .. import db
from pybo.models import Question
from pybo.forms import QuestionForm

...
@bp.route('/create', methods=('GET','POST')) # GET, POST 요청을 받음
def create():
    form = QuestionForm()
    if request.method == 'POST' and form.validate_on_submit(): # validate_on_submit() 입력받은 폼의 정합성 검사
        question = Question(subject=form.subject.data, content=form.content.data, create_date=datetime.now())
        db.session.add(question)
        db.session.commit()
        return redirect(url_for('main.index'))
    return render_template('question/question_form.html', form=form)


# 질문 폼 템플릿 추가
\pybo\templates\question\question_form.html
{% extends 'base.html' %}
{% block content %}
<div class="container">
    <h5>질문등록</h5>
    <form method="post">
        {{ form.csrf_token }}
        {{ form.subject.label }}
        {{ form.subject() }}

        {{ form.content.label }}
        {{ form.content() }}

        <button type="submit">저장하기</button>
    </form>
</div>
{% endblock %}

## 수작업 폼
    <form method="post">
        {{ form.csrf_token }}
        <label for="subject">제목</label>
        <input type="text" name="subject">

        <label for="content">내용</label>
        <textarea name="content" id="" rows="10"></textarea>
        <button type="submit">저장하기</button>
    </form>


### 폼의 내용없이 저장버튼 누르면 에러메시지 출력 시 제목란에 입력한게 사라지지 않게
        <input type="text" name="subject" value="{{ form.subject.data or '' }}">


# 입력란이 비었을 때 오류 메시지 출력
> question_form.html - <form> 내부에 추가 
        {% if form.errors %}
        {% for field, errors in form.errors.items() %}
        <strong>{{ form[field].label }}</strong>
        <ul>
            {% for error in errors %}
            <li>{{ error }}</li>
            {% endfor %}
        </ul>
        {% endfor %}
        {% endif %}

> forms.py
class QuestionForm(FlaskForm):
    subject = StringField('제목', validators=[DataRequired('제목은 필수')])
    # validators 검증, DataREquired-필수항목인지 체크, Email-이메일인지 체크, Length-길이 체크 등
    content = TextAreaField('내용', validators=[DataRequired('내용도 필수')])
    
```

네비게이션 include
--------------------

![image](https://user-images.githubusercontent.com/30430227/179896280-1deef101-d1cf-471d-a0a4-bb153cc0666d.png)

```
pybo\template\navbar.html
<nav>
    <div>
        <a href="{{url_for('main.index')}}">홈</a>
        <div>
            <ul>
                <li><a href="#">계정생성</a></li>
                <li><a href="#">로그인</a> </li>
            </ul>
        </div>
    </div>
</nav>

base.html에 추가
    {% include 'navbar.html' %}

```

게시판 페이징 - paginate 함수
-----------------------------

```
$ export FLASK_APP=pybo
$ flask shell
> from pybo import db
> from pybo.models import Question
> from datetime import datetime

> for i in range(300):
    q = Question(subject='테스트 데이터입니다:[%03d]' % i, content='내용무', create_date=datetime.now())
    db.session.add(q)

>  db.session.commit()
```

```
\pybo\views\question_views.py
@bp.route('/list/')
def _list():
    page = request.args.get('page',type=int, default=1)
    # '.../?page=5' 방식으로 요청한 URL에서 page값을 가져온다, default=1(page 요청 URL이 없으면 기본값인 1 즉 /?page=1을 보여준다)
    question_list = Question.query.order_by(Question.create_date.desc())
    question_list = question_list.paginate(page, per_page=10)
    # paginate 함수, page(페이지 번호), per_page(페이지게시물 건 수)
    return render_template('question/question_list.html',question_list=question_list)
```

![image](https://user-images.githubusercontent.com/30430227/179907027-1d44c8c6-1705-4f0d-8e1d-a64ec34c80cf.png)

```
# pagenate 객체
items	현재 페이지에 해당하는 게시물 리스트	[<Question 282>,<Question 283>, ...]
page	현재 페이지 번호	2
iter_pages	페이지 범위	[1, 2, 3, 4, 5, None, 30, 31]
prev_num / next_num	이전 페이지 번호 / 다음 페이지 번호	현재 페이지가 3인 경우, 2 / 4
has_prev / has_next	이전 페이지 존재 여부 / 다음 페이지 존재 여부	True / False

\pybo\templates\question\question_list.html
        {% for question in question_list %}를
        {% for question in question_list.items %}로 바꾼다
        
# 페이지 이동버튼 추가
</table>
<ul class="paginate">
    {% if question_list.has_prev %}
    <li><a href="?page={{ question_list.prev_num }}">이전</a></li>
    {% else %}
    <li>이전</li>
    {% endif %}
    {% for page_num in question_list.iter_pages() %}
    {% if page_num %}
    {% if page_num !=question_list.page %}
    <li><a href="?page={{page_num}}">{{page_num}}</a></li>
    {% else %}
    <li>{{page_num}}</li>
    {% endif %}
    {%else%}
    <li>...</li>
    {%endif%}
    {% endfor %}
    <!-- 다음페이지 -->
    {% if question_list.has_next %}
    <li><a href="?page={{question_list.next_num}}">다음</a></li>
    {% else %}
    <li>다음</li>
    {% endif %}
</ul>

/style.css
ul.paginate{
    display:flex;
    list-style: none;
}

.paginate li{
    padding-left:10px
}
```

템플릿 필터로 날짜 포멧 바꾸기
-------------------------

![image](https://user-images.githubusercontent.com/30430227/179908658-021eabb7-ee54-4a2f-9a8a-7677d942b5e6.png)

![image](https://user-images.githubusercontent.com/30430227/179908695-626634c1-a13a-4433-a5f0-59171ea4afd2.png)

```
\pybo\filter.py
def format_datetime(value, fmt='%Y년 %m월 %d일 %p %I:%M'):
    return value.strftime(fmt)
    
\pybo\__init__.py 에 추가
    #필터
    from .filter import format_datetime
    app.jinja_env.filters['datetime']=format_datetime

    return app

\question_list.html 에 적용
   <td>{{ question.create_date|datetime }}</td>
            
```


게시물 번호 매기기
------------------

![image](https://user-images.githubusercontent.com/30430227/179911866-be00e6fe-4264-485c-abbe-7d99c20f16d0.png)

```
# 공식
.total - (.page -1)*.per_page - loop.index0
> question_list.total전체 개수, ..page현재 페이지, ..per_page페이지당 게시물 수, loop.index0 해당 페이지의 나열 인덱스(0을 붙이면 0,1,2,3..으로 번호가 붙는다)
>> .total 는 끝 번호
>> .total -(.page -1)*.per_page 는 다음 페이지의 시작 번호가 된다. 여기서 나열 인덱스 0 ~ 갯수만큼 뺀 것이 순서대로 번호가 된다

\question_list.html 수정
{{ loop.index }} => {{ question_list.total -((question_list.page-1)*question_list.per_page)- loop.index0 }}

```

답변 개수 추가
--------------

![image](https://user-images.githubusercontent.com/30430227/179912496-fe08cfc1-7203-4024-a7a6-9424c2d02bbc.png)

```
이미지는 일부러 CSS 적용함 \question_list.html에 추가
    <a href="{{ url_for('question.detail', question_id=question.id) }}">{{ question.subject }}</a> 아래에
    {% if question.answer_set|length >0 %}
    <span>{{question.answer_set|length}}</span>
    {%endif%}
```

회원가입
---------

![image](https://user-images.githubusercontent.com/30430227/179930929-478f484b-2773-40b7-b982-66c277b7e6ac.png)

```
# 회원 모델 생성 \models.py
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(20), unique=True, nullable=False)
    password = db.Column(db.String(20), nullable=False)
    email = db.Column(db.String(20), unique=True, nullable=False)
> id 는 자동으로 증가하는 기본키
> unique 는 같은 값 불가

# 리비전(리~버전 생성)
$ flask db migrate
후 DB도 변경
$ flask db upgrade

# 회원가입 폼 추가 \forms.py 수정 - Length 길이 검증, EqualTo 같은지 검증
from flask_wtf import FlaskForm
from wtforms import StringField, TextAreaField, PasswordField, EmailField
from wtforms.validators import DataRequired, Length, EqualTo, Email
...

class UserCreateForm(FlaskForm):
    username = StringField('사용자이름', validators=[DataRequired(), Length(min=3, max=15)])
    password = PasswordField('비밀번호', validators=[DataRequired(), EqualTo('password2', '비밀번호가 일치하지 안소')])
    password2 = PasswordField('비밀번호확인', validators=[DataRequired()])
    email = EmailField('이메일', validators=[DataRequired(), Email()])

# 이메일 검증을 위한 모듈 설치
$  pip install email_validator

# 회원가입 블루프린트 생성 \views\auth_views.py
from flask import Blueprint, url_for, render_template, flash, request
from werkzeug.security import generate_password_hash
from werkzeug.utils import redirect

from pybo import db
from pybo.forms import UserCreateForm
from pybo.models import User

bp = Blueprint('auth',__name__,url_prefix='/auth')

@bp.route('/signup',methods=('GET','POST'))
def signup():
    form = UserCreateForm()
    if request.method =='POST' and form.validate_on_submit():
        user = User.query.filter_by(username=form.username.data).first() # 기존 유저가 있으면 User에 대입
        if not user:
            user = User(username=form.username.data, password=generate_password_hash(form.password1.data), email=form.email.data)
            db.session.add(user)
            db.session.commit()
            return redirect(url_for('main.index'))
        else:
            flash('이미 존재하는 사용자입니다') # flash 에러 발생 함수
    return render_template('auth/signup.html', form=form)


# 블루프린트 등록 __init__.py
    from .views import main_views, question_views, answer_views, auth_views
    ...
    app.register_blueprint(auth_views.bp)


# 회원가입 템플릿 - \templates\auth\signup.html
>> form action 을 비워두면 현재 URL로 폼을 전송한다
{% extends 'base.html' %}
{% block content %}
<div>
    <h5>계정생성</h5>
    <form action="" method="post">
        {{form.csrf_token}}
        {% include "form_errors.html" %}
        <div>
            <label for="username">사용자이름</label>
            <input type="text" name="username" id="username" value="{{ form.username.data or '' }}">
        </div>
        <div>
            <label for="password1">비밀번호</label>
            <input type="password" name="password1" id="password1" value="{{ form.password1.data or '' }}">
        </div>
        <div>
            <label for="password2">비밀번호 확인</label>
            <input type="password" name="password2" id="password2" value="{{ form.password2.data or '' }}">
        </div>
        <div>
            <label for="email">이메일</label>
            <input type="text" name="email" id="email" value="{{ form.email.data or '' }}">
        </div>
        <button type="submit">생성하기</button>
    </form>
</div>

{% endblock %}


# \templates\form_errors.html
form_errors.html 템플릿 파일은 다음과 같이 "필드에서 발생한 오류를 표시하는 부분"과 "flash를 거치면서 발생한 오류를 표시하는 부분"으로 구성된다.
필드 오류는 폼 validators 검증에 실패한 경우 표시되고, flash 오류는 flash('이미 존재하는 사용자입니다.')와 같은 로직에 의해 표시된다.

<!-- 필드오류 -->
{% if form.errors %}
<div>
    {% for field, errors in form.errors.items() %}
    <strong>{{ form[field].label }}</strong>
    <ul>
        {% for error in errors %}
        <li>{{ error }}</li>
        {% endfor %}
    </ul>
    {% endfor %}
</div>
{% endif %}

<!-- flash오류 -->
{% for message in get_flashed_messages() %}
<div>{{message}}</div>
{% endfor %}


\navbar.html 수정
<li><a href="{{ url_for('auth.signup') }}">계정생성</a></li>


$ flask shell 에서 등록한 사용자 확인
> from pybo.models import User
> User.query.all()
> User.query.first().username

```

로그인
-------

![image](https://user-images.githubusercontent.com/30430227/179962334-f054da8a-bd0a-47b8-a138-f5d452640bb4.png)

![image](https://user-images.githubusercontent.com/30430227/179965626-ed31d1e8-80e4-428f-9675-1ec380c772ae.png)

```
사용자도 존재하고 비밀번호도 일치한다면 플라스크 세션(session)에 사용자 정보를 저장한다.세션은 서버에 브라우저별로 생성되는 메모리 공간
쿠키는 서버가 웹 브라우저에 발행하는 값이다. 웹 브라우저는 서버에서 받은 쿠키를 저장한다. 이후 서버에 다시 요청을 보낼 때는 저장한 쿠키를 HTTP 헤더에 담아서 전송한다.
그러면 서버는 웹 브라우저가 보낸 쿠키를 이전에 발행했던 쿠키값과 비교하여 같은 웹 브라우저에서 요청한 것인지 아닌지를 구분할 수 있다.
이때 세션은 바로 쿠키 1개당 생성되는 서버의 메모리 공간이라고 할 수 있다.
\forms.py
class UserLoginForm(FlaskForm):
    username = StringField('사용자이름', validators=[DataRequired(), Length(min=3, max=15)])
    password = PasswordField('비밀번호', validators=[DataRequired()])
    
\auth_views.py
from flask import Blueprint, url_for, render_template, flash, request, session
from werkzeug.security import generate_password_hash, check_password_hash
...
from pybo.forms import UserCreateForm, UserLoginForm
...
@bp.route('/login', methods=('GET','POST'))
def login():
    form = UserLoginForm()
    if request.method =='POST' and form.validate_on_submit():
        error=None
        user = User.query.filter_by(username=form.username.data).first()
        if not user:
            error ='존재하지 않는 사용자니더'
        elif not check_password_hash(user.password, form.password.data):
            error='비빌번호가 올바르지 않아서'
        if error is None:
            session.clear()
            session['user_id']=user.id
            return redirect(url_for('main.index'))
        flash(error)
    return render_template('auth/login.html', form=form)
    

\templates\auth\login.html 생성
{% extends 'base.html' %}
{% block content %}
<div>
    <h5>로그인</h5>
    <form action="" method="post">
        {{form.csrf_token}}
        {% include 'form_errors.html' %}
        <div>
            <label for="username">사용자이름</label>
            <input type="text" name="username" id="username" value="{{ form.username.data or '' }}">
        </div>
        <div>
            <label for="password">비밀번호</label>
            <input type="password" name="password" id="password" value="{{ form.username.data or '' }}">
        </div>
        <button type="submit">로그인</button>
    </form>
</div>
{% endblock %}

\navbar.html 추가
 <li><a href="{{ url_for('auth.login') }}">로그인</a> </li>


# 로그인 여부 -\auth_views.py
@bp.before_app_request는 라우팅 함수보다 먼저 실행된다.
> g는 플라스크의 컨텍스트 변수, session 변수에 user_id값이 있으면(session.get) user_id에 대입
> User DB에서 조회query.get하여 user 객체 g.user에 대입 

from flask import Blueprint, url_for, render_template, flash, request, session , g
...
@bp.before_app_request
def load_logged_in_user():
    user_id = session.get('user_id')
    if user_id is None:
        g.user = None
    else:
        g.user = User.query.get(user_id)

@bp.route('/logout')
def logout():
    session.clear()
    return redirect(url_for('main.index'))
    
\navbar.html 수정
        <div>
            {% if g.user %}
            <ul>
                <li><a href="{{url_for('auth.logout')}}">{{ g.user.username }}(로그아웃)</a></li>
            </ul>
            {% else %}
            <ul>
                <li><a href="{{ url_for('auth.signup') }}">계정생성</a></li>
                <li><a href="{{ url_for('auth.login') }}">로그인</a> </li>
            </ul>
            {% endif %}
        </div>

```

모델 수정하기
--------------

```
# SQLite 버그패치 __init__.py
...
from sqlalchemy import MetaData

import config

naming_convention = {
    "ix": 'ix_%(column_0_label)s',
    "uq": "uq_%(table_name)s_%(column_0_name)s",
    "ck": "ck_%(table_name)s_%(column_0_name)s",
    "fk": "fk_%(table_name)s_%(column_0_name)s_%(referred_table_name)s",
    "pk": "pk_%(table_name)s"
}
db = SQLAlchemy(metadata=MetaData(naming_convention=naming_convention))
migrate = Migrate()
...
    db.init_app(app)
    if app.config['SQLALCHEMY_DATABASE_URI'].startswith("sqlite"):
        migrate.init_app(app, db, render_as_batch=True)
    else:
        migrate.init_app(app, db)
    from . import models
    
>> flask db migrate > flask db upgrade 명령 실행하여 DB 변경한다


# Question 모델 필드 추가 user_id
class Question(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    subject = db.Column(db.String(200), nullable=False)
    content = db.Column(db.Text(), nullable=False)
    create_date = db.Column(db.DateTime(), nullable=False)
    user_id = db.Column(db.Integer, db.ForeignKey('user.id',ondelete='CASCADE'), nullable=False)
    user = db.relationship('User', backref=db.backref('question_set'))

에러! user_id의 nullable=False인데 이미 저장되어있는 question 데이터에는 user_id가 없어서 발생
> nullable =True > server_default='1'(기본 user_id를 1로, 이전 데이터도 1의 값을 추가한다
    user_id = db.Column(db.Integer, db.ForeignKey('user.id',ondelete='CASCADE'), nullable=True, server_default='1')
> flask db upgrade 명령을 수행할 때 server_default는 이전 데이에도 1의 값 추가<=>default는 앞으로 추가할 데이터에만 적용)
> 최종리비전과 현재 리비전이 달라 upgrade가 수행되지 않는다(>flask db heads > flask db current) > flask db stamp heads
> migrate, upgrade 실행
> nullable=False 로 바꾸고 server_default는 제거한다 >migrate, upgrade 실행


# Answer 모델도 같은 작업
    user_id = db.Column(db.Integer, db.ForeignKey('user.id',ondelete='CASCADE'), nullable=True, server_default='1')
    user = db.relationship('User', backref=db.backref('answer_set'))
> migrate, upgrade 실행 > nullable=False로 바꾸고 server_default 제거 후 migrate, upgrade 실행


# question_vies.py 수정
from flask import Blueprint, render_template, request, url_for, g # g 추가
...
question = Question(subject=form.subject.data, content=form.content.data, create_date=datetime.now(),user=g.user) # user=g.user 추가


# 로그아웃 시 '질문등록' 누르면 로그인페이지로 가기 - 코드 중복을 피하기위해 데코레이션 생성
> @functools- 기존함수를 감싸서 실행, g.user가 없으면 로그인 페이지로, next는 로그인 후 원래페이지로 되돌아가기 위한 파라미터
\auth_views.py
import functools
...
def login_required(view):
    @functools.wraps(view)
    def wrapped_view(*args,**kwargs):
        if g.user is None:
            _next=request.url if request.method == 'GET' else ''
            return redirect(url_for('auth.login', next=_next))
        return view(*args, **kwargs)
    return wrapped_view

# \auth_views.py > login 함수 수정
        if error is None:
            session.clear()
            session['user_id']=user.id
            _next = request.args.get('next','')
            if _next:
                return redirect(_next)
            else:
                return redirect(url_for('main.index'))
        flash(error)
        
# \question_views.py 수정
from pybo.views.auth_views import login_required 추가

@bp.route('/create', methods=('GET','POST'))
@login_required # 이부분에 추가
def create():
    form=QuestionForm()


# 로그아웃 상태에는 답변등록 불가하게 \question_detail.html 수정
<textarea {% if not g.user %}disabled{%endif%} name="content" id="content" rows="10"></textarea>

```


글쓴이 표시하기 
------------------

![image](https://user-images.githubusercontent.com/30430227/180122138-566dbb2c-6fc3-494d-9aea-d8d08d538ee9.png)

```
\question_list.html
            <th>제목</th>
            <th>글쓴이</th>
            <th>작성일시</th>
...            
            <td>{{question.user.username}}</td>
```


게시물 수정/삭제
----------------

```
\models.py > Question 클래스에 추가
    modify_date = db.Column(db.DateTime(), nullable=True)
    
# migrate, upgrade 실행
\question_views.py
from flask import Blueprint, render_template, request, url_for, g, flash # flash 추가
...
@bp.route('/modify/<int:question_id>', methods=('GET','POST'))
@login_required
def modify(question_id):
    question = Question.query.get_or_404(question_id)
    if g.user != question.user:
        flash('수정권한이 없습니다')
        return redirect(url_for('question.detail', question_id=question_id))
    if request.method == 'POST':
        form = QuestionForm()
        if form.validate_on_submit():
            form.populate_obj(question)
            # .populate_obj(question)는 form 변수에 들어 있는 데이터(화면에서 입력한 데이터)를 question 객체에 업데이트 하는 역할
            question.modify_date = datetime.now()
            db.session.commit()
            return redirect(url_for('question.detail', question_id=question_id))
    else:
        form=QuestionForm(obj=question)
    return render_template('question/question_form.html', form=form)

@bp.route('/delete/<int:question_id>')
@login_required
def delete(question_id):
    question = Question.query.get_or_404(question_id)
    if g.user !=question.user:
        flash('삭제권한나이')
        return redirect(url_for('question.detail', question_id=question_id))
    db.session.delete(question)
    db.session.commit()
    return redirect(url_for('question._list'))

\question_detail.html 에 flash 기능, 수정 버튼 추가
<!-- flash오류 -->
{% for message in get_flashed_messages() %}
<s>{{message}}</s>
...
    <a href="{{url_for('question.modify', question_id=question.id)}}">
        <input type="button" value="수정">
    </a>
    

# 삭제버튼 추가 - 정말로? 확인 기능을 추가
\base.html - 화면이 전부 로딩된 후에 스크립트 실행하기 위해서 </body>태그 바로 위에 넣어준다
...
    {% block script %}
    {% endblock %}
</body>


\question_detail.html
> javascript:void(0)로 설정하면 해당 링크를 클릭해도 아무런 동작도 하지 않는다
> data-uri - 자바스크립스에 전달
> "삭제" 버튼을 클릭하고 "확인"을 선택하면 data-uri 속성에 해당하는 {% url 'pybo:question_delete' question.id %} URL이 호출될 것이다.
    <a href="javascript:void(0" class="delete" data-uri="{{ url_for('question.delete',question_id=question.id) }}">
        <input type="button" value="삭제">
    </a>
...
{% block script %}
<script>
    const delete_elements = document.querySelectorAll('.delete')
    Array.from(delete_elements).forEach(function (element) {
        element.addEventListener('click', function () {
            if (confirm('정말로 삭제하시겠습니?')) {
                location.href = this.dataset.uri;
            }
        })
    })
</script>
{% endblock %}

```


추천 기능 추가 
----------------


```
# 테이블 객체 생성
\models.py
> 사용자 id와 질문 id를 쌍으로 갖는 테이블 객체
> user_id와 question_id 는 프라이머리키이므로 두개의 값이 모두 같은 데이터는 저장될 수 없다.

question_voter = db.Table(
    'question_voter',
    db.Column('user_id', db.Integer, db.ForeignKey('user.id', ondelete='CASCADE'), primary_key=True),
    db.Column('question_id', db.Integer, db.ForeignKey('question.id', ondelete='CASCADE'),primary_key=True)
)
```

![image](https://user-images.githubusercontent.com/30430227/180150509-193f2c75-8c66-4cf3-b6f9-cadd2d998968.png)
![image](https://user-images.githubusercontent.com/30430227/180150582-86c6f017-5348-45b2-b3ae-e697ad6d7a84.png)

```
# \models.py
> Question 클래스에 추천인 필드 추가
> secondary - 실재 데이터가 저장되는 테이블을 question_voter로 정한다

    voter = db.relationship('User', secondary=question_voter, backref=db.backref('quesion_voter_set'))

> migrate, upgrade 실행

```

![image](https://user-images.githubusercontent.com/30430227/180158196-40f594e4-019f-4827-9cd5-0da01532843c.png)

```    
* 추천 라우팅 함수 \question_views.py
@bp.route('/vote/<int:question_id>')
@login_required
def vote(question_id):
    _question = Question.query.get_or_404(question_id)
    if g.user == _question.user:
        flash('본인은 추천불가!!')
    else:
        _question.voter.append(g.user)
        db.session.commit()
    return redirect(url_for('question.detail', question_id=question_id))


* 질문 추천 버튼 \quesion_detail.html
<a href="javascript:void(0)" data-uri="{{ url_for('question.vote', question_id=question.id) }}" class="recommend">추천</a>
<s>{{ question.voter|length}}</s>
...
    const recommend_elements = document.querySelectorAll('.recommend')
    Array.from(recommend_elements).forEach(function (element) {
        element.addEventListener('click', function () {
            if (confirm('정말로?')) {
                location.href = this.dataset.uri
            }
        })
    })
    

```


검색 기능 
----------

```
* Join - 한줄로
> 홍길동인 user가 작성한 질문들만 찾기
user = User.query.get(User.username=='홍길동')
Question.query.filter(Question.user_id==user.id)
=> Question.query.join(User).filter(User.username=='홍길동')

* 아우터조인 
$ flask shell
> from pybo.models import Question, Answer >Question.query.count() >Answer.query.count()
>Question.query.join(Answer).count() # join은 교집합의 갯수를 출력한다
>Question.query.outerjoin(Answer).count() # outerjoin은 합집합
> distinct 붙이면 outjoin에서 Qeustion 갯수만 나옴

* 서브쿼리 - 모델 자체를 사용하기보다는 필요한 데이터만 모아서 조회하는 데 사용(join하여)


\question_views.py _list 함수에 검색 기능 추가
from ..models import Question, Answer, User
...
@bp.route('/list/')
def _list():
    page = request.args.get('page',type=int, default=1)
    # '.../?page=5' 방식으로 요청한 URL에서 page값을 가져온다, default=1(page 요청 URL이 없으면 기본값인 1 즉 /?page=1을 보여준다)
    question_list = Question.query.order_by(Question.create_date.desc())
    # paginate 함수, page(페이지 번호), per_page(페이지게시물 건 수)
    kw = request.args.get('kw', type=str, default='')
    if kw:
        search = '%%{}%%'.format(kw)
        sub_query = db.session.query(Answer.question_id, Answer.content, User.username)\
            .join(User, Answer.user_id == User.id).subquery()
        question_list = question_list \
            .join(User) \
            .outerjoin(sub_query, sub_query.c.question_id == Question.id) \
            .filter(Question.subject.ilike(search) |   # 질문제목, ilike -대소문자 구분안함
                Question.content.ilike(search) |       # 질문 내용
                User.username.ilike(search) |          # 질문 작성자
                sub_query.c.content.ilike(search) |    # 답변 내용
                sub_query.c.username.ilike(search)     # 답변 작성자
             ).distinct()
    question_list = question_list.paginate(page, per_page=10) # 이 라인 위치 중요. paginate 는 outerjoin 후에 처리한다
    return render_template('question/question_list.html',question_list=question_list, page=page, kw=kw)

```


![image](https://user-images.githubusercontent.com/30430227/180179299-8bc5005e-39ce-455e-bbd9-efdd54c51c5c.png)

```
\question_list.html 검색창 추가
<div>
    <input type="text" id="search_kw" value="{{ kw or '' }}">
    <button id="btn_search">찾기</button>
</div>

* 검색과 페이징이 동시 처리되려면 위에서 모든 페이지 링크를 href 속성에 직접 입력하는 대신
  form을 통해 페이징이 요청 data-page 속성으로 값을 읽을 수 있도록 변경(?page=1 방식)

... 수정내용
    <li><a href="javascript:void(0)" data-page="{{ question_list.prev_num }}" class="page_link">이전</a></li>
    <li><a href="javascript:void(0)" data-page="{{page_num}}" class="page_link">{{page_num}}</a></li>
    <li><a href="javascript:void(0)" data-page="{{question_list.next_num}}" class="page_link">다음</a></li>
    
<form action="{{ url_for('question._list')}}" method="get" id="searchForm">
    <input type="hidden" id="kw" name="kw" value="{{ kw or '' }}">
    <input type="hidden" id="page" name="page" value="{{ page }}">
</form>
{% endblock %}

```


라즈베리파이 
---------------

`핀번호 보기 > pinout`

```
# happy.py
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return 'Hi'

if __name__=='__main__':
    app.run(debug=True, port=80, host='0.0.0.0')
    
    
# 실행 
> export FLASK_APP='hello'
> export FLASK_ENV=development
> flask run

## 외부 연결 목적으로 실행
> sudo python3 hello.py

## 외부 컴에서 접속
192.168.0.80

# HTML
\templates\index.html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>라즈베리파</title>
</head>

<body>
    <h1>GPIO 테스트</h1>
    <hr>
    <div>
        <h3>something to do</h3>
        <ul>
            <li>eat</li>
            <li>study</li>
            <li>watching</li>
        </ul>
    </div>
</body>

</html>

## hello.py 수정
from flask import Flask, render_template
...
@app.route('/')
def index():
    return render_template('index.html')


# URL함수 추가
@app.route('/<username>')
def hello(username):
    return render_template('index.html', user=username)

## HTML 수정
...
<body>
    {% if user %}
    <p>Nice to meet you. {{ user }}</p>
    {% endif %}
    <h1>GPIO 테스트</h1>
...

```


모터 제어 
----------

![image](https://user-images.githubusercontent.com/30430227/179503879-edea1222-9c0a-4e18-bbc2-c2b6797c9f8f.png)

```
# hello.py
from flask import Flask, render_template, url_for, redirect
import RPi.GPIO as GPIO
from time import sleep

GPIO.setmode(GPIO.BCM)

GPIO.setup(16, GPIO.OUT)
GPIO.setup(20, GPIO.OUT)
GPIO.setup(21, GPIO.OUT)

pwm = GPIO.PWM(16,100)
pwm.start(0)
pwm.ChangeDutyCycle(30)

app = Flask(__name__)


@app.route('/')
def index():
    return render_template('index.html')

@app.route('/<dir>')
def motor(dir):
    if dir=='forward':
        print('앞으로')
        GPIO.output(20, 1)
        GPIO.output(21, 0)
    elif dir=='backward':
        print('뒤로')
        GPIO.output(20, 0)
        GPIO.output(21, 1)
    elif dir=='stop':
        GPIO.output(20, 0)
        GPIO.output(21, 0)
    return render_template('index.html', dir=dir)
    
@app.route('/<int:speed>')
def speed(speed):
    pwm.ChangeDutyCycle(speed)
    return render_template('index.html')

if __name__=='__main__':
    app.run(debug=True, port=80, host='0.0.0.0')


# index.html
    <div>
        <h3>something to do</h3>
        <p>
            <b>모터방향: {% if dir=='forward' %}전진
                {% elif dir=='backward' %}후진
                {% elif dir=='stop' %}정지
                {% endif %}
            </b>
            <a href="{{ url_for('motor', dir ='forward') }}"><input type="button" value="전진"></a>
            <a href="{{ url_for('motor', dir = 'backward') }}"><input type="button" value="후진"></a>
            <a href="{{ url_for('motor', dir = 'stop') }}"><input type="button" value="정지"></a>
        </p>
        <p>
            <b>스피드</b>
            <a href="{{ url_for('speed', speed=10) }}">스피드10</a>
            <a href="{{ url_for('speed', speed=50) }}">스피드50</a>
            <a href="{{ url_for('speed', speed=100) }}">스피드100</a>

        </p>
</div>

</html>

```
