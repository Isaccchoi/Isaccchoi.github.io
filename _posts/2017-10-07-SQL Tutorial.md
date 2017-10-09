# SQL Tutorial

> https://www.w3schools.com/sql/default.asp


```sql
SELECT * FROM Customers;
```

CustomerID | CustomerName| ContactName| Address | City|PostalCode|Country
-----------|-------------|------------|---------|-----|----------|-------
1|Alfreds FutterKiste|Maria Anders|Obere Str. 57|Berlin|12209|Germany
2|Ana Trujillo Emparedados y helados| Ana Trujillo|Avda. de la Constitucion 2222|Mexico D.F.|05021|Mexico
3|Antronio Moreno Taqyeria|Antonio Moreno| Mataderos 2312|Mexico D.F.|05023|Mexico
4|Around the Horn|Thomas Hardy|120 Hanover Sq.| London | WA1 1DP | UK
5|Berglunds snabbköp | Christina Berglund |Berguvsvägen 8|Luleå|S-958 22|Sweden



- **SELECT** - 데이터 베이스에서 추출
- **UPDATE** - 데이터 베이스에 데이터를 업데이트
- **DELETE** - 데이터 베이스에서 데이터를 삭제
- **INSERT INTO** - 데이터 베이스에 데이터를 삽입
- **CREATE DATABASE** - 새로운 데이터 베이스를 새성
- **ALTER DATABASE** - 데이터베이스를 수정 
- **CREATE TABLE** - 새로운 테이블 생성
- **ALTER TABLE** - 테이블 수정
- **DROP TABLE** - 테이블 제거
- **CREATE INDEX** - 인덱스를 생성(검색키)
- **DROP INDEX** - 인덱스를 삭제


## SELECT 문법

```SQL
SELECT column1, column2, ...
From table_name;
```
상기 방법으로 추출시 해당 컬럼만 나오게 된다
```
SELECT CustomerName, City FROM Customer;
```


CustomerName | City
-------------|-----
Alfreds FutterKiste| Berlin
Ana Trujillo Emparedados y helados| Mexico D.F.
Antronio Moreno Taqyeria|Mexico D.F.
Around the Horn| London


### SELECT DISTINCT
해당 문법 사용시 뒤에 작성한 Column에서 겹치지 않는 유일한 값만 찾아낸다(여러개가 있을 경우 *한가지만* 출력)


## WEHRE 문법
조건을 주어 원하는 값을 찾아낼 수 있다.(여러값 가능)

```SQL
SELECT * FROM Customers
WHERE CustomerID=1;
```
이 경우 에는 CustomerID가 1인 값만 추출 하며

```SQL
SELECT * FROM Customers
WHERE Country='Mexico';
```
이 경우 에는 Country가 Mexico인 값만 추출해준다.



## SQL AND, OR and NOT 문법

- **AND** - 조건을 모두 만족할 경우에 추출 
- **OR** - 조건중 한가지를 만족할 경우에 추출
- **NOT** - 조건이 아닌 경우만 추출


```SQL
SELECT column1, column2, ...
FROM tabla_name
WHERE condition1 AND condition2 AND.... ;
```

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE codition1 OR condition2 OR ...;
```
```SQL
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition; 
```

## ORDER BY 
정렬을 해주는 문법

- DESC - 역순
- ASC - 정순

```SQL
SELECT column1, column2, ....
FROM table_name
ORDER BY column1, column2, .... ASC|DESC;
```

## INSER INTO
데이터 삽입
맨 마지막에 데이터가 삽입 된다. 
```SQL
INSERT INTO Customers
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```
## NULL
Where문을 통해 NULL 값을 찾을 수도 있으며 삽입시 넣을수도 있음 

## UPDATE
기존 데이터 변경 문법

```SQL
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
WHERE CustomerID = 1;
```
<small style='color: gray;'>CustomerID 가 1번인 값을 찾아 ContactName과 City를 변경</small>


