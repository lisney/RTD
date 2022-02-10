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
          <input type="email" id="form1example" class="form-control" placeholder=" " /> //placeholder 있고/없고 차이
          <label for="form1example" class="form-label">Email address</label>
        </div>
      </form>

* textarea에도 사용
  <textarea class="form-control" placeholder="Leave a comment here" id="floatingTextarea"></textarea>
  <label for="floatingTextarea">Comments</label>

```

![image](https://user-images.githubusercontent.com/30430227/153341657-bc11ae7f-a659-40f5-b9af-4cd4bb3049ed.png)

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

3. 버튼

![image](https://user-images.githubusercontent.com/30430227/153342369-17c4c898-dff1-4087-aabd-72f6df9482a3.png)

```
            <div class="row">
                <button type="submit" class="btn btn-primary btn-block shadow">Sign in</button>
            </div>
```


