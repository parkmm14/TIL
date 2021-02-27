### JOIN



#### 1. INNER JOIN

INNER JOIN( = EQUI JOIN) 

조인 대상 테이블의 컬럼값이 서로 모두 동일한 경우에 사용한다. 

동일한 값이 있는 행만을 출력한다는 특징이 있다. 다른 값을 가지는 행은 출력되지 않는다.

내부조인은 WHERE절에서만 명시하는 조건을 FROM절에 정의하겠다는 표시이므로 USING 조건절이나 ON 조건절을 

필수적으로 사용해야 한다.

```` mysql
SELECT EMP, DEPTNO, EMPNO, ENAME, DNAME (1)
FROM EMP (INNER) JOIN DEPT							(2)
ON EMP.DEPTNO = DEPT.DEPTNO							(3)

(1) 두 테이블의 값이 겹치지 않을 경우, 테이블1.컬럼명 으로 작성하지 않아도 된다.
(2) INNER JOIN은 JOIN의 default 값이므로 inner는 생략이 가능하다.
(3) SELECT와 달리, 컬럼명이 다르더라도 명확하게 테이블 명과 같은 접두사를 사용해야 한다.
````

---



#### 2. 3개 이상의 INNER JOIN

T1, T2를 조인한 결과를 T3와 조인한다.

*예제) 홍팀이 3점 이상 차이로 승리한 경기의 경기장 이름, 경기 일정, 홍팀 이름과 원정팀 이름 정보를 출력한다.*

``` mysql
SELECT ST.STADIUM_NAME, SC.STADIUM_ID, SCHE_DATE, HT.TEAM_NAME, AT.TEAM_NAME, HOME_SCORE, AWAY_SCORE
FROM SCHEDULE SC JOIN STADIUM ST
ON SC.STADIUM_ID = ST.STADIUM.ID
	JOIN TEAM HT
ON SC.HOMETEAM_ID = HT.TEAM_ID
	JOIN TEAM AT
	ON SC.AWAYTEAM_ID = AT.TEAM_ID
WHERE HOME_SCORE >= AWAY_SCORE +3;

TEAM 테이블을 구분한 HT, AT로 구분한 것은 팀 이름을 구분하기 위함이다.
```

---

#### 3. OUTER JOIN

T1과 T2의 **LEFT OUTER JOIN**의 결과 :

T1과 T2를 조인하되, T2에 Join 데이터가 있는 경우에는 T2 테이블의 데이터를 함께 출력하고 

데이터가 없는 경우에는 NULL 값으로 출력한다.

왼쪽 테이블(T1)의 데이터를 온전히 출력하고 싶을 때 **LEFT OUTER JOIN**

오른쪽 테이블(T2)의 데이터를 온전하게 출력하고 싶을 때 **RIGHT OUTER JOIN**

*예제) STADIUM에 등록된 운동장 중에는 홈팀이 없는 경기장도 있다. STADIUM과 TEAM을 조인하되 홈팀이 없는 경기장의 정보도 함께 출력하도록 한다.*

``` mysql
SELECT STADIUM_NAME, STADIUM.STADIUM_ID, SEAT_COUNT, HOMETEAM_ID, TEAM_NAME
FROM STADIUM LEFT (OUTER) JOIN TEAM				(1)
ON STADIUM.HOMETEAM_ID = TEAM.TEAM_ID
ORDER BY HOMETEAM_ID;

(1) LEFT, RIGHT JOIN이 가능한 경우에는 OUTER JOIN 밖에 없으므로 OUTER는 생략이 가능하다.
LEFT JOIN이므로 실행결과에는 STADIUM 행(레코드) 중에서 TEAM과 JOIN하지 못한 행이 존재할 수 있음을 알 수 있다.
```

**FULL OUTER JOIN**

LEFT OUTER JOIN과 RIGHT OUTER JOIN을 합친 FULL OUTER JOIN이 있다.

테이블1과 테이블2 각각을 기준으로 모든 데이터를 읽어 JOIN한 결과를 생성한 것이다.

```mysql
SELECT *
FROM DEPT FULL OUTER JOIN DEPT_TEMP
ON DEPT.DEPTNO = DEPT_TEMP.DEPTNO;
```

위 코드는 아래의 코드와 정확히 일치한다.

```mysql
SELECT *
FROM DEPT LEFT JOIN DEPT_TEMP
ON DEPT.DEPTNO = DEPT_TEMP.DEPTNO
UNION			(1)
SELECT *
FROM DEPT RIGHT JOIN DEPT_TEMP
ON DEPT.DEPTNO = DEMP_TEMP.DEPTNO;
```

(1) **UNION 연산은 두 테이블의 레코드를 합집합하는 연산**이다.



UNION 연산이 중요한 점은 두 테이블에 공통된 항이 존재할 경우 이를 생략한다는 점이다.

이는 장점이기도 하지만, 동시에 연산량이 늘어난다는 의미이기도 하므로 단점이 될 수도 있다. **만약 공통된 행이 존재하지 않을 것을 미리 알고 있다면 UNION 연산 대신 UNION ALL 연산을 사용하는 것이 바람직하다.**



