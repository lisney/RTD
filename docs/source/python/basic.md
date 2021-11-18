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

2차원 배열에 저장
> result =[]; // for i in data: sub=[]; //하위 for j in i: sub.append()// result.append(sub)

```

10. 함수 

```
//세 개의 숫자를 입력받아 가장 큰 수를 출력하는 함수
def print_max(a,b,c):
    max = 0
    if a>max:
        max=a
    if b>max:
        max=b
    if c>max:
        max=c
    print max


//문자열을 입력받아 역순으로 출력
def print_reverse(a):
    print(a[::-1])

//딕셔너리에서 키 값만 출력하는 함수
def print_keys(a):
    for key in a.keys():
        print(key)
	
	
//입력 문자열을 다섯 글자씩 출력하는 함수
def print_5xn(c):
    num = round(len(c)/5)
    for i in range(num +1):
        print(c[i*5:i*5+5])

print_5xn("아이엠어보이유알어걸")


//문자열을 숫자로 출력하는 함수 "1,234,567"
def convert_int(c):
    return int(c.replace(',',''))

print(convert_int("1,234,567"))

```

<br>

11. 모듈 

```
// 핸재 시간 출력 -  datetime
import datetime
print(datetime.datetime.now())

// 5일 간 날짜 출력 - timedelta
import datetime
now = datetime.datetime.now()
for i in range(5,0,-1):
    delta = datetime.delta(days=i)
    date = now-delta
    print(date)

// 타임 문자열로 포멧팅 - strftime, "18:35:01"
import datetime
now = datetime.datetime.now()
print(now.strftime("%H:%M:%S"))

// 문자열 타임포멧 변환 - datetime.datetime.strptime(파싱)
import datetime
day = "2020-05-04"
form = datetime.datetime.strptime(day, "%Y-%m-%d")
print(form)

//1초에 한 번 sleep(1)
import time, datetime

while True:
    now = datetime.datetime.now()
    print(now)
    time.sleep(1)


// os 모듈
import os
print(os.getcwd()) //현재 디렉토리

```

<br>

12. 클래스 

```
class Human:
    def __init__(self):  //생성자
        print("응애응애")
	
areum = Human()  //객체 생성, areum은 Human클래스의 인스턴스다


// 생성자
class Human:
    def __init__(self, name, age, sex):
        self.name = name
	self.age = age
	self.sex = sex
areum = Human("브러신",25,"남자")
print(areum.name)


//출력 매소드
def who(self):
    print(f"이름: {self.name}")


//입력 매소드
def setInfo(self, name, age):
    self.name = name
    self.age = age
    

//소멸자
def __del__(self):
    print(f"{self.이름}의 죽음을 알리지마라")

del areum   //소멸

--------------------------------------------------
은행계좌 Account Class - 입력(name, balance-잔금), 자동생성(bank="SC은행", account_number="000-00-000000"(랜덤넘버)
-------------------------------------------------------------------
import random

class Account:
    def __init__(self, name, balance):
        self.name = name
	self.balance = balance
	
	num1 = random.randint(0,999)
	num2 = random.randint(0,99)
	num3 = random.randint(0,999999)
	
	num1 = str(num1).zfill(3)
	num2 = str(num2).zfill(2)
	num3 = str(num3).zfill(6)
	
	self.account_number = f"{num1}-{num2}{num3}"
	//f-string 으로 표현하면 zfill 불필요 f"{num1:#03d}-{num2:#02d}-{num3:#06d}"
	// #으로 시작 - 앞은 0으로 채움 - 자릿수 - d(변수타입 정수)

kim = Account("김민수", 100)
----------------------------------------------------------------------

// 클래스 변수 - 계좌 수 카운트
account_count = 0  // __init__ 에 카운트를 넣을려면 self.account_count 변수를 만든다
....
__init__ 매서드에서
Account.account_count += 1

// 클래스 변수 사용 매서드
def get_account_num(cls):
    print(cls.account_count)

// 입금 매서드
def deposit(self, amount):
    if amount >= 1:
        self.balance += amount

// 파이썬 콤마 추가/제거 방법
num1 = 1234567890
num2 = "1234567890원"

print(f"{num1:,}원")
print(num2[:-1].replace(',',''))

----------------------------------------------------------------------
클래스 상속
------------------------------------------------------------------------
class 차:
    def __init__(self, 바퀴, 가격):
        self.바퀴 = 바퀴
	self.가격 = 가격
	
class 자전차(차):
    def __init__(self, 바퀴, 가격, 구동계):
        super().__init__(바퀴, 가격) // super()는 부모 즉 '차.' 로 바꿀 수 있다
	self.구동계 = 구동계
	
bicycle = 자전차(2, 100, "시마노")

print(bicycle.바퀴)
-------------------------------------------------------------------

<br>

13. 파일 입출력과 예외

```
//파일 쓰기
f = open("c:/users/3dprinter/desktop/매수종목.txt", mode="wt", encoding="utf-8")
f.write("364845\n")
f.close()


// csv 쓰기
import csv

f = open("c:/users/3dprinter/desktop/매수종목.csv", mode="wt", encoding="cp949", newline="") #newline='' 자동줄바꿈 안함

writer = csv.writer(f)
writer.writerow(["종목명","종목코드","PER"])
writer.writerow(["삼성전자", "003724",15.64])

f.close()


// txt 파일 읽기
 f = open


```


