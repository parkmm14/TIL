

#### if

> ##### 분기, 조건문

``` python
weather = input("오늘 날씨는 어때요? ")
if weather == "비":
  print("우산을 챙기세요)
elif weather == "미세먼지":
        print("마스크를 챙기세요")
else:
        print("준비물 필요 없어요.")
        
temp = int(input("기온은 어때요? "))
if 30 <= temp:
        print("너무 더워요, 나가지 마세요")
elif 10 <= temp and temp <30:
        print("괜찮은 날씨에요")
elif 0 <= temp < 10:
        print("외투를 챙기세요")
else:
        print("너무 추워요. 나가지 마세요")
```



#### for 

> ##### 반복문

``` python
for waiting_no in [0, 1, 2, 3, 4]:					#in 뒤에 나오는 list의 값들을 순차적으로 대입
  print("대기번호 : {0}" .format(waiting_no)) 
  
# randrange()
for waiting_no in range(1, 6): # 1, 2, 3, 4, 5						
  print("대기번호 : {0}" .format(waiting_no))
  
starbucks = ["아이언맨", "토르", "아이엠 그루트"]
for customer in starbucks:
  print("{0}, 커피가 준비되었습니다." .format(customer))
```



#### while

> ##### 어떤 조건이 만족할 때까지 반복

```` python
customer = "토르"
person = "Unknown"

while person != customer :
  print("{0}, 커피가 준비 되었습니다." .format(customer))
  person = input("이름이 어떻게 되세요? ")
````



#### continue, break

``` python
absent = [2, 5] # 결석
no_book = [7] # 책을 깜빡했음
for student in range(1, 11):		# 1,2,3,4,5,6,7,8,9,10
 if student in absent:
  continue			# 문장을 계속 진행시키지 않고 다음 반복문으로 이동하라.
 elif student in no_book:
  break			#지금 상황에서 바로 반복문을 종료하여 끝냄.
 print("{0}, 책을 읽어봐" .format(student))

```



#### 한 줄 for 문

``` python
# 출석번호가 1 2 3 4, 앞에 100을 붙이기로 함 -> 101, 102, 103, 104
students = [1, 2, 3, 4, 5]
print(students)
students = [i+100 for i in students]		# students 에 있는 i 값을 하나씩 불러오면서 i+100 값을 list에 집어 넣어라.
print(students)			# [101, 102, 103, 104] 출력

# 학생 이름을 길이로 변환
students = ["Iron man", "Thor", "I am groot"]
students = [len(i) for i in students]
print(students)			# [8, 4, 10]

# 학생 이름을 대문자로 변환
students = [i.uppser() for i in students]
print(students)



```



##### *Quiz*

``` python
# Quiz) 당신은 Cocoa 서비스를 이용하는 택시 기사님입니다.
# 50명의 승객과 매칭 기회가 있을 때, 총 탑승 승객 수를 구하는 프로그램을 작성하시오.

# 조건1 : 승객별 운행 소요 시간은 5분 ~ 50 분 사이의 난수로 정해집니다.
# 조건2 : 당신은 소요 시간 5분 ~ 15 분 사이의 승객만 매칭해야 합니다.


from random import * 

cnt=0       # 총 탑승 승객 수 
for i in range(1, 51):      # 1 ~ 50 이라는 수 (승객)
    time = randrange(1, 51) # 5분 ~ 50분 소요 시간
    if(5 <= time <= 15): # 5분 ~ 15분 이내의 손님 (매칭 성공), 탑승 승객 수 증가 처리
        print("[O] {0}번째 손님 (소요시간 : {1}분" .format(1, time))
        cnt += 1
    else:   # 매칭 실패한 경우
        print("[] {0}번째 손님 (소요시간 {1}분" .format(i, time))


print("총 탑승 승객 : {0} 분" .format(cnt))
```



#### 함수

- #### 함수 호출방법



- ##### 전달값과 반환값

``` python
def open_account():		# 함수 정의
  print("새로운 계좌가 생성되었습니다.")
  
open_account()			# 함수 호출

def deposit(balance, money):		# 입금
  print("입금이 완료되었습니다. 잔액은 {0} 원입니다" .format(balance + money))
  return balance + money

def withraw(balance, money):
  if balance >= money: #잔액이 출금보다 많으면
    print("출금이 완료되었습니다. 잔액은 {0} 원입니다." .format(balance - money))
    return balance - money
  else:
    print("출금이 완료되지 않았습니다. 잔액은 {0} 원입니다." .format(balance))
    return balance
def withraw_night (balance, money):		# 저녁에 출금
  commission = 100 # 수수료 100원
  return commission, balance - money - commission
 	
balance = 0 # 잔액
balance = deposit(balance, 1000)	# 입금이 완료되었습니다. 잔액은 1000 원입니다.
# balance = withraw(balance, 500)	# 출금이 완료되었습니다. 잔액은 500 원입니다.
commission, balance = withraw_night(balance, 500)
print("수수료 {0} 원이며, 잔액은 {1} 원입니다." .format(commission, balance))

# 새로운 계좌가 생성되었습니다.
# 입금이 완료되었습니다. 잔액은 1000 원입니다
# 수수료 100 원이며, 잔액은 400 원입니다 
```



- ##### 기본값

``` python
def profile(name, age=17, main_lang="파이썬"):
  print("이름 : {0}\t나이 : {1}\t주 사용 언어: {2}" \
       	.format(name, age, main_lang))
  
profile("유재석")
profile("김태호")

# 같은 학교 같은 학년 같은 반 같은 수업.
```



- ##### 키워드값

``` python
def profile(name, age, main_lang): 	#이렇게 키워드를 선언해주면
  print(name, age, main_lang)
profile(name="유재석", main_lang="파이썬", age=20)		#순서가 뒤섞여 있어도 값을 잘 전달
profile(main_lang="자바", age=25, name="김태호 ")

```



- ##### 가변인자

> ##### 서로 다른 갯수의 값을 넣어줄 때 사용한다.

``` python
# del profile (name, age, lang1, lang2, lang3, lang4, lang5):
#  print("이름: {0}\t나이 :{!}\t".format(name, age), end=" ")
#  print(lang1, lang2, lang3, lang4, lang5)

del profile (name, age, *language):
  print("이름 : {0}\t나이: {1}\t" .format(name, age), end=" ")
	for lang in language:
    print(lang, end=" ")
  print()


# profile("유재석", 20, "Python", "Java", "C", "C++", "C#")
# profile("김태호", 25, "Kotlin", "Swift", "", "", "")

profile("유재석", 20, "Python", "Java", "C", "C++", "C#")
profile("김태호", 25, "Kotlin", "Swift")

```



- ##### 지역변수와 전역변수

``` python
gun = 10

def checkpoint(soldiers): 	# 경계근무
  global gun	# 전역 공간에 있는 gun 사용
  gun = gun - soldiers
  print("[함수 내] 남은 총 : {0}".format(gun))
  
def checkpoint_ret (gun, soldiers):
  gun = gun - soldiers
  print("[함수 내] 남은 총 : {0}" . format(gun))
  return gun

  
print("전체 총 : {0}".format(gun))
checkpoint(2)	# 2명이 경계 근무 나감
gun = checkpoint_ret(gun, 2)
print("남은 총 : {0}" .format(gun))


# checkpoint 함수사용
# 전체 총 : 10
# [함수 내] 남은 총 : 8
# 남은 총 : 8

# checkpoint_ret 함수 사용
# 전체 총 : 10
# [함수 내] 남은 총 : 8
# 남은 총 : 8
```

