## 개요

> 우만지 `server`, `client` 간 `request`, `reply` 스팩, 그리고 `payload` 스팩을 정의한다. 모든 우만지 open api 목록은 이곳에서 업데이트 된다. 참고로 이 문서의 API 목록 순서나 묶음 단위는 `화면단위` 를 우선 기준으로 삼았다. 그렇게 하는것이 개발의 편의성이나 문서 연관성 면에서 가장 적합하다고 생각했기 때문이다.

#### Reply Payload JSON 기본 형태

> 다음과 같은 기본 형태를 가지며, API 에 따라 `data` 내용이 달라진다.

```
{
    "code" : {string} // 상태 코드
    "msg"  : {string} // 상세 메시지
    "data" : {json}   // 응답 데이터, 요청에 따라 적절한 json 이 채워진다.
}
```

#### REST `CRUD` 범례

> API 설명에 사용된 CRUD 이미지는 다음과 같으며, 열쇠모양은 `인증필요` 를 의미한다.

* <img align="center" src="../_img/POST.png"> <img align="center" src="../_img/GET.png"> <img align="center" src="../_img/PUT.png"> <img align="center" src="../_img/DELETE.png">
* <img align="center" src="../_img/POST_auth.png"> <img align="center" src="../_img/GET_auth.png"> <img align="center" src="../_img/PUT_auth.png"> <img align="center" src="../_img/DELETE_auth.png">
* 모든 URL 은 버전으로 시작된다.

#### 이슈 사항

* 모바일 번호 입력시 혜택 논의 ?
* 가상의 주민번호 시스템 논의 (예, QQ, ICQ 스타일) ?
* 복수 역할이 있는 사람은 작성자 레벨과 직책을 어떻게 정할것인가 ?
* 복수개의 직책이 있다면 어떻게 선택 / 표현 할거냐 ?
* 기본화면에서 클라이언트 요청시 하드 필터 기능 (빌딩만, 스페이스만, 커뮤니티만 등등)

-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*