#### 람다(lambda)

`lambda 인자 : 표현식`

``` python
>>> def hap(x, y):
...		return x + y
...
>>> hap(10, 20)
30
```



``` python
>>> (lambda x,y : x + y)(10, 20)
30
```



#### map()

---

`map(함수, 리스트)` 

리스트로부터 원소를 하나씩 꺼내서 함수에 적용시킨 다음, 

그 결과를 새로운 리스트에 담아줌.

``` python
>>> map(lambda x: x ** 2, range(5))
[0, 1, 4, 9, 16]
>>> list(map(lambda x: x **2, range(5)))
[0, 1, 4, 9, 16]

```



#### reduce()

---

`reduce(함수, 순서형 자료)` 

순서형 자료(문자열, 리스트, 튜플)의 원소들을 누적적으로 함수에 적용시킴.

``` python
>>> from functiools import reduce
>>> reduce(lambda x, y: x + y, [0, 1, 2, 3, 4])
10

>>> reduce(lambda x, y:y + x, 'abcde')
'edcba'
```



#### filter()

---

`filter(함수, 리스트)`

리스트에 들어 있는 원소들을 함수에 적용시켜서 결과가 참인 값들로 새로운 리스트를 만들어줌.

``` python
>>> filter(lambda x: x<5, range(10))		
[0, 1, 2, 3, 4]
>>> list(filter(lambda x: x<5, range(10)))
[0, 1, 2, 3, 4]
```



홀수를 돌려주는 필터

``` python
>>> filter(lambda x:x % 2, range(10))
[1, 3, 5, 7, 9]
>>> list(filter(lambda x: x % 2, range(10)))
[1, 3, 5, 7, 9]
```

