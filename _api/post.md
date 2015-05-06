## 포스트

> 포스트 할 수 있는 컨텐츠는 `동영상`, `이미지`, `텍스트`, `사운드` 등이 있을 수 있다. 세부적인 컨텐츠 타입은 `MIME-Type` 정의를 따른다.

#### 포스트 생성 : 사이트에 포스팅

* <img align="center" src="../_img/POST_auth.png"> : **/v1/posts/at/{site-id}**

* URL params :

|params        |type          |note                   |
|:-------------|:-------------|:----------------------|
|site-id       |string        |포스팅 할 사이트 아이디|

* Query params : N/A

* Request :

```
{
    "email"     : "meinzug@me.com",
    "post"      : POST                // 포스트 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

#### 포스트 생성 : 맵에 포스팅

> `URL parameter` 에 직접 `위도`, `경도` 를 입력할 수 있다.

* <img align="center" src="../_img/POST_auth.png"> : **/v1/posts?lat=123.123456&long=123.123456/**

* URL params : N/A

* Query params :

|params        |type          |note           |
|:-------------|:-------------|:--------------|
|latitude      |string        |위도           |
|longitude     |string        |경도           |

* Request :

```
{
    "email" : "meinzug@me.com",
    "post"  : "POST"                 // 포스트 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

*  Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success"
}
```

#### 포스트 조회

* <img align="center" src="../_img/GET.png"> : **/v1/posts/{post-id}**

* URL params :

|params      |type     |note           |
|:-----------|:--------|:--------------|
|post-id     |string   |포스트 아이디  |

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
    "data" : POST        // POST 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

#### 포스트 목록 조회

* <img align="center" src="../_img/GET.png"> : **/v1/posts/at/{site-id}**

* URL params :

|params      |type     |note                            |
|:-----------|:--------|:-------------------------------|
|site-id     |string   |포스트 목록을 얻을 사이트 아이디|

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
    "data" : [POST, POST, POST...]        // POST 참고
}
```

    <iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

#### 포스트 수정

* <img align="center" src="../_img/PUT_auth.png"> : **/v1/posts/{post-id}**

* URL params :

|params      |type     |note           |
|:-----------|:--------|:--------------|
|post-id     |string   |포스트 아이디  |

* Query params : N/A

* Request :

```
{
    "email" : "meinzug@me.com",
    "post"  : POST              // POST 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" : POST        // POST 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

#### 포스트 삭제

* <img align="center" src="../_img/DELETE_auth.png"> : **/v1/posts/{post-id}**

* URL params :

|params      |type     |note           |
|:-----------|:--------|:--------------|
|post-id     |string   |포스트 아이디  |

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

#### 나의 포스트

* <img align="center" src="../_img/GET_auth.png"> : **/v1/posts?user=1ifm3l03jt9dk2f3g**

* URL params : N/A

* Query params :

|params      |type     |note         |
|:-----------|:--------|:------------|
|user        |string   |맴버 아이디  |
 
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
    "data" : [POST, POST, POST...]   // POST 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*
