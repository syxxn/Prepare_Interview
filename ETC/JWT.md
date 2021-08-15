# JWT

JWT는 Json Web Token의 줄임말로, 토큰의 타입과 알고리즘 방식을 저장하는 Header, 토큰에서 사용할 정보들(클레임)을 담고 있는 Payload, 토큰을 암호화하거나 유효성 검증을 할 때 사용하는 Signature로 나누어 지고, 각 파트는 점으로 구분합니다. JWT는 보통 access token과 refresh token으로 나누어 사용합니다. 생성된 토큰은 HTTP 통신을 할 때 Authorization이라는 key의 value로 사용하는데, access token의 경우 앞에 Bearer이 붙습니다.

<br>

____

<br>

```json
{ //HEADER
	"alg": "HS256", //Signature 부분에서 사용한다.
    "typ": "access_token"
}

{ //PAYLOAD
    "sub": "1", //보통 entity의 id값으로 정함. user를 구분할 수 있는 값
    "exp": 1628382445, //expiration
    "iat": 1628172165, //issued at
}

//SIGNATURE
HMACSHA256(
    base64UrlEncode(header) + "." + base64UrlEncode(payload), secretKey
)
//위의 것은 JWS(Json Web Signature)의 구조이며, 각각의 대해 Base64로 인코딩하고 .으로 구분하면 JWT가 된다.

(Header).(Payload).(Signature)
eyJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjgzODI1MDAsImlhdCI6MTYyODE3.fXoJ5dNFkT6Ab83jgKxqYtXBo-FhXc-Pr 
```

+ 회원 인증/인가, 정보교류 등과 같은 상황에서 JWT를 사용한다.
+ Payload는 등록된 클레임(sub, exp, iat ...), 공개 클레임("https://github.com/syxxn/is_admin" : true), 비공개 클레임("username": "syxxn")로 구성할 수 있다.
+ 각 파트의 key값은 3글자로 하는것이 관례적이다.
+ Signature는 Header의 인코딩 값과 Payload의 인코딩 값을 합친후 주어진 secret key로 해쉬를 하여 생성한다. 

<br>

+ JWT 사용을 권장하는 이유
  + URL 파라미터와 헤더로 사용할 수 있다.
  + 독립적이다.
  + 만료시간이 내장되어 있다.
  + 트래픽에 대한 부담이 낮다.
  + 토큰 자체에 사용자 인증에 대한 정보가 들어 있어 별도의 인증 저장소가 필요 없다.
+ JWT 단점
  + 토큰은 클라이언트에 저장되어, 데이터베이스에서 사용자 정보가 수정된 경우 토큰에 직접 적용할 수 없다.
  + 더 많은 필드가 추가되면 토큰이 길어진다.