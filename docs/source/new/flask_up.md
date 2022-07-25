FlaskUP
========

1. .flaskenv, 폴더 생성

```
* .flaskenv
$ touch .flaskenv
FLASK_APP=base
FLASK_ENV=development

$ mkdir core
$ cd core
$ touch __init__.py 
```


2. Template - 플라스크는 jinja2 신사 템플릿을 기본으로 사용한다

![image](https://user-images.githubusercontent.com/30430227/180363701-9bc0971f-5be9-4f56-ad2f-c190d6a35a93.png)

```
$ cd core
$ mkdir templates
$ touch index.html
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

3. \core\__init__.py

```
* __name__ 생성한 모듈명 즉 'core'
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    greet ='Hello there, Ace'
    return render_template('index.html', greet=greet)

$ cd ..
$ touch base.py
from core import app

$ flask run

```


To Do List
----------------

![image](https://user-images.githubusercontent.com/30430227/180382412-f89fa670-de46-44b2-b172-cf44603258cd.png)

1. DB

```
* 모듈 설치
$ pip install flask-migrate //flask-sqlalchemy도 같이 설치됨


* 보안
$ touch .env
SECRET_KEY = lisney

$ touch config.py
import os
from dotenv import load_dotenv

load_dotenv()
BASE_DIR = os.path.abspath(os.path.dirname(__file__))

class Configuration(object):
    SECRET_KEY = os.environ.get('SECRET_KEY')
    SQLALCHEMY_DATABASE_URI = 'sqlite:///' + os.path.join(BASE_DIR, 'todo.db')
    SQLALCHEMY_TRACK_MODIFICATIONS = False //database 가 변경될 때 알림기능 끔


* __init__.py 수정
from flask import Flask, render_template
from config import Configuration
from flask_sqlalchemy import SQLAlchemy
from flask_migrate import Migrate

app = Flask(__name__)
app.config.from_object(Configuration)
db=SQLAlchemy(app) # db.init_app(app) -db 객체를 app에 등록
migrate = Migrate(app, db) # migrate.init_app(app,db) - migrate에 app과 db 등록

from . import models

@app.route('/')
def index():
    greet ='Hello there, Ace'
    return render_template('index.html', greet=greet)


* \core\models.py 데이터 모델 생성
from core import db

class Todo(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    create_date = db.Column(db.DateTime, nullable=False)
    category = db.Column(db.String, db.ForeignKey('category.id'))
    # 추후 category 데이터베이스에 연결된다
    def __repr__(self): # 이 객체를 표시할 형식 지정, 게시물등에서..
        return '<ToDo {}>'.format(self.title)

```

2. Task 블루프린트 

```
$ pip install flask-wtf //폼 모듈 설치

* \core\task\__init_.py
from flask import Blueprint

task = Blueprint('task',__name__,template_folder='templates') # template_folder 없어도 

from . import views


* \core\task\models.py
from .. import db

class Category(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(20))

    def __repr__(self):
        return '<Category {}>'.format(self.name)
        
        
 * \core\task\forms.py
 from flask_wtf import FlaskForm
from wtforms import StringField, TimeField, DateField, SubmitField, SelectField
from wtforms.validators import DataRequired, Length, Email, EqualTo 

class TaskForm(FlaskForm):
    title = StringField('제목', validators=[DataRequired()])
    category = SelectField('카테고리', coerce=int, validators=[DataRequired()])
    # coerce 강제, int() 함수를 강제로 적용하다?
    date = DateField('날짜', format='%Y-%m-%d', validators=[DataRequired()])
    time = TimeField('시간', format='%H:%M', validators=[DataRequired()])
    submit = SubmitField('작업추가')
 
* \core\task\views.py
from flask import render_template, redirect, url_for, request
from .models import Category
from ..models import Todo
from . import task
from .forms import TaskForm
from .. import db
from datetime import datetime

@task.route('/create-task', methods=['GET','POST'])
def tasks():
    check=None # 템플릿 오류 전달 변수
    todo=Todo.query.all() 
    date=datetime.now()
    now=date.strftime('%Y-%m-%d') # .strftime 날짜시간 포멧 함수

    form = TaskForm()
    form.category.choices = [(category.id, category.name) for category in Category.query.all()]

    return render_template('task/tasks.html',todo=todo, title='Create Tasks', form=form, DateNow=now, check=check) ## todo를 맨앞에 두기
    
    
* 블루프린트 등록 \core\__init__.py 에 추가
...
from .task import task as task_blueprint
app.register_blueprint(task_blueprint)

```


3. DB 생성 \flask\ -- dotenv 에러 시 $ sudo pip install python-dotenv

```
$ flask db init
$ flask db migrate
% flask db upgrade

* 카테고리 생성
$ flask shell
>>> from core.task.models import Category
>>> from core import db
>>> ctgry1 = Category(name='Business')
>>> ctgry2 = Category(name='Personal')
>>> ctgry3 = Category(name='Other')
>>> db.session.add(ctgry1)
>>> db.session.add(ctgry2)
>>> db.session.add(ctgry3)
>>> db.session.commit()
>>> categories = Category.query.all()
>>> for c in categories:
...     print(c.name)
... 
Business
Personal
Other

```


4. base Template생성 \core\templates\base.html

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    {% if title %}
    <title>{{ title }}</title>
    {% else %}
    <title>Todo List</title>
    {% endif %}
</head>

<body>
    {% block content %}
    {% endblock content %}
</body>

</html>
```


5. tasks.html 생성 \core\templates\task\tasks.html

```
* novalidate 폼 제출 시 유효성 검사 하지 않음
* {{ form.hidden_tag() }} - cross site request forgery(csrf) 공격을 막는 csrf token을 가져온다

{% extends 'base.html' %}

{% block content %}

<div class="task_content categories">
    <div class="">
        <div class="content">
            <div class="welcome">
                <button id="openbutton" class="openbtn">&#9776;</button>
                <span class="welcome-text">Manage Your ToDo List</span>
            </div>

            <form action="" method="post" novalidate>
                {{ form.hidden_tag() }}
                <div class="inputContainer Task">
                    {{ form.title.label }}<br>
                    {{ form.title(size=20) }}
                    {% for error in form.title.errors %}
                    <span style="color: red;">[{{ error }}]</span>
                    {% endfor %}
                </div>
                <div class="inputContainer choice ">
                    {{ form.category.label}}<br>
                    {{ form.category}}
                    {% for error in form.category.errors %}
                    <span style="color: red;">[{{ error }}]</span>
                    {% endfor %}
                </div>
                <div class="inputContainer  date ">
                    {{ form.date.label }}<br>
                    {{ form.date }}
                    {% for error in form.date.errors %}
                    <span style="color: red;">[{{ error }}]</span>
                    {% endfor %}
                </div>
                <div class="inputContainer  time">
                    {{ form.time.label }}<br>
                    {{ form.time }}
                    {% for error in form.time.errors %}
                    <span style="color: red;">[{{ error }}]</span>
                    {% endfor %}
                </div>
                <div class="buttons">
                    {{ form.submit(class="taskAdd btn") }}
                </div>
            </form>
            <!-- Task Delete Error alert -->
            {% if check %}
            <div class="alert alert-warning" role="alert">
                <span class="closebtns" onclick="this.parentElement.style.display='none';">&times;</span>
                {{check}}
            </div>
            {% endif %}
            <!-- End Task Delete error alert -->

            <form action="" method="post">
                {{ form.hidden_tag() }}
                <!-- csrf token for security -->

                <div class="tabs effect-1">
                    <!-- tab-content -->
                    <div class="tab-content">
                        <section id="tab-item-1">
                            <ul class="taskList">
                                {% for todo in todo %}
                                <li class="currentTaskItem">
                                    <input type="checkbox" class="taskCheckbox" name="checkedbox" id="{{ todo.id }}"
                                        value="{{ todo.id }}">
                                    <label for="{{ todo.id }}"><span class="complete-">{{ todo.title }}</span></label>
                                    <span class="taskDone">at</span>
                                    <strong class="taskDone"><i class="fa fa-clock-o"></i> {{ todo.time }}</strong>
                                    <span class="taskDone">on</span>
                                    <strong class="taskDatee taskDone"><i class="fa fa-calendar"></i> {{ todo.date
                                        }}</strong>
                                    <span class="categorypage-{{ todo.category }}">{{ todo.category }}</span>
                                    <button class="taskDelete " name="taskDelete" formnovalidate="" type="submit"><i
                                            class="fa fa-trash-o icon"></i></button>
                                </li>
                                {% endfor %}
                            </ul>
                            <!--end All-Tasks-List -->
                        </section>
                    </div><!-- end tab content -->
                </div><!-- end tab effect -->
            </form>
        </div><!-- end content -->

    </div><!-- container -->
</div>

{% endblock %}
```


6. POST 처리

![image](https://user-images.githubusercontent.com/30430227/180715393-d20da1c4-8185-4576-aa27-6dc660442053.png)

```
* \task\views.py 수정
from flask import render_template, url_for, request
from werkzeug.utils import redirect
from .models import Category
from ..models import Todo
from . import task
from .forms import TaskForm
from .. import db
from datetime import datetime

@task.route('/create-task', methods=['GET','POST'])
def tasks():
    check=None
    todo=Todo.query.all()
    date=datetime.now()
    now=date.strftime('%Y-%m-%d')

    form = TaskForm()
    form.category.choices = [(category.id, category.name) for category in Category.query.all()]

    if request.method =='POST':
        if request.form.get('taskDelete') is not None:
            deleteTask = request.form.get('checkedbox')
            if deleteTask is not None:
                todo = Todo.query.filter_by(id=int(deleteTask)).one()
                db.session.delete(todo)
                db.session.commit()
                return redirect(url_for('task.tasks'))
            else:
                check = '삭제할 작업의 체크박스를 선택하세'

        elif form.validate_on_submit():
            selected = form.category.data
            category=Category.query.get(selected)
            todo = Todo(title=form.title.data, date=form.date.data, time=form.time.data, category=category.name)
            db.session.add(todo)
            db.session.commit()
            return redirect(url_for('task.tasks'))

    return render_template('task/tasks.html', todo=todo, title='업무 생성', form=form, DateNow=now, check=check)

```


Authentication
---------------------



파일업로드 
-------------

```
** <form>태그의 속성인 method는 전송 방식, action은 전송 목적지, enctype은 전송되는 데이터 형식을 설정

** enctype 속성은 세가지의 값으로 지정될 수 있음
1. application/www-form-urlencoded 디폴트값이다. 폼데이터는 서버로 전송되기 전에 URL-Encode 됨
2. multipart/form-data 파일이나 이미지를 서버로 전송할 경우 이 방식을 사용
3. text/plain 이 형식은 인코딩을 하지 않은 문자 상태로 전송

```

![image](https://user-images.githubusercontent.com/30430227/180392037-b90ad6b5-a881-41a2-862b-5cddec57d499.png)

1. \core\ 폴더 아래 static, static\uploads 폴더 생성


2. configy.py 파일

```
import os
from dotenv import load_dotenv

load_dotenv()
BASE_DIR = os.path.abspath(os.path.dirname(__file__))


class Config(object):
    SECRET_KEY = os.environ.get('SECRET_KEY')
    UPLOAD_FOLDER = os.path.join(BASE_DIR, 'core/static/uploads')
    ALLOWED_EXTENSIONS = {'jpg'}
    MAX_CONTENT_LENGTH = 16 * 1024 * 1024

```

3. \core\__init__.py

```
from flask import Flask
from config import Config

app = Flask(__name__)
app.config.from_object(Config)

from core import views
```

4. \core\views.py

```
from flask import render_template, flash, request, redirect
from core import app
from werkzeug.utils import secure_filename
from config import Config
import os

@app.route('/', methods=['POST', 'GET'])
def index():
    greeting = 'Hello there, Ace'

    if request.method =='POST':
        file = request.files['file']
        if file.filename =='':
            flash('No file was selected')
            return redirect(request.url)
        elif file and allowed_file(file.filename):
            filename = secure_filename(file.filename)
            file.save(os.path.join(Config.UPLOAD_FOLDER, filename))
            flash('Image has been successfully uploaded')
            return redirect('/')
        else:
            flash('Allowed media type are - jpg')
            return redirect(request.url)
    else:
        return render_template('index.html', greet=greeting)


def allowed_file(filename):
    return '.' in filename and  \
        filename.rsplit('.', 1)[1].lower() in Config.ALLOWED_EXTENSIONS

```

5. Template \core\templates\index.html

```
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

    {% with messages = get_flashed_messages() %}
    {% if messages %}
    <ul class="flashes">
        {% for message in messages %}
        <li>{{ message }}</li>
        {% endfor %}
    </ul>
    {% endif %}
    {% endwith %}

    <form method="post" enctype="multipart/form-data">
        <input type="file" name="file">
        <input type="submit" value="Upload">
    </form>
</body>

</html>
```


OSError: [Errno 98] Address already in use
----------------------------------------------

```
* 비정상적으로 서버가 종료되어 flask run 이 실행되지 않는 문제

$  sudo lsof -i:5000
flask   12458 brush    3u  IPv4  68014      0t0  TCP localhost:5000 (LISTEN)
$ sudo kill -9 12458 12458


* 모든 파일/폴더 지우기
$ rm *
$ rm -r *


스키마는 데이터베이스의 구조와 제약 조건을 기술한 메타데이터의 집합이다
> entries 테이블이 있으면 drop 없으면 생성, 이 테이블의 각 row에는 id, title, text 컬럼으로 구성된다.
id 는 정수로 자동으로 증가되는 프라이머리 키(primary key) 이다. 나머지 두개의 컬럼은 null이 아닌 문자열(strings) 값을 가진다.
* flaskr\schema.sql
drop table if exists entries;
create table entries{
    id integer primary key autoincrement,
    title string not null,
    text string not null
}


* error -  script argument must be unicode. 발생한다면
(f.read().decode('utf-8')) 로 수정 후 실행

```


