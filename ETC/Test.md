# Test code

소프트웨어 테스트란, 시스템이 정해진 요구를 만족하는지, 예상과 실제 결과가 어떤 차이를 보이는지를 검사하고 평가하는 일련의 과정을 말합니다. 테스트의 종류로는 개발된 각 컴포넌트를 통합하면서 발생할 수 있는 버그를 확인하는 통합 테스트, 단위 기능 즉, 함수의 기능 하나하나를 테스트하는 유닛 테스트 등이 있습니다. 저는 거의 모든 프로젝트에서 JUnit을 사용하여 통합 테스트를 하거나 Assertions를 사용하여 유닛 테스트를 진행하였습니다. 테스트 코드를 작성함으로써 값에 따라 알맞게 예외처리가 발생하는지, 값이 제대로 저장되고 반환되는지 등 실제로 서비스를 실행시키지 않아도 여러 상황을 테스트 해볼 수 있어 시간을 단축할 수 있었습니다. 또한, 원하는 값이 반환되지 않을 경우 빠르게 코드를 수정하여 실제 서비스의 오류를 줄일 수 있었습니다.

<br>

___

<br>

+ 테스트 코드를 작성하는 이유

  + 서버를 실행하는 등의 시간을 절약할 수 있다.
  + 문서로서의 역할이 가능하다. (어떤 값이 들어갔을 때 어떤 결과를 원하는지 알 수 있음)

+ 테스트 코드 팁

  + 어떤 값이 주어지고(given), 무엇을 했을 때(when), 어떤 값을 원한다(then)을 나누어 직관적으로 볼 수 있도록 한다.

  ```java
  public class PersonTest {
      @Test
      public void test() throws Exception {
          //given
          String name = "JJY";
          Person p1 = new Person();
          
          //when
          String ment = p1.hi(name);
          
          //then
          assertThat(ment, is("hi JJY"));
      }
  }
  ```

  + 다양한 Response에 대한 테스트를 진행한다.