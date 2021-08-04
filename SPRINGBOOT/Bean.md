# Bean

스프링 빈은 IoC 컨테이너가 관리하는 자바 객체를 말합니다. 

보통 싱글톤으로 생성되며, @Component 어노테이션, 또는 @Bean 어노테이션을 붙여 빈으로 등록합니다.

빈은 객체 생성 - 의존 설정 - 초기화 - 사용 - 소멸 과정의 생명 주기를 가지고 있습니다.

<br>

____

<br>

+ 싱글톤 : 최초 한번만 메모리를 할당하고, 그 메모리에 객체를 만들어서 사용하는 디자인 패턴

+ 빈 등록 방법

  + 클래스에 @Component 또는 @Conponent를 정의한 @Service, @Controller, @Repository 등의 어노테이션을 사용한다.

    > main 클래스에 @ComponentScan 어노테이션을 붙여 모든 하위 클래스를 훑어보여 @Component 어노테이션을 찾아 빈으로 등록시켜준다.

  + @Configuration 클래스 필드에 직접 @Bean 어노테이션을 붙인다.

+ 빈의 스코프 종류에는 Singleton, Prototype, Request, Session, Application이 있다.
  + Singleton : 기본 스코프로서, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프이다.
  + Prototype : 빈의 생성과 의존관계 주입까지만 관여하는 짧은 범위의 스코프이다. 프로토타입을 받은 클라이언트가 객체를 관리해야 한다.
  + Request : 각각의 요청이 들어오고 나갈 때까지 유지되는 스코프이다.
  + Session : 세션이 생성되고 종료될때까지 유지되는 스코프이다.
  + Application : 서블릿 컨텍스트 생명주기 동안 사용되는 스코프이다.

```java
@Component
public class A {

	@Autowired
	private B b;

}

@Component
@Scope(value = "prototype") //이런식으로 빈의 스코프를 설정해줄 수 있다.
public class B {

}
```

