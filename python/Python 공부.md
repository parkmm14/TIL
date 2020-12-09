- #### print() 함수

  - "+"가 아닌 "," 로도 여러 문장을 합칠 수 있다.
  - 이 때는 정수형 부울형 변수도 str() 쓰지 않고 그대로 써서 출력 가능하지만 띄어쓰기가 함께 들어 간다.

- #### 연산자

  - print(1+1) # 2
  - print(3-2) # 1
  - print(2**3) # 2^3 = 8 
  - print(10%3) # 나머지 구하기 1
  - print(5//3) # 5를 3으로 나눈 몫 1 
  - print(10//3) # 3 
  - print(10 > 3) # True
  - print(4 >= 7) # False
  - print(1 != 3) # True
  - print(not(1 != 3)) # False
  - print((3 > 0) and (3 < 5)) # True
  - print((3 > 0) & ( 3 < 5) # True
  - print((3 > 0) | (3 > 5)) # True
  - print(5 > 4 > 3) # True
  - Print(5 > 4 > 7) # False

- #### 수식

  - print(2 + 3 * 4) # 14
  - print((2 + 3) * 4) # 20
  - number = 2 + 3 * 4 # 14 
  - print(number)
  - number = number + 2 # 16
  - print(number)
  - number += 2 # 18
  - number *= 2 #  36
  - number /2 = # 18
  - number -= 2 # 16
  - number %= 5 # 1

- #### 숫자 처리 함수

  - print(abs(-5))  # 5

  - print(pow(4, 2)) # 4^2 = 4*4 = 16 

  - print(max(5, 12)) # 12

  - print(min(5, 12)) # 5 

  - print(round(3.14)) # 3

  - print(round(4.99)) # 5

    

  - from math import *

    Print(floor(4.99)) # 내림. 4

    Print(ceil(3.14)) # 올림. 4

    Print(sort(16)) # 제곱근. 4

    

    from random import *

     

    print(random()) # 0.0 ~ 1.0 미만의 임의의 값 생성

    print(random() * 10) # 0.0 ~ 10.0 미만의 임의의 값 생성

    print(int(random() * 10)) # 0 ~ 10 미만의 임의의 값 생성

    print(int(random() * 10)) # 0 ~ 10 미만의 임의의 값 생성

    print(int(random() * 10) + 1) # 1 ~ 10 이하의 임의의 값 생성

    print(int(random() * 45) + 1) # 1 ~ 45 이하의 임의의 값 생성

     

    print(randrange(1, 46)) # 1 ~ 46 미만의 임의의 값 생성 

      

    print(randint(1, 45)) #  1 ~ 45 이하의 임의의 값 생성

    

    

- #### 문자열

  - sentence = '나는 소년입니다'

    print(sentence)

    sentence2 = "파이썬은 쉬워요"

    print(sentence2)

    sentence3 = """

    나는 소년이고,

    파이썬은 쉬워요

    """

    print(sentence3) # 줄바꿈인 """ 을 포함해서 총 4줄이 출력 된다.

- #### 슬라이싱

   필요한 정보만 자르기

  -  jumin = "990120-1234567"  # 첫 번째는 인덱스 0부터 시작

  ​        print("성별 : " + jumin[7])

  ​        print("연 : " + jumin[0:2]) # 0 부터 2 직전까지 (0, 1)

  ​		print("월: "  + jumin[2:4])

  ​		print("일: " + jumin[4:6])

  ​		

  ​		print("생년월일 : "+ jumin[:6]) # 처음부터 6 직전까지  

  ​		print("뒤 7자리 : "+ jumin[7:]) # 7 부터 끝까지 

  ​		print("뒤 7자리 (뒤에부터) : " + jumin[-7:]).  # 맨 뒤에서 7번째부터 끝까지

  

  

- #### 문자열 처리 함수

  ​	python = "Python is Amazing"

  ​	print(python.lower()) # 모든 문자 소문자로 출력

  ​	print(python.upper()) # 모든 문자 대문자로 출력

  ​	print(python[0].isupper()) # 이 위치의 문자가 대문자 인지 알려 준다.

  ​	print(len(python)) # 이 전체 문자열의 길이 반환

  ​	print(python.replace("Python", "Java")) # 이 문자 중에서 Python 찾은 다음 이 부분을 Java로 바꿈

     

  ​	index = python.index("n") # 어떤 문자가 몇 번째 위치에 있는지 확인.

  ​	print(index) # 5의 위치 확인

  ​	index = python.index("n", index + 1) # 앞에서 찾은 5라는 위치에서 1을 더한 6의 위치에서 시작해서 n이 나오는 위치 찾음 ---> 15의 위치

  ​	

  ​	print(python.find("Java")) #  원하는 값이 없을 때(=이 변수에 포함되지 않을 때) -1 반환 

  ​	print(python.index("Java")) # 오류 --- 변수 python에는 원하는 값이 없기 때문에 에러 반환하고 프로그램 종료

  ​	

  ​	print(python.count("n")) # 이 변수에서 n이 총 몇 번 등장하는 지 









