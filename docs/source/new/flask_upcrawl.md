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


2. 모듈 설치

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


VSCode 앱에서 정규식
-----------------

```
* 네이버코믹 랭킹
* app.py
rankA = soup.find_all('li', attrs={"class":re.compile('rank.*')})
rankA = soup.find_all('li', class_ =re.compile('rank.*')) # class는 파이썬 예약어이므로 대신 'class_' 사용
rankA = soup.find_all('li', re.compile('rank.*')) # find의 두 번째 인자는 CSS 클래스이다
rankA = soup('li', re.compile('rank.*'))  #soup 기본은 find_all이다
rankA = soup.select('.asideBoxRank > li ')

def home():
    return render_template('home.html', date=datetime.now(), m=m, lst=lst, soup=soup, rankA=rankA)

*\home.html
<ul>
    {% for rank in rankA %}
    <li>{{ rank.a['title']}} </li>
    {% endfor %}
</ul>

* limit
rankA = soup.find_all('li', class_ =re.compile('rank.*'), limit=10) # 10위까지만
rankA = soup.select('.asideBoxRank > li ', limit=10)

<ol type="1"> => 1,2,3숫자 매김

```


이미지 끌어오기, enumerate, starswith, image.content
----------------

1. 1위부터 5위까지

```
url = 'https://search.daum.net/search?w=tot&q=2021%EB%85%84%EC%98%81%ED%99%94%EC%88%9C%EC%9C%84&DA=MOR&rtmaxcoll=MOR'
res = requests.get(url)
res.raise_for_status()
soup = BeautifulSoup(res.text, 'lxml')

images = soup.find_all("img", class_ ="thumb_img", limit=5) # 강의에선 limit 대신 if i >= 4: break

for i, image in enumerate(images):
    image_url = image['src']
    if image_url.startswith('//'):
        image_url = 'https:' + image_url
        images[i]['src'] = image_url
    
    image_res = requests.get(image_url)
    image_res.raise_for_status()

    with open('movie{}.jpg'.format(i + 1), 'wb') as f:
        f.write(image_res.content)
```


2. 2019~2020


```
* for year 문으로 기존 for문을 감싼다
for year in range(2019,2021):
    url = 'https://search.daum.net/search?w=tot&q={}%EB%85%84%EC%98%81%ED%99%94%EC%88%9C%EC%9C%84&DA=MOR&rtmaxcoll=MOR'.format(year)
    res = requests.get(url)
    ...


* 저장 이미지의 이름이 중복되므로 format 변경
    for i, image in enumerate(images):
...
        with open('movie_{}_{}.jpg'.format(year,i + 1), 'wb') as f:
    
```


3. 썸네일 

![image](https://user-images.githubusercontent.com/30430227/181448074-b12daeb3-abdf-4155-8e4d-7f1ad380bb70.png)

```
\app.py
images = soup.find_all("img", class_ ="thumb_img", limit=5 )
img_names = soup.select('.info_tit > a', limit=10)

    return render_template('home.html', date=datetime.now(), images=images, img_names=img_names)
    
    
\home.html
<ol type="1">
    {% for image in images %}
    <li>
        <img src="{{image['src'] }}" alt="" width="100">
        <span>{{img_names[loop.index].text}}</span>  // loop.index -1 해줘야 매칭이된다^^;
    </li>
    {% endfor %}
</ol>


```
