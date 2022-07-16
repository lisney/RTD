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
@echo off
cd myproject/script
activate

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

```

