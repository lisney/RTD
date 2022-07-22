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
