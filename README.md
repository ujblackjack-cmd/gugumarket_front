## 🛒 GuguMarket – 실시간 중고거래 플랫폼

Bootcamp Team Project

GuguMarket은 중고 상품 거래 과정을 **실시간 1:1 채팅, 알림(Notification), 위치 기반 탐색** 기능으로 강화한 웹 서비스입니다. 본 프로젝트는 특히 사용자 **회원가입, 로그인 인증, 마이페이지 개인화** 기능에서 높은 안정성과 사용 편의성을 확보하는 데 중점을 두었습니다.

***

### 🧩 기술 스택

**Frontend**

* **프레임워크**: React
* **라우팅**: React Router
* **상태 관리**: Zustand (전역 상태 관리)
* **통신**: Axios, JWT Interceptor를 포함한 JWT Axios
* **스타일**: TailwindCSS, Bootstrap Icons
* **실시간**: WebSocket(STOMP) 클라이언트 (`@stomp/stompjs`, `sockjs-client`)

**Backend**

* **프레임워크**: Spring Boot 3.x
* **보안**: Spring Security + JWT 기반 인증/인가 시스템
* **데이터베이스**: MySQL, JPA / Querydsl
* **실시간**: WebSocket(STOMP) 서버

***

### 📁 프로젝트 구조

프로젝트는 백엔드와 프론트엔드로 분리되어 있으며, 각 컴포넌트는 다음과 같이 구성되어 있습니다.

* **backend/**:
    * `controller/`: AuthController, UserController, MypageController 등 사용자 요청 처리
    * `service/`: 비즈니스 로직 처리
    * `repository/`: 데이터베이스 접근 (JPA)
    * `config/`: Spring Security 설정, WebSocket 설정 등
* **frontend/**:
    * `pages/`: Login, Signup, MyPage, Edit 등 라우팅 페이지
    * `components/`: UserProfile, MySales, ChatRoomModal 등 재사용 가능한 UI 컴포넌트
    * `hooks/`: 인증 로직, WebSocket 연결 관리 등 커스텀 훅
    * `stores/`: Zustand를 이용한 전역 상태 관리
    * `api/`: 백엔드 API 요청 함수 모음

***

### 📌 핵심 기능 요약

* **사용자 서비스**: 일반/소셜 로그인, 회원가입, 프로필 수정, 마이페이지 통합 관리.
* **실시간 채팅**: 상품 기반 1:1 채팅, 메시지 읽음 처리, 실시간 미확인 메시지 카운트.
* **알림 시스템**: 채팅, 댓글, 거래 상태 변경 등 다양한 유형의 실시간 알림.
* **상품 거래**: 등록/수정/삭제, 찜하기, 신고하기, 결제(무통장/KakaoPay 연동 준비).
* **지도 기반 기능**: 위치 기반 상품 조회 및 필터링.

***

### 🔑 사용자 서비스

* **통합 로그인**: 일반 로그인 및 **Kakao 소셜 로그인**을 통한 간편 접속 구현.
* **회원가입**: 아이디 중복 확인 및 Daum 주소 검색 API를 통합한 상세 정보 입력 페이지 구현.
* **마이페이지**: **구매 내역, 판매 내역, 찜한 목록, 알림, 신고 내역**을 탭으로 분류하여 제공하는 통합 대시보드를 구현했습니다.
* **프로필 수정**: 닉네임, 이메일, 주소, 비밀번호 변경 및 프로필 이미지 업로드/삭제 기능을 구현했습니다.
* **계정 복구**: 아이디 찾기 및 이메일 인증을 통한 비밀번호 재설정 기능을 제공합니다.

***

### 💬 실시간 채팅 (WebSocket/STOMP)

* **기반 기술**: Spring WebSocket과 STOMP 프로토콜을 기반으로 실시간 양방향 통신을 구현했습니다.
* **기능**: 상품 기준의 채팅방 생성/조회, 메시지 전송 및 수신, 읽음 처리, 채팅방 목록 실시간 갱신 기능을 제공합니다.

***

### 🔔 알림 시스템

* **전송 방식**: WebSocket을 활용하여 실시간으로 사용자에게 알림을 전송합니다.
* **알림 유형**: 좋아요, 댓글, 구매 요청 (`PURCHASE`), 거래 상태 변경 (`TRANSACTION`) 등 다양한 유형의 알림을 처리합니다.

***

### 📍 지도 기반 기능

* **지도 연동**: Kakao 지도 SDK를 사용하여 메인 화면과 별도의 지도 페이지에서 상품 위치를 시각화합니다.
* **필터링**: 현재 위치 및 반경 기반 필터, 가격 범위 필터링 기능 제공.

***

### 👥 팀 구성 및 역할

**신의진 님**이 팀장으로서 사용자 인증/개인화 흐름을 총괄하였으며, 각 팀원의 담당 역할은 다음과 같습니다.

* **신의진 (팀장)**:
    * **담당 Backend**: MypageController, UserController를 구현하고, WebConfig를 통해 CORS 설정을 관리했으며, SecurityConfig의 인증/인가/JWT 설정을 담당하며 전체 프로젝트 관리 및 아키텍처 점검을 총괄했습니다.
    * **담당 Frontend**: SignupPage, MyPage, UserDetail (프로필 수정 포함) 등 인증/마이페이지 흐름을 총괄했습니다.

* **최동원**:
    * **담당 Backend**: JWT 인증·인가 구조 및 WebSocket 채팅/알림 서버 등 구조를 만드는데 일조했습니다.
    * **담당 Frontend**: 채팅 UI, Notification, Admin Page, 라우팅 전체 구성, LoginPage를 담당했습니다.

* **김보민**:
    * **담당 Backend**: KakaoAuth, Map, Category, Main Controller를 담당했습니다.
    * **담당 Frontend**: KakaoCallbackPage, MapPage, MainPage를 담당했습니다.

* **김동민**:
    * **담당 Backend**: Comment, Purchase Controller를 담당했습니다.
    * **담당 Frontend**: Purchase, PurchaseComplete, TransactionDetail 페이지를 담당했습니다.

* **박성훈**:
    * **담당 Backend**: Image, Qna Controller를 담당했습니다.
    * **담당 Frontend**: QnA List / Form 페이지를 담당했습니다.

* **김봉환**:
    * **담당 Backend**: Like, Product, Transaction Controller를 담당했습니다.
    * **담당 Frontend**: Product Detail / Write / Edit 페이지 및 댓글 UI를 담당했습니다.

***

### 📅 개발 기간

2024.11.24 ~ 2024.12.08
***
