# Singleton Pattern

싱글톤 패턴이란, 애플리케이션이 시작될 때 어떤 클래스가 최초 한번만 메모리를 할당하고 그 메모리에 인스턴스를 만들어 사용하는 디자인 패턴입니다.

생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고, 최초 생성 이후에 생성자를 호출하더라도 최초에 생성한 객체를 반환합니다.

<br>

____

<br>

+ IoC 컨테이너에서 대부분 싱글톤 패턴으로 빈을 생성한다.

+ 싱글톤 패턴의 장점

  + 고정된 메모리 영역을 얻으면서 하나의 인스턴스를 사용하기 때문에 메모리 낭비를 방지할 수 있다.
  + 싱글톤으로 만들어진 인스턴스는 전역 인스턴스이기 때문에 다른 클래스의 인스턴스들이 데이터를 공유하기 쉽다.
  + 인스턴스가 절대적으로 한 개만 존재하는 것을 보증하고 싶을 경우 사용한다.

+ 싱글톤 패턴의 문제점

  + 싱글톤 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유시킬 경우 다른 클래스의 인스턴스들 간에 결합도가 높아져 SOLID 원칙 중 OCP를 위반하게 된다.

    > OCP(Open-Closed Principle) : 개방-폐쇄 원칙
    >
    > 확장에는 열려 있어야 하고, 변경에는 닫혀 있어야 한다.
    >
    > 기능을 변경하거나 확장할 수 있으면서 그 기능을 사용하는 코드는 수정하지 않도록 하여 연쇄적으로 변화를 일으키는 것을 방지하고자 한다.

  + 수정이 어려워지고 테스트하기 어려워진다.

  + 멀티스레드 환경에서 컨트롤이 어렵다.