# Docker & Docker-compose

Docker는 각각의 애플리케이션을 컨테이너라는 단위로 실행 환경을 분리하여 실행하고 관리하는 프로그램입니다. Docker를 사용하지 않으면, 한 컴퓨터에서는 동일한 환경변수의 이름을 사용할 수 없지만, 도커를 사용하면 컨테이너 당 컴퓨터를 사용하는 것 같은 효과를 주어, 다른 애플리케이션에서도 동일한 환경 변수의 이름을 사용할 수 있습니다.

Docker compose는 휴먼에러를 방지하고, 여러 컨테이너의 실행을 한 번에 효율적으로 관리 할 수 있도록 도와줍니다.

<br>

____

<br>

### Docker

+ 컨테이너 기술을 사용하여 훨씬 가볍고, 빠르며, 메모리를 훨씬 적게 차지한다.

  > 독립적인 실행환경을 보장하기 위해 도커를 사용하는 것이기 때문에, 하나의 컨테이너에는 하나의 이미지만 넣는다.

+ 도커 파일을 바탕으로 이미지를 빌드한다.

  > 도커 이미지 : 도커 컨테이너를 구성하는 파일 시스템과 실행할 애플리케이션 설정을 하나로 합친 것이다.

### Docker-compose

+ Dockerfile과 docker-compose.yml이 있을 때, 프로젝트의 루트 디렉토리에서 실행하면 된다.
+ 명령어를 일일이 입력하지 않고 간편하게 사용할 수 있다.
+ 여러 컨테이너의 생명 주기를 묶는 이유 : 예를 들어, 서버와 DB를 Docker를 사용하여 관리한다고 할 때, DB는 내렸는데 서버는 내리지 않는 경우, 휴먼에러가 발생 할 수 있다. 이런 경우 DB와 서버 컨테이너를 하나로 묶어 관리하면 간편하다.

```
docker-compose up -d --build [서비스명]
> docker-compose up : 여러 컨테이너 일괄 생성 및 실행
> -d : 백그라운드 실행
> --build : 이미지 새로 생성(Dockerfile 수정했을 경우) . 아마 이미지를 빌드하지 않으면 기존의 이미지를 사용하는 듯
> 서비스명 : 각 프로젝트 안에서 실행하는 경우 서비스명을 써주지 않아도 된다.

docker-compose down
> 일괄 서비스 종료
```

```
docker-compose ps
> 여러 컨테이너의 상태를 확인할 수 있다.
```

<br>

+ 환경 변수 파일은 `.env` 파일을 만들어 사용하면 된다. (`ls` 명령으로는 보이지 않는다.)