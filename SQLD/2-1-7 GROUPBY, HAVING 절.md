<<<<<<< HEAD
# 2-1-7 GROUPBY, HAVING 절



# 1. 집계 함수(Aggregate Function)

​    \- 여러 행들의 그룹이 모여 그룹당 단 하나의 결과를 반환하는 다중행 함수

​    \- 집계 함수의 특성 : 여러 행들의 그룹이 모여 그룹 당 하나의 결과를 돌려준다, GROUP BY 절은 행들을 소그룹화 한다, SELECT & HAVING & ORDER BY 절에 사용할 수 있다

​    \- 구문 : *집계함수명([옵션] 칼럼)*

​    \- 옵션에는 ALL(DEFAULT 옵션, 생략 가능)과 DISTINCT(같은 값을 하나의 데이터로 간주할 때 사용, 중복 값을 가지면 한 번만 출력함)가 있다

| **함수**                | **사용 목적**                                     |
| ----------------------- | ------------------------------------------------- |
| **COUNT(\*)**           | NULL 값을 포함한 전체 행의 수 출력                |
| **COUNT(표현식)**       | 표현식의 값이 NULL 값인 것을 제외한 행의 수 출력  |
| **SUM(옵션 표현식)**    | 표현식의 NULL 값을 제외한 합계 출력               |
| **AVG(옵션 표현식)**    | 표현식의 NULL 값을 제외한 평균 출력               |
| **MAX(옵션 표현식)**    | 표현식의 최대값 출력(문자, 날짜 데이터 타입 가능) |
| **MIN(옵션 표현식)**    | 표현식의 최소값 출력(문자, 날짜 데이터 타입 가능) |
| **STDDEV(옵션 표현식)** | 표현식의 표준 편차 출력                           |
| **VARIAN(옵션 표현식)** | 표현식의 분산 출력                                |
| **기타 통계 함수**      | 각 SQL마다 다양한 통계식을 제공한다               |

​    EX) *SELECT COUNT(\*) "전체 행수", COUNT(HEIGHT) "키 건수", MAX(HEIGHT) 최대키, MIN(HEIGHT) 최소키, ROUND(AVG(HEIGHT, 2) 평균키 FROM PLAYER;*



# 2. GROUP BY 절

​    \- SQL문에서 FROM 절과 WHERE 절 뒤에 위치하며, 데이터들을 작은 그룹으로 분류하여 소그룹에 대한 항목별 통계 정보를 얻을 때 추자하여 사용한다

​    \- 구문 : *SELECT [DISTINCT] 칼럼명 [ALIAS명] FROM 테이블명 [WHERE 조건식] [GROUP BY 칼럼] [HAVING 그룹조건식]*

​    \- 특성 : GROUP BY 절로 소그룹 기준을 정한 후 SELECT 절에 집계 함수(통계 정보는 NULL 값을 가진 행은 제외하고 수행)를 사용한다, GROUP BY 절에서는 ALIAS 명을 사용할 수 없다, 집계함수는 WHERE 절에 올 수 없다

​    EX) *SELECT POSITION 포지션, COUNT(\*) 인원수, COUNT(HEIGHT) 키대상, MAX(HEIGHT) 최대키, MIN(HEIGHT) 최소키, ROUND(AVG(HEIGHT), 2) 평균키 FROM PLAYER GROUP BY POSITION;*



# 3. HAVING 절

​    \- WHERE 절은 FROM 절에 정의된 집합(테이블)의 개별 행에 WHERE 절의 조건절이 먼저 적용되고, WHERE 절의 조건에 맞는 행이 GROUP BY 절의 대상이 된다

​    \- 그 후 결과 집합의 행에 HAVING 조건절이 적용된다

​    \- 결과적으로 HAVING 절의 조건을 만족하는 내용만 출력된다

​    \- 즉, HAVING 절은 WHERE 절과 비슷하지만 그룹을 나타내는 결과 집합의 행에 조건이 적용되는 차이가 있다

​    EX) *SELECT POSITION 포지션, AVG(HEIGHT) 평균키 FROM PLAYER HAVING AVG(HEIGHT) >= 180 GROUP BY POSITION;*

**

​    \- GROUP BY 소그룹의 데이터 중 일부만 필요한 경우, WHERE 절에서 조건을 먼저 적용해서 필요한 데이터만 추출한 후 GROUP BY 연산 수행하는 방법과. GROUP BY 연산 후 HAVING 절에서 필요한 데이터만 필터링하는 방법이 있다

​    \- 가능하면 WHERE 조건절에서 GROUP BY의 계산 대상을 줄이는 것이 효율적이다

​    EX) *SELECT POSITION 포지션, ROUND(AVG(HEIGHT), 2) 평균키 FROM PLAYER BY POSITION HAVING MAX(HEIGHT) >= 190;*



# 4. CASE 표현을 활용한 월별 데이터 집계

​    EX) *(Oracle) SELECT ENAME, DEPTNO, EXTRACT(MONTH FROM HIREDATE) 입사월, SAL FROM EMP;*

​    EX) *(SQL Server) SELECT ENAME, DEPTNO, DATEPART(MONTH, HIREDATE) 입사월, SAL FROM EMP;*

​    EX) *(SQL Server) SELECT ENAME, DEPTNO, MONTH(HIREDATE) 입사월, SAL FROM EMP;*



# 5. 집계 함수와 NULL

​    \- 다중행 함수는 입력 값으로 전체 건수가 NULL 값인 경우만 함수의 결과가 NULL이 나오고, 전체 건수 중 일부만 NULL인 경우는 NULL인 행을 대상에서 제외하고 연산을 수행한다

=======
# 2-1-7 GROUPBY, HAVING 절



# 1. 집계 함수(Aggregate Function)

​    \- 여러 행들의 그룹이 모여 그룹당 단 하나의 결과를 반환하는 다중행 함수

​    \- 집계 함수의 특성 : 여러 행들의 그룹이 모여 그룹 당 하나의 결과를 돌려준다, GROUP BY 절은 행들을 소그룹화 한다, SELECT & HAVING & ORDER BY 절에 사용할 수 있다

​    \- 구문 : *집계함수명([옵션] 칼럼)*

​    \- 옵션에는 ALL(DEFAULT 옵션, 생략 가능)과 DISTINCT(같은 값을 하나의 데이터로 간주할 때 사용, 중복 값을 가지면 한 번만 출력함)가 있다

| **함수**                | **사용 목적**                                     |
| ----------------------- | ------------------------------------------------- |
| **COUNT(\*)**           | NULL 값을 포함한 전체 행의 수 출력                |
| **COUNT(표현식)**       | 표현식의 값이 NULL 값인 것을 제외한 행의 수 출력  |
| **SUM(옵션 표현식)**    | 표현식의 NULL 값을 제외한 합계 출력               |
| **AVG(옵션 표현식)**    | 표현식의 NULL 값을 제외한 평균 출력               |
| **MAX(옵션 표현식)**    | 표현식의 최대값 출력(문자, 날짜 데이터 타입 가능) |
| **MIN(옵션 표현식)**    | 표현식의 최소값 출력(문자, 날짜 데이터 타입 가능) |
| **STDDEV(옵션 표현식)** | 표현식의 표준 편차 출력                           |
| **VARIAN(옵션 표현식)** | 표현식의 분산 출력                                |
| **기타 통계 함수**      | 각 SQL마다 다양한 통계식을 제공한다               |

​    EX) *SELECT COUNT(\*) "전체 행수", COUNT(HEIGHT) "키 건수", MAX(HEIGHT) 최대키, MIN(HEIGHT) 최소키, ROUND(AVG(HEIGHT, 2) 평균키 FROM PLAYER;*



# 2. GROUP BY 절

​    \- SQL문에서 FROM 절과 WHERE 절 뒤에 위치하며, 데이터들을 작은 그룹으로 분류하여 소그룹에 대한 항목별 통계 정보를 얻을 때 추자하여 사용한다

​    \- 구문 : *SELECT [DISTINCT] 칼럼명 [ALIAS명] FROM 테이블명 [WHERE 조건식] [GROUP BY 칼럼] [HAVING 그룹조건식]*

​    \- 특성 : GROUP BY 절로 소그룹 기준을 정한 후 SELECT 절에 집계 함수(통계 정보는 NULL 값을 가진 행은 제외하고 수행)를 사용한다, GROUP BY 절에서는 ALIAS 명을 사용할 수 없다, 집계함수는 WHERE 절에 올 수 없다

​    EX) *SELECT POSITION 포지션, COUNT(\*) 인원수, COUNT(HEIGHT) 키대상, MAX(HEIGHT) 최대키, MIN(HEIGHT) 최소키, ROUND(AVG(HEIGHT), 2) 평균키 FROM PLAYER GROUP BY POSITION;*



# 3. HAVING 절

​    \- WHERE 절은 FROM 절에 정의된 집합(테이블)의 개별 행에 WHERE 절의 조건절이 먼저 적용되고, WHERE 절의 조건에 맞는 행이 GROUP BY 절의 대상이 된다

​    \- 그 후 결과 집합의 행에 HAVING 조건절이 적용된다

​    \- 결과적으로 HAVING 절의 조건을 만족하는 내용만 출력된다

​    \- 즉, HAVING 절은 WHERE 절과 비슷하지만 그룹을 나타내는 결과 집합의 행에 조건이 적용되는 차이가 있다

​    EX) *SELECT POSITION 포지션, AVG(HEIGHT) 평균키 FROM PLAYER HAVING AVG(HEIGHT) >= 180 GROUP BY POSITION;*

**

​    \- GROUP BY 소그룹의 데이터 중 일부만 필요한 경우, WHERE 절에서 조건을 먼저 적용해서 필요한 데이터만 추출한 후 GROUP BY 연산 수행하는 방법과. GROUP BY 연산 후 HAVING 절에서 필요한 데이터만 필터링하는 방법이 있다

​    \- 가능하면 WHERE 조건절에서 GROUP BY의 계산 대상을 줄이는 것이 효율적이다

​    EX) *SELECT POSITION 포지션, ROUND(AVG(HEIGHT), 2) 평균키 FROM PLAYER BY POSITION HAVING MAX(HEIGHT) >= 190;*



# 4. CASE 표현을 활용한 월별 데이터 집계

​    EX) *(Oracle) SELECT ENAME, DEPTNO, EXTRACT(MONTH FROM HIREDATE) 입사월, SAL FROM EMP;*

​    EX) *(SQL Server) SELECT ENAME, DEPTNO, DATEPART(MONTH, HIREDATE) 입사월, SAL FROM EMP;*

​    EX) *(SQL Server) SELECT ENAME, DEPTNO, MONTH(HIREDATE) 입사월, SAL FROM EMP;*



# 5. 집계 함수와 NULL

​    \- 다중행 함수는 입력 값으로 전체 건수가 NULL 값인 경우만 함수의 결과가 NULL이 나오고, 전체 건수 중 일부만 NULL인 경우는 NULL인 행을 대상에서 제외하고 연산을 수행한다

>>>>>>> bac486b0f38872d8328c1454556236eb8c1145c0
​    \- CASE 표현 사용 시 ELSE 절을 생략하게 되면 DEFAULT 값이 NULL이다