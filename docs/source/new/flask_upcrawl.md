Crawling
===========

1. requests 설치

```
import requests

res = requests.get('http://google.com')
res.raise_for_status() # 문제 발생 시 예외처리(200 -정상), 실행 멈춤
print('응답코드 :', res.status_code)
print(len(res.text))

with open('mygoogle.html', 'w', encoding='utf8') as f:
    f.write(res.text)


* User-Agent 웹 클라이언트 정보 넣고 요청하기  - 에러나는 사이트에 접속하기
url = 'http://nadocoding.tistory.com'
headers = {"User-Agent":"Mozilla/5.0 ..."} # 검색 'user agent' 보여주는 사이트에서 복사해옴
res = requests.get(url, headers=headers
res.raise_for_status()
with open...

```


2. 정규식

```
p = re.compile('ca.e')

m=p.match('cahe')

@app.route('/')
def home():
    return render_template('home.html',m=m)

* 템플릿    
<p>{{ m.group() }}</p>


* search
m=p.search('good care')

{% if m %}
<strong>"{{ m.group() }}"</strong> 을 '{{m.string}}' 문자열에서 발견[시작 index : {{m.start()}}]
{% else %}
<strong>니주글래!</strong>


* findall - 매칭되는 모든 문자열 리스트로 반환
lst = p.findall('good care cafe')

```


3. 모듈 설치

```
$ pip install beautifulsoup4
$ pip install lxml  # 구문분석용 파서


import requests
from bs4 import BeautifulSoup

url = 'https://comic.naver.com/index'
res = requests.get(url)
res.raise_for_status()

soup = BeautifulSoup(res.text, 'lxml') # 불러온 문서res.text를 lxml 파서를 통해 BeautifulSoup 객체 생성

<템플릿>
{% if soup %}
<strong>"{{ soup.title }}"</strong>
<p>{{ soup.title.get_text() }}</p>
<p>{{ soup.a }}</p>  // 첫 번째 발견되는 a 엘리먼트 반환
<p>{{ soup.a.attrs }}</p> // a 엘리먼트의 속성들 딕셔너리로 반환
<p>{{ soup.a["href"] }}</p> // href 속성 값을 반환
<p>{{ soup.find('span', attrs={"class":"Ntxt_best_challenge"}) }}</p>

```

![image](https://user-images.githubusercontent.com/30430227/180943279-fcd02808-4873-4ea2-9632-39ce41c5404f.png)

```
<p>{{ soup.find('li', attrs={"class":"rank01"}).a.get_text() }}</p>
<p>{{ soup.find('li', attrs={"class":"rank01"}).next_sibling.next_sibling.a.get_text() }}</p>
<p>{{ soup.find('li', attrs={"class":"rank01"}).find_next_sibling('li').a.get_text() }}</p>

<ul>
    {% for rank in soup.find('li', attrs={"class":"rank01"}).find_next_siblings('li') %}
    <li>{{ rank.a.get_text() }}</li>
    {% endfor %}
</ul>
<span class="soup" data-uri='{{ soup.find("li", attrs={"class":"rank01"}).a.get_text() }}'></span>

// 자바스크립트로 data 전달 후 경고창 띄우기
<script>
    const soup = document.querySelector('.soup')
    alert(soup.dataset.uri)
</script>


* find_all 조건에 맞는 모든 엘리먼트 배열로 반환 \app.py
cartoons = soup.find_all("a", attrs={"class":"title"})

```




