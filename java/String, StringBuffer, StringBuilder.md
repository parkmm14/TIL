### Java에서의 String, StringBuffer, StringBuilder



### String vs StringBuffer, StringBuilder

Java.lang은 별도로 import 해주지 않아도 사용할 수 있는 class들이 모여 있다.

Boolean, Byte, Integer등과 같은 Wrapper Class들도 찾아볼 수 있다. 그중에서 String, StringBuffer, StringBuilder를 눈여겨 보자.



String을 직접 더하는 것보단 StringBuilder나 StringBuffer를 사용하는게 낫다.

이유)

String은 새로운 값을 할당할 때마다 새로 생성되기 때문에 그 때마다 클래스의 주소값이 다르다.

이와 달리 StringBuffer는 값은 memory에 append하는 방식으로 클래스를 직접 생성하지 않는다. 논리적으로 따져 보면 클래스는 생성될 때 variable과 method를 함께 생성하는데 StringBuffer는 이런 시간을 사용하지 않는다.



또한 String이 여러 번 더해지는 경우 각 String의 주소값이 Stack에 쌓이고 클래스들은 Garbage Collector가 호출되기 전까지 heap에 지속적으로 쌓이게 된다. 메모리 관리 측면에서는 치명적이라고 볼 수 있다.

---

### StringBuffer와 StringBuilder

둘 다 memory에 값을 append하는 방식이지만 *StringBuilder*는 변경가능한 문자열이지만 asynchronization이 적용되지 않았다.

하지만 *StringBuffer*는 thread-safe라는 말처럼 변경불가능하지만 multi thread 환경에서 안전한 클래스이다.



*StringBuilder*의 값이 더 작은 이유는 쓰레드들이 동시에 *StringBuilder클래스에* 접근할 수 있기 때문이다. 이와 달리*StringBuffer*는 multi thread환경에서 다른 값을 변경하지 못하도록 하므로 web이나 소켓환경과 같이 비동기로 동작하는 경우가 많을 때는 *StringBuffer*를 사용하는 것이 안전할 것이다.







