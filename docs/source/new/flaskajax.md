AJAX
========

![image](https://user-images.githubusercontent.com/30430227/182115142-76374169-57c2-4887-b045-f2439e1e1d53.png)

```
{% block content %}
<button onclick="onButtonClicked()">전 송</button>
{% endblock %}

{% block script %}
<script>
    function onButtonClicked() {
        fetch('/ajax').then(response =>
            response.text()).then((data) =>
                alert('전송받은 내용: ' + data))
    }
</script>
{% endblock %}


* Json
            response.json()).then((data) =>
                alert('전송받은 내용: ' + JSON.stringify(data)))



* app.py
mydata ={"한글":"워드프로세서","마소":"오피스"}

@app.route('/ajax')
def ajax():
    return mydata
                
```


`POST`

```
    let user = {
        name: 'John',
        surname: 'Smith'
    }
    function onButtonClicked() {
        fetch('/ajax', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(user)
        }).then(response =>
            response.text()).then((data) =>
                alert('전송받은 내용: ' + data))
    }

---------------------------------------------------
@app.route('/ajax', methods=['GET','POST'])
def ajax():
    if request.method =='POST':
        return 'Hello!'
    return mydata 
    
```

