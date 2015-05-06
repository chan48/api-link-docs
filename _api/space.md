## 스페이스

#### 스페이스 생성

* <img align="center" src="../_img/POST_auth.png"> : **/v1/spaces/at/{parent-site-id}**

* URL params : 

|params        |type          |note            |
|:-------------|:-------------|:---------------|
|parent-site-id|string        |부모 빌딩 아이디|

* Query params : N/A

* Request :

```
{
    "email" : "meinzug@me.com",
    "space" : SPACE             // SITE 참고
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

#### 스페이스 조회

* <img align="center" src="../_img/GET.png"> : **/v1/spaces/{site-id}**

* URL params :

|params |type  |note           |
|:------|:-----|:--------------|
|site-id|string|스페이스 아이디|

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
    "data" : SPACE       // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 스페이스 목록 조회

> `스페이스 조회` 의 `payload` 가 배열에 담겨 반환 된다.

* <img align="center" src="../_img/GET.png"> : **/v1/spaces/at/{parent-site-id}**

* URL params :

|params        |type          |note            |
|:-------------|:-------------|:---------------|
|parent-site-id|string        |부모 빌딩 아이디|

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
    "data" : [SPACE, SPACE, SPACE...]    // SPACE 참고
}
```

#### 스페이스 수정

> `space` 의 모든 항목을 수정할 수 있으며, 수정한 항목만 기술할 수 있다.

* <img align="center" src="../_img/PUT_auth.png"> : **/v1/spaces/{site-id}**

* URL params :

    |params        |type          |note            |
    |:-------------|:-------------|:---------------|
    |site-id       |string        |스페이스 아이디 |

* Query params : N/A

* Request : 

```
{
    "email" : "meinzug@me.com",
    "space" : SPACE       // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" : SPACE       // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 스페이스 삭제

> 스페이스 삭제 프로세스 논의 필요.

* <img align="center" src="../_img/DELETE_auth.png"> : **/v1/spaces/{site-id}**

* URL params :

|params        |type          |note           |
|:-------------|:-------------|:--------------|
|site-id       |string        |스페이스 아이디|

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