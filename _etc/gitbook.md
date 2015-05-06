## gitbook 문서를 보는 방법

> 본 문서는 [마크다운](http://en.wikipedia.org/wiki/Markdown) 으로 작성된 문서이며, [GitBook](https://www.gitbook.com) 을 사용해 출판되었습니다. [마크다운](http://en.wikipedia.org/wiki/Markdown) 이나 [GitBook](https://www.gitbook.com) 에 대해 자세히 알고 싶다면 해당 링크 확인 바란다. 여기서는 간단한 사용법만 소개 하기로 한다.

#### 1단계 : 프로젝트 설치

> 터미널에서 다음 명령어로 프로젝트를 clone 한다.

```
$ git clone https://github.com/umanji/umanji-docs.git
```

#### 2단계 : gitbook 설치

> 다음 명령어로 gitbook 을 설치한다. 이미 설치가 되어 있다면 다음 단계로 넘어 간다.

```
$ npm install -g gitbook-cli
```

#### 3단계 : gitbook 빌드 및 실행

> 다음 명령어로 gitbook 문서를 빌드하고 실행한다.

```
$ gitbook build

$ gitbook serve
```

#### 4단계 : 문서 열람

> gitbook 기본 URL 을 통해 작성된 문서를 열람한다.

```
http://localhost:4000
```



-
*&copy; 2015 SIRIUS INFRA WORKS Inc. [meinzug@siw.com](mailto:meinzug@siw.com)*