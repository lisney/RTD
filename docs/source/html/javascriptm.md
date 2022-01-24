Javascript Middle
==================

1. 변수의 생성과정 - 호이스팅

```
var 1.선언 및 초기화 단계  2.할당 단계
let 1.선언 단계 2.초기화 단계 3.할당 
const 1.선언, 초기화, 할당 -동시
```

<br>

2. 생성자 함수

```
어떤 함수도 생성자 함수가 될 수 있다 - New붙이면
    function User(name1, age){
        this.name = name1
        this.age = age
        this.showAge = function(){
            console.log(`안녕하세요 ${this.name}님 나이는 ${this.age}`)
        }
    }
    let user1 = new User('Mike', 30)
    let user2 = new User('Jane', 22)

    user1.showAge()
```

<br>

3. Computed Property(연산 속성)

```
    let a = 'name'

    const user ={
        [a+'a']: 'Mike'
    }
    console.log(user.namea)
```

<br>

4. 객체 Meshods

```
Object.assign() -추가 - const newUser = Object.assign({}, user} 로 user 객체 복사 구현
Objects.keys() - 객체에서 키 값만은 배열로 추출
Objects.values()
Object.entries() - 키와 값으로 구성한 배열
    const user = {
        name: "Mike",
        age: 30
    }
    console.log(Object.entries(user))
    <결과>
    [Array(2), Array(2)]

Object.fromEntries() - entries와 반대로 배열을 객체로
```

<br>

5. 
