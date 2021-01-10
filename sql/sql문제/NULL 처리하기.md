### NULL 처리하기



https://programmers.co.kr/learn/courses/30/lessons/59410



NULL 처리 함수로

- NVL(exp1, exp2)

- CASE WHEN 컬럼명 IS NOT NULL THEN exp1 ELSE exp2(=NULL시 값) END

- COALESCE(컬럼명, NULL시 값)

- IFNULL(컬럼명, NULL시 값) 

  등등이 있는데,

 MySQL 에서는 NVL을 지원하지 않으므로  나는 COALESCE () 함수를 이용해서 풀었다.

문제 조건에서 'No Name'이 아닌 'No name'임을 주의!

``` mysql
SELECT ANIMAL_TYPE, COALESCE(NAME, 'No name'), SEX_UPON_INTAKE
FROM ANIMAL_INS;
```



