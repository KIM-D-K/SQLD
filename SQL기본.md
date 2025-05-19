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
- 
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
6) TRIM([위치][특정문자][FROM]문자열) *[]는 옵션 : 옵션이 하나도 없을 경우 문자열의 왼쪽과 오른쪽 공백을 제거하고, 그렇지 않을 경우 문자열을 위치(LEADING or TRAILING or BOTH)로 지정된 곳부터 한 글자씩 특정 문자와 비교하여 같으면 제거하고 같지 않으면 멈춘다. LTRIM, RTRIM과는 달리 특정 문자는 한글자만 지정할 수 있다. (SQL Server(MSSQL)의 경우 공백 제거만 가능하다.)  
![image](https://github.com/user-attachments/assets/7d29bd7f-1dc4-4dac-869e-29e70e9a5060)
![image](https://github.com/user-attachments/assets/92b82761-60fd-4018-849c-8ee6e6ea60dc)
![image](https://github.com/user-attachments/assets/55b0de47-913e-438d-bee0-2c3763920767)
7) SUBSTR(문자열, 시작점 [,길이]) *[]는 옵션 : 문자열의 원하는 부분만 잘라서 반환해주는 함수이다. 길이를 명시하지 않았을 경우 문자열의 시작점부터 문자열의 끝까지 반환된다. (SQL Server(MSSQL)의 경우 SUBSTRING(문자열))
![image](https://github.com/user-attachments/assets/28af9439-f018-4430-8f24-37d8d4519965)
![image](https://github.com/user-attachments/assets/cfa83246-4b38-4698-9c3c-2312b741c355)
8) LENGTH(문자열) : 문자열의 길이를 반환해주는 함수이다. (SQL Server(MSSQL)의 경우 LEN(문자열))
![image](https://github.com/user-attachments/assets/7324bdbb-5b8d-409a-883d-2686d7ea4906)
![image](https://github.com/user-attachments/assets/087c9d43-762a-4233-a5ab-a3bb4832bdd5)
9) REPLACE(문자열, 변경 전 문자열 [,변경 후 문자열]) *[]는 옵션 : 문자열에서 변경 전 문자열을 찾아 변경 후 문자열로 바꿔주는 함수이다. 변경 후 문자열을 명시해주지 않으면 문자열에서 변경 전 문자열을 제거한다.
![image](https://github.com/user-attachments/assets/7fa3fe96-82c1-48f0-bbf0-0e568b841a45)
![image](https://github.com/user-attachments/assets/985fba8c-14d9-4091-9531-ceb889ece10b)
10) LPAD(문자열, 길이, 문자) : 문자열이 설정한 길이가 될 때까지 왼쪽을 특정 문자로 채우는 함수이다. 
![image](https://github.com/user-attachments/assets/5f2d7888-3f10-48f6-a5d7-ed93389572a3)
- - -

### <숫자 함수>
1) ABS(수) : 수의 절댓값을 반환해주는 함수이다.
![image](https://github.com/user-attachments/assets/9c26a6a9-8934-4cb9-8fe3-eacdd4d10ccb)
![image](https://github.com/user-attachments/assets/4237ff58-7dc1-4188-8480-3e1898ba5609)
2) SIGN(수) : 수의 부호를 반환해주는 함수이다. 양수이면 1, 음수이면 -1, 0이면 0을 반환한다.
![image](https://github.com/user-attachments/assets/9240fd40-0084-4306-907e-5056b09d52fd)
![image](https://github.com/user-attachments/assets/010fe721-4e0a-421e-a2aa-73596ba83892)
3) ROUND(수 [,자리수]) *[]는 옵션 : 수를 지정된 소수점 자릿수까지 반올림하여 반환해주는 함수이다. 자릿수를 명시하지 않았을 경우 기본값은 0이며 반올림된 정수로 반환하고 자릿수가 음수일 경우 지정된 정수부를 반올림하여 반환한다.
![image](https://github.com/user-attachments/assets/e823e370-a406-4acd-99b7-da5bb159cb9b)
![image](https://github.com/user-attachments/assets/ddda079b-dfcf-41e1-86ad-edf7074d9c1a)
4) TRUNC(수 [,자릿수]) *[]는 옵션 : 수를 지정된 소수점 자릿수까지 버림하여 반환해주는 함수이다. 자릿수를 명시하지 않았을 경우 기본값은 0이며 버림된정수로 반환하고 자릿수가 음수일 경우 지정된 정수부에서 버림하여 반환한다.
![image](https://github.com/user-attachments/assets/70588667-7e84-4c66-9ab6-34ba3693d8d1)
![image](https://github.com/user-attachments/assets/21892db5-d0f2-4829-b4ca-5212538e4090)
5) CEIL(수) : 소수점 이하의 수를 올림한 정수를 반환해주는 함수이다. (SQL Server(MSSQL)의 경우 CEILING(문자열))
![image](https://github.com/user-attachments/assets/95947830-643e-4f5e-83e8-570e5b4dcb74)
![image](https://github.com/user-attachments/assets/3b0f5011-bd9c-4c19-a502-8dbba934b3ca)
6) FLOOR(수) : 소수점 이하의 수를 버림한 정수를 반환해주는 함수이다.
![image](https://github.com/user-attachments/assets/ccb0444e-12b2-4410-8498-702ec525e1fd)
![image](https://github.com/user-attachments/assets/6ffd24af-1c0a-45f8-94db-e8e752208b52)
7) MOD(수1, 수2) : 수1을 수2로 나눈 나머지를 반환해주는 함수이다. 단, 수2가 0일 경우 수1을 반환한다.
![image](https://github.com/user-attachments/assets/4e01177e-f6b2-4503-92db-5466a35e7380)
![image](https://github.com/user-attachments/assets/345f76bc-3860-47dd-9da6-2d5fb3cea56c)
- - -
### <날짜 함수>
1) SYSDATE : 현재의 연, 월, 일, 시, 분, 초를 반환해주는 함수이다(nls_date_format에 따라서 sysdate의 출력 양식은 달라질 수 있음). (SQL Server(MSSQL)의 경우 GETDATE())
![image](https://github.com/user-attachments/assets/6a4ab10a-9537-4055-8c4a-1d57e17dfecf)
2) EXTRACT(특정 단위 FROM 날짜 데이터) : 날짜 데이터에서 특정 단위(YEAR, MONTH, DAY, HOUR, MINUTE, SECOND)만을 출력해서 반환해주는 함수이다. (SQL Server(MSSQL)의 경우 DATEPART(특정 단위, 날짜 데이터))
![image](https://github.com/user-attachments/assets/65fdebcb-52c7-49da-b896-0690a1149632)
3) ADD_MONTHS(날짜 데이터, 특정 개월 수) : 날짜 데이터에서 특정 개월 수를 더한 날짜를 반환해주는 함수이다. 날짜의 이전 달이나 다음 달에 기준 날짜의 일자가 존재하지 않으면 해당 월의 마지막 일자가 반환된다. (SQL Server(MSSQL)의 경우 DATEADD(MONTH, 특정 개월 수, 날짜 데이터))
![image](https://github.com/user-attachments/assets/ea5faebe-386d-4daf-961e-3b0b5e4fb03b)
- - -
### <변환 함수>
1) 명시적 형변환과 암시적 형변환
  - 명시적 형변환 : 변환 함수를 사용하여 데이터 유형 변환을 명시적으로 나타냄
  - 암시적 형변환 : 데이터베이스가 내부적으로 알아서 데이터 유형을 변환함
2) 명시적 형변환에 쓰이는 함수 (SQL Server(MSSQL)의 경우 CONVERT나 CAST 함수를 사용할 수 있다.)
  - TO_NUMBER(문자열) : 문자열을 숫자형으로 변환해주는 함수이다.
  ![image](https://github.com/user-attachments/assets/fd933fef-3e3d-4dd1-94af-6182522f2d20)
  ![image](https://github.com/user-attachments/assets/ba98d8fe-3204-434f-9403-4a908f18cf26)
  - TO_CHAR(수 or 날짜[, 포맷]) *[]는 옵션 : 수나 날짜형의 데이터를 포맷 형식의 문자형으로 변환해주는 함수이다.
  ![image](https://github.com/user-attachments/assets/aacb1210-fcee-45d2-8e2e-247ab147fd44)
  ![image](https://github.com/user-attachments/assets/c7a6d12c-918f-4f8a-a2e1-55a5faea8881)
  - TO_DATE(문자열, 포맷) : 포맷 형식의 문자형의 데이터를 날짜형으로 변환해주는 함수이다.
  ![image](https://github.com/user-attachments/assets/5c2e32ae-0a4c-45f5-ab17-d57bb11ee48c)
  ![image](https://github.com/user-attachments/assets/20f90418-1666-415f-8922-f808948238fd)
- - -
### <NULL 관련 함수>







