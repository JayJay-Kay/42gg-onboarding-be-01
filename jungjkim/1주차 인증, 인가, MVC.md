# 1주차 인증, 인가, MVC

## 인증 (Authentication = Who are you?)

- 신원 확인 과정
    - 예시: 회원가입, 로그인
- 인증 절차를 통해 Access Token 발급

## 인가 (Authorization = What can you do?)

- 사용자의 요청을 실행할 수 있는 권한 여부 확인 절차
- 접근 권한 부여하거나 거부하는 행위
- DB에서 사용자 권한 확인

## MVC패턴

- Model, View, Controller (소프트웨어 디자인 패턴)
- MVC1, MVC2
    - 클라이언트의 요청 사항을 모듈화 되지 않은 하나의 파일로 처리할 것인지 각각의 기능을 담당하는 모듈들이 역할을 분담해서 처리할 것인지 결정
- Model
    - 애플리케이션의 정보, 데이터의 가공을 책임지며 DB와 상호작용하며 비즈니스 로직을 처리하는 모듈, 컴포넌트
- View
    - 사용자에게 보여주는 화면 (User Interface)
- Controller
    - Model과 View를 연결해주며 제어하는 모듈