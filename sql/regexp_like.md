### REGEXP_LIKE 

LIKE와 IN을 합한 것과 같은 함수. regexp_like는 단순히 문자열이 포함되어 있는지 비교하는 LIKE를 넘어서, 정규식을 비교하여 일치할 경우 추출해주는 함수이다.



#### 필요한 상황 예시

```mysql
select *
from employees
where phone_number like '011%';
-- 폰 넘버가 011로 시작하는 행을 추출해라.
```

*만약 011로 시작하는거 외에도 555로 시작하는 행들도 뽑고 싶다면?*

```mysql
select *
from employees
where phone_number like '011%'
or phone_number like '555%';
```

*근데 조건이 이 두 개뿐만 아니라 011, 551, 552, 553 중에 하나로 시작하는 애들을 뽑고 싶다면?*

**Like와 in은 함께 사용할 수 없다.** 대신 regexp_like 함수를 이용해 구현한다.

```mysql
select *
from employees
where regexp_like (phone_number, '^551|^552|^553|^011');
-- 자칫하면 길어질 수 있는 다중 LIKE 상황을 간단하게 줄여주는 예시이다.
-- 그 외에 로그인 아이디가 이메일 형식인지 단순 아이디인지 포맷 일치를 확인하고 싶다던가 이러때도 사용할 수 있는게
-- regexp_like 이다.
```



#### REGEXP_LIKE 문법 SYNTAX

- 단일 패턴 검색 

  *REGEXP_LIKE(대상 문자열(ex칼럼명) , 정규식 패턴, 매칭 파라미터(옵션) )*  

- 매칭 파라미터 생략 가능 - 그럼 디폴트로 적용됨.

   *REGEXP_LIKE(대상 문자열(ex컬럼명), 패턴 )* 

- 다중 패턴 검색

  *REGEXP_LIKE(대상 문자열(ex컬럼명) , [패턴1] | [패턴2] | [패턴3], 매칭 파라미터(옵션) )* 

리턴 값 : 총 조건에 일치하는 행의 개수 리턴.



REGEXP_LIKE 매칭 파라미터 

​	i : 대소문자 구별하지 않고 매칭

   c : 대소문자 구별해서 매칭

#### EXAMPLES 예시들

​	특정 문자열이 들어있는 데이터를 추출할 때

```mysql
select * from employees
where regexp_like(first_name, 'ne');
-- employees 테이블의 first_name 컬럼에서 'ne'라는 문자열을 포함하고 있는 데이터들을 출력해라!
```

​	특정 문자열이 들어 있는 데이터를 추출하는 데 대소문자를 구분하지 않고 검색하고 싶을 때

```mysql
select * from employees
where regexp_like(first_name, 'ne', 'i');
-- employees 테이블의 first_name 칼럼에서 대소문자 관계없이 'ne'라는 문자열을 포함하고 있는 데이터를 출력해라.
```

​	 두 개의 문자열 중 하나를 포함하고 있는 행 추출하기

```mysql
select * from employees
where regexp_like(first_name, 'ett|ana');
-- employees 테이블의 first_name 컬럼값중 'ett'라는 문자열이 들어가 있거나 'ana'라는 문자열이 들어가 있는 행 검색하기.
```

​	정규식 패턴 안에 파이프를 사용해서 여러 조건 검색하기

``` mysql
select * from employees
where regexp_like(first_name, 'an(c|i|e)');
-- employees 테이블의 first_name 컬럼에서 anc 또는 ani 또는 ane 가 포함된 결과값들을 찾아서 보여줘
```

​	대소문자 관계 없이 특정 문자열로 시작하거나 끝나는 결과만 뽑기

```mysql
select * from employees
where regexp_like(first_name, '^na | na$', 'i');
```

'^'는 시작을 의미하고 '$'은 끝을 의미한다. 

Employees 테이블의 first_name 컬럼에서 대소문자 관계업싱 na로 시작하거나 끝나는 행들만 찾는다.

#### REGEXP_LIKE 이외에 더 알아두면 좋을 정규식 함수들

- REGEXP_REPLACE : 정규식 패턴을 검색하여 대체 문자열로 변경한다.

- REGEXP_INSTR : 정규식 패턴에 대해 문자열을 검색하고 일치가 발견된 위치를 반환한다.

- REGEXP_SUBSTR: 지정된 문자열 내에서 정규식 패턴을 검색하고 일치하는 부분 문자열을 추출한다.

- REGEXP_COUNT : 입력 문자열에서 패턴 일치가 발견되는 횟수를 반환한다.

  





