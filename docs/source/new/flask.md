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

