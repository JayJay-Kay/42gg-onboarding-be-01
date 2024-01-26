# 1주차 HTTP, DevTool, RestAPI

## 개발 환경 세팅

- IntelliJ
    - Java 개발툴
- MySQL
    - 가장 널리 사용되고 있는 관계형 데이터베이스 관리 시스템(RDBMS: Relational DBMS)
    - SQL: 관계형 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- redis 설치
    - Key, Value구조의 비정형 데이터를 저장 및 관리하기 위한 오픈 소스 기반의 비관계형 데이터 베이스 관리 시스템 (DBMS)
    - “캐시”로 이해하기?

## HTTP (HyperText Transfer Protocol)

- 텍스트 기반의 통신 규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜
    - 월드 와이드 웹의 토대
- 특징: 무상태성(Stateless) → 요청과 응답 이후, 이전 데이터 휘발됨
- 예시
    1. 웹 브라우저 주소창에 [naver.com](http://naver.com) 입력하고 enter 누름
    2. 웹 클라이언트와 웹 서버 사이에 HTTP연결이 맺어지고 웹 클라이언트는 웹 서버에 HTTP 요청 메세지를 보냄
    3. 웹 서버는 요청에 따른 처리 진행 후 그 결과를 웹 클라이언트에 HTTP 응답 메세지로 보냄
    4. 1~3번 반복으로 웹 사용이 가능해짐
    
    ![Untitled](1%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%20HTTP,%20DevTool,%20RestAPI%2031b5e43414714484abf0734eeffc998d/Untitled.png)
    

## HTTP Method

- 클라이언트와 서버 사이에 이루어지는 요청(Request)과 응답(Response) 데이터를 전송하는 방식
- 종류
    - 주요 메소드
        - GET: 리소스 조회
        - POST: 요청 데이터 처리 (예시: 등록)
        - PUT: 리소스 대체/덮어쓰기, 해당 리소스 없으면 생성
        - PATCH: 리소스 부분 변경 (PUT은 전체변경, PATCH는 일부 변경)
        - DELETE: 리소스 삭제
    - 기타 메소드
        - HEAD: GET과 비슷하지만 메세지 부분(body)제외하고 상태 줄과 헤더만 반환
            - 대충 크기 파악하고 싶을때 쓰는듯?
        - OPTIONS: 대상 리소스에 대한 통신 기능 옵션 설명
            - 주로 CORS(Cross-Origin Resource Sharing)에서 사용
        - CONNECT: 대상 자원으로 식별되는 서버에 대한 터널을 설정
        - TRACE: 대상 리소스에 대한 경로를 따라 메세지 루프백 테스트 수행
- 멱등성(idempotent)
    - 전산학, 수학 용어로 연산을 여러번 적용해도 결과가 달라지지 않는 성질, 연산을 여러번 반복하여도 한번만 수행된 것과 같은 성질을 의미

## HTTP status code (상태 코드 표)

- 서버의 처리 결과는 응답 메세지의 상태 라인에 있는 상태 코드(status code)를 보고 파악 가능
- 상태 코드는 세 자리 숫자로 구성
    - 첫번째 숫자는 HTTP 응답의 종류를 구분
    - 나머지 2개의 숫자는 세부적인 응답 내용 구분
- 현재 100~500번대까지 상태 코드가 정의되어 있으며 첫번째 자리 숫자에 따라 5가지로 분류
    - 1XX: Informational (정보 제공)
        - 임시 응답으로 현재 클라이언트의 요청까지는 처리되었으니 계속 진행하라는 의미
        - HTTP 1.1버전부터 추가됨
    - 2XX: Success (성공)
        - 클라이언트 요청이 서버에서 성공적으로 처리됨
    - 3XX: Redirection (리다이렉션)
        - 완전한 처리를 위해 추가 동작이 필요한 경우
        - 주로 서버의 주소 또는 요청한 URI의 웹 문서가 이동되었으니 그 주소로 다시 시도하라는 의미
    - 4XX: Client Error (클라이언트 에러)
        - 없는 페이지를 요청하는 등, 클라이언트의 요청 메세지 내용이 잘못된 경우를 의미
    - 5XX: Server Error (서버 에러)
        - 서버 사정으로 메세지 처리에 문제가 발생한 경우
        - 서버 부하, DB처리 과정 오류, 서버에서 익셉션이 발생한 경우

## HTTP 헤더

- 부가적인 정보 전송
- 대소문자를 구분하지 않고 이름과 콜론( : ) 다음에 오는 값으로 이루어짐
- context에 따라 분류
    - General Header
        - HTTP헤더 내 일반 헤더 항목
        - 요청 및 응답 메세지 모두에서 사용 가능한 기본적인 헤더 항목
    - Entity Header
        - HTTP헤더 내 엔티티/개체 헤더(Entity Header) 항목
        - 바디의 길이를 명시하는 헤더
        - 요청 및 응답 메세지 모두에서 사용 가능한 Entity(콘텐츠, 본문, 리소스 등)에 대한 설명 헤더 항목
    - Request Header
        - HTTP헤더 내 요청 헤더
        - 요청 헤더는 HTTP 요청 메세지 내에서만 나타나며 가장 방대함
    - Response Header
        - HTTP헤더 내 응답 헤더
        - 특정 유형의 HTTP요청이나 특정 HTTP헤더를 수신했을 때, 이에 응답함
    - Cash/Cookie Header
- 프록시 처리 방법에 따라 분류
    - 종단간 헤더
    - 홉간 헤더

## 개발자 도구 (DevTools)

- 개발자들이 홈페이지를 수정하고 발생한 문제의 원인을 쉽게 파악하기 위해 브라우저에서 제공하는 도구
- 개발자 도구 단축키
    - window: f12
    - mac: alt+cmd+i
- 개발자 도구 패널(DevTools panel)
    1. Elements Panel
        1. 개발자 도구의 기본탭
    2. Console Panel
        1. 컴퓨터의 키보드&마우스를 동작하기 위한 패널
        2. 여기서 자바스크립트 즉시 실행 가능
    3. Network Panel
        1. 웹사이트에서 통신하고 있는 모든 정보를 목록으로 보여줌
    4. Application Panel
        1. 브라우저 저장소
            1. Local Storage
            2. Session Storage
            3. Cookie

## Rest API

- Representational State Transfer
- 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것
    1. HTTP URI(Uniform Resource Identifier를 통해 자원/resource을 명시하고
    2. HTTP Method(POST, GET, PUT, DELETE, PATCH)등을 통해
    3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것
        1. CRUD = 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능 (Create, Read, Update, Delete)
        2. Create: 데이터 생성(POST)
        3. Read: 데이터 조회(GET)
        4. Update: 데이터 수정(PUT, PATCH)
        5. Delete: 데이터 삭제 (DELETE)
- Rest 구성 요소
    - Resource(자원)
        - 모든 자원에 고유한 ID가 존재하고, 이 자원은 서버에 존재함
    - Verb(자원에 대한 행위)
        - HTTP Method
    - Representation of Resource(장원에 대한 행위의 표현)
        - Client가 자원의 상태(정보)에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representation)을 보냄
        - REST에서 하나의 자원을 JSON, XML, TEXT, RSS등 여러 형태의 Representation으로 나타낼 수 있음
- Rest의 특징
    - Server-Client 구조
    - Stateless(무상태)
        - Client의 context를 server에 저장하지 않음
    - Cacheable(캐시 처리 가능)
        - 웹 표준 HTTP프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용 가능
    - Layered System (계층화)
        - Client는 REST API Server만 호출함
    - Uniform Interface(인터페이스 일관성)
        - URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행함
- REST의 장단점
    - 장점
        - HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API사용을 위한 별도 인프라 구축 불필요
        - HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능
        - REST API 메세지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악
    - 단점
        - 표준 자체가 존재하지 않아 정의가 필요
        - HTTP Method 형태가 제한적
            - 사용할 수 있는 메소드는 4가지
        - 구형 브라우저에서 호환 안됨(인터넷 익스플로러)
- API
    - Application Programming Interface
    - 다른 소프트웨어 시스템과 통신하기 위해 따라야 하는 규칙 정의
    - 클라이언트와 웹 리소스 사이의 게이트웨이
- REST API
    - REST기반으로 서비스 API 구현하는 것
    - 설계 규칙
        - URI는 정보의 자원을 표현(행위는 HTTP Method로)
        - /는 계층 관계를 나타냄
        - -는 URI가독성 높임
        - _는 사용안함
        - URI경로에는 소문자가 적합
        - 파일 확장자는 URI에 포함 안함
- RESTful
    - REST의 원리를 따르는 시스템
    - REST 아키텍어를 구현하는 웹 서비스를 나타내기 위해 사용되는 용어
    - REST API를 제공하는 웹 서비스 → RESTful함