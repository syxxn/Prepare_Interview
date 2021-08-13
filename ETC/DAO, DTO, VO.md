# DAO, DTO, VO

DAO(Data Access Object)는 Repository, Entity 처럼 데이터베이스의 데이터에 직접 접근하기 위한 객체를 말합니다.

DTO(Data Transfer Object)는 계층 간의 데이터 교환을 위한 객체로서, 로직 없이 geter와 setter만 가지고 있습니다.

VO는 불변의 값을 가지고 있어 중간에 값을 바꿀 수 없다는 특징이 있습니다. (읽기 전용 DTO)

<br>

____

<br>

+ DAO는 비즈니스 로직과 데이터 접근 로직을 분리하기 위해 사용한다. DB를 사용해 데이터를 CRUD하는 기능을 담당한다.
+ DTO는 Controller, Service, Client 등 계층 간의 데이터 교환을 위해 사용하는 객체이다. DTO의 값을 변경해도 실제 데이터의 값은 변하지 않는다.
+ VO는 DTO와 혼용해서 쓰이지만, setter가 없어 값을 한번 설정하면 바꿀 수 없다.