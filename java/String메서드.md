### 자주 쓰이는 String 메서드



### indexOf

---



**int indexOf(int ch) **: 현재 문자열 객체에서 ch문자가 첫 번째로 발견된 위치를 반환, 없으면 -1 반환.

**int indexOf(String str)** : 현재 문자열 객체에서 str문자가 첫 번째로 발견된 위치를 반환, 없으면 -1 반환.



### substring

---

문자열을 잘라주는 메서드 

**String substring(int start)** 

: 현재 문자열 객체 start위치부터 끝까지 문자열 발췌. = String의 시작 위치를 잡아서 새롭게 String을 반환해주는 메서드.

**String substring(int start, int end) **

: 현재 문자열 객체에서 start 부터 end 직전까지 문자열 발췌. 



substring 이용할 때 대상의 시작 위치를 모를 때? => indexOf 와 함께 사용.





예시) Apple Banana Orange 에서 Banana 발췌

``` java
String str = "Apple Banana Orange";
// Banana의 시작 인덱스와 끝 인덱스를 알 때
String str2 = str.substring(6, 12);

// Banana의 시작 인덱스와 끝 인덱스르 모를 때 -> indexOf로 대상의 인덱스 알아내기.
// 방법1)
String str2 = str.substring(str.indexOf("Banana"), str.indexOf(" Orange"));

// 방법2)
String str2 = str.substring(str.indexOf("Banana"), str.indexOf("Banana") + length("Banana"));
```



​														



