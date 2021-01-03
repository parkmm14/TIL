정렬을 할 때 단순히 오름차순이나 내림차순이 아닌 특정 조건을 기준으로 정렬을 해야 하는 경우가 있다. 

이런 경우에 ORDER BY 부분에서 DECODE나 CASE를 이용하여 표현할 수 있다.



1. CASE 사용방법

``` sql
SELECT *
FROM 테이블명
ORDER BY (
			CASE 컬럼명
					WHEN 조건A THEN 1
					WHEN 조건B THEN
					ELSE 3
					END
)
```

THEN과 ELSE뒤에 숫자는 출력 순서를 나타낸다.



2. DECODE 사용법

``` sql
SELECT *
FROM 테이블명
ORDER BY DECODE(컬럼명, 조건A, 1, 조건B, 2, 3)
```

위에 CASE로 정렬한 것과 같은 내용이며, 역시 숫자는 출력 순서를 나타낸다.

