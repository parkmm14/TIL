내가 찾고자 하는 문자열 A가 문자열 B의 맨 앞에 있는지의 여부를 알려 준다.

기본적으로는 무자열 strB에 문자열 strA 가 **맨 앞** 에 있다면 True를 반환하고, 아니면 False를 반환한다.

``` python
strB = 'abcdefg'
print(strB.startswitch('ab')) #True
print(strB.startswitch('bcd')) #False
# 찾고자 하는 문자열 'bcd'가 strB의 앞에 없음.
```

