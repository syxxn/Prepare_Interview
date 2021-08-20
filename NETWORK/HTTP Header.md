# HTTP Header

HTTP 메시지는 시작줄과 헤더, 본문으로 구성됩니다. 그 중 헤더는 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있도록 해줍니다. 헤더는 대소문자를 구분하지 않는 key와 value로 이루어져있습니다. 요청 헤더는 메시지의 컨텐츠와는 관련이 없으며, Host, User-Agent, Authorization 등이 있습니다. 응답 헤더에는 Age, Location 또는 Server 등이 있고, 이는 더 상세한 응답의 컨텍스트를 제공하기 위해 사용됩니다.

<br>

____

<br>

+ 헤더는 최종 수신자에게 전송되어야 하는 최종 수신자(요청에서는 서버, 응답에서는 클라이언트)에게 전송되어야 하는 종단간 헤더와 재전송되거나 캐시되어서는 안되는 홉간 헤더가 있다.

  > 홉간 헤더 : Connection, Keep-Alive ...

```http
GET http://localhost:8080/hello HTTP/2 

Host : localhost:8080 
User-Agent: insomnia/7.1.1
Content-Type: application/json
Authorization : Bearer asdf.asdf.asdf

{
	"message":"hello"
}
```

+ Host : 서버의 도메인명과 TCP 포트번호를 명시한다.
+ Content-Type : 리소스의 미디어 타입을 나타낸다.
+ Authorization : 유저를 증명하기 위해 사용한다.

