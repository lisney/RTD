Sphinx
========

설치 및 시작하기
-------------------

1. 설치  
`pip install sphinx`

2. 시작하기  
`sphinx-quickstart`

3. html 빌드하기  
`make html`

4. 실행  
`build/html 에 있는 index.html 실행`

<br>

테마 바꾸기
------------
https://sphinx-themes.org/
```
$ pip install sphinx-rtd-theme
html_theme = 'sphinx_rtd_theme'
```

<br>

환경설정
---------

주석 해제
![image](https://user-images.githubusercontent.com/30430227/129860199-51d984a5-1614-4b47-b5db-4ed3ca12942f.png)

```
pip install --upgrade myst-parser

extensions = ['myst_parser',]
source_suffix = {
    '.rst': 'restructuredtext',
    '.txt': 'markdown',
    '.md': 'markdown',
}
```

<br>

이미지 Paste
-------------

VSCode Extension 'Paste Image'

<br>

마크다운 테이블
-----------------
```
pip install sphinx-markdown-tables

extensions = [
    'sphinx_markdown_tables',
]
```

<br>

docTree
-----------

caption 은 제목/ 경로를 적어준다. 확장자 불필요

![image](https://user-images.githubusercontent.com/30430227/128325388-ce62aa8f-8288-459d-8a1b-acc953a91fb9.png)
![image](https://user-images.githubusercontent.com/30430227/128325485-758847c0-0693-448e-9c2f-b8b65398be6f.png)

<br>

```

# 파일 링크
:doc:`usage`

# 주소 링크
`CNN <http://cnn.com>`_

# 이미지 
.. image:: 주소

# 블럭 감싸기 - 문단(줄 나누기)이 끝날 때까지 계속 감싼다
>>> 

# 코드블럭 감싸기
.. code-block:: console
[1줄 띄우고]
[3칸 띄우고 시작]first install it using pip:

# 빨강 강조 
``   ``

# italic 
*   *

# Bold
**   **

# 트리메뉴 

.. toctree:: 
   경로 혹은 toctree 파일(하위 트리)
   
```

md파일
![image](https://user-images.githubusercontent.com/30430227/128325216-90bf0faf-6c9b-479d-ad7d-b81e730fa4bc.png)

```
노드JS
=======

express
--------
express
--------
```

<br>

파이썬 pip 패키지 설치경로
---------------------------

`C:\Users\3DPrinter\AppData\Local\Programs\Python\Python38-32\Lib\site-packages`

<br>

테마에 로고 이미지 넣기
-----------------------

![image](https://user-images.githubusercontent.com/30430227/128329082-33ae7f2b-0f30-4189-a039-4e77ba3bcfe1.png)

`html_logo = '4g2.jpg'`

<br>
<br>

깃허브
============

<br>

RTD 업로드
-----------

https://readthedocs.org/

- Git Bash 이용 github 업로드
    - git bash here 실행
    - git init //현재 폴더를 로컬저장소로 사용
    - git status //깃허브에 올라가지 않은 파일 빨간색으로 표시
    - git add . //작업공간 파일을 준비영역에 추가한다 .점 띄어쓴다
    - git config core.autocrlf true // OS 문제로 add가 되지 않으면 명령어를 실행하고 다시 git add.
    - git commit -m "올림" //로컬저장소에 올림
    - git remote add origin Git Repository 주소 //원격 저장소와 연결
    - git push origin master //서버에 올린다

<br>

깃허브 이용 프로세스
--------------------

1. 깃허브에 새 리포지토리 생성
2. 상위 폴더에서 gitbash > git clone 리포지토리주소
3. 상위 폴더 아래 로컬 리포지토리폴더가 생성된다
4. 리포지토리 폴더에서 sphinx-quickstart
5. git add . > git commit -m 'add' > git push 실행(리모트 폴더가 'master'가 아니라 'main'일 때) 

> RTD 컴파일 후 변화 없을 때(Ctrl + F5 새로고침) -으이그~ 크로무시끼
> PDF 다운로드도 마찬가지 크롬 설정>인터넷 사용 기록 삭제

<br>

```
## 깃허브 폴더
빈폴더는 생성할 수 없으니 파일 생성 시 '폴더명/파일명'하면된단다  

## 폴더명 바꾸기...는 없고  
파일 수정에 들어가서 이름란에서 BackSpace 누르면 경로를 수정할 수 있다  

## requirements.txt 만들기

> pip freeze > requirements.txt

## 리포지토리 복사
새 리포지토리 생성 > 맨 아래 메뉴에 복사할 기존 리포지토리 주소를 넣는다(주의. 복사한 리포지토리는 RTD에서 에러가난다)

## 웹 VSCode?
편집하려는 페이지 화면에서 '.'키를 누르면 
```

<br>

<br>

Git Bash
-----------

```
## Git Bash 한글 안될 때(Bash : 유닉스 쉘)
상단 오른 쪽 클릭 > Options...> Text > Locale :: ko_KR, UTF-8로 변경

## 깃을 초기화한다(로컬저장소로 만든다)
$ git init

## 올릴 파일이 있는지 확인. (빨간색으로 되어있지만 add작업을 하면 녹색으로 변함)
$ git status

## 올릴 파일 추가
$ git add . (. : 모든 파일, 파일명 혹은 폴더명을 적는다)

## 커밋
$ git commit -m "메시지"

## 깃허브에서 repository 주소 복사, bash에 등록
$ git remote add origin [repository 주소] (ctrl + v 가 안먹히니 마우스 오른클릭)

## 깃허브와 Bash연결
$ git remote -v

## 원격  저장소에 올림
$git push origin master

//git remote ::리모트(원격) 저장소 확인
//git remote ::-v 단축이름과 URL을 함께 봄
//git fetch <remote>  ::리모트 저장소로 가져옴
//git push origin master :: origin은 원격 저장소 이름, master은 현재 사용하는 컴퓨터의 브랜치 이름
```
```
## 원격 저장소에서 가져오기
$git pull origin master

## 원격 저장소 바꾸기
1. 보기 git remote -v
2. 바꾸기 git remote set-url origin 리포지토리 주소

error: Your local changes to the following files would be overwritten by merge
발생 시
$git stash
$git pull

## git clone <원격 주소> //로컬로 복사해온다( tortose>Git 복제하기)

## tortose 깃>원격>origin:: URL 에 원격주소 붙여넣기//일반>Git:: 이름, 메일주소 넣기

## package.json 을 참조하여 모듈 설치
git install

## master -> master (fetch first) ...에러발생 시
git push origin +master로 해결

할 수 있지만 변경 내용만 push되는 것이 아니라 소스 전체가 다시 push 되는 것으로 보인다.
기존 데이터를 보장 못할 수도 있기 때문에
pull을 받는 다
pull url 을 push url 로 변경한다
pull --force진행한다 //-force, --force?
merge관련 메시지가 발생하는 경우가 있는데 자동화를 위해 이를 무시하려 force옵션을 사용한다.
push
pull url 원복
```
```
## git push 에러창 뜰 때
To solve this:
press "i"
write your merge message.
press "esc"
write ":wq"
then press enter.
```

<br>

Mark Down
-----------
```
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```
```
이텔릭체는 *별표(asterisks)* 혹은 _언더바(underscore)_를 사용하세요.
두껍게는 **별표(asterisks)** 혹은 __언더바(underscore)__를 사용하세요.
**_이텔릭체_와 두껍게**를 같이 사용할 수 있습니다.
취소선은 ~~물결표시(tilde)~~를 사용하세요.
<u>밑줄</u>은 `<u></u>`를 사용하세요.
--- //수평선
```
```
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브) 
  - 순서가 필요하지 않은 목록(서브) 
```
```
[GOOGLE](https://google.com)
[NAVER](https://naver.com "링크 설명(title)을 작성하세요.")
//링크

![대체 텍스트(alternative text)를 입력하세요!](http://www.gstatic.com/webp/gallery/5.jpg "링크 설명(title)을 작성하세요.") //이미지

[![Vue](/images/vue.png)](https://kr.vuejs.org/) //이미지 링크

`background`혹은 `background-image` 속성으로 요소를 강조합니다

```html
<a href="https://www.google.co.kr/" target="_blank">GOOGLE</a>
```
```
## 블럭 강조
`....`로 감싸기 grave

//테이블

| 값 | 의미 | 기본값 |
|---|:---:|---:|
| `static` | 유형(기준) 없음 / 배치 불가능 | `static` |
| `relative` | 요소 자신을 기준으로 배치 |  |
| `absolute` | 위치 상 부모(조상)요소를 기준으로 배치 |  |
| `fixed` | 브라우저 창을 기준으로 배치 |  |
//헤더 셀을 구분할 때 3개 이상의 -(hyphen/dash) 기호가 필요합니다.
//헤더 셀을 구분하면서 :(Colons) 기호로 셀(열/칸) 안에 내용을 정렬할 수 있습니다.
//가장 좌측과 가장 우측에 있는 |(vertical bar) 기호는 생략 가능합니다.

## 인용문을 작성하세요!
>> 중첩된 인용문(nested blockquote)을 만들 수 있습니다.
>>> 중중첩된 인용문 1
//<blockquote> 태그로 변환됩니다.

## 줄 바꾸기 :: #
스페이스 두 번 __

## 마크다운 문법이 아닌 원시 HTML 문법을 사용할 수 있습니다.
```





 

