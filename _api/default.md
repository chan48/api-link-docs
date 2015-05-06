## 기본 화면

#### 마커 목록 조회

> 서비스의 메인화면. 크게 `맵 영역`과 `포스트 영역`으로 나누어 진다. 현재 맵은 `Google Maps API` 를 사용하고 있다.

* <img align="center" src="../_img/GET.png"> : **/v1/markers**

* URL params : N/A

* Query params : `A안` (줌레벨, 위도-경도 경계값 사용)

|params       |type          |note       |
|:------------|:-------------|:----------|
|zoom         |number        |맵의 줌레벨|
|latitude_min |latitute.data |위도 최소값|
|latitude_max |latitute.data |위도 최대값|
|longitude_min|longitude.data|위도 최소값|
|longitude_max|longitude.data|위도 최대값|
|filter       |FILTER        |FILTER 참고|

* Query params : `B안` (줌레벨, 위도-경도 센터값)

|params       |type          |note       |
|:------------|:-------------|:----------|
|zoom         |number        |맵의 줌레벨|
|latitude_min |latitute.data |위도 최소값|
|latitude_max |latitute.data |위도 최대값|
|longitude_min|longitude.data|위도 최소값|
|longitude_max|longitude.data|위도 최대값|
|filter       |FILTER        |FILTER 참고|

<iframe src="../_json/filter.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:200px"></iframe>

* Request :

```
{
    "email" : "meinzug@me.com"    // 추후 오픈 API 활용을 위한 요청자 email
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" :
    {
        "marker_list" : [MARKER, MARKER, MARKER...], // MARKER 참고
        "posts"       : [POST, POST, POST...]        // POST 참고
    }
}
```

<iframe src="../_json/marker.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:200px"></iframe>
<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

## 포스트 상세 보기

* <img align="center" src="../_img/GET.png"> : **/v1/posts/{post-id}**

* URL params :

|params       |type          |note         |
|:------------|:-------------|:------------|
|post-id      |string        |포스트 아이디|
    
* Query params : N/A

* Request :

```
{
    "email" : "meinzug@me.com",
}
```

* Reply :

```
{
    "code" : "REPLY_OK",
    "msg"  : "Success",
    "data" : POST       // POST 참고
}
```

<iframe src="../_json/post.json" scrolling="no" style="border:1px #D8D8D8 solid; width:100%; height:350px"></iframe>

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*.json