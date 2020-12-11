



#### 문자열 포맷

> ##### `	print("a"+"b")` 나 `print("a", "b")` 로 나타낼 수 있음.

- ##### 방법 1 : %

``` python
print("나는 %d살 입니다." % 20) #는 정수
print("나는 %s를 좋아해요." % "파이썬")
print("Apple은 %c로 시작해요." % "A")
print("나는 %s색과 %s색을 좋아해요." %("파란", "빨간"))
```

	- ##### 방법 2 : {}

``` python
print("나는 {}살입니다.".format(20))
print("나는 {}색과 {}색을 좋아해요.".format("파란", "빨간"))
print("나는 {0}색과 {1}색을 좋아해요.".format("파란", "빨간"))
print("나는 {1}색과 {0}색을 좋아해요." format("파란", "빨간")) #{}쓸땐 연속으로 입력한 값이 나오게 되고, 숫자를 넣으면 순번에 맞게 출력
```

- ##### 방법 3 

```python
print("나는 {age}살이며, {color}색을 좋아해요".format(age = 20, color="빨간"))
print("나는 {age}살이며, {color}색을 좋아해요" .format(color="빨간", age= 20))
```

- ##### 방법 4 (v3.6 이상 ~)

``` python
age = 20ㅔ
color = "빨간"
print("나는 {age} 살이며, {color}색을 좋아해요.")
```



#### 탈출 문자 

- ##### \n : 줄바꿈

```  python
print("백문이 불여일견 \n백견이 불여일타")
```

- ##### `\" `  `\'` : 문장 내에서 따옴표

``` python
# 저는 "박민재"입니다.
print("저는 \"박민재\" 입니다.")
print("저는 \'박민재\' 입니다.")
```

- ##### `\\` : 문장 내에서 \

- ##### `\r` : 커서를 맨 앞으로 이동

``` python
print("Red Apple\rPine") # PineApple 으로 출력.
```

- ##### `\b` : 백스페이스 (한 글자 삭제)

```python
print("Redd\bApple") # RedApple 출력
```

- ##### `\t` : 탭

``` python
print("Red\tApple") # Red	Apple
```

#####  

##### Quiz) 사이트별로 비밀번호를 만들어 주는 프로그램을 작성하시오.

``` python
# 예) http://naver.com
# 규칙1 : http:// 부분은 제외 => naver.com
# 규칙2 : 처음 만나는 점(.) 이후 부분은 제외 => naver
# 규칙3 : 남은 글자 중 처음 세자리 + 글자 갯수 + 글자 내 'e' 갯수 + "!"로 구성
#												(nav)			 	(5)						(1)		 (!)
# 예) 생성된 비밀번호 : nav51!

domain = "http://naver.com"
pw = domain[7:]
index = pw.index(".")
pw = pw[0:index]
letter = pw[:3]
cnt = len(pw)
cnt_e = pw.count("e")

print(letter+str(cnt)+str(cnt_e)+"!")

my_str = domain.replace("http://", "")
# print(my_str)
my_str = my_str[:my_str.index(".")]
print(my_str)
password = my_str[:3] + str(len(my_str)) + str(my_str.count("e")) + "!"
print("{0} 의 사이트의 비밀번호는 {1} 입니다" .format(domain, password))
```



#### 리스트 []

``` python
# 지하철 칸별로 10명, 20명, 30명
# subway1 = 10
# subway2 = 20
# subway3 = 30

subway = [10, 20, 30]
print(subway)

subway = ["유재석", "조세호", "박명수"]
print(subway)

# 조세호씨가 몇 번째 칸에 타고 있는가?
print(subway.index("조세호"))  # 1 출력

# 하하씨가 다음 정류장에서 다음 칸에 탐
subway.append("하하")
print(subway)      						#['유재석', '조세호', '박명수', '하하'] 출력 

# 정형돈씨를 유재석 / 조세호 사이에 태워봄
subway.insert(1, "정형돈")
print(subway)  		 						#[ '유재석', '정형돈', '조세호', '박명수', '하하'] 출력

# 지하철에 있는 사람을 한 명씩 뒤에서 꺼냄
print(subway.pop())  # 하하 출력

# 같은 이름의 사람이 몇 명 있는지 확인
subway.append("유재석")
print(subway.count("유재석"))   # 2 출력

# 정렬도 가능
num_list = [5, 2, 4, 3, 1]
num_list.sort()
print(num_list) # [1, 2, 3, 4, 5] 출력

# 순서 뒤집기 가능
num_list.reverse()
print(num_list) 	# [5, 4, 3, 2, 1] 출력

# 모두 지우기
# num_list.clear()
# print(num_list)

# 다양한 자료형 함께 사용
num_list = [5,2,4,3,1]
mix_list = ["조세호", 20, True]

# 리스트 확장 
num_list.extend(mix_list)
print(num_list) #[5, 2, 4, 3, 1, '조세호', 20, True]

```



#### 사전

> 일반적으로 단어를 찾으면 그 단어와 단어에 대한 정의가 나오는 것처럼, key 와 value 형태로 나온다.
>
> key는 중복 허용되지 않음.

``` python
cabinet = {3:"유재석", 100: "김태호"}
print(cabinet[3])    # 유재석 
print(cabinet[100])		# 김태호

print(cabinet.get(3))		# 유재석

print(cabinet[5])		# 5라는 key가 없기 때문에 오류를 리턴하고 종료.
print("hi")					# 실행 안됨.

print(cabinet.get(5))		# get을 사용하면 key 값이 없어도 none 리턴하고 종료 안함.
print("hi")							#실행 됨.

print(cabinet.get(5), "사용 가능") # key 값 없으면 "사용 가능" 리턴.

print(3 in cabinet)				# key in var   - True 
print(5 in cabinet)				# key in var	 - False

cabinet = {"A-3":"유재석", "B-100":"김태호"}
print(cabinet["A-3"])				# 유재석
print(cabinet["B-100"])			# 김태호

# 새 손님
print(cabinet)
cabinet["A-3"] = "김종국" # key에 값 할당 - 만약 키가 이미 사용중이면 값이 update
cabinet["C-20"] = "조세호"

# 간 손님
del cabinet["A-3"]

# key 들만 출력
print(cabinet.keys())

# value 들만 출력
print(cabinet.values())

# key, value 쌍으로 출력
print(cabinet.items())

# 목욕탕 폐점
cabinet.clear()
print(cabinet)				# {} 출력

```



#### 튜플

> #####  리스트와는 다르게 내용을 변경이나 추가를 할 수 없다.
>
> ##### 속도가 리스트보다 빠르다. 변경되지 않는 목록을 사용할 때 튜플 활용할 수 있다.

``` 
menu = ("돈까스", "치즈까스")
print(menu[0])		# 돈까스
print(menu[1])		# 치즈까스

menu.add("생선까스")    # 오류 (튜플은 add 기능 제공 x) 

name = "김종국"
age = 20
hobby = "코딩"
print(name, age, hobby)

(name, age, hobby) = ("김종국", 20, "코딩")		# 튜플을 이용해 한 번에 값을 선언 - 서로 다른 변수에 서로 다																							# 른 값들을 한 번에 넣어줄 수 있다.
print(name, age, hobby)
```



#### 집합 (set)

> ##### 중복 안됨, 순서 없음 

``` python
my_set = {1, 2, 3, 3, 3}
print(my_set)

java = {"유재석", "김태호", "양세형"}
python = set(["유재석", "박명수"])

# 교집합 (java 와 python 을 모두 할 수 있는 개발자)
print(java & python) 										# {'유재석'}
print(java.intersection(python))				# {'유재석'}

# 합집합 (java 할 수 있거나 python 할 수 있는 개발자)
print(java | python)										# {'김태호', '박명수', '양세형', '박명수'}
print(java.union(python))								# {'김태호', '박명수', '양세형', '박명수'}

# 차집합 (java 할 수 있지만 python은 할 줄 모르는 개발자)
print(java - python)										# {'김태호', '양세호'}
print(java.difference(python))

# python 을 할 줄 아는 사람이 늘어남
python.add("김태호")
print(python)														# {'박명수', '김태호', '유재석'}

# java 를 잊었어요
java.remove("김태호")
print(java)															# {'유재석', '양세형'}
```



#### 자료구조의 변경

``` python
#커피숍

menu = {"커피", "우유", "쥬스"}
print(menu, type(menu))							# {'주스', '우유', '커피'} <class 'set'>

menu = list(menu)										
print(menu, type(menu))							# ['주스', '우유', '커피'] <class 'list'>

menu = tuple(menu)
print(menu, type(menu))							# ('주스', '우유', '커피') <class 'tuple'>

menu = set(menu)				
printt(menu, type(menu))						# {'주스', '우유', '커피'} <class 'set'>
```



##### Ramdom 클래스 내장 함수

- ##### shuffle : list 안의 값을 무작위로 바꾼다.

- ##### sample : sample(list, 1)  첫 번째 인자 리스트에서 두 번째 인자 개수 만큼 무작위로 뽑는다.



#### Quiz

```python
# Quiz) 당신의 학교에서는 파이썬 코딩 대회를 주최합니다.
# 참석률을 높이기 위해 댓글 이벤트를 진행하기로 하였습니다.
# 댓글 작성자 중에 추첨을 통해 1명은 치킨, 3명은 커피 쿠폰을 받게 됩니다.
# 추첨 프로그램을 작성하시오.

# 조건1 : 편의상 댓글은 20명이 작성하였고 아이디는 1~20 이라고 가정
# 조건2 : 댓글 내용과 상관 없이 무작위로 추첨하되 중복 불가
# 조건3 : random 모듈의 shuffle 과 sample 을 활용

# (출력 예제)
# -- 당첨자 발표 --
# 치킨 당첨자 : 1
# 커피 당첨자 : [2, 3, 4]
# -- 축하합니다 --

# (활용 예제)
# from random import *
# lst - [1,2,3,4,5]
# print(lst)
# shuffle(lst)
# print(lst)
# print(sample(lst, 1))

from random import *


users = range(1, 21)              # 1부터 20까지 숫자를 생성
users = list(users)

# print(users)
shuffle(users)
# print(users)

# # 내가 한 방법
rank1 = sample(users, 1)
rank2 = sample(set(users)-set(rank1), 3)

print(" -- 당첨자 발표 -- ")
print("치킨 당첨자 : ", rank1)
print("커피 당첨자 : ", rank2)
print("-- 축하합니다 --")

# 다른 방법

winners = sample(users, 4)      # 4명 중에서 1명은 치킨, 3명은 커피

print("-- 당첨자 발표 -- ")
print("치킨 당첨자 : {0}" .format(winners[0]))
print("커피 당첨자 : {0}" .format(winners[1:]))
```

