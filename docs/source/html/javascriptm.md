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
    console.log(user['name'])
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

5. 심볼 생성 - 유일한 프로퍼티

```
- for을 사용하면 전역 심볼이 된다
    const id1 = Symbol('id')
    const id2 = Symbol('id')

    const id3 = Symbol.for('id')
    const id4 = Symbol.for('id')

    console.log(id1===id2)
    console.log(id3===id4)

- 심볼을 키로 사용 시 Object.keys() 배열에 생성되지 않는다(숨겨진다)
- Reflect.ownKeys(user) 심볼을 포함한 객체의 모든 키를 배열로

    const id = Symbol('id')

    const user ={
        name:'Mike',
        [id]:'myid'
    }

    console.log(Object.keys(user))
    console.log(Reflect.ownKeys(user))
```

<br>

`예제` 

```
- 심볼을 사용하지 않고 멤버를 추가하면 기존 메시지에 추가되어 버린다
- 심볼 멤버에 접근하기 위해서는 []를 사용한다
    <!-- 기존 객체 -->
    const user ={
        name: "Mike",
        age:30
    }

    <!-- 중간에 넣기 -->
    const showName = Symbol("show name")
    user[showName] = function(){
        console.log(this.name)
    }

    user[showName]()

    <!-- 기존 메시지 -->
    for(let key in user){
        console.log(`His ${key} is ${user[key]}.`)
    }
```

<br>

6. 숫자 함수

```
- toString() - ()안의 진법인 문자열로 반환
let num = 10

num.toString()
num.toString(2)
num.toString(16)


- toFixed() - 소수점 자릿수에서 반올림, 문자열로 반환
let userRate = 30.1234

userRate.toFixed(2) //소수점 둘째자리
userRate.toFixed(6) //소수점을 0으로 채워준다


- isNaN - 숫자인지 아닌지 불 값 반환

- parseInt() - 문자열을 정수로
let margin = '10px'

parseInt(margin) // 10
Number(margin) //NaN

let redColor = 'f3'
parseInt(recColor) //NaN
parseInt(redColor, 16) //243

- Math.pow(n,m) - 제곱
- Math.sqrt() - 루트






```






