



collections 모듈 - Counter



### collections.Counter()

---

컨테이너에 동일한 자료가 몇 개인지를 파악하는데 사용하는 객체

`collections.Counter()` 의 결과값(return)은 딕셔너리 형태로 출력된다.

사용ex)프로그래머스 lv2 위장 :  입력값을 카테고리화하여 개수 카운트 



### 1. Counter()의 다양한 입력값들



### 1) 리스트(List)

`lst = ['aa', 'cc', 'dd', 'aa' ,'ee']` 의 요소 개수를 collection.Counter()를 이용하여 구할 수 있다.

 출력 결과는 Dictionary 형태로  반환



``` python
# collections.Counter 예제 (1)
# list를 입력값으로 함

import collections

lst = ['aa','bb','dd','aa','ee']
print(collections.Counter(lst))

'''
결과
Counter({'aa':2,'cc':1,'dd':1,'bb':1,'ee':1})
'''
```



### 2) 딕셔너리(Dictionary)



또한, `collections.Counter()` 는 요소의 개수가 많은 것부터 출력해 준다.

입력값을 `Dictionary` 형태로 넣어주면, 결과값 또한 `Dictionary` 이다.



3) 값 = 개수 형태

collections.Counter() 에는 `값=개수`형태로 입력이 가능하다.

예를 들어, `collections.Counter(a=2, b=3, c=2)` 는 `['a', 'a','a','b','b','b','c','c']` 와 같다.

```python
# collections.Counter 예제 (3)
# '값=개수' 입력값으로 함

import collections

c = collections.Counter(a=2, b=3, c=2)
print(collections.Counter(c))
print(sorted(c.elements()))

'''
결과
Counter({'b':3, 'c':2, 'a':2})
['a', 'a', 'b', 'b', 'b', 'c', 'c']
'''
```



### 4) 문자열(String)

문자열을 입력했을 경우 `{문자 : 개수}` 의 딕셔너리 형태로 반환해 준다.

``` python
# collections.Counter 예제 (4)
# '문자열'을 입력값으로 함

import collections

container = collections.Counter()
container.update("aabcdeffgg")
print(container)

...
결과
Counter({'f':2, 'g':2, 'a':2, 'e':1, 'b': 1, 'c':1, 'd':1})

for k, v in container.items():
  	print(k, ':', v)
'''
결과
f : 2
e : 1
b : 1
g : 2
c : 1
a : 2
d : 1
'''
```



### 2. Counter의 메소드(method)들 



### 1) update()

`update()` 는 Counter의 값을 갱신하는 것을 의미한다. 딕셔너리 update 와 비슷하지만

입력값을 문자열 형태로도 입력 가능하다.

예제(5)는 입력값을 문장열로 했을 때와 딕셔너리 형태로 입력했을 때의 예제이다.

```python
# collections.Counter 예제(5)
# update() 메소드 사용

import collections

# 문자열
a = collections.Counter()
print(a)
a.update('abcdefg')
print(a)
'''
결과
Counter()
Counter({'f':1, 'e': 1, 'a':1, 'c':1,'d':1,'g':1,'b':1})
'''

# 딕셔너리
a.update({'f':3, 'e':2})
print(a)
'''
결과
Counter({'f':4, 'e':3, 'a':1', 'c':1, 'd':1, 'g':1, 'b':1})
'''
```



### 2) elements()

입력된 값의 요소에 해당하는 값을 풀어서 반환한다. 요소는 무작위로 반환하며,

 요소 수가 1보다 작을 경우 `elements()` 는 이를 출력하지 않는다.

예제(5)는 "Hello Python"의 문자열을 elements()를 사용하여 출력한 결과이다. 

`elements()` 는 대소문자를 구분하며, `sorted()` 를 이용항여

정렬해줄 수 있다.



``` python
# collections.Counter 예제 (6)
# elements() 메소드 사용

import collections

c = collections.Counter("Hello Python")
print(list(c.elements()))
print(sorted(c.elements()))
'''
결과
['n', 'h', 'l', 'l', 't', 'H', 'e', 'o', 'o',' ', 'y', 'P']
[' ','H','P','e','h','l','l','n','o','o', 't','y']
'''

c2 = collections.Counter(a=4, b=2, c=0, d=-2)
print(sorted(c.elements()))
'''
결과
['a','a','a','a','b','b']
'''

```

### 3) most_common(n)



`most_common` 은 입력된 값의 요소들 중 빈도수(frequency)가 높은 순으로 상위 (n)개를 리스트(list) 안의 튜플(tuple) 형태로

반환한다. (n)을 입력하지 않은 경우, 요소 전체를 [('값', '개수')]의 형태로 반환한다.

### 4) subtract()

`subtract()` 은 말 그대로 요소를 빼는 것을 의미한다. 다만, 요소가 없는 경우에는 음수 값이 출력된다.

문자열 'hello python'에서 'i love python'을 `subtract()` 를 이용해서 빼주게 되면 

'hello python'에 존재하지 않는 'i', 'v'는 음수가 나타나게 된다.

