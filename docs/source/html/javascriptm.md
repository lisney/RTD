Javascript Middle
==================

`VScode edge Debugger 설치 > launch > VScode, Edge 동시에 뜸, 브라우저에서 색상 바꿈`

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

<br>

7. 문자 함수

```
- indexOf(text) -찾는 문자 없으면 '-1' 반환, True/False 판별 '>-1' 혹은 str.includes() 사용
    let desc = "Hi guys. Nice to meet you."
    console.log(desc.indexOf('to'))
    console.log(desc.indexOf('man'))
    if(desc.indexOf('man')> -1){
        console.log('Hi가 포함된 문장입니다.')
    }
   
- slice(n,m) -m 없으면 문자열 끝까지 양수면 그 숫자까지 음수면 끝에서부터 셈
    let desc ='abcdefg'

    desc.slice(2)
    desc.slice(0,5)
    desc.slice(2,-2)

- str.substr(n, m) - n 부터 시작 m 개를 가져옴

- str.substring(n,m) - n과 m 사이 문자열 반환, n과 m 을 바꿔도 동작함. 음수는 0으로 인식  

- str.trim() - 앞 뒤 공백 제거
    let desc = " coding     "
    console.log(desc.trim())

- str.repeat(n) - n 번 반복

```

<br>

8. 배열 

`push()-뒤에 삽입, pop()-뒤에 삭제, shift()-앞에 삭제, unshift()-앞에 삽입`

```
- arr.splice(n, m) - 연결 n시작, m개수를 제거하고 연결, 반환값(삭제된 요소)
- 요소 지우고 추가(arr.splice(n,m,x,...), 삽입 arr.splice(1,0,x) - 1번째 위치에 x 삽입
    let arr = [1,2,3,4,5]
    arr.splice(1,2)
    console.log(arr)
```

```
arr.concat(arr2, arr3...) - 합쳐서 새 배열 반환
    let arr = [1,2]
    console.log(arr.concat([3,4],[5,6]))

    
```

```
arr.forEach((item, index, arr)=>{...})

arr.indexOf(요소) - 탐색 후 요소가 있으면 요소의 Index를 반환, 없으면 -1 <-> arr.lastIndexOf -뒤에서부터 탐색
arr.includes

arr.find(fn) - 함수 내 조건에 맞는 요소를 찾으면 멈추고 요소값 리턴, 없으면 undefind(arr.findIndex(Fn)-인덱스 값 반환)
    let arr = [1,2,3,4,5]
    const result = arr.find((item)=>{
        return item % 2 ===0
    })

    console.log(result)
--------
    let userList =[
    {name:"Mike", age:30},
    {name:"Jane", age:27},
    {name:"Tom", age:10}
    ]
    const result = userList.find((user)=>{
        if(user.age < 19){
            return true
        }
        return false
    })
    console.log(result)   


* arr.filter(fn) - 만족하는 모든 요소를 배열로 반환 - find와 사용법은 동일

arr.reverse() - 배열을 역순으로 재정렬

arr.map(fn) -  함수를 받아 특정 기능을 시행하고 새로운 배열을 반환
    let userList =[
    {name:"Mike", age:30},
    {name:"Jane", age:27},
    {name:"Tom", age:10}
    ]
    let newUserList = userList.map((user, index)=>{
        return Object.assign({}, user,{
            isAdult: user.age>19,
            id: index +1
        })
    })
    console.log(newUserList)
    
배열을 문자열로 - arr.join() - 괄호 안에는 묶을 문자, 없으면 ',' <->split
    let arr = ["안녕","나는","철수야"]
    let result = arr.join()
    console.log(result)
    let reresult = result.split(',')
    console.log(reresult)
    //split('') 하면 모든 철자로 배열 생성
    
배열인지 확인 array.isArray() 불값 반환 - 'typeof array' 하면 객체로 반환

정렬 arr.sort() -배열 자체를 바꾼다, 문자로 파악하여 정렬한다, 인수로 정렬 로직을 담은 함수를 사용하여 숫자정렬
    let arr = [27, 8, 5,13]
    arr.sort((a,b)=>{
        return a-b
    })
    console.log(arr)
   
 모든 값 합치기 arr.reduce((누적 계산값, 현재값) => {return 계산값},0) - 0은 초기값 않쓰면 index[0]
    let arr = [27, 8, 5,13]
    const result = arr.reduce((prev, cur)=>{
        return prev + cur
    }, 0)
    console.log(result)

특정 요소만 추출
    let userList = [
    {name:"Mike", age:30},
    {name:"Tom", age:10},
    {name:"jane", age:27},
    {name:"Harry", age:42},
    {name:"Steve", age:60},
    ]

    let result = userList.reduce((prev, cur)=>{
        if(cur.age > 19){
            prev.push(cur.name)
        }
        return prev
    }, [])

    console.log(result)

[Lodash](https://lodash.com/)    
    
```

9. Lodash

