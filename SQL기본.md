관계형 데이터베이스 개요
========================

### <데이터베이스>
1) 예를들어 버스정류장 도착시간, 학식 메뉴, 드라마 방영시간 등 매일매일 수많은 데이터와 마주하며 살아간다. 한마디로 데이터베이스는 이런 데이터들을 저장하는 공간이다.
- - -
### <관계형 데이터베이스>
1) 흔히 RDB(Relational Database)라고 불리는 관계형 데이터베이스는 말 그대로 관계형 데이터 모델에 기초로 둔 데이터베이스이다. 관계형 데이터베이스에서의 설계는 모든 데이터를 2차원 테이블 형태로 표현한 뒤 각 테이블 간의 관계를
 정의하는 것으로 시작된다. RDBMS(Relational Database Management System)는 이러한 RDB를 관리 · 감독하기 위한 시스템이며, 우리가 익히 알고 있는 Oracle, SQL Server(MSSQL), MySQL, MariaDB, PostgreSQL 등이 이에 속한다.
- - -

### <테이블>

1) 관계형 데이터베이스는 모든 데이터를 2차원 테이블 형태로 표현한다. 2차원 테이블 형태는 우리가 엑셀을 작성할 때 흔히 이용하는 표 형식을 떠올라면 이해하기 쉽다. (아래 그림 엑셀 예시)

![image](https://github.com/user-attachments/assets/11ff0fd2-79e3-4857-a6b7-8c55154a9164)
- 테이블 형태

 ![image](https://github.com/user-attachments/assets/08bdd9cc-8b1a-4c0d-8b5b-9b999039ffbd)

테이블은 관계형 데이터베이스의 기본 단위이고 일반적으로 데이터베이스는 여러 개의 테이블로 구성된다. 아렇게 데이터를 저장하는 주된 목적은 데이터를 활용하는 데에 있고 우리는 그것을 테이블 형태로 조회하고 변경하고 삭제할 수 있다.
- - -
### <SQL(Structured Query Language)>
1) SQL은 관계형 데이터베이스에서 데이터를 다루기 위해 사용하는 언어이다.
- - -

SELECT문
----------------

### <조회>
- 저장되어 있는 데이터를 조회하고자 할 때 사용하는 명령어이다.
![image](https://github.com/user-attachments/assets/3f239b01-3472-482c-9501-601897b22d42)
컬럼을 따로 명시하지 않고 *(asterisk)를 쓰면 전체 컬럼이 조회되며 조회되는 컬럼의 순서는 테이블의 컬럼 순서와 동일하다. 그리고 별도의 WHERE 절이 없으면 테이블의 전체 Row가 조회된다.
![image](https://github.com/user-attachments/assets/9ce7ae41-41ab-4416-9787-68db95f102ea)
테이블명이나 컬럼명에 별도의 별칭(Alias)을 붙여줄 수 있는데, 붙여주는 목적은 요즘 우리가 줄임말을 즐겨 쓰는 이유와 비슷하다. 여러 개의 테이블을 JOIN하거나 서브쿼리가 있을 때 컬럼명 앞에 테이블명을 같이 명시해야 하는 경우
 테이블명은 비교적 길기 때문에 짧게 줄여 쓰기 위해 Alias를 붙여 주는 것이다. Alias를 붙일 때는 앞에 AS를 넣어도되고 넣지 않아도 된다.
![image](https://github.com/user-attachments/assets/853bc19b-1526-4dd4-9203-2f51c0e43a30)
- - -
### <산술 연산자>
- 수학에서 사용하는 사칙연산의 기능을 가진 연산자이다. NUMBER나 DATE 유형의 데이터와 같이 사용할 수 있으며, 다른 컬럼끼리의 연산에 NULL이 포함되어 있는 경우 결과값은 NULL이 된다.
![image](https://github.com/user-attachments/assets/f3ba212c-40a3-4c69-b396-49bf96866c81)
- - -
### <합성 연산자>
- 문자와 문자를 연결할 때 사용하는 연산자이다.
![image](https://github.com/user-attachments/assets/0e6b0860-dc53-4037-9455-1f3473391a52)
![image](https://github.com/user-attachments/assets/79995f3e-edf4-4638-b158-f313ad6a0d3c)
- - -

함수
----

### <문자 함수>
1) CHR(ASCII 코드) : ASCII 코드는 총 128개의 문자를 숫자로 표현할 수 있도록 정의해 놓은 코드이다. CHR 함수는 ASCII 코드를 인수로 입력했을 때 매핑되는 문자가 무엇인지를 알려주는 함수이다. (SQL Server(MSSQL)의 경우 CHAR(ASCII 코드)
![image](https://github.com/user-attachments/assets/6431f1f1-1869-4572-9e0a-5d3742c049f4)
2) LOWER(문자열) : 문자열을 소문자로 변환해주는 함수이다.
![image](https://github.com/user-attachments/assets/39741818-6094-4c73-bb64-6a3346d50993)
3) UPPER(문자열) : 문자열을 대문자로 변환해주는 함수이다.
![image](https://github.com/user-attachments/assets/5c3c8f0c-a33e-4c1c-b4fe-588d2f7808a5)
4) LTRIM(문자열 [,특정 문자]) *[]는 옵션 : 특정 문자를 따로 명시해주지 않으면 문자열의 왼쪽 공백을 제거하고, 명시해주었을 경우 문자열을 왼쪽부터 한 글자씩 특정 문자와 비교하여 특정 문자에 포함되어 있으면 제거하고 포함되지 않았으면 멈춘다. (SQL Server(MSSQL)의 경우 공백 제거만 가능하다.)
![image](https://github.com/user-attachments/assets/6509f720-6aaa-41e0-89f8-a2d497e00f5c)
![image](https://github.com/user-attachments/assets/532699c1-f10d-4022-8e7d-3790e78405d6)
5) RTRIM(문자열 [,특정 문자] *[]는 옵션 : 특정 문자를 따로 명시해주지 않으면 문자열의 오른쪽 공백을 제거하고, 명시해주었을 경우 문자열을 오른쪽부터 한 글자씩 특정 문자와 비교하여 특정 문자에 포함되어 있으면 제거하고 포함되지 않았으면 멈춘다. (SQL Server(MSSQL)의 경우 공백 제거만 가능하다.)
![image](https://github.com/user-attachments/assets/252f0e8c-020b-4c81-952a-c4e215090362)
![image](https://github.com/user-attachments/assets/12d48015-287f-4034-8f45-b0a0e7787e4f)






