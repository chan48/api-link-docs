## json web token 개요

> 우만지는 `client` 인증에 `jwt` 를 사용하기로 했다. 이번 페이지에서는 `server` 와 `client` 간 Auth Control Flow 와 Session Control Flow 를 정리해 본다.

#### Sequence of Auth Control Flow

1. `client` : 로그인 시도
2. `server` : 정상 사용자 판단 (id, pw 등등)
3. `server` : `jwt` 생성, `jwt claim` 셋팅
4. `server` : `jwt` 를 `http header` 에 담아 응답

#### Sequence of Session Control Flow

1. `client` : 리소스 요청
2. `server` : 토큰 유효성 판단 및 세션 만료 판단
2. `server` : 세션 만료 경우, 토큰 재요청 하라는 메시지 response
3. `client` : 세션 만료 response 시, 클라이언트에서 토큰 재요청

#### Token Renewal Strategy

> 여러가지 전략이 가능하지만 세션 만료시 되로록 유저가 정보를 재입력하지 않도록 설계된다면 가장 좋을것 같다. 기본적으로는 다음과 같은 방법이 있을수 있고, 추후 수정 보완해 나가면 될 것 같다.

- 앱 설치시 마다 적절한 본인 인증 후 (`email otp link`, `sms 인증` 등), `secret token` 발급
- 발급 성공하면, 이 후 본인 인증시 `secret token` 이용
- 필요에 따라 적절한 본인 인증 후 `secret token` 재발급 가능
- 분실, 해킹등 예외상황의 경우도 `secret token` 재발급하여 사용
- 기본적으로 [https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section-4.1](https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section-4.1) 기술대로 동작하도록 충실히(?) 구현

#### JWT 보안 사항

> `jwt header` `jwt body(claim)` 는 단지 Base64 Encode 결과물 이기 때문에, 누구나 claim 부분을 Base64 Decode 하여 볼 수 있다는 특징이 있다. 따라서 별도의 암호화 과정을 거치지 않을거라면 노출되도 무방한 데이터만 담아야 한다. 혹은 중요한 데이터를 담기 위해서는 https 를 사용하든지 `jwe` 를 사용 해야만 안전하다. 기본적으로 `token` 으로써 충실히 사용하고 지나치게 많은 역할로 활용하지는 말자. 무엇이든 *Silver Bullet* 은 없는 법 이니깐. 
`jwe` 를 사용하려면 `jwt header` 의 `cty` 값을 "JWE" 로 넣은 후 `claim` 부분을 `jwe spec` 에 맞게 생성해야 한다.

#### JWT Claim Registered Names 참고

> 구체적인 JWT 전체 스팩은 [https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32](https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32) 을 참고한다. 여기서는 claim 부분만을 언급한다.

* `iss` : Issuer Claim (OPTIONAL) : ***StringOrURI*** <p>
서비스가 여러 서버로 구성된 경우, 토큰 발행자를 구분하는데 사용될 수 있다. 혹은 리소스 요청자를 `application` 단위로 구분하는데 사용할 수도 있겠다. 예를 들어 우만지 API 를 활용하는 여러 클론앱이나 서비스들이 있을 수 있는데, 이때 앱이나 서비스 마다 `token` 으로 구분하여 사용토록 한다면, 이 필드에 특정 문자열을 넣어 활용할 수 있다.

* `sub` : Subject Claim (OPTIONAL) : ***Globally Unique StringOrURI*** <p>
일종의 토큰 타입으로 활용 할 수 있겠다. 예를들어 어떤 토큰은 일시적으로 사용되며 지정된 시간 동안만 유효하고 갱신없이 강제 만료되는 경우가 있을 수 있고, 어떤 토큰은 예약된 시간에 활성화 되는 등의 특수 동작을 하는 토큰이 있을 수 있다. 서비스 운영 정책에 따라 여러가지 라이프 사이클을 가질수도 있다. 이런식으로 토큰 타입 분류자로 사용될 수 있다.

* `aud` : Audience Claim (OPTIONAL) : ***Globally Unique StringOrURI*** <p>
토큰 사용자 그룹으로 활용 가능. 예를 들어 어떤 토큰은 어떤 그룹에게만 허용될 수 있다. 그 그룹이라는것이 어떤 사용자군을 의미하기도 하지만, 사용하도록 허락받은(?) 서드파티를 구분 짓는 용도로 활용 될수도 있다.

* `exp` : Expiration Time  Claim (OPTIONAL) : ***NumericDate*** <p>
토큰의 유효기간을 기록한다. 유효기간 이후에는 절대 사용되도록 해선 안되며, 반드시 `date/time` 이 기록되야 한다. 그런데 스펙에선 구체적으로 `date/time` 이라는 녀석의 모양새를 정의 하지는 않았다. 그냥 `application` 에서 알아서 사용하면 될 듯.

* `nbf` : Not Before  Claim (OPTIONAL) : ***NumericDate*** <p>
토큰 활성화 예정 시각을 지정할 수 있다. 다시 말해 이 `date/time` 이전의 토큰은 무효하게 동작하고, 이 시각 이후에는 유효하게 만들어야 할 때 사용한다. 당장 떠오르진 않지만, 나중에 이런 케이스가 발생 할지도 모르니 알고 있자.

* `iat` : Issued At Claim (OPTIONAL) : ***NumericDate*** <p>
토큰 발행 시각을 기록한다. `time stamp` 역할. 이 값으로 `token` 나이를 계산할 수 있다.

- `jti` : JWT ID (OPTIONAL) : ***Unique ID String*** <p>
`Unique ID Sgtring` 으로 기술한 녀석의 구체적 모양새는 정의되지 않았지만, 발급된 토큰이 재사용 되어서는 안된다든지, 유일한 구분자를 넣어 순서가 중요한 동작을 수행할때 순서를 지키도록 한다든지 목적으로 활용 가능하다. 예를 들어 원자성 중요하고, 반복이나 내부적으로 재동작 되어선 안되고, 동작의 순서가 중요한 트랜젝션이 있다고 할 때, 잘~ 활용하면 되겠다.

- `any payload` : ***Any JSON Type***<p>
위에 기술한 [https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section-4.1](https://tools.ietf.org/html/draft-ietf-oauth-json-web-token-32#section-4.1) 에 예약된 이름만 피한다면, 임의로 `json type parameters` 를 만들어 쓸 수 있다. 하지만 앞서 이야기 했듯 너무 많은 역할을 수행하도록 만들지는 말자. `token` 은 `token` 일뿐, *Silver Bullet* 욕심을 경계하자.


-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*