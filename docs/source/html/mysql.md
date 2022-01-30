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

