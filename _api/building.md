## 빌딩

> 모든 객체 (`빌딩`, `스페이스`, `커뮤니티`, `맴버`, `포스트` 등등) 에 대해 CRUD 순으로  기술 하였다.

#### 빌딩 생성

> 기본적으로 `생성`, `수정` 로직은 인증을 필요로 한다. 빌딩, 스페이스, 커뮤니티, 그룹 등의 키워드 생성 로직에 대해 논의가 필요하다. 어느 정도까지 일괄 입력 가능? 수동입력? 자동생성? 

* <img align="center" src="../_img/POST_auth.png"> : **/v1/buildings**

* URL params : N/A

* Query params : N/A

* Request :

```
{
    "email"    : "meinzug@me.com",
    "building" : BUILDING,                  // SITE 참고
    "spaces"   : [SPACE, SPACE, SPACE...]   // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

#### 빌딩 조회

* <img align="center" src="../_img/GET.png"> : **/v1/buildings/{site-id}**

* URL params :

|params       |type          |note       |
|:------------|:-------------|:----------|
|site-id      |string        |빌딩 아이디|

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
    "data" : BUILDING            // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 빌딩 수정

> `building` 의 모든 항목을 수정할 수 있으며, 수정한 항목만 기술할 수 있다.

* <img align="center" src="../_img/PUT_auth.png"> : **/v1/buildings/{site-id}**

* URL params :
    
    |params       |type          |note       |
    |:------------|:-------------|:----------|
    |site-id      |string        |빌딩 아이디|

* Query params : N/A

* Request : 

```
{
    "email"    : "meinzug@me.com",
    "building" : BUILDING    // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" : BUILDING    // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 빌딩 삭제

> 빌딩 삭제시 삭제 프로세스 논의 필요.

* <img align="center" src="../_img/DELETE_auth.png"> : **/v1/buildings/{site-id}**

* URL params : 

|params       |type          |note       |
|:------------|:-------------|:----------|
|site-id      |string        |빌딩 아이디|

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