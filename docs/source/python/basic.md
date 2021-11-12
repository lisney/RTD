Basic
=======

> 이전 학습

```
# 2, 3 버전 따로 실행 설정(명령창에서 python2 혹은 python3으로 실행하면 됨)

검색창에서 cmd 검색 -> 명령프롬프트 우클릭 -> 관리자 권한으로 실행 후

Python 2.7 버전은
mklink c:\windows\python2.exe C:\Python27\python.exe
 
Python 3.7 버전은
mklink c:\windows\python3.exe C:\Users\whdmf\AppData\Local\Programs\Python\Python37-32\python.exe
이렇게 설정 해주면 된다.

예) mklink c:\windows\python2.exe [ Python2 경로 ]
mklink c:\windows\python3.exe [ Python3 경로 ]

# Django 설치
	pip install django

# Django 실행
	django-admin startproject web_prj(프로젝트 명)
	cd web_prj
	python manage.py runserver(서버 실행)

# 파이참이 python(.py)파일을 인식하지 못할 때
실수로 텍스트 파일 myfilename을 (를) 이름을 myfilename.py 버전으로 바꾸었지만 확장명을 변경 한 후에도 텍스트 파일 형식을 유지했습니다.

File > Settings > Editor > File Types > Text로 이동
Registered Patterns 아래 목록에서 새로운 myfilename.py를 찾았습니다.
- 버튼으로 목록에서 제거하십시오
Ok를 클릭하십시오.

## f-String

날짜
import datetime
date = datetime.datetime.now()
print(f'{date:%Y년 %m월 %d일}은 {date:%A}입니다')

빈공간
print(f'{500:*<+10}') // :, *(채울 문자), <>(오른쪽,왼쪽), +(부호붙임)
>>+500******

print(f'{5000000000000:+,}')
>>+5,000,000,000,000

print(f'{500000000076600:^<+30,}')
>>+500,000,000,076,600^^^^^^^^^^

print(f'{5/3:.2f}') // 소수점 표시, .2(소수점 2번째 자리까지)
>>1.67

## 집합(set)
.add()
.remove()
&, |, -(intersection, Union, Difference)

## round(값, 반올림할 소수점 자리)

## random  모듈
random.shuffle(리스트) 
random.sample(리스트, 갯수)
random.randint(2, 10), random.randrange(A, B)

## 문자열 채우기
.zfill()
.ljust(채울공간), .rjust()

## tkinter JPG 이미지 불러오기(기본 PhotoImage는 JPG 못불러온다)

## 파일 검색 및 폴더 열기 한방에 os.walk
import os

for root, dirs, files in os.walk(r'c:\users\3dprinter\desktop\files'):
    for file in files:
        if 'ply' in file:
            print(file, root)
            os.startfile(root)

## Django 로컬 서버 휴대폰에서 열기
settings.py
ALLOWED_HOSTS =['192.168.1.200'] 또는 IP 주소가 무엇이든.
==서버 주소는 데스크탑의 주소를 사용한다(ipconfig로 확인가능)

## 한 줄 서버
index.html 이 있는 폴더에 가서
	python -m http.server 실행
Address already in use 이라는 에러가 난다면, 다른 포트번호를 입력
	python -m http.server 8080

## 파이썬 심플 서버
import http.server
import socketserver

handler = http.server.SimpleHTTPRequestHandler

with socketserver.TCPServer(('',8080),handler) as httpd:
    print('Server listening on port 8080')
    httpd.serve_forever()

## 명령행으로 프로그램 인자값 받기 - sys.argv
어느 언어나 프로그램 실행시 명령행을 통해 필요한 인자값(Arguments Value)을 받을 수 있는 방법을 제공합니다. 자바나 C언어 등 에서도 main 메서드를 통해 명령행 매개변수를 받는 방법을 제공하는것과 같습니다.

파이썬에는 명령행을 받기위해 sys 라이브러리를 import 해주어야 합니다.
import sys                                                                                

sys.argv 는 배열입니다. sys.argv[0]에는 기본적으로 python 실행파일의 경로가 담겨있기 때문에 sys.argv 배열의 길이는 기본적으로 1입니다.

print(len(sys.argv))                                                                 
print(sys.argv[0]) 

## Emmet 언어설정
Ctrl + ,
검색에 emmet 한 후
Edit in setting.json에서

"emmet.extensionsPath": "c:/lee"

한 후

해당 폴더에 
snippets.json 파일을 생성 후

{
       "variables": {
           "lang": "ko"
       },
       "html": {
           "snippets": {
               "!": "!!!+html[lang=${lang}]>(head>meta[charset=UTF-8]+title{Document})+body"
           }
       }
}

```

1. VSCode

`실행: Ctrl - F5`
`Ctrl - D: 같은 단어 연속 `

> `자동완성 괄호 Tab으로 나가기 Extension 'TabOut' 설치`

<br>

2. 출력

```
print(...,...,..., sep="사이에 넣을 문자")
print(...,...,..., end="마지막에 넣을 문자")

```

<br>

3. 변수 타입 보기

`type(변수명)`

<br>

4. 문자열

```
오프셋
>print(string[::2])    => 1,3,5

Replace - 문자열은 변경할 수 없는 자료형이므로 새 값을 리턴한다
>phone_number1 = phone_number.replace('-', ' ') // '-' 을 ' '로 치환

Split 
>url.split('.') // '.'을 기준으로 나누고 각각을 배열로 저장, split() -공백을 기준으로 나눔

Formatting
> print("이름: %s 나이: %d"%(name1, age1))
> print("이름: {} 나이: {}".format(name1,age1))
> print(f"이름: {name1} 나이: {age1})  // 3.5 이상 버전

Strip - 문자열 좌우 공백 제거
> print(data.strip())

capitalize
> print(ticker.capitalize())     => Kim

endswith - 확장명 확인 <-> startswith
> print(file_name.endswith('xlsx'))    => True
> print(file_name.endswith(('xlsx, 'xls')))   // 복합

```
<br>

5. 리스트

```
insert 메소드
>movie_rank.insert(1, "슈퍼맨"); print(movie_rank)

del 예약어, remove() 매서드
> del movie_rank[3]
> movie_rank.remove("슈퍼맨");print(movie_rank)

min, max, sum, len 함수
> min(nums)  //배열의 최솟값

Slicing
> print(nums[1::2]) // filter 두 번째 인덱스(1)를 시작으로 2칸 건너 출력

join 매써드 - 배열을 문자열로 <-> split
> " ".join(interest)  // 배열 interest의 원소들을 공백으로 연결하고 문자열을 반환

sort 매써드 - 데이터 변경, 반환값 없음
> data.sort();print(data)

```

<br>

6. 튜플

```
언팩킹 - list도 된다
> a, b, c = number;print(a,b,c)

1부터 100까지 짝수를 원소로 하는 튜플
> data = tuple(range(2,100,2);print(data)

```

<br>

7. 딕셔너리

```
별 표현식(star Expression)
> a,b,*c = 리스트 // 언패킹: 리스트 중 a, b 할당하고 나머지 스베떼 c에 리스트로 할당

항목 추가
> ice['죠스바'] = 1200

딕셔너리 추가
> icecream.update(new_product)

zip
> result = dict(zip(keys, vals))

```

<br>

8. 분기문

```
입력
> user = input("입력");print(user * 2) 

짝홀수 판별(if, else, elif)
>if user % 2 == 0:
>    print("짝수")
>else:
>    print("홀수")

'if ~ in 배열' 조건문
> if user in fruit // 딕셔너리의 경우 fruit 가 fruit.keys() 를 나타낸다(items() 참조)

islower()
> if user.islower():;print(user.upper())

비트코인
import requests
btc = requests.get("https://api.bithumb.com/public/ticker/").json()['data']

키값 opening_price, closing_price, min_price,	max_price
> print(btc["closing_price"]

```

<br>

9. 반복문 

```
리스트의 반복문
> for i in range(len(price_list)) // 인덱스 i, 항목 price_list[i]
enumerate > for i, item in enumerate(price_list) // 인텍스 i, 항목 item

리스트 역순
> for i in apart[::-1] // range(시작, 종 -1, 변위)

```

