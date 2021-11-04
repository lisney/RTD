Basic
=======

1. VSCode

`실행: Ctrl - F5`

`자동완성 괄호 Tab으로 나가기 Extension 'TabOut' 설치`

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

```
