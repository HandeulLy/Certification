# 2-1-8 ORDER BY 절





# 1. ORDER BY 정렬

​    \- SQL문으로 조회된 데이터들을 다양한 목적에 맞게 특정 칼럼(칼럼 대신에 SELECT 절에서 사용한 ALIAS 명이나 칼럼 순서를 나타내는 정수도 사용 가능)을 기준으로 정렬 및 출력하는데 사용한다

​    \- 별도로 정렬 방식을 지정하지 않으면 기본적으로 오름차순이 적용된다

​    \- Oracle에서는 NULL 값을 가장 큰 값으로 취급하고, SQL Server에서는 반대로 정렬한다

​    \- 구문 : *SELECT 칼럼명 [ALIAS명] FROM 테이블명 [WHERE 조건식] [GROUP BY 칼럼] [HAVING 조건식] [ORDER BY 칼럼 옵션]*

​    *Ex) SELECT PLAYER_NAME 선수명, POSITION 포지션, BACK_NO 백넘버 FROM PLAYER ORDER BY PLAYER_NAME DESC;*

​    *Ex) SELECT PLAYER_NAME 선수명, POSITION 포지션, BACK_NO 백넘버 FROM PLAYER ORDER BY 포지션 DESC;*

​    *Ex) SELECT PLAYER_NAME 선수명, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키 FROM PLAYER WHERE HEIGHT IS NOT NULL ORDER BY HEIGHT DESC, BACK_NO;*

​    *Ex) SELECT PLAYER_NAME 선수명, POSITION 포지션, BACK_NO 백넘버 FROM PLAYER WHERE BACK_NO IS NOT NULL ORDER BY 3 DESC, 2, 1;*





# 2. SELECT 문장 실행 순서

​    \- 구문 : *SELECT 칼럼명 [ALIAS명]* *FROM 테이블명* *[WHERE 조건식]* *[GROUP BY 칼럼]* *[HAVING 조건식]* *[ORDER BY 칼럼 옵션]*

​    *- 순서 : FROM > WHERE > GROUP BY > HAVING > SELECT > ORDER BY*

​    \- 설명 : 발췌 대상 테이블을 참조한다(FROM) > 발췌 대상 데이터가 아닌 것은 제거한다(WHERE) > 행들을 소그룹화 한다(GROUP BY) > 그룹화 된 값의 조건에 맞는 것만 출력한다(HAVING) > 데이터 값을 출력 및 계산한다(SELECT) > 데이터를 정렬한다(ORDER BY)



# 3. TOP N 쿼리

**가. ROWNUM**

​    \- Oracle에서 순위가 높은 N개의 로우를 추출하기 위해 ORDER BY, WHERE 절에 사용한다

​    \- Oracle의 경우 정렬이 완료된 후 데이터의 일부가 출력되는 것이 아니라, 데이터의 일부가 먼저 추출된 후 데이터에 대한 정렬 작업을 수행하기 때문에 주의해야 함

​    Ex) *SELECT ENAME, SAL FROM EMP WHERE ROWNUM < 4 ORDER BY SAL DESC;*

​    Ex) *SELECT ENAME, SAL FROM (SELECT ENAME, SAL FROM EMP ORDER BY SAL DESC) WHERE ROWNUM < 4;*

**나. TOP()**

​    \- SQL Server에서 TOP 조건을 사용하면 별도 처리 없이 관련 ORDER BY 절의 데이터 정렬 후 일부 데이터만 출력할 수 있다

​    \- 구문 : TOP (칼럼) [PERCENT] [WITH TIES]

​    Ex) *SELECT TOP(2) ENAME, SAL FROM EMP ORDER BY SAL DESC;*

​    Ex) *SELECT TOP(2) WITH TIES ENAME, SAL FROM EMP ORDER BY SAL DESC;*