# Spring에서 CORS 해결하는 법

CORS(Cross-Origin Resource Sharing)란 서로 다른 도메인끼리 정보를 주고 받을 수 있도록 하는 것입니다.

Spring에서는 컨트롤러마다 @CrossOrigin 어노테이션을 붙이거나, 프로그램 전체 configure에서 addCorsMappings를 오버라이드 하는 방법이 있습니다.

<br>

____

<br>

+ 여기서 말하는 출처란 도메인(naver.com) 정도로 생각하면 된다.

+ 브라우저에서 다른 출처의 리소스 요청을 제한하는 정책으로 CORS와 SOP(Same Origin Policy)가 존재한다.

  SOP는 '같은 출처에서만 리소스를 공유할 수 있다'라는 규칙을 가진 정책이고, 몇 가지 예외 사항을 둔 것을 CORS라고 한다.

+ 기본적으로 브라우저는 cross-origin 요청을 전송하기 전에 OPTIONS 메소드로 preflight(사전 전달)를 전송한다. CORS가 허용된 웹서버라면 사용 가능한 리소스(어떤 origin과 어떤 method를 사용하는지)를 헤더에 담아 응답한다.

  만약 허용되지 않은 웹서버라면 CORS error를 보내는 것이다.



1. 컨트롤러 마다 @CrossOrigin을 붙이는 방법

   ```java
   @CrossOrigin
   @RestController
   public class PostController {
   }
   
   @CrossOrigin
   @RestController
   public class UserController {
   }
   ```

2. 전체 Configure에서 메소드 오버라이드 하는 방법

   ```java
   @Configuration
   public class SecurityConfig implements WebMvcConfigurer {
       
       @Override
       public void addCorsMappings(CorsRegistry registry) {
           registry.addMapping("/**")
                   .allowedOrigins("*")
                   .allowedMethods("*");
       }
   
   }
   ```

   