Bootstrap
=============

로그인 폼
--------

1. form-floating - 레이블을 폼박스 안에 넣는다

![image](https://user-images.githubusercontent.com/30430227/153338277-c5932ad7-c2f5-4e99-bcdc-856c24d07186.png)
![image](https://user-images.githubusercontent.com/30430227/153338344-1b69b088-6241-484d-bd10-f1e027393f3b.png)

```
      <form action="">
        <div class="form-floating mb-5"> //mb(0~5) - margin-bottom
          <input type="email" id="form1example" class="form-control" placeholder=" " /> //placeholder 위치에
          <label for="form1example" class="form-label">Email address</label>
        </div>
      </form>
```
```
* textarea에도 사용
  <textarea class="form-control" placeholder="Leave a comment here" id="floatingTextarea"></textarea>
  <label for="floatingTextarea">Comments</label>
```
![image](https://user-images.githubusercontent.com/30430227/153341657-bc11ae7f-a659-40f5-b9af-4cd4bb3049ed.png)

```
* 인풋 그룹
<div class="input-group mb-5">
    <div class="input-group-text">@</div>
    <input type="text" class="form-control" id="inlineFormInputGroupUsername" placeholder="Username" />
</div>
```
![image](https://user-images.githubusercontent.com/30430227/153344241-9ff52c01-68ce-49a1-b920-aa24adcc2275.png)

<br>

2. 그리드

![image](https://user-images.githubusercontent.com/30430227/153340238-361c7211-1e83-481e-82d5-bef075f8b065.png)

```
            <div class="row mb-4"> // 열 시작
                <div class="col d-flex justify-content-center"> // 첫 번째 행
                    <div class="form-check">
                        <input type="checkbox" id="form1example3" class="form-check-input" checked />
                        <label for="form1example3" class="form-check-label">Remember me</label>
                    </div>
                </div>
                <div class="col"> // 두 번째 행
                    <a href="#!">Forget password?</a>
                </div>
            </div>
```


`<div class="form-check form-switch"> // form-switch 클래스`

![image](https://user-images.githubusercontent.com/30430227/153343546-85db7dba-cc5c-4f49-a2c2-bc7b6b4f33f3.png)


<br>

3. 버튼

![image](https://user-images.githubusercontent.com/30430227/153342369-17c4c898-dff1-4087-aabd-72f6df9482a3.png)

```
            <div class="row">
                <button type="submit" class="btn btn-primary btn-block shadow">Sign in</button> //btn-block 가로100% 채운다
            </div>
```

![image](https://user-images.githubusercontent.com/30430227/153342595-18764884-a2b3-4768-89b2-45ef8a639140.png)

```
* 셀렉트
                <div class="col">
                    <select class="form-select">
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>
```

![image](https://user-images.githubusercontent.com/30430227/153345048-cfd39830-6ea3-485f-9bbe-0edbd46ee398.png)

```
* 버튼 그룹 - 접착
            <div class="btn-group mt-4"> 
                <button class="btn btn-primary">1</button>
                <button class="btn btn-primary">2</button>
                <div class="btn-group" role="group"> // 그룹 네스팅
                    <button type="button" id="btnGroupDrop" class="btn btn-primary dropdown-toggle" //dropdown-toggle
                        data-bs-toggle="dropdown" aria-expanded="false"> // dropdown 은 부트스트랩 자바스크립트 필요
                        Dropdown
                    </button>
                    <ul class="dropdown-menu" aria-labelledby="btnGroupDrop">
                        <li><a href="#" class="dropdown-item">Dropdown1</a></li>
                        <li><a href="#" class="dropdown-item">Dropdown2</a></li>
                        <li>
                            <hr class="dropdown-divider">
                        </li>
                        <li><a href="#" class="dropdown-item">Dropdown3</a></li>
                    </ul>
                </div>
            </div>
```

![image](https://user-images.githubusercontent.com/30430227/153348397-54c4ca4b-71bc-4cdb-a01c-207fdaa7877e.png)

```
* 페이지네이션
        <nav>
            <ul class="pagination">
                <li class="page-item"><a href="#" class="page-link">Previous</a></li>
                <li class="page-item"><a href="#" class="page-link">1</a></li>
                <li class="page-item active"><a href="#" class="page-link">2</a></li>
                <li class="page-item"><a href="#" class="page-link">3</a></li>
                <li class="page-item"><a href="#" class="page-link">Next</a></li>
            </ul>
        </nav>
```

![image](https://user-images.githubusercontent.com/30430227/153349286-2a2d48a2-df12-48c2-8f75-051e028fbd6a.png)

<br>

4. Navbar

![image](https://user-images.githubusercontent.com/30430227/153352698-faa8af58-48ca-468d-877f-01d29da7f46f.png)

![image](https://user-images.githubusercontent.com/30430227/153352645-064e5172-8d03-43f9-a32b-e2499804d223.png)


```
* #navbarSupportedContent 토글(<button>/ <div>)
    <header>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <!-- navbar-expand-lg: lg 즉 992px 이상일 때 펼친다 -->
            <div class="container-fluid">
                <a href="#" class="navbar-brand">Navbar</a>
                <button type="button" class="navbar-toggler" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item">
                            <a href="#" class="nav-link active" aria-current="page">Home</a>
                        </li>
                        <li class="nav-item">
                            <a href="#" class="nav-link">Link</a>
                        </li>
                        <li class="nav-item dropdown">
                            <a href="#" id="navbarDropdown" class="nav-link dropdown-toggle" role="button"
                                data-bs-toggle="dropdown" aria-expanded="false">
                                Dropdown
                            </a>
                            <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                                <li><a href="#" class="dropdown-item">Action</a></li>
                                <li><a href="#" class="dropdown-item">Something else here</a></li>
                            </ul>
                        </li>
                        <li class="nav-item">
                            <a href="#" class="nav-link disabled">Disabled</a>
                        </li>
                    </ul>
                    <form action="" class="d-flex">
                        <input type="search" class="form-control me-2" placeholder="Search" aria-label="Search">
                        <button type="submit" class="btn btn-outline-success">Search</button>
                    </form>
                </div>
            </div>
        </nav>
    </header>
```
