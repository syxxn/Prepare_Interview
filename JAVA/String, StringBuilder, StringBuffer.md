# String, StringBuilder, StringBuffer

String와 StringBuilder, StringBuffer는 자바에서 문자열을 다루는 대표적인 클래스입니다. String은 불변의 속성을 가지고 있어 기존 문자열에 다른 문자열을 더하는 연산을 수행할 경우, 기존 문자열의 메모리는 GC에 의해 사라지고, 새로운 객체를 생성합니다. 변하지 않는 문자열을 읽어들일때는 String이 좋지만, 연산이 빈번하게 발생할 경우에는 StringBuilder 또는 StringBuffer를 사용하는 것이 더 좋습니다. StringBuilder와 StringBuffer는 동일한 기능을 가지고 있으며, 멀티 스레드 환경인 경우엔 StringBuffer, 단일 스레드 또는 동기화를 고려하지 않아도 되는 경우에는 StringBuilder를 사용하는 것이 적합합니다.

<br>

____

<br>

| Strnig                                                       | StringBuilder/StringBuffer                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image info](https://t1.daumcdn.net/cfile/tistory/99948B355E2F13350F) | ![image info](https://t1.daumcdn.net/cfile/tistory/9923A9505E2F133608) |

+ 많은 연산 사용시 String 클래스를 사용하면, 힙 메모리에 많은 임시 Garbage가 생성되어 힙 메모리 부족이 발생할 수 있다.
+ StringBuilder/StringBuffer는 가변성을 가지기 때문에 .append(), .delete() 등의 메소드를 이용하여 동일 객체 내에서 문자열을 변경하는 것이 가능하다.