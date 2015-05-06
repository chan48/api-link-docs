## 사이트 (그룹, 빌딩, 스페이스, 커뮤니티)

#### 사이트 조회

* <img align="center" src="../_img/GET.png"> : **/v1/sites/{site-id}**

* URL params :

|params       |type          |note         |
|:------------|:-------------|:------------|
|site-id      |string        |사이트 아이디|

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
    "data" : SITE           // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 사이트 목록 조회

* <img align="center" src="../_img/GET.png"> : **/v1/sites/at/{parent-site-id}**

* URL params :

|params          |type          |note         |
|:---------------|:-------------|:------------|
|parent-site-id  |string        |사이트 아이디|

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
    "data" : [SITE, SITE, SITE...]           // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 소유 사이트 조회

* <img align="center" src="../_img/GET.png"> : **/v1/sites?user=18jh983jd02jd/**

* URL params : N/A

* Query params :

|params       |type          |note         |
|:------------|:-------------|:------------|
|user         |string        |사용자 아이디|

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
    "data" : [SITE, SITE, SITE...]           // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

#### 참여 사이트 조회

* <img align="center" src="../_img/DELETE_auth.png"> : **/v1/sites/user=abcxyz&involved=true**

* URL params : N/A

* Query params :

|params    |type          |note         |
|:---------|:-------------|:------------|
|user      |string        |사용자 아이디|
|involved  |bool          |참여 여부    |

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
    "data" : [SITE, SITE, SITE...]    // SITE 참고
}
```

<iframe src="../_json/site.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:280px"></iframe>

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*