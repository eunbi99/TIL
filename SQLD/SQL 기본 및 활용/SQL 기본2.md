### 📌 BEGIN TRANSACTION
ROLLBACK 구분을 만나면 최초의 BEGIN TRANSACTION 시점까지 ROLLBACK이 된다.

저장점(SAVE POINT)를 정의하면 롤백(ROLLBACK)할 때 트랜잭션에 포함된 전체 작업을 롤백하는 것이 아니라 현 시점에서 SAVEPOINT 까지 트랜잭션의 일부만 롤백 가능하다.<br>

#### 📍 [ORACLE]
SAVEPOINT SVPT1;<br>
...<br>
ROLLBACK TO SVPT1;

#### 📍 [SQL Server]
SAVE TRANSACTION SVPTR1;<br>
...<br>
ROLLBACK TRANSACTION SVTR1;
<hr>

### 내장함수
💎 단일행 함수
- 단일행 함수는 SELECT, WHERE, ORDER BY, UPDATE의 SET절에 사용 가능

💎 다중행 함수
- 다중행 함수는 집계함수, 그룹 함수, 윈도우 함수로 구분된다.

#### [주의!]
- 1:M관계의 테이블을 조인할 때 단일행 함수를 사용 할 수 있다.
    - 1:M 조인이더라도 M쪽에서 출력된 행이 하나씩 단일행 함수의 입력값으로 사용되므로 사용 가능하다.
- 단일행 함수와 다중행 함수는 여러개의 인수가 입력되어도 단일 값만을 반환한다.

<hr> 

### 연산자의 종류
#### [ 부정 SQL 연산자 ]  
- `NOT BETWEEN a AND b` : a와 b 값 사이에 있지 않다.(a와 b를 포함하지 않는다)
- NOT IN (list) : list값과 일치하지 않는다.
- NOT 칼럼명 > : ~보다 크지 않다.

#### [ 부정 비교 연산자 ]
- `!=` : 같지 않다.
- `^=` : 같지 않다.
- `<>` : 같지 않다.
- `NOT 칼럼명` = : ~와 같지 않다.
- `NOT 칼럼명` > : ~보다 크지 않다.

#### [ SQL 연산자 ]
-  `BETWEEN a AND b` : a와 b의 값 사이에 있으면 된다. (a와 b의 값이 포함됨.)
- `IN (list)` : 리스트에 있는 값 중에서 어느 하나라도 일치하면 된다.
- `LIKE '비교 문자열'` : 비교문자열과 형태가 일치하면 된다.(%, _사용)
- `IS NULL` : NULL 값인 경우   
<hr>

### 📌 NULL 
널 값은 아직 정의되지 않은 값으로 0 또는 공백과 다르다.
- 테이블을 생성할 때 NOT NULL 또는 PRIMARY KEY로 정의되지 않은 모든 데이터 유형은 널 값을 포함 할 수 있다.
- NULL이 포함된 사칙연산 결과는 무조건 NULL이다.
- 결과 값을 NULL이 아닌 다른 값을 얻고자 할 때 NVL/ISNULL 함수를 사용

```
💎 NVL(표현식1,표현식2) / ISNULL(표현식1,표현식2) 
: 표현식1의 결과값이 NULL일 경우, 표현식2를 출력  

ex) ISNULL(COL2,'X') -> COL2의 값이 NULL일 경우 'X' 출력

💎 NULLIF(표현식1,표현식2) 
: 표현식1과 표현식2의 값이 같으면 NULL 반환, 같지 않으면 표현식1을 반환

💎 COALESCE(표현식1,표현식2)
: 임의의 개수 표현식에서 NULL이 아닌 최초의 표현식 반환. 만약 모두 NULL일 경우 NULL 반환
```
