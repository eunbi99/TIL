### SQL 문장들의 종류
#### 데이터 조작어 (DML : Data Manipulation Language)
- SELECT : 데이터베이스에 들어 있는 데이터를 조회하거나 검색하기 위한 명령어를 말하는 것으로 `RETRIEVE` 라고도 한다.
- INSERT / UPDATE / DELETE : 데이터베이스의 테이블에 들어 있는 데이터에 변형을 가하는 종류의 명령어 <br>
🚀 DML은 사용자가 무슨 데이터를 원하는지만을 명세한다. <br>
🚀 절차적데이터 조작어(PL/SQL(오라클), T-SQL(SQLServer)은 사용자가 무슨 데이터를 원하는지, 어떻게 그것을 접근해야 되는지를 명세한다.

#### 데이터 정의어 (DDL : Data Definition Language)
- CREATE / ALTER / DROP / RENAME : 테이블과 같은 데이터 구조를 정의하는데 사용되는 명령어들. 데이터 구조와 관련된 명령어들

#### 데이터 제어어 (DCL : Data Control Language)
- GRANT / REVOKE : 데이터 베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 명령어

#### 트랜잭션 제어어 (TCL : Transaction Control Language)
- COMMIT / ROLLBACK : 논리적인 작업의 단위를 묶어서 DML에 의해 조작된 결과를 작업단위(트랜잭션) 별로 제어하는 명령어
<hr>

### 테이블 칼럼에 대한 정의 변경
#### [ORACLE]
- ALTER TABLE 테이블명 MODIFY (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 ...);

#### [SQLServer]
- ALTER TABLE 테이블명 ALTER (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 ...);
<br>👉 여러개의 컬럼을 동시에 수정하는 구문은 없다.
<hr>

###  Cascade 
- 부모테이블을 삭제하면 자식 테이블도 삭제된다.

### 제약조건의 종류
- PRIMARY KEY (기본키) 
  -  주키로 테이블당 `1개만 생성` 가능하다.
  -  `NULL 값이 존재 X`
- UNIQUE KEY (고유키) 
  -  테이블 내에서 중복되는 값이 없으며 `NULL 입력 가능`하다!
- NOT NULL 
  -  명시적으로 NULL 입력을 방지한다.
- CHECK 
  -  데이터를 입력할 때 해당 값이 조건에 부합하는지 체크한다. 부합이 되면 입력, 부합되지 않으면 입력되지 않도록 한다.
  -  데이터베이스에서 데이터의 무결성을 유지하기 위하여 테이블의 특정 컬럼에 설정하는 제약이다.
- FOREIGN KEY (외래키) 
  -   외래키로 테이블당 `여러 개` 생성이 가능하다.
  -   테이블 생성시 설정 가능하다.
  -   `NULL값을 가질 수 있다`.
  -   참조 무결성 제약을 받을 수 있다.
<hr>

### 테이블 생성의 주의사항
- 테이블명은 객체를 의미할 수 있는 적절한 이름 사용, 가능한 단수형 권고!
- 테이블 명은 다른 테이블과 중복 X 
- 한 테이블 내에서는 칼럼명이 중복되게 지정 X
- 테이블 이름을 각 지정하고 각 칼럼들은 괄호 "()"로 묶어 지정
- 각 칼럼들은 콤마 ","로 구분, 생성문의 끝은 항상 세미콜론 ";"으로 끝난다.
- 칼럼에 대해서는 일관성 있게 사용하는 것이 좋다,
- 칼럼 뒤에 데이터 유형은 꼭 지정해주어야 한다.
- 테이블명과 칼럼명은 반드시 문자로 시작, 길이에 대한 한계가 있다.
- 사전에 정의한 예약어는 사용 X
- A-Z,a-z,0-9,_,$,# 문자만 허용
<hr>

###  테이블의 불필요한 칼럼 삭제
- `ALTER TABLE` 테이블명 `DROP COLUMN` 삭제할 칼럼명;

###  테이블의 이름을 변경
- `RENAME` 기존 테이블명 `TO` 변경 할 테이블명;

### 테이블에 데이터를 입력
- INSERT INTO 테이블명 (COLUMN_LIST) VALUES (COLUMN_LIST에 넣을 VALUE_LIST);
- INSERT INTO 테이블명 VALUES (전체 COLUMN에 넣을 VALUE_LIST);

### 입력된 데이터의 수정 
- UPDATE 테이블명 SET 기존 칼럼명 = 수정 값;

### 데이터 조회
- SELECT [ALL / DISTINCT] 칼럼명 ... FROM 테이블명;
  - ALL : 중복된 데이터가 있어도 모두 출력
  - DISTINCT : 중복 제외해서 출력 
<hr>

### TRUNCATE TABLE / DROP TABLE / DELETE 의 차이

|DROP|TRUNCATE|DELETE|
|------|---|---|
|DDL|DDL(일부 DML)|DML|
|RollBack 가능|RollBack 불가능|Commit 이전 RollBack 가능|
|Auto Commit|Auto Commit|사용자 Commit|
|로그 X|로그 X|로그 O|
|정의 삭제|최초 초기상태|데이터만 삭제|
|Auto Commit|Auto Commit|사용자 Commit|
<hr>

### 롤백(ROLLBACK)
- 데이터의 변경 사항이 취소되어 데이터의 이전 상태로 복구, 관련된 행에 대한 잠금(LOCKING)이 풀리고 다른 사용자들이 데이터를 변경 O
- ORACLE - DDL 수행후 자동으로 COMMIT O
- SQLServer - DDL 수행 후 자동 COMMIT X
<hr>

### 트랜잭션 : 데이터베이스의 논리적 연산단위로서 밀접히 관련되어 분리될 수 없는 한 개 이상의 데이터베이스 조작
#### 트랜잭션의 종료를 위한 대표적인 명령어
- 데이터에 대한 변경사항을 데이터베이스에 영구적으로 반영하는 COMMIT
- 변경사항을 모두 폐기하고 변경전의 상태로 되돌리는 ROLLBACK 
### 트랜잭션 특성
- 원자성(atomicity) : 트랙잭션에서 정의된 연산들은 모두 실행 or 전혀 실행되지 않은 상태로 남아야 함(all or nothing)
- 일관성(consistency) :트랙잭션이 실행되기 전에 잘못 되어 있지 않다면 실행된 이후에도 데이터베이스의 내용이 잘못이 있으면 안된다.
- 고립성(isolation) : 트랙잭션이 실행되는 도중에 다른 트랜잭션의 영향을 받아 잘못된 결과를 만들어서는 안 된다.
- 지속성(durability): 트랙잭션이 성공적으로 수행되면 갱신한 데이터베이스의 내용은 영구적으로 저장된다.
<hr>
