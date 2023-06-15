# DB CS / 면접 질문

- JDBC란?
- DDL / DML / DCL
- MySQL / ORACLE
- NoSQL
- RDBMS
- JOIN

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

### DCL : Data Control Language

### TCL : Transaction Control Language
