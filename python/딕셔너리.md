### 딕셔너리 자료형

---

구별이 가능하도록 대응 관계를 나타낼 수 있는 파이썬의 자료형. 대부분 언어에선 연관 배열(Associative array) 또는 해시(Hash) 자료형이라고 한다.

``` python
{Key1: Value1, Key2:Value2, Key3:Value3}
```

**Key 를 통해 Value 값을 얻음.** (순차적으로 해당 요솟값을 구하는 리스트나 튜플과의 차이점)

> Key 에는 변하지 않는 값을 사용하고, Value에는 변하는 값과 변하지 않는 값 모두 사용. --> Key에 리스트 불가능.



### 딕셔너리 쌍 추가, 삭제하기

---

``` python
# 딕셔너리 쌍 추가
>>> a= {1: 'a'}
>>> a[2] = 'b'
>>> a
{1: 'a', 2: 'b'}

>>> a['name'] = 'pey'
>>> a
{1: 'a', 2: 'b', 'name': 'pey'} # 딕셔너리 a에 'name': 'pey' 쌍 추가됨.

>>> a[3] = [1,2,3]
>>> a
{1: 'a', 2:'b', 'name':'pey', 3: [1,2,3]}

# 딕셔너리 쌍 삭제
>>> del a[1]
>>> a
{2: 'b', 'name': 'pey', 3: [1,2,3]} # 지정한 키에 해당하는 {key : value} 쌍이 삭제된다.

```



### 딕셔너리 사용하는 방법

---

사용 예시: 사람 이름과 특기를 한 쌍으로 하는 딕셔너리

``` python
{"김연아":"피겨스케이팅", "류현진":"야구", "박지성":"축구", "귀도":"파이썬"}
```



#### 딕셔너리에서 Key 사용해 Value 얻기

리스트나 튜플, 문자열은 요솟값을 얻고자 할 때 인덱싱이나 슬라이싱 기법 중 하나를 사용했지만, 딕셔너리는 한 가지 방법 뿐임.

---> 어떤 Key의 Value를 얻기 위해선	`딕셔너리변수이름[Key]` 사용 (Key에 해당하는 Value 값을 얻는다.)

``` python
>>> a = {1:'a', 2:'b'}
>>> a[1]
'a'
>>> a[2]
'b'

>>> dic = {'name':'pey', 'phone':'11'}
>>> dic['name']
'pey'
```



#### 딕셔너리 만들 때 주의 사항

Key는 공유한 값이므로 중복되는 Key 값을 설정해 놓으면 하나를 제외한 나머지 것들이 무시된다.

Key에 리스트를 쓸 수 없다.(어떤 Key에 해당하는 Value를 불러야 할지 알 수 없기 때문)



#### 딕셔너리 관련 함수들

---

``` python
>>> a = {'name':'pey', 'phone': '011', 'birth':'1118'}
>>> a.keys()
dict_keys(['name', 'phone', 'birth'])
```

a.keys() : 딕셔너리 a의 Key만을 모아서 dict_keys 객체를 돌려줌.

> Python 3.0 이후 버전에서 반환값으로 dict_keys 객체가 아닌 리스트가 필요한 경우  `list(a.keys())` 사용하면 된다.
>
> dict_keys, dict_values, dict_items 등은 리스트로 반환되지 않더라도 기본적인 반복(iterate)구문 (예:for문)을 실행할 수 있다.

dict_keys 객체는 리스트를 사용하는 것과 차이가 없지만, 리스트 고유의 append, insert, pop, remove, sort 함수는 수행할 수 없다.

``` python
>>> for k in a.keys():
  		 print(k)
name
phone
birth

>>> list(a.keys())
['name', 'phone', 'birth']
```



#### Value 리스트 만들기 (values)

``` python
# Value 리스트 맏르기 (values)
>>> a.values()
dict_values('pey', '011', '1118')

# Key, Value 쌍 얻기 (items)
>>> a.items()
dict_items([('name', 'pey'), ('phone', '011'), ('birth', '1118')])

# Key: Value 쌍 모두 지우기 (clear)

>>> a.clear()
>>> a
{}

#Key로 Value얻기 (get)   a['nokey'] 의 차이 : 존재하지 않을 경우 a['nokey']는 key 오류, a.get('nokey')는 None 리턴
>>> a = {'name':'pey', 'phone':'011', 'birth':'1118'}
>>> a.get('name')
'pey'
>>> a.get('phone')
'011'

# 해당 Key가 딕셔너리 안에 있는지 조사하기(in)

>>> a = {'name':'pey', 'phone':'011', 'birth': '1118'}
>>> 'name' in a
True
>>> 'email' in a
False
```

*점프투파이썬 참조

