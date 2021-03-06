# Spring Triangle

Spring 프레임워크의 3대 핵심 기술을 Spring Triangle이라고 하며, IoC, AOP, PSA가 있습니다.

IoC는 객체의 생명주기를 개발자가 아닌 프레임워크가 관리하는 것이고, AOP는 핵심 기능과 공통 기능을 분리 시켜놓고, 공통 기능을 필요로 하는 핵심 기능들에서 사용하는 방식입니다. PSA는 환경의 변화와 관계 없이 일관된 방식의 기술을 사용할 수 있게끔 제공하는 추상화 구조를 말합니다.

___

+ IoC

  + 개발자가 비즈니스 로직에만 신경쓰게 할 수 있도록 객체의 생명주기를 프레임워크에서 관리하는 것이다.

+ AOP 

  + AOP는 중복을 줄여서 적은 코드 수정으로 전체 변경을 할 수 있도록 하는 것이다.
  + 쉽게 말해, 어떤 로직을 기준으로 핵심과 부가로 관점을 나누어 분리한 부가기능을 Aspect라는 모듈형태로 설계하고 개발하는 방법이다.
  + IoC가 낮은 결합도와 관련된 것이라면, AOP는 높은 응집도와 관련되어 있다.

+ PSA 

  + @Transactional 어노테이션을 추가하면, 우리는 별 다른 코드를 작성하지 않아도 트랜잭션 기능을 사용할 수 있다.

    @Controller 어노테이션을 추가하면, 별 다른 설정 없이도 MVC 구조의 API를 작성할 수 있다.

    이렇게 추상화 계층을 사용하여, 구현을 내부에 숨기고 개발자에게 편의성을 제공해 주는 것을 PSA라고 생각하면 쉬울 듯 하다.