## 로그인 / 로그아웃

> 클라이언트는 `email`, `password` 등 사용자 식별 정보를 전송하고, 서버는 인증 성공시 `HTTP HEADER` 에 `TOKEN` 을 담아 응답한다. 보안 혹은 개발 편의를 위해, `request` 시 `email`, `password` 전달은 `secret token` 으로 대체할 수도 있다.

#### 로그인

> 사용자가 자격증명시 단순 `email`, `password` 를 사용할 수 있지만, 자동 로그인 같은 편의 기능을 위해선 단말에 사용자 식별 정보를 저장 해야만 한다. 이때 여러 전략이 가능하다. `password` 부분만 암호화를 하여 저장 할 수도 있고, `email` 과 `password` 문자열을 시드로 하는 `SECRET TOKEN` 을 만들어 사용할 수도 있다.

* <img align="center" src="../_img/POST.png"> : **/v1/auth/login**

* URL params : N/A

* Query params : N/A

* Request :

```
// secret token 미사용 경우
{
    "email"    : "meinzug@me.com",
    "password" : "20fj39fh387dgs"    // 암호화된 패스워드 문자열
}
```
```
// secret token 사용 경우
{
    "secret_token" : "dkj39fhj38fghfrhw83tyrbdf82" // 암호화된 id/pw 문자열
}
```

* Reply : `JWT` 세부내용은 [json web token](../_etc/jwt.md) 참고

```
// header
"Authorization" : "Bearer 032idkwyd.sk30fjfm2f.fm3w3gjfw3g" // JWT
```

```
// payload
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" :
    {
        "token": "032idkwyd.sk30fjfm2f.fm3w3gjfw3g",    // JWT String
        "user" : USER                                   // USER 참고
    }
}
```



#### 로그아웃

> 로그아웃을 하면 즉시 해당 토큰은 무효화 처리가 된다. 이를 위해 서버측은 `JWT 스펙` 에 추가적인로 로그아웃 전략을 구현하여야 한다. 로그인과 마찬가지로 로그아웃도  `secret_token` 을 사용할 수 있다. (논의 필요)

* <img align="center" src="../_img/POST_auth.png"> : **/v1/auth/logout**

* URL params : N/A

* Query params : N/A

* Request :

```
// secret token 미사용 경우
{
    "email"    : "meinzug@me.com",
    "password" : "secret1234"       // 암호화된 패스워드 문자열
}
```
```
// secret token 사용 경우
{
    "secret_token" : "fj30fj2fmgn34058dn30tu3mf2f03" // 암호화된 TOKEN String
}
```

* Reply :

```
// payload :
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*