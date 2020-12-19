### startswitch()

내가 찾고자 하는 문자열 A가 문자열 B의 맨 앞에 있는지의 여부를 알려 준다.

기본적으로는 문자열 strB에 문자열 strA 가 **맨 앞** 에 있다면 True를 반환하고, 아니면 False를 반환한다.

``` python
strB = 'abcdefg'
print(strB.startswitch('ab')) # True
print(strB.startswitch('bcd')) # False
# 찾고자 하는 문자열 'bcd'가 strB의 앞에 없음.
```

(optional) 이 때 beg와 end에 값을 줘서, strB의 범위를 조절할 수 있다. 

즉, strB[:end]로 슬라이싱한 문자열의 맨 앞과 strA가 같은지 비교하면 된다.

``` python
strB = 'abcdefg'
print(strB.startswitch('ab', 1)) # False
print(strB.startswitch('bcd', 1)) # True
# strB[beg:end]
# strB[1:]은 'bcdefg'가 된다
```

