## 맴버

#### 맴버 추가

* <img align="center" src="../_img/POST_auth.png"> : **/v1/members/at/{parent-site-id}**

* URL params :

|params        |type          |note              |
|:-------------|:-------------|:-----------------|
|parent-site-id|string        |부모 사이트 아이디|

* Query params : N/A

* Request :

```
{
    "email"  : "meinzug@me.com",
    "member" : MEMBER               // MEMBER 참고
}
```

<iframe src="../_json/member.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:170px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

#### 맴버 목록 조회

* <img align="center" src="../_img/GET.png"> : **/v1/members/at/{parent-site-id}**

* URL params :

|params        |type          |note              |
|:-------------|:-------------|:-----------------|
|parent-site-id|string        |부모 사이트 아이디|

* Query params : N/A

* Request :

```
{
    "email" : "meinzug@me.com"
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" :
    {
        "site_id" : "kd9dd0fw-ek2b-fk34-fl39-fj49dpf98393"  // 사이트 아이디
        "members" : [MEMBER, MEMBER, MEMBER...]             // MEMBER 참고
    }
}
```

<iframe src="../_json/member.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:170px"></iframe>

#### 맴버 삭제

> 빌딩 삭제시 삭제 프로세스 논의 필요.

* <img align="center" src="../_img/DELETE_auth.png"> : **/v1/members/{member-id}**

* URL params :

|params   |type     |note       |
|:--------|:--------|:----------|
|member-id|string   |맴버 아이디|

* Query params : N/A

* Request : 

```
{
    "email" : "meinzug@me.com"
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*