Javascript Middle
==================

`VScode edge Debugger 설치 > launch > VScode, Edge 동시에 뜸, 브라우저에서 색상 바꿈`

[더 예쁜](https://prettier.io/docs/en/options.html)

![image](https://user-images.githubusercontent.com/30430227/150918814-7f1d5bef-3ac1-4c29-b923-5e99f3cb0608.png)

![image](https://user-images.githubusercontent.com/30430227/150919852-1c3fccf7-14a8-479b-9843-0c539d6e154a.png)

![image](https://user-images.githubusercontent.com/30430227/150919061-7440de15-d065-419f-a94a-cec3b563d79e.png)

```
File > Preference > Javascript> Format:Enable 체크 헤제 >
> Default Formatter(Prettier - code...) > 오른 쪽 위 버튼 클릭 > settings.json 편집

    "editor.formatOnSave": true,
    
코드 스타일을 통일해야하는 경우가 생길 때는
.prettierrc 파일을 프로젝트 최상단에 만들어 사용합니다.
```

`TabOut - VSCode 따옴표 탭 Extension`

<br>

1. 변수의 생성과정 - 호이스팅

```
var 1.선언 및 초기화 단계  2.할당 단계
let 1.선언 단계 2.초기화 단계 3.할당 
const 1.선언, 초기화, 할당 -동시
```

<br>

2. 생성자 함수 - 첫글자는 대문자로 할 것을 권장

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
- ` 백틱에서는 . 멤버 접근이 안된다 - []를 사용
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
예) isAdult(true/false), id(숫자) 멤버 추가

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
    
배열인지 확인 Array.isArray(arr) 불린 값 반환 - 'typeof array' 하면 객체로 반환

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

특정 요소만 추출 - 나이가 19 초과하는 사람의 이름
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
```
[Lodash -수학함수 라이브러리](https://lodash.com/)    
    
<br>

9. 구조 분해 할당(Destructuring assignment) - 인덱스 대신 변수명으로 사용할 수 있다

```
let [a,b,c] = [1,2] //c에는 undefined가 들어간다
let [a=3, b=4, c=5] = [1,2] //기본값을 사용하면 c=5

let a =1; let b=2 //임의 변수 없이 값 바꾸기 -> ';' 필수
    let a = 1;
    let b = 2;
    [a,b] =[b,a]
    console.log(b)

객체 구조 분해
    let user = {name: 'Mike', age: 30}
    let {name, age} = user

    console.log(name)
    
객체 구조 분해 : 새로운 변수명으로 할당    
    let user = {name: 'Mike', age: 30}
    let {name:userName, age:userAge} = user

    console.log(userName)
객체 구조 분해 : 기본값
    let user = {name: 'Mike', age:30}
    let {name, age, gender='male'} = user //user에 gender 멤버가 없다면 기본값 'gender:'male' 

```

<br>

10. Rest Parameters(...), Spread syntax (parameter매개변수/변수, argument전달인자/인수)

```
- arguments : 함수로 넘어 온 모든 인수에 접근, Array 형태의 객체, 배열의 내장 메서드(forEach..) 없음
    function showName(){
        console.log(arguments.length)
        console.log(arguments[0])
        console.log(arguments[1])
    }

    showName('Mike', 'Tom')


- Rest Parameter - 내장 메서드(forEach, reduce등) 사용가능, 나머지 매개변수는 항상 맨 뒤에 있어야한다
    function add(...numbers){ // ...args
        let result = 0
        numbers.forEach(num=>{
            result+= num
        })
        console.log(result)
    }

    add(1,2,3)
     // forEach 대신 reduce
---- let result = numbers.reduce((prev,cur)=>prev + cur) //화살표 함수(Prev+cur 가 리턴값이다)
----- let result = numbers.reduce((prev,cur)=>{return prev + cur} //블록함수(직접 리턴해줘야한다)


- Rest prameter 사용 객체 생성자 함수
    function User(name, age, ...skills){
        this.name = name
        this.age = age
        this.skills = skills
    }

    const user1 = new User("Mike", 30, "Html", "css")
    const user2 = new User("Tom", 20, "JS", "React")
    const user3 = new User("Mike", 30, "English")
    
    console.log(user1)
```

```
전개 구문(Spread syntax)

    let arr1 = [1,2,3]
    let arr2 = [4,5,6]
    let result = [0, ...arr1, ...arr2, 7,8,9]
    console.log(result)

- 복제
    let arr = [1,2,3]
    let arr2 = [...arr]
-------------------------
    let user = {name:"Mike", age: 30}
    let user2 = {...user}

    user2.name = "Tom"

    console.log(user.name)
    console.log(user2.name)
-------------------------
- 전개 구문 arr1을 [4,5,6,1,2,3] 으로
    let arr1 = [1,2,3]
    let arr2 = [4,5,6]

    arr2.reverse().forEach(num=>{
        arr1.unshift(num)
    })
    console.log(arr1)
    
    arr1 = [...arr2, ...arr1] // forEach 대신 전개 구문을 사용
   
- 객체 생성 
    let user = {name: "Mike"}
    let info = {age: 30}
    let fe = ["JS", "React"]
    let lang = ["Korean", "Engligh"]

    user = Object.assign({}, user, info, {skills:[]})

    fe.forEach(item=>{
        user.skills.push(item)
    })
    lang.forEach(item=>{
        user.skills.push(item)
    })

    console.log(user)
    
- 전개 구문 사용
   user = {
    ...user, ...info, skills: [...fe, ...lang]
    } 
```

<br>

11. Closer - 함수와 어휘적-Lexical 환경의 조합


`함수가 생성될 당시의 외부 변수를 기억, 생성 이후에도 계속 접근 가능`

```
    function makeCounter() {
      let num = 0; //은닉화

      return function () {
        return num++;
      };
    }

    let counter = makeCounter();

    console.log(counter());
    console.log(counter());
```

<br>

12. setTimeout / setInterval

`setTimeout(함수, 시간, 인수)`

```
function showName(name){
    console.log(name);
}
setTimeout(showName, 3000, 'Mike');
```

![image](https://user-images.githubusercontent.com/30430227/150924903-38433b36-a165-4a41-b8d4-e010002f2b1f.png)

```
    let num = 0;

    function showName(name) {
      console.log(`접속한지 ${num++}초가 지났습니다`);
      if (num > 5) {
        clearInterval(tid);
      }
    }

    const tid = setInterval(showName, 1000);
```

<br>

13. call, apply, bind

`call 메서드 this 특정값으로 지정`

```
    const mike = {
      name: "Mike",
    };
    function showThisName() {
      console.log(this.name);
    }

    showThisName(); //this 최상위인 window
        //this는 '.' 앞에 있는 객체다 user.show에서  'user'이 this
    showThisName.call(mike); //mike가 this가 된다

    function update(birthYear, occupation) {
      this.birthYear = birthYear;
      this.occupation = occupation;
    }

    update.call(mike, 1999, "singer"); //this, 인수...

    console.log(mike);
```

`apply - call은 매개변수를 직접받고, apply는 매개변수를 배열로 받는다`

```
update.apply(mike, [1999, "singer"]);

예)
    const nums = [3, 10, 1, 6, 4];

    const maxNum = Math.max(...nums);
    const minNum = Math.min.apply(null, nums);

    console.log(maxNum, minNum);
```

`bind - 함수의 this 값을 정한 함수를 새로 생성`

```
    ...위 예제에 이어서
    const updateMike = update.bine(mike);
    updateMike(1980, "police");
```
```
    const user = {
      name: "Mike",
      showName: function () {
        console.log(`hello, ${this.name}`);
      },
    };

    user.showName(); //. 점 앞의 user 이 this다

    let fn = user.showName; //함수로

    fn(); //this 가 없다
    fn.call(user); //user 를 this로
```

<br>

14. 상속, prototype


`객체의 공통적인 멤버를 프로토타입으로 만들어 상속한다 - 프로토타입 체인`

```
    const car = {
      wheels: 4,
      drive() {
        console.log("drive..");
      },
    };

    const bmw = {
      color: "red",
      navigation: 1,
    };

    bmw.__proto__ = car;

    const x5 = {
      color: "white",
      name: "x5",
    };

    x5.__proto__ = bmw;

    console.log(x5.wheels);

    for (p in x5) {
        if(x5.hasOwnProperty(p)){ //hasOwnProperty 매써드는 객체의 프로퍼티는 true, 상속은 false 반환 
            console.log('o', p);
        }else{
            console.log('x', p);
        }
    }
```

```
생성자 함수 사용 프로토타입 추가 

    const Bmw = function (color) {
      this.color = color;
    };

    Bmw.prototype.wheels = 4;
    Bmw.prototype.drive = function () {
      console.log("drive..");
    };

    const x5 = new Bmw("red");
    const x4 = new Bmw("blue");

    x5.drive();
```

```
- 생성자 프로토타입 다른 방법
    Bmw.prototype = {
        constructor: Bmw, //constructor을 명시 않으면 <생성자확인> .constructor 가 없게된다
        wheel: 4,
        drive(){
            console.log("drive..")
        },
        navigation: 1
    }
```

`instanceof - 해당 생성자에서 생성되었으면 true, 아니면 false 반납`

```
- 생성자 확인
    console.log(x5 instanceof Bmw);
    console.log(x5.constructor === Bmw);
```

```
- 인스턴스에서 컬러를 바꿀 수 있는 생성자
    const Bmw = function (color) {
      this.color = color;
    };

- 인스턴스에서 컬러를 바꿀 수 없는 생성자(Closer)
    const Bmw = function (color) {
        const c = color;
        this.getColor = function(){
            console.log(c)
        }
    };
----------생성--------------
    const x5 = new Bmw("red");
```

<br>

15. Class 클래스

```
- 생성자함수와 클래스 비교
    const User1 = function (name, age) {
      this.name = name;
      this.age = age;
    };
    User1.prototype.showname = function () {
      console.log(this.name);
    };
------클래스로 구현
    class User2 {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }
      showName() {
        console.log(this.name);
      }
    }

```

```
메소드 오버라이딩 
    class Car {
      constructor(color) {
        this.color = color;
        this.wheels = 4;
      }
      drive() {
        console.log("drive..");
      }
      stop() {
        console.log("STOP!");
      }
    }

    class Bmw extends Car {
      park() {
        cnsole.log("PARK");
      }
      stop() {
        super.stop(); //부모클래스의 메소드를 사용하려면 추가
        console.log("OFF");
      }
    }

    const z4 = new Bmw("blue");
```

```
- Constructor 오버라이딩 - 반드시 super 추가해줘야함(메소드오버라이딩과 차이)
- 상속 클래스를 변경하면 
    class Bmw extends Car {
      constructor(color, navigation) {
        super(color);
        this.navigation = navigation;
      }
      park() {
        cnsole.log("PARK");
      }
      stop() {
        super.stop();
        console.log("OFF");
      }
    }
```

16. Promise 

`const pr = new Promise((resolve, reject)=>{...});  - resolve 성공 시 실행

```
판매자 코드-프로미스 생성
const pr = new Promise((resolve, reject)=>{
    setTimeout(()=>{resolve('OK')},3000) //성공 전달
    //setTimeout(()=>{reject('OK')},3000) // 실패 전달
})

소비자 코드-프로미스 사용
pr.then(function(result){ console.log(result + '가지러 가자.');}, // 성공resolve 시 실행
    function(err){ console.log('다시 주문해 주세요');}   );  // 실패reject 시 실행
    
소비자 코드 -  catch문 사용해 표현
pr.then(function(result){}).catch(function(err){}) //같은 기능, 명확하고 에러 검출 용이


pr.then().catch().finally(function(){console.log('--- 주문 끝 ---')}) - 처리가 완료되면 항상 실행
```

```
콜백지옥과 프로미스
    const f1 = (callback) => {
      setTimeout(function () {
        console.log("1번 주문 완료");
        callback();
      }, 1000);
    };
    const f2 = (callback) => {
      setTimeout(function () {
        console.log("2번 주문 완료");
        callback();
      }, 3000);
    };
    const f3 = (callback) => {
      setTimeout(function () {
        console.log("3번 주문 완료");
        callback();
      }, 2000);
    };

    console.log("시작");
    console.time("경과시간"); //경과시간 시작
    f1(function () {
      f2(function () {
        f3(function () {
          console.log("끝");
          console.timeEnd("경과시간"); //경과시간 출력
        });
      });
    });
    
------ 프로미스로 구현 ---
    const f1 = () => {
      return new Promise((res, rej) => {
        setTimeout(function () {
          res("1번 주문 완료");
        }, 1000);
      });
    };
    const f2 = (message) => {
      console.log(message);
      return new Promise((res, rej) => {
        setTimeout(function () {
          res("2번 주문 완료");
        }, 3000);
      });
    };
    const f3 = (message) => {
      console.log(message);
      return new Promise((res, rej) => {
        setTimeout(function () {
          res("3번 주문 완료");
        }, 2000);
      });
    };
    
---------프로미스 체이닝으로 실행
    console.log("시작");
    console.time("경과시간");
    f1()
      .then((res) => f2(res))
      .then((res) => f3(res))
      .then((res) => {
        console.log(res);
        console.timeEnd("경과시간");
      });

------- Promise.all 로 실행 ------ 프로미스를 동시에 실행 모두 마치면 종료
    console.time("경과시간");

    Promise.all([f1(), f2(), f3()]).then((res) => {
      console.log(res);
      console.timeEnd("경과시간");
    });
    
-------- Promise.race --- 먼저 완료된 프로미스 실행 
- 용량이 큰 이미지를 보여줄 때 하나라도 로딩되면 보여줌
    console.time("경과시간");

    Promise.race([f1(), f2(), f3()]).then((res) => {
      console.log(res);
      console.timeEnd("경과시간");
    });
```

<br>

17. async, await





