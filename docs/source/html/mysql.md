MySQL
=======

[테스트 사이트W3DSchools](https://www.w3schools.com/mysql/trymysql.asp?filename=trysql_select_all)

`--주석`

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
각각 '아이디', '고객명', '도시', '국가' 별명으로 불러오되, City가 London 또는 Mexico 인 데이터만 불러온다
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

