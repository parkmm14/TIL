### [algorithm] level-1 완주하지 못한 선수 

#### 다른 사람의 풀이

##### 1_ collection.Counter().py

``` python
import collections

def solution (participant, completion):
  answer = collections.Counter(participant) - collections.Counter(completion)
  return list(answer.keys())[0]
```

Counter() 는 dict와 같이 hash형 자료들의 값의 개수를 셀 때 사용하는데 딕셔너리처럼 {'자료이름':'개수'} 형식으로 만들어진다. Counter 객체끼리 뺄셈도 가능



##### collection.Counter().py

``` python
p = ['mislav', 'stanko', 'mislav', 'ana']
c = ['stanko', 'ana', 'mislav']

print(collections.Counter(p))
# Counter({'mislav: 2, 'stanko': 1, 'ana': 1})

print(collections.Counter(c))
# Counter({'stanko':1, 'ana': 1, 'mislav':1})

print(collections.Counter(p) - collections.Counter(c)) #mislav
```







