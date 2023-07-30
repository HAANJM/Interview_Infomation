# DB CS / 면접 질문

- JDBC란?
- DDL / DML / DCL
- MySQL / ORACLE
- NoSQL
- RDBMS
- JOIN
- 인덱싱
- 파티셔닝

## JDBC란?

## DDL / DML / DCL
### DML : Data Manipulation Language

데이터 조작어 : 정의된 데이터베이스에 입력된 레코드를 수정하거나 조회, 삭제하는 역할을 하는 언어. <br>
우리가 jdbc / myBatis 등을 통해서 주로 사용하는 쿼리문에 해당한다. 
- select : 데이터 조회 <br>
  사용 예시 ex) <br>
  ```
  SELECT *
  FROM BOARD
  ```
- insert : 데이터 삽입 <br>
  사용 예시 ex) <br>
  ```
  모든 컬럼에 데이터를 삽입할 때
  INSERT INTO TABLE
  VALUES(#, #, #, #)

  특정 컬럼에만 데이터를 삽입할 때
  INSERT INTO TABLE(A, B, C)
  VALUES(#, #, #)
  ```
- update : 데이터 수정 <br>
  사용 예시 ex) <br>
  ```
  UPDATE TABLE
  SET COL1 = #
  AND COL2 = #
  WHERE COL3 = #
  ```
- delete 데이터 삭제 <br>
  사용 예시 ex) <br>
  ```
  DELETE FROM TABLENAME
  WHERE COL1 = #

  조건이 없으면 테이블 데이터가 전체 삭제된다
  ```

### DDL : Data Definition Language

데이터베이스를 정의하는 언어이며, 데이터를 생성, 수정, 삭제하는 등의 데이터의 전체의 골격을 결정하는 역할을 하는 언어이다. <br>

- create : 데이터베이스, 테이블 등을 생성하는 역할
- alter : 테이블을 수정하는 역할
- drop : 데이터베이스, 테이블을 삭제하는 역할
- truncate : 테이블을 초기화시키는 역할

### DCL : Data Control Language

데이터베이스에 접근하거나 객체에 권한을 주는 등의 역할을 하는 언어이다. <br>

- grant : 특정 데이터베이스 사용자에게 특정 작업에 대한 수행권한을 부여
- revoke : 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 박탈, 회수
- commit : 트랜잭션의 작업을 취소 및 원래로 복구하는 역할
- rollback : 트랜잭션의 작업을 취소 및 원래대로 복구하는 역할

### TCL : Transaction Control Language

일부에서는 DCL에서 트랜잭션을 제어하는 commit과 rollback을 TCL이라고 표현하기도 한다. <br>
