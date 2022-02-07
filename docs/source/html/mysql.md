MySQL
=======

[테스트 사이트W3DSchools](https://www.w3schools.com/mysql/trymysql.asp?filename=trysql_select_all)

<br>

XAMPP & MariaDB
----------------

[XAMPP Apache + MariaDB + PHP + Perl](https://www.apachefriends.org/index.html)

```
* MariaDB 접속
c:\xampp\mysql\bin>mysql -u root -p 

* 데이터 추출 - password가 없다
select host, user, password from user;

* 암호설정
alter user 'root'@'localhost' identified by 'brush';
alter user 'root'@'127.0.0.1' identified by 'brush';
alter user 'root'@'::1' identified by 'brush';

* 갱신 - 신규 사용자 등록 후에도 실행
flush privileges; //특권,권한 - 현재 사용중인 MySQL의 캐시를 지우고 새로운 설정을 적용

* 신규 사용자
create user brush@localhost identified by 'brush';
create user brush@127.0.0.1 identified by 'brush';
//delete from user where user = 'pma';// 사용자 삭제

* 권한 추가 - 해당 DB에 접근할 수 있는 권한
> grant all privileges on db이름.* to 계정명@'%' identified by '비밀번호';
> grant all privileges on db이름.* to 계정명@'localhost' identified by '비밀번호';
> flush privileges;```
// 계정명@'%' : 해당 계정이 모든 클라이언트에서 접근 가능
// 계정명@'localhost' : 해당 계정이 localhost(본인 pc)에서만 접근 가능
// 해당 사용자로 DB에 접속 cmd창에서 'mysql -h호스트명 -u계정명 -p DB명'
// mysql -h127.0.0.1 -ubrush -p test > 실행하면 암호 묻는다
// 정상 접속됬는지 확인 'select version();'
// 나가기 'quit;'
```

```
* 데이터베이스 생성
create database testDB;

* 데이터베이스 보기
show databases;

* 데이터베이스 삭제
drop database testDB;

* 데이터베이스 사용
use test; // 프롬프터가 MariaDB [test] 로 바뀜
```

<br>

얄코의 Mysql
-----------

```
* SELECT ... from ...; //import ...from ...와 비슷
* ... WHERE ... //조건

SELECT * FROM Orders WHERE EmployeeID = 3; //Orders 테이블에서 EmployeeID가 3 인 것 전부 불러들임
SELECT * FROM OrderDetails where quantity<5; //5보다 작은 데이터
```

```
* 정렬 order
select * from Customers order by ContactName desc; //order 데이터를 역순으로 정렬해서 출력

* 갯수 제한 limit num1, num2; //num1부터 num2갯수
select * from Customers limit 10,5;

* 원하는 별명 alias으로 데이터 가져오기
select CustomerId  as ID, CustomerName as NAME from Customers; // 한글 사용 시 '아이디' 콤마로 묶어준다
```

```
예제 Customers 데이터 테이블에서 CustomerID, CustomerName, City, country를
각각 '아이디', '고객명', '도시', '국가' 별명으로 불러오되, City가 London 또는 Country가 Mexico 인 데이터만 불러온다
정렬은 CurtomerName로 갯수는 0에서 5개로 한다.

select
	CustomerID as '아이디',
    CustomerName as '고객명',
    City as '도시',
    Country as '국가'
from Customers
where
	City = 'London' or Country = 'Mexico'
order by CustomerName
```
<br>

1. 수식

```
select 3*(2+4)/2 as NUMBER, 'Hello' as TEXT;
select 'Hello' + '002'; //문자는 숫자 0으로 해석
select '1' + '002'; //문자열이라도 숫자가 있으면 숫자로 해석

* OrderID와 ProductID 를 더한 행 추가 
select
	OrderID, ProductID,
    OrderID+ProductID
from OrderDetails;

* Products 에서 ProductName과 Price, 반값HalfPrice, SalePrice(0.75)를 추출
select
	ProductName,
    Price,
    Price / 2 as HalfPrice,
    Price * 0.75 as SalePrice
from Products;

select (true is false) is not true; //조건문

* 사칙연산
= 
!=, <>
>,<
>=, <= 

select 'a' > 'b'; //문자는 다음에 오는 문자가 크다(대소문자 구분안한다)

* Procutss 에서 Price 가 20보다 큰지 비교 후 Expensive 행에 추가한다
select
	ProductName, Price,
    Price > 20 as Expensive
from Products;

select 5 between 1 and 10; //1과 10 사이에 5가 있는가?

* OrderDetails 에서 ProductID가 1에서 4 사이에 있는 데이터 추출
select * from OrderDetails
where ProductID between 1 and 4;

select 1 + 2 in (2,3,4); // 선택지 안에 있으면 True '1'

* LIKE '%', '_'
select 'Hello' like 'hel%'; // true '%'-0개 이상 문자가 올 수 있다
select 'Hello' like '%H'; // false

select 'hello' like 'h__lo'; // true '_'-1개의 문자만 올 수 있다
select 'hello' like '_h__lo'; //false

* Customers 테이블에서 CustomerName 이 b로 시작되는 모든 데이터 추출
select * from Customers
where CustomerName like 'b%';

```

<br>

2. 함수

```
* Products 데이터에서 price과 Price의 반올림, 천정값을 추출
select
	Price,
    round(price),
    floor(price)
from Products;

* abs를 사용해서 OrderDetails 에서 quantity가 5보다 크고 15보다 작은 데이터 추출
(|x| < 5 ->   -5 < x < 5, :: 5는 최대최소, x-a 의 a는 센터값 즉 10을 기준으로 +-5)
select * from OrderDetails
where abs(quantity - 10) < 5;

* truncate 소수점 이하/이상 삭제/0으로 채움
- Products에서 price가 12.XX인(소수점 무시) 데이터 추출
select * from Products
where truncate(price,0)=12;

* 문자열 합치기
select concat('Hello',' ','This is ', 2002)
select concat_ws('-', 2002, 8, 15, 'AM');
select concat('O-ID: ', orderid) from Orders;
select concat_ws(' ', firstname, lastname) as FullName from Employees;

* 문자열 자르기
select
	left('ABCDEFG',3),
	right('ABCDEFG',3),
	substr('ABCDEFG',3,3),
	substr('ABCDEFG',-4,2);

* Orders 데이터에서 orderdate의 년월일 값을 각각  Year, Month, Day 행으로 추출
select 
	orderdate,
    left(orderdate, 4) as Year,
    substr(orderdate, 6, 2) as Month,
    right(orderdate, 2) as Day
from Orders;

* 문자열 길이
select
	length('안녕하세요'),
	char_length('안녕하세요');//한글 길이

* trim 잘라내기
select
	concat('|',trim(' Hello '),'|');
	
* pad 채우기
select
	lpad('ABC',5,'*'),
   	rpad('ABC',5,'*');

* replace 바꾸기
select
	replace('맥도날드에서 맥도날드 햄버거를 먹었다.','맥도날드','버거킹');
	
* instr 문자열 찾기(위치 인덱스)
select
	instr('ABCDE', 'BC');
	
** 문자열의 첫번째 단어가 철자가 6보다 작은 데이터 추출

select * from Customers
where instr(customername, ' ') between 1 and 6;

* cast 자료형 변환
select
    '01' = '1',
    convert('01', decimal) = convert('1', decimal);
```

<br>

3. 시간/날짜 함수

```
select curdate(), curtime(), now();

* 문자열을 날짜/시간 데이터로 변환
select
    date('2021-6-21'),
    time('01:22');
    time('2021-6-21 01:22');

* Orders 데이터 orderdate 행 사용 추출 예
select
	orderdate,
    year(orderdate) as YEAR,
    monthname(orderdate) as MONTHNAME
from Orders;

* 예
select
    OrderDate,
    concat(
        concat_ws(
            '/', year(orderdate),month(orderdate),day(orderdate)
            ),' ', upper(left(dayname(orderdate),3))
        )
 from Orders;

* 월요일만 추출
select * from Orders
where weekday(orderdate) = 0;

* 날짜 더하기/빼기 AddDate Interval
select
    adddate('2021-06-20', interval 2 month),
    adddate('2021-06-20', interval -4 day);
    
* 날짜 경과 DateDiff
select
   OrderDate,
   Now(),
   datediff(now(),orderdate)
from Orders;

* date_format()
select
    date_format(now(), '%Y년 %m월 %d일 %p %h시 %i분 %s초');

* AM/PM을 오전/오후 로 변환
select replace(
    replace(
        date_format(now(), '%Y년 %m월 %d일 %p %h시 %i분 %s초'),
        'AM', '오전'
        ), 'PM','오후');

* IF(A,B,C) -A조건, B참일 때(ifnull(A,B) - null일 때 A)
select if(1 > 2, '1은 2보다 크다.','1은 2보다 작다.');

* case
select
    case
        when -1 > 0 then '-1은 양수다.'
        when -1 = 0 then '-1은 0이다.'
        else '-1은 음수다.'
    end;

```

<br>

4. 조건에 따라 그룹으로 묶기

```
* Group - 파이썬의 집합set과 비슷(중복되지않는다)
select Country from Customers group by country;

select country, city, concat_ws(', ',City,country)
from Customers
group by Country, city;

* 날짜그룹마다 주문 갯수
select
count(*), orderdate // count - 행의 숫자합(* Null까지 센다)
from Orders
group by orderdate;

* 카테고리 ID마디 최대, 최소, 중간값, 평균값 추출
select categoryid,
max(price) as MaxPrice,
min(price) as MinPrice,
truncate((max(price)-min(price))/2, 2) as MedianPrice,
truncate(avg(price), 2) as AveragePrice
from Products
group by categoryid;

* Customers 테이블에서 country, city 그룹의 갯수
select
concat_ws(', ', city, country) as Location,
count(customerID) // count(*) - Null 포함
from Customers
group by country, city;
with rollup;

* with rollup - 마지막 열에 갯수의 합

* having - 그룹 후 데이터의 조건(where 는 그룹 전 데이터에 사용)
select
count(*) as Count, Orderdate
from Orders
where orderdate > date('1996-12-31')
group by orderdate
having count > 2;

having averageprice between 20 and 30 and medianprice < 40; // 위 중간,평균 쿼리문에 추가해본다

* distinct 별개의 - 그룹처럼 중복은 제거하나 순서정렬은 하지않고 그대로 추출 -group 보다 처리가 빠르다
select distinct categoryid
from Products;

//distinct 정렬
select distinct country
from Customers
order by country;

//group와 함께 사용 - 국가별 도시 갯수
select country, count(distinct city)// 중복된 city 제거
from Customers
group by country;

```

Selection 깊게 파기
--------------------

1. 비상관 서브쿼리

```
* ()사용
select categoryid, categoryname, description,
(select ProductName from Products where productid =1)
from Categories;

* 가격의 평균보다 적은 product를 추출
select * from Products
where Price < (select avg(price) from Products);

* (Products 에서 Chais 인) categoryid (1)인 데이터를 추출
select categoryID, categoryName, description
from Categories
where categoryID = (select categoryid from Products where productname = 'Chais');

* 서브쿼리가 하나이상의 값을 추출하는 경우 '=' 대신 'in' 사용
select categoryID, categoryName, description
from Categories
where categoryID in (select categoryid from Products where price > 50);

* All
select * from Products
where price > all(select price from Products where categoryid =2);
// 서브쿼리의 categoryid가 2인 가격 모두 보다 큰 가격을 가진 자료 추출)

* Any
select categoryid, categoryName, description
from Categories
where CategoryID = any
(select categoryid from Products where price > 50);
// any 를 in으로 바꿔도 같은 결과?
```












