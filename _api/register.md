## 회원가입

> 이메일을 기본 아이디로 하며, 추후 가상의 주민번호의 쓰임새와 유사한 일련번호 부여도 고려해 볼만하다. 가입시 이메일 인증 절차가 있으며, 패스워드 분실시 새로운 패스워드를 발급하는 용도 등으로 사용된다.

#### 회원가입

* <img align="center" src="../_img/POST.png"> : **/v1/auth/register**

* URL params : N/A

* Query params : N/A

* Request :

```
{
    "email"    : "meinzug@me.com", // 호출자 아이디
    "password" : "secret1234",     // 패스워드 (암호화 필요)
    "name"     : "John Smith"      // 사용자 이름
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",    // 추후 각 reply 마다 상세 업데이트 필요
    "data" : USER          // USER 참고
}
```

<iframe src="../_json/user.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:160px"></iframe>

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*