# 2-1-5 WHERE 절



# 1. WHERE 조건절 개요

**가. 개요**

​    \- 사용자들이 원하는 자료만을 검색하기 위해 SQL 문장에 WHERE 절을 이용하여 자료에 대한 제한을 줄 수 있다

​    \- WHERE 절에는 두 개 이상의 테이블에 대한 조인 조건이나 결과를 제한하기 위한 조건을 기술할 수 있다

​    \- 조회하려는 데이터에 특정 조건을 부여하는 목적이기 때문에 FROM 절 뒤에 위치한다

​    \- 구문 : *SELECT [DISTINCT또는ALL] 칼럼명 [ALIAS명] FROM 테이블명 WHERE 조건식;*

**나. 연산 우선순위**

​    \- 괄호 > NOT 연산자 > 비교 연산자, SQL 연산자 > AND > OR



# **2. 비교 연산자**

| **연산자** | **의미**         |
| ---------- | ---------------- |
| **=**      | 같다             |
| **>**      | 보다 크다        |
| **>=**     | 보다 크거나 같다 |
| **<**      | 보다 작다        |
| **<=**     | 보다 작거나 같다 |

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE TEAM_ID = 'K02';*

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE HEIGHT >= 170;*



# **3. SQL 연산자**

| **연산자**          | **의미**                                     |
| ------------------- | -------------------------------------------- |
| **BETWEEN a AND b** | a와 b 값 사이에 있는 데이터(a와 b의 값 포함) |
| **IN (LIST)**       | 리스트에 있는 값 중 하나라도 일치하는 데이터 |
| **LIKE '문자열'**   | 비교 문자열과 형태가 일치하는 데이터         |
| **IS NULL**         | 데이터가 NULL인 경우                         |

**가. BETWEEN 연산자**

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE HEIGHT BETWEEN 170 AND 180;*

**나. IN 연산자**

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE TEAM_ID IN ('K02', 'K07');*

​    Ex) *SELECT ENAME, JOB, DEPTNO*

​          *FROM EMP*

​          *WHERE (JOB, DEPTNO) IN (('NAMAGER', 20), ('CLERK', 30));*

​    Ex) *SELECT ENAME, JOB, DEPTNO*

​          *FROM EMP*

​          *WHERE JOB IN ('MANAGER', 'CLERK') AND DEPTNO IN (20, 30);*

**다. LIKE 연산자**

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE POSITION LIKE 'MF';*

​    \- 와일드카드 : 한개 혹은 0개 이상의 문자를 대신 사용하기 위한 특수문자, %(0개 이상의 어떤 문자를 의미)과 _(1개인 단일 문자를 의미), 두 가지가 있다

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE PLAYER_NAME LIKE '장%';*

**라. IS NULL 연산자**

​    \- NULL은 값이 존재하지 않는 것, 확정되지 않은 값을 표현하는 것이기 때문에 어떤 값보다 크거나 작은지 비교 자체가 불가능한 값이다

​    \- 따라서 NULL 값과의 수치 연산은 NULL 값을 리턴, 비교 연산은 FALSE를 리턴한다

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE POSITION = NULL; (또는 WHERE POSITION IS NULL;)*



# **4. 논리 연산자**

| **연산자** | **의미**                                                     |
| ---------- | ------------------------------------------------------------ |
| **AND**    | 앞에 있는 조건과 뒤에 오는 조건이 참이면 결과도 참즉, 앞 조건과 뒤 조건 모두 만족해야 한다 |
| **OR**     | 앞의 조건이 참이거나 뒤에 오는 조건이 참이면 결과도 참즉, 앞뒤 조건 중 하나만 만족하면 된다 |
| **NOT**    | 뒤에 오는 조건에 반대되는 결과를 반환한다참이면 거짓, 거짓이면 잠 |

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE TEAM_ID = 'K02' AND HEIGHT >= 170;*

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE TEAM_ID IN ('K02', 'K07') AND POSITION = 'MF';*

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE* *TEAM**_**ID* *IN* *('K02','K07') AND POSITION =* *'MF'* *AND* *HEIGHT* *BETWEEN* *170* *AND* *180;*



# **5. 부정 연산자**

| **종류**                | **연산자**                | **의미**                                             |
| ----------------------- | ------------------------- | ---------------------------------------------------- |
| **부정 논리****연산자** | **!=**                    | 같지 않다                                            |
| **^=**                  | 같지 않다                 |                                                      |
| **<>**                  | 같지 않다                 |                                                      |
| **NOT 칼럼명 =**        | ~와 같지 않다             |                                                      |
| **NOT 칼럼명 >**        | ~보다 크지 않다           |                                                      |
| **부정 SQL****연산자**  | **NOT BETWEEN a AND b**   | a와 b의 값 사이에 있지 않다(a, b 값을 포함하지 않음) |
| **NOT IN (LIST)**       | LIST 값과 일치하지 않는다 |                                                      |
| **IS NOT NULL**         | NULL 값을 갖지 않는다     |                                                      |

​    Ex) *SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키*

​          *FROM PLAYER*

​          *WHERE NOT POSITION = 'MF' AND NOT HEIGHT BETWEEN 175 AND 185;*

​    Ex) *SELECT PLAYER_NAME 선수이름, NATION 국적*

​          *FROM PLAYER*

​          *WHERE NATION IS NOT NULL;*



# **6. ROWNUM, TOP 사용**

**가. ROWNUM**

​    \- 테이블이나 집합에서 원하는 만큼의 행만 가져오고 싶을 때 WHERE 절에서 행의 개수를 제한한다

​    \- 1건의 행만 가져올 때 : *SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM = 1;*

​    \- 두 건 이상의 행을 가져올 때 : SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM <= n;

**나. TOP**

​    \- 결과 집합으로 출력되는 행의 수를 제한

​    \- 구문 : *SELECT TOP (개수) [PERCENT옵션] [WITH TIES 옵션];*

​    \- PERCENT 옵션 : 쿼리 결과 집합에서 처음부터 (개수)%의 행만 반환

​    \- WITH TIES 옵션 : ORDER BY 절이 지정된 경우에만 사용 가능, TOP N(PERCENT)의 마지막 행과 같은 값이 있는 경우에는 그 행까지 추가해서 출력

​    \- 1건의 행만 가져올 때 : *SELECT TOP(1) PLAYER_NAME FROM PLAYER;*

​    \- 두 건 이상의 N행을 가져올 때 : *SELECT TOP(N) PLAYER_NAME FROM PLAYER*