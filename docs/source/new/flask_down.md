flaskdown
==========

```
* 폴더 생성 
flaskr\
flaskr\static\
flaskr\templates\

```


데이터베이스 스키마
--------------------

```
이 스키마는 entries 라는 이름의 테이블로 구성되어 있으며 이 테이블의 각 row에는 id, title, text 컬럼으로 구성된다. id 는 자동으로 증가되는 정수이며 프라이머리 키(primary key) 이다. 나머지 두개의 컬럼은 null이 아닌 문자열(strings) 값을 가져야 한다.
* flaskr\schema.sql
drop table if exists entries;
create table entries(
    id integer primary key autoncrement,
    title string not null,
    text string not null
);

```


앱생성 
-------

```
클라이언트에서의 세션을 안전하게 보장하기 위해서는 secret_key 가 필요하다
\flaskr\flaskr.py
# 모든 임포트
import sqlite3
from flask import Flask, request, session, g, redirect, url_for, abort, render_template, flash

# 설정
DATABASE = '/tmp/flaskr.db'
DEBUG = True
SECRET_KEY = 'development key'
USERNAME ='admin'
PASSWORD = '12345'

# 앱 생성
app = Flask(__name__)
app.config.from_object(__name__)

# db 연결
def connect_db():
    return sqlite3.connect(app.config['DATABASE'])

# 단독 서버로 실행되는 애플리케이션을 위한 서버 실행코드 추가
if __name__ == '__main__':
    app.run()

```

`실행 $ python flaskr.py`


데이터베이스 생성 
------------------

```
* flaskr.py 추가
from __future__ import with_statement
from contextlib import closing

# 모든 임포트 위에..
...
# db 초기화 함수 - with ~ as 파일 열고 닫을 때 자동으로 close 해준다
def init_db():
    with closing(connect_db()) as db:
        with app.open_resource('schema.sql') as f:
            db.cursor().executescript(f.read())
        db.commit()


* 실행 
$ python
> from flaskr import init_db
> init_db()

* error -  script argument must be unicode. 발생한다면
(f.read().decode('utf-8')) 로 수정 후 실행

```


데이터베이스 커넥션 요청
----------------------

```
* flaskr.py 추가 init_db() 다음에
> before_request() 함수는 리퀘스트가 실행되기 전에 호출되는 함수
> 예외상황은 teardown_request() 으로 전달된다.
> 데이터베이스 커넥션을 특별하게 저장하는 Flask 'g' 객체
@app.before_request
def before_request():
    g.db = connect_db

@app.teardown_request
def teardown_request(exception):
    g.db.close()
    
```



뷰 함수들 
---------

```
# 뷰 함수들
@app.route('/')
def show_entries():
    cur = g.db.execute('select title, text from entries order by id desc')
    entries = [dict(title=row[0], text=row[1]) for row in cur.fetchall()]
    return render_template('show_entires.html', entries=entries)

@app.route('/add', methods=['POST'])
def add_entry():
    if not session.get('logged_in'):
        abort(401)
    g.db.execute('insert into entries (title, text) values (?,?)',[request.form['title'], request.form['text']])
    g.db.commit()
    flash('New entry was successfully posted')
    return redirect(url_for('show_entries'))

@app.route('/login', methods=['GET','POST'])
def login():
    error = None
    if request.method =='POST':
        if request.form['username'] != app.config['USERNAME']:
            error = 'Invalid username'
        elif request.form['password'] != app.config['PASSWORD']:
            error = 'Invalid password'
        else:
            session['logged_id'] = True
            flash('You were logged in')
            return redirect(url_for('show_entries'))
    return render_template('login.html', error=error)

# dict객체의 pop() 함수에 두번째 파라미터(기본값)를 전달하여 사용하면 이 함수는 dict객체에서 해당 키를 삭제할 것이다. 
@app.route('/logout')
def logout():
    session.pop('logged_in', None)
    flash('You were logged out')
    return redirect(url_for('show_entires'))
    
```



템플릿 
----------

```
* \templates\layout.html
<!doctype html>
<title>Flaskr</title>
<link rel=stylesheet type=text/css href="{{ url_for('static', filename='style.css') }}">
<div class=page>
  <h1>Flaskr</h1>
  <div class=metanav>
  {% if not session.logged_in %}
    <a href="{{ url_for('login') }}">log in</a>
  {% else %}
    <a href="{{ url_for('logout') }}">log out</a>
  {% endif %}
  </div>
  {% for message in get_flashed_messages() %}
    <div class=flash>{{ message }}</div>
  {% endfor %}
  {% block body %}{% endblock %}
</div>


* \show_entries.html
{% extends "layout.html" %}
{% block body %}
  {% if session.logged_in %}
    <form action="{{ url_for('add_entry') }}" method=post class=add-entry>
      <dl>
        <dt>Title:
        <dd><input type=text size=30 name=title>
        <dt>Text:
        <dd><textarea name=text rows=5 cols=40></textarea>
        <dd><input type=submit value=Share>
      </dl>
    </form>
  {% endif %}
  <ul class=entries>
  {% for entry in entries %}
    <li><h2>{{ entry.title }}</h2>{{ entry.text|safe }}
  {% else %}
    <li><em>Unbelievable.  No entries here so far</em>
  {% endfor %}
  </ul>
{% endblock %}


* \login.html
{% extends "layout.html" %}
{% block body %}
  <h2>Login</h2>
  {% if error %}<p class=error><strong>Error:</strong> {{ error }}{% endif %}
  <form action="{{ url_for('login') }}" method=post>
    <dl>
      <dt>Username:
      <dd><input type=text name=username>
      <dt>Password:
      <dd><input type=password name=password>
      <dd><input type=submit value=Login>
    </dl>
  </form>
{% endblock %}

```


스타일 추가 
----------

```
* \static\style.css
body            { font-family: sans-serif; background: #eee; }
a, h1, h2       { color: #377BA8; }
h1, h2          { font-family: 'Georgia', serif; margin: 0; }
h1              { border-bottom: 2px solid #eee; }
h2              { font-size: 1.2em; }

.page           { margin: 2em auto; width: 35em; border: 5px solid #ccc;
                  padding: 0.8em; background: white; }
.entries        { list-style: none; margin: 0; padding: 0; }
.entries li     { margin: 0.8em 1.2em; }
.entries li h2  { margin-left: -1em; }
.add-entry      { font-size: 0.9em; border-bottom: 1px solid #ccc; }
.add-entry dl   { font-weight: bold; }
.metanav        { text-align: right; font-size: 0.8em; padding: 0.3em;
                  margin-bottom: 1em; background: #fafafa; }
.flash          { background: #CEE5F5; padding: 0.5em;
                  border: 1px solid #AACBE2; }
.error          { background: #F0D6D6; padding: 0.5em; }
```
