# Annotation

어노테이션의 사전적 정의는 주석입니다. 자바에서의 어노테이션은 클래스, 필드, 메소드 등에 사용되어 프로그램에게 추가적인 정보(의미, 기능)를 제공합니다. 대표적인 어노테이션으로는 @Getter, @Setter, @Override 등이 있습니다.

<br>

___

<br>

+ 어노테이션은 다음과 같은 형태로 정의한다.

  ```java
  @Target({ElementType.[적용대상]})
  @Retention(RetentionPolicy.[정보유지되는대상])
  public @interface [어노테이션명]{
  	public 타입 elementName() [default값]
  }
  ```

  ```java
  @Target({ElementType.METHOD})
  @Retention(RetentionPolicy.RUNTIME)
  public @interface MyAnnotation {
      String value() default "-";
      int number() default 15;
  }
  
  public class MyService {
      @MyAnnotation
      public void method1() {
          System.out.println("실행 결과1 : ");
      }
      
      @MyAnnotation("*")
      public void method1() {
          System.out.println("실행 결과1 : ");
      }
      
      @MyAnnotation(value = "*", number = 20)
      public void method1() {
          System.out.println("실행 결과1 : ");
      }
  }
  
  //getDeclaredAnnotation()로 어노테이션 정보를 얻고
  //annotation.value(), annotation.number() 메소드로 어노테이션 안에 저장된 값을 사용할 수 있다.
  ```

  + @Type에는 어떠한 값(클래스, 필드, 메서드)에 어노테이션을 적용할 것인지 나타낼 수 있다.

    | ENUM            | 적용대상                      |
    | --------------- | ----------------------------- |
    | TYPE            | 클래스, 인터페이스, 열거 타입 |
    | FIELD           | 필드                          |
    | ANNOTATION_TYPE | 어노테이션                    |

  + @Retention에는 어노테이션 값들을 언제까지 유지할 것인지 값을 입력하는데, 보통 어노테이션은 Runtime시에 많이 사용하므로 RUNTIME으로 설정되어 있다.

    | ENUM    | 설명                                                         |
    | ------- | ------------------------------------------------------------ |
    | SOURCE  | 소스상에서만 어노테이션 정보를 유지하여 바이트 코드 파일에는 정보가 남지 않는다. |
    | CLASS   | 바이트 코드 파일까지 어노테이션 정보를 유지할 수는 있지만, 리플렉션을 이용해서 어노테이션 정보를 얻을 수는 없다. |
    | RUNTIME | 바이트 코드 파일까지 어노테이션 정보를 유지하면서 리플렉션을 이용해서 런타임에 어노테이션 정보를 얻을 수 있다. |

  + 필드, 생성자, 메소드에 적용된 어노테이션 정보는 .class로부터 얻을 수 있다.

