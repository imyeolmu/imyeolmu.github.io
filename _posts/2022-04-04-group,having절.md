---

categories: SQL

---

### GROUP BY
- ~별
- GROUP BY 절에 명시되지 않는 열을 SELECT절에 사용했을 경우 오류가 발생한다
- 80번 부서의 직급별 총급여와 평균급여를 구하시오
```
select departmnet_id,job_id,sum(salary),avg(salary) from employees where department_id = 80 
group by department_id,job_id;
```

```
DEPARTMENT_ID	JOB_ID	SUM(SALARY)	AVG(SALARY)
80	SA_REP	243500	8396.551724137931034482758620689655172414
80	SA_MAN	61000	12200
```
- 현재 부서별 사원수 조회하기
```
  select department_id,count(*) from employees
group by department_id;
```
```
DEPARTMENT_ID	COUNT(*)
100	6
30	6
	1
90	3
20	2
70	1
110	2
50	45
80	34
40	1
60	5
10	1
```
- null 값인 부서는 제외하고 부서별 사원수 조회하기
```
select department_id, count(*)
from employees
where department_id is not null
group by department_id;
```
```
DEPARTMENT_ID	COUNT(*)
10	1
20	2
30	6
40	1
50	45
60	5
70	1
80	34
90	3
100	6
110	2
```
&nbsp;

- 오류 발생: ORA-00979: GROUP BY 표현식이 아닙니다.
- 컬럼의 차이로 인한 오류 발생 (GROUP BY는 조회하는 함수를 모두 포함해야한다 )
```
select employee_id,department_id,job_id,avg(salary)
from employees
group by department_id,job_id
```


&nbsp; 

### HAVING 절
- GROUP BY절에서 조건을 줄 때 사용한다
- 조건에 맞는 그룹을 선택할때 사용한다
- where절은 from절에 정의된 테이블의 개별행에 먼저적용된다.(집계되지 않은 자료에 대한 조건)
- where절의 조건에 맞는 행이 GROUP BY절의 대상이된다
- 그다음 HAVING 조건절이 적용된다(집계된 자료에 대한 조건)
&nbsp;

- null 값인 부서는 제외하고 부서별 사원수가 10명 이상인 부서만 조회하기
```
select department_id, count(*)
from employees
where department_id is not null
group by department_id
having count(*) >= 10;
```

&nbsp;

-문제1) 각 부서별 평균급여, 최대급여, 최소급여, 사원수를 출력하세요
평균급여는 소수점을 제외하세요.(집계함수는 null값을 제외하고 통계를 낸다)

```
SELECT DEPARTMENT_ID,
       TRUNC(AVG(SALARY)) AS "평균급여",
       MAX(SALARY) AS "최대급여",
       MIN(SALARY) AS "최소급여",
       COUNT(*) AS "사원수"
FROM EMPLOYEES
GROUP BY DEPARTMENT_ID;
```
&nbsp;

문제 2> 같은 직책(job_id)에 종사하는 사원이 3명 이상인 직책과 인원수를 출력하세요.
```
SELECT JOB_ID,
       COUNT(*)
FROM EMPLOYEES
GROUP BY JOB_ID
HAVING COUNT(*) >= 3; 
```

&nbsp;

문제 3> 사원들의 입사연도를 기준으로 부서별로 몇명이 입사했는지 출력하세요. 입사연도, 부서번호, 사원수
```
SELECT TO_CHAR(HIRE_DATE, 'YYYY') AS 입사연도,
       DEPARTMENT_ID 부서번호,
       COUNT(*) AS 사원수
FROM EMPLOYEES
GROUP BY TO_CHAR(HIRE_DATE, 'YYYY'), DEPARTMENT_ID
ORDER BY TO_CHAR(HIRE_DATE, 'YYYY'), DEPARTMENT_ID;
```