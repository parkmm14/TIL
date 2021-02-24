### 두 객체의 값 비교 (Equals, CompareTo)



다른 언어에선 두 값이 동일한지 비교할 때 == 을 사용하지만 자바에서는 String.equals() 메소드를 사용해야 한다.

자바에서 ==은 객체가 같은지를 판별하기 때문에 객체의 값을 비교하기에 부정확하다. 

String.equals() 는 자바의 최상위 클래스인 Object 클래스를 부모로 갖는다.

주의할 점: 호출자인 객체가 Null일 때 NullPointerException 발생하고, 인자인 객체가 Null일 때는 발생하지 않는다.

이런 게 싫으면 null을 체크하는 Object.equals(o1, o2) 사용하기. 

두 객체의 값에 대한 사전적 순서 및 관계를 비교할 때는 CompareTo 메소드 사용한다.



### 배열정렬 (Sorting)

Arrays.sort() 이용하면 Integer, String 상관없이 쉽게 배열을 정렬할 수 있다. 

기본적으로 객체는 Comparable 인터페이스가 구현되어 있고 Compaable에 의해 리턴되는 값을 비교해 내림차순, 오름차순으로 정렬한다.

#### Arrays.sort(객체, 정렬조건)

Arrays.sort()는 오름차순 정렬, Arrays.sortt(arr, Collections.reverseOrder()) 은 내림차순 정렬.

---> Collections.reverseOrder()는 직접 구현해야 하는 Comparator 객체이지만 빈번하게 사용되는 까닭에  Collections에서 기본으로 제공

##### int 배열 정렬 (오름차순, 내림차순)

```java
//내림차순 Comarator를 직접 구현
//Comparator로 비교할 때는 int가 아닌 Integer를 사용해야 함.
Integer[] arr = {1, 26, 17, 25, 99, 44, 303};

Arrays.sort(arr, new Comparator<Integer>(){
  @Override
  public int compare(Integer i1, Integer i2) {
    return i2 - i1;
  }
});

System.out.println("Sorted arr[] : " + Arrays.toString(arr));


//Lambda를 사용하여 더 짧게 구현

Arrays.sort(arr, (i1, i2) -> i2 - i1);

```

##### 

##### int 배열, 부분 정렬

처음 index와 끝 index를 전달하여 정렬할 범위 지정.

``` java
// sort(객체, 시작인덱스, 끝인덱스)
int[] arr = {1, 26, 17, 25, 99, 44, 303};

Arrays.sort(arr, 0 , 4);

```



##### String 배열 정렬 (Sorting)

String배열도 Integer와 동일함. 알파벳의 아스키 값으로 비교를 하여 정렬한다.

내림차순 정렬도 동일!



##### String 배열, 문자열 길이 순서로 정렬 (Sorting)

만약 문자열 길이 순서로 정렬을 하고 싶을 때는 직접 Comparator를 구현해야 한다

``` java
String[] arr = {"Apple", "Kiwi", "Orange", "Banana", "Watermellon", "Cherry"};

Arrays.sort(arr, new Comparattor<String>(){
  @Override
  public int compare(String s1, String s2){
    return s1.length() - s2.length();
  }
});

System.out.println("Sorted arr[]: ", + Arrays.toString(arr));

//Lambda를 사용하여 아래처럼 더 간결하게 구현 가능
Arrays.sort(arr, (s1, s2) -> s1.length() - s2.length());

```



##### 객체 배열 정렬 (Sorting)

객체를 갖고 있는 배열도 정렬할 수 있다. 이 경우에는 클래스에 Comparable을 구현하여 비교할 수 있게 해야 함.

``` java
//Comparble<Fruit>를 구현하고 있는 Fruit 라는 클래스
public static class Fruit implements Comparable<Fruit>{
  private String name;
  private int price;
  public Fruitt(String name, int price) {
    this.name = name;
    this.price = price;
  }
  
  @Override
  public String toString(){
    return "{name:" + name + ", price: " + price + "}";
  }
  
  @Override
  public int compareTo(@NotNull Fruit fruit) {
    return this.price - fruit.price;
  }
}
```

