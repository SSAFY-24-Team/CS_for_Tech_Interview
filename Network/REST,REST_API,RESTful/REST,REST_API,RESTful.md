# REST, REST API, RESTful

# REST

### 배경

- 효율적이고 확장 가능한 통신을 위한 표준 제공

### 개념

- REpresentational State Transfer의 약자
- 자원을 이름(자원의 표현)으로 구분해 해당 자원의 상태(정보)를 주고 받는 모든 것
- 자원(resource)의 표현(representation)에 의한 상태(state) 전달(transfer)
    - 자원: 해당 소프트웨어가 관리하는 모든 것
- 하이퍼미디어 기반 분산 시스템(WEB)을 구축하기 위한 소프트웨어 개발 아키텍처
- 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나
- HTTP URI(Uniform Resource Identifier)를 통해 자원을 명시하고, HTTP Method(Post, Get, Put, Delete)를 통해 해당 자원에 대한 CRUD Operation을 적용
    - 자원 기반의 구조(ROA) 설계 중심에 Resource가 있고 HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍처
    - 모든 자원에 고유한 ID인 HTTP URI 부여
    - CRUD Operation
        - Create: 생성(Post)
        - Read: 조회(Get)
        - Update: 수정(Put)
        - Delete: 삭제(DELETE)
        - HEAD: header 정보 조회(HEAD)

### REST 구성 요소

- 자원(Resource): URI
    - Server에 존재하는 모든 자원은 고유한 ID가 존재
    - 자원을 구별하는 ID는 ‘/groups/:group_id’와 같은 HTTP URI
    - Client는 URI를 이용해 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청
- 행위(Verb): HTTP Method
    - HTTP 프로토콜의 GET, POST, PUT, DELETE 메서드를 사용
- 표현(Representation of Resource)
    - Client와 Server의 데이터를 주고받는 표현 방법
    - JSON, XML, RSS, TEXT 등의 여러 형태로 표현

### 특징

- Server-Client 구조
    - REST Server: API를 제공하고 비즈니스 로직 처리 및 저장
    - Client: 사용자 인증이나 context등을 직접 관리하고 책임
    - 역할 구분으로 인해 의존성이 줄어든다.
- Stateless(무상태)
    - HTTP 프로토콜은 Stateless Protocol로 REST 역시 무상태성을 갖음
    - Server는 각각의 요청을 별개로 인식하고 처리
    - Client의 context를 Server에 저장하지 않는다.
- Cacheable(캐싱 기능)
    - HTTP 프로토콜의 강력한 특징인 캐싱 기능 적용
    - Last-Modified 태그나 E-Tag를 이용해 캐싱 구현
- Layered System(계층화)
    - Client는 REST Server만 호출
    - REST Server는 다중 계층으로 구성
        - API Server는 순수 비즈니스 로직 수행
        - 앞단에는 보안, 로드밸런싱, 암호화, 사용자 인증 등을 추가
    - PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체 사용 가능
    - 구조상의 유연성을 가짐
- Uniform Interface(인터페이스 일관성)
    - URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행
    - HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용 가능

### 장단점

- 장점
    - HTTP 프로토콜의 인프라와 표준을 활용
    - Hypermedia API의 기본을 충실히 지키면서 범용성 보장
    - REST API 메시지로 명확하게 의도를 파악
    - 서버와 클라이언트의 역할 분리
- 단점
    - 표준이 존재하지 않는다.
    - 메서드가 제한적이다.
    - 구형 브라우저가 제대로 지원해주지 못하는 부분이 있다.

# REST API

![image.png](/img/REST,REST_API,RESTful/0.png)

### 개념

- REST 기반으로 서비스 API를 구현한 것

### 특징

- REST 기반으로 시스템을 분산해 확장성과 재사용을 높여 유지보수 및 운용을 편리하게 할 수 있다.
- HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현할 수 있다.

### 설계 기본 규칙

![image.png](/img/REST,REST_API,RESTful/1.png)

- 슬래시(/)는 계층 관계를 나타내는데 사용한다.
- URI는 정보의 자원을 표현해야 한다.
    - 도큐먼트 : 객체 인스턴스나 데이터베이스 레코드와 유사한 개념
    - 컬렉션 : 서버에서 관리하는 디렉터리라는 리소스
    - 스토어 : 클라이언트에서 관리하는 리소스 저장소
    - 도큐먼트 이름은 단수 명사로 사용하고, 컬렉션과 스토어의 이름은 복수 명사로 사용한다.
    - 동사보다는 명사를 사용한다.
- 자원에 대한 행위는 URI에 포함하지 않고, HTTP Method를 사용해 표현한다.
- Control Resource의 경우 동사 형태를 허용한다.
    - HTTP Method로 표현되는 행위가 아닌 다른 행위를 표현하는 경우 동사 형태로 허용
- URI 마지막 문자로 슬래시(/)를 포함하지 않는다.
    - URI에 포함되는 모든 글자는 리소스의 유일한 식별자로 사용되어야한다.
    - 분명한 URI를 만들어 통신하기 위해 혼동을 주지 않기 위함.
- 밑줄(_)을 사용하지 않고 하이픈(-)을 사용한다.
    - 긴 URI를 사용하게 될 경우 가독성을 높인다.
- URI는 소문자로만 구성한다.
    - RFC 3986(URI 문법형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정
- 응답에는 HTTP 상태코드를 사용한다.
    - 1xx : 전송 프로토콜 수준의 정보 교환
    - 2xx : 클라어인트 요청이 성공적으로 수행됨
    - 3xx : 클라이언트는 요청을 완료하기 위해 추가적인 행동을 취해야 함
    - 4xx : 클라이언트의 잘못된 요청
    - 5xx : 서버 오류로 인한 상태코드
- 파일확장자는 URI에 포함하지 않는다.
    - Accept header를 사용한다.

# RESTful

### 개념

- REST라는 아키텍처를 구현하는 웹 서비스를 나타내기 위한 용어
- REST 원칙을 준수하여 설계된 API

# 예제 질문

<details>
   <summary>REST API의 특징은?</summary>
HTTP 프로토콜의 특징을 따라서 캐싱 기능과 무상태성이라는 특징을 가지고 있다.
또한, 클라이언트-서버 구조를 가지며 계층적으로 구성되어 있다.

    
<br />
</details>   

> 참고자료
> 

[https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)
<br>
[https://tech.trenbe.com/2022/01/16/rest-api.html](https://tech.trenbe.com/2022/01/16/rest-api.html)
<br>
[https://devoong2.tistory.com/entry/REST-API-REST-RESTful-API-란](https://devoong2.tistory.com/entry/REST-API-REST-RESTful-API-%EB%9E%80)