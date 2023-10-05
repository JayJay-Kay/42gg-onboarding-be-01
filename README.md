## 42gg-onboarding-be-01

### 개발 환경 세팅

- IDE는 IntelliJ 사용
- IntelliJ Community 버전에서 Ultimate 버전 업그레이드 하기 (학생 라이센스 신청)
    - Email address : 대학 재학생 혹은 졸업생일 경우 학교 이메일 또는 42계정 이메일(”intraId”@student.42seoul.kr) 사용 가능
    https://goddaehee.tistory.com/215
- MySQL 설치
    - DataGrip 추천
     https://luminitworld.tistory.com/82
- redis 설치
    - macOS https://herojoon-dev.tistory.com/170
    - windows [https://inpa.tistory.com/entry/REDIS-📚-Window10-환경에-Redis-설치하기](https://inpa.tistory.com/entry/REDIS-%F0%9F%93%9A-Window10-%ED%99%98%EA%B2%BD%EC%97%90-Redis-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)

### EX00 간단한 이론 공부

- **HTTP METHOD** [https://inpa.tistory.com/entry/WEB-🌐-HTTP-메서드-종류-통신-과정-💯-총정리](https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-HTTP-%EB%A9%94%EC%84%9C%EB%93%9C-%EC%A2%85%EB%A5%98-%ED%86%B5%EC%8B%A0-%EA%B3%BC%EC%A0%95-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC)
- **HTTP Status Code** [https://hongong.hanbit.co.kr/http-상태-코드-표-1xx-5xx-전체-요약-정리/](https://hongong.hanbit.co.kr/http-%EC%83%81%ED%83%9C-%EC%BD%94%EB%93%9C-%ED%91%9C-1xx-5xx-%EC%A0%84%EC%B2%B4-%EC%9A%94%EC%95%BD-%EC%A0%95%EB%A6%AC/)
- **HTTP 헤더** https://gmlwjd9405.github.io/2019/01/28/http-header-types.html
- **크롬 개발자도구 (Network, Application 위주로)** [https://velog.io/@remon/개발자-도구의-기능을-뜯어보자](https://velog.io/@remon/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%8F%84%EA%B5%AC%EC%9D%98-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EB%9C%AF%EC%96%B4%EB%B3%B4%EC%9E%90)
- **REST API** 란 무엇인가?
- 쿠키와 세션, JWT토큰
- MVC, MVC2
- 인증, 인가의 차이
- 심화
    - java 리플렉션 이란?
    - synchronized 키워드의 역할
    - DB Lock 은 무엇인가
    - Nginx, Docker
    - HashMap
        - equals(), hashcode()
- 인프라
    - HTTPS
    - DNS 서버
    - CI/CD

### EX01 컨벤션 정하기

git / github / code 컨벤션은 42gg notion에 있는 자료를 적극 반영합니다.

[3기 코딩 스타일 정리](https://www.notion.so/3-8604532f14ab4ad7a214e95735f79dbd?pvs=21)

### EX02 역할 분담

- 팀장 _ jira
- 스크럼 마스터 _ 노션 스크럼 진행

### EX02 DB 커넥션 설정

yml 파일 이용해 db커넥션 설정 후 확인
