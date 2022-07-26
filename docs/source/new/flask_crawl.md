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

