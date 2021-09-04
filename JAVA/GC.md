# GC

GC란 Gabage Collection(또는 Garbage Collertor)의 줄임말로서, 힙 영역에서 더이상 사용하지 않는 객체를 메모리에서 제거하는 JVM의 작업을 말합니다. 

더 자세히 말하면, 객체는 힙 영역에 저장되고 스택 영역에 이를 가리키는 주소값이 저장되는데 참조되지 않는(자신을 가리키는 포인터가 없는) 객체를 메모리에서 제거합니다.

GC 덕분에 덕분에 개발자는 직접 메모리 할당/해제를 담당하지 않기 때문에 부담을 덜게 됩니다.

<br>

____

<br>

+ Java 힙 메모리는 Young, Tenured, Permanent Generation의 세 영역으로 구성되어 있다.

  ![image info](https://mirinae312.github.io/img/jvm_gc/JVMObjectLifecycle.png)

  + Young : 새로운 객체가 할당되고, 나이를 먹는다. young generation 영역이 채워지면 minor GC가 일어난다. young generation 객체들이 노화되고 임계값이 충족되면 old generation으로 이동한다.

  + Old : 오랫동안 살아 남은 객체들을 저장하는 데 사용한다. old generation에서 일어나는 GC는 major GC라고 부릅니다.

    > minor garbage collection과 major garbage collection은 stop the world 이벤트이다. 모든 애플리케이션의 스레드가 운영이 완료될 때까지 멈춘다는 뜻이다.
    >
    > major gc는 모든 살아있는 객체에 대해 동작하여 조금 더 느리기 때문에 반응형 프로그램에서는 gc를 최소화해야 한다.

  + Permanent : 애플리케이션의 클래스, 메소드를 설명하는 메타 데이터를 포함하고 있다. 애플리케이션에서 사용중인 클래스를 기반으로 JVM에 채워진다.

    > JVM이 더 이상 필요하지 않고, 다른 클래스에 공간이 필요할 경우, 클래스가 제거될 수 있다. 

+ 객체는 살아있는 스레드나 static 참조를 통해 도달할 수 없게 되면 GC 대상이 된다.
  1. 원형 참조는 참조로 간주하지 않으며, 모든 객체의 참조가 모두 null일 경우
  2. 객체가 블럭 안에서 생성되고 블럭이 종료되었을 경우
  3. 부모 객체가 null이 되었을 경우, 자식 또는 포함된 객체

+ 객체를 메모리에서 제거하기 전에 Garbage Collector 스레드는 해당 객체의 finalize() 메소드를 호출한다.

  > finalize() : 객체가 소멸될 때 호출되기로 약속된 메소드이다. 
  >
  > 필요 없어진 순서대로 실행되지 않고 무작위로 실행된다. 함수 실행 후 모두 지우는 것이 아니라 메모리 용량에 따라 소멸 여부를 결정한다.

+ GC를 강제로 수행할 수는 없으며, JVM이 힙 사이즈에 기반해서 필요한 경우에만 수행한다.

  > GC 요청을 보내기 위한 System.gc(), Runtime.gc()가 있지만 GC를 보장하지 않는다.
  >
  > : finalizer가 실행될 가능성을 높여줄 뿐 반드시 실행됨을 보장하지 않는다.

+ 힙에 새로운 객체를 생성할 메모리가 없다면 JVM은 OOM(Out Of Memory Error)를 던진다.

  > OOM : 애플리케이션이 대량의 메모리를 이용하여 시스템 메모리가 부족해지면, OS에 따라 앱은 강제 종료된다.

**자바에서 GC를 수동으로 수행할 수 있는 방법은 없다.**

#### GC 처리방식

1. Serial GC : 적은 메모리와 CPU 코어 갯수가 적을 때 적합하다.
2. Paraller GC : Serial GC와 알고리즘은 같지만 GC를 처리하는 스레드가 여러 개이다. 메모리와 코어가 충분할 때 적합하다.
3. Paraller Old GC : Paraller GC에서 Old GC 알고리즘을 개선한 버전이다.