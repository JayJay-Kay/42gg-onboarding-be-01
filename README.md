# 42gg-onboarding-be-01

### 개발 환경 세팅

- IDE는 IntelliJ 추천
- IntelliJ Community 버전에서 Ultimate 버전 업그레이드 하기 (학생 라이센스 신청)
    
     Email address : 대학 재학생 혹은 졸업생일 경우 학교 이메일 또는 42계정 이메일(”intraId”@student.42seoul.kr) 사용 가능
    
    https://goddaehee.tistory.com/215
    
- MySQL 설치
    - MySQLWorkbench 이용
    - MySQL workbench에서 외부 접속하기
        
        [https://velog.io/@woals4815/MySQL-외부-접속-하기MySQLWorkbench-이용](https://velog.io/@woals4815/MySQL-%EC%99%B8%EB%B6%80-%EC%A0%91%EC%86%8D-%ED%95%98%EA%B8%B0MySQLWorkbench-%EC%9D%B4%EC%9A%A9)
        
- redis 설치

## 공통 조건

- 온보딩 프로젝트는 개인 계정으로 fork하여 진행하고 PR로 제출합니다.
- git / github / code 컨벤션은 42gg notion에 있는 자료를 적극 반영합니다.

## EX00 DB 커넥션 설정
- yml 파일 이용한 db커넥션 설정 후 확인
~
## EX01 jpa entity class 만들기
- @Entity (JPA 찍먹)
    - Post entity class 생성
    - db에 해당 Post 클래스와 매핑되는 table insert query문 만들기 (post table 생성)
    - 매핑이 잘되었는지 validate 옵션으로 확인(ddl auto로 table 생성 x)


## EX02 CRUD 구현
- @RestController
    - GET 매핑
    - POST 매핑
    - DELETE 매핑
    - PUT 매핑