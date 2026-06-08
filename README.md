# 안녕하세요, 기술의 본질과 문제 해결에 집중하는 개발자 chzhxkd100 입니다.

저는 화려한 디자인이나 트렌디한 도구에 매몰되기보다, **시스템의 구조적 문제를 분석하고 이를 효율적으로 해결하는 과정**에 깊은 흥미를 느끼는 프로그래머입니다. 

다양한 언어(C#, Java, Python, C++, JavaScript)와 프레임워크를 경험하며 웹 백엔드, 클라우드 서버리스 인프라, 게임 엔진 및 실시간 연동 툴까지 넓은 스펙트럼에서 기술적 도전을 거듭해 왔습니다.

---

## 🛠️ Tech Stack & Capabilities

| 분류 | 기술 기술 스택 | 상세 설명 |
| :--- | :--- | :--- |
| **Languages** | `C#`, `Java`, `Python`, `C++`, `JavaScript`, `OCaml`, `GDScript` | 다중 패러다임 언어 활용, 문제에 맞는 최적의 언어 선택 |
| **Web & Backend** | `Node.js (Express)`, `FastAPI`, `Flask`, `Spring Boot`, `EJS` | RESTful API 설계, 효율적인 웹 서버 라우팅 및 동적 렌더링 |
| **Cloud & DevOps** | `GCP (Cloud Run, Firestore, GCS)`, `Docker`, `Firebase`, `GitHub Actions` | 서버리스 컨테이너 배포, CI/CD 배포 자동화 파이프라인 구축 |
| **Databases** | `Redis`, `MariaDB`, `Local Mock DB (JSON Engine)` | 캐싱 전략 및 분산 환경 설계, 데이터 모델링 및 모의 DB 엔진 구현 |
| **Game Engine** | `Godot Engine 4 (2D/3D)` | C# 및 GDScript 기반 물리 제어, 2D/3D 게임 로직 및 네트워크 동기화 |

---

## 🚀 Featured Projects & Technical Challenges

제 깃허브 레포지토리들은 단순한 튜토리얼 따라 하기를 넘어, **실제 마주한 기술적 한계와 비효율을 어떻게 정의하고 극복했는지**에 대한 기록을 담고 있습니다.

### 1. [DarkBrood](https://github.com/chzhxkd100/darkbrood) - 레트로 다크 에어로 감성의 풀스택 아카이브 서비스
GCP 서버리스 인프라와 EJS 템플릿 엔진을 활용해 다크 모드 감성의 익명 게시판 및 다이어리 아카이브를 구축한 프로젝트입니다.
*   **Firebase Hosting 쿠키 필터링 극복**: Firebase Hosting을 Edge Proxy로 사용할 때 발생하는 세션 쿠키 필터링(`__session`을 제외한 다른 쿠키 삭제 정책) 문제를 해결하기 위해, 표준 세션 라이브러리에 의존하지 않고 Payload를 서버 사이드 비밀 키로 서명해 단일 `__session` 쿠키에 담는 **보안 세션 검증 환경**을 직접 설계하여 우회 적용했습니다.
*   **Zero-Config 로컬 하이브리드 아키텍처**: 다른 개발자가 복잡한 GCP 크리덴셜 없이도 프로젝트를 구동할 수 있도록 GCP 연동 여부에 따라 분기 처리되는 Fallback 아키텍처를 도입했습니다. Firestore 미연결 시 로컬 `db.json`을 사용하여 `where`, `orderBy`, `limit` 쿼리를 흉내 내는 **자체 Mock 데이터베이스 엔진**(`src/db.js`)을 구현했습니다.
*   **Cloud Storage 보안 및 경로 유실 버그 수정**: Uniform Bucket-Level Access 활성화 시 ACL 주입으로 발생하는 `400 Bad Request` 에러를 차단하기 위해 IAM 수준에서 공공 읽기 권한을 바인딩하고, `multer-cloud-storage` 라이브러리의 경로 분리 설정 방식을 개선해 업로드된 이미지가 유실 없이 버킷 내 특정 경로에 안전하게 위치하도록 정립했습니다.

### 2. Godot & C# 기반 Game Development 
Godot 4 엔진과 C# 언어를 주력으로 삼아 다양한 장르의 게임 아키텍처와 게임 물리 시스템을 실험했습니다.
*   **[Dtown (2D Side-Scrolling MMORPG)](https://github.com/chzhxkd100/Dtown)**:
    *   2D 물리 엔진을 활용한 이단 점프, 대시 및 넉백 이동 물리 알고리즘을 C# 스크립트로 제어했습니다.
    *   상태 패턴(State Pattern) 기반의 몬스터 AI 제어 루프를 설계하여 확장성 있는 전투 시스템의 틀을 다졌습니다.
*   **[Godot 3D low-poly MMORPG 연구](https://github.com/chzhxkd100/Godot)**:
    *   3D 1인칭 시점 제어 시 카메라의 각도와 속도를 물리 연산 프레임(`_PhysicsProcess`)에 유기적으로 동기화하여 지연 현상을 최소화했습니다.
    *   애니메이션 리소스 유실 시 발생하는 NPC의 T-Pose 문제를 해결하기 위해, 뼈대(Skeleton3D)를 스크립트로 동적 제어하는 **절차적 애니메이션(Procedural Animation)** 기반을 실험했습니다.
*   **[3D Squash the Creeps Starter](https://github.com/chzhxkd100/3d_squash_the_creeps_starter)**: Godot 3D 엔진의 물리 바디 및 충돌 레이어(Collision Layers & Masks) 메커니즘을 상세 분석하고, 3D 환경에서의 벡터 수학 연산을 응용한 조작감을 학습했습니다.

### 3. 실시간 플랫폼 자동화 및 그래픽 렌더링 헬퍼
실시간 API 연동 및 개인화 도구를 만들어 수동 작업의 비효율을 자동화로 개선한 도구들입니다.
*   **[ChatPlayer (치지직 실시간 채팅 통합 및 모듈)](https://github.com/chzhxkd100/chatplayer)**:
    *   네트워크 소켓 연동을 통해 인터넷 방송 플랫폼(치지직)의 채팅 API를 실시간 캡처하는 통합 모듈을 Java로 구현했습니다.
    *   인증 만료 주기가 잦은 API 키 토큰을 로컬 파일 시스템에 안전하게 캐싱 및 갱신하도록 설계하여, 서버 시작 시 수동 개입 없는 **완전 자동 시작 시퀀스**를 정립했습니다.
*   **OBS Persona Chat Overlay**:
    *   방송 송출 소프트웨어(OBS)의 가벼운 웹뷰 오버레이용으로, 채널 운영자(스트리머)의 메시지 발생 여부만을 고성능으로 감지하여 특정 시간(1~2초) 노출 후 페이드아웃하는 필터링 엔진을 구현했습니다.
    *   시스템에서 지정한 커스텀 폰트 파일(`.ttf`)을 로컬 자산 파일에서 직접 파싱하여 텍스트 영역 내에 정확히 안착시키도록 렌더링을 튜닝했습니다.
*   **[DJMax Auto Ready Feature](https://github.com/chzhxkd100/chzhxkd100)**: AFK(자리비움) 상황에서 대기 방의 다른 플레이어들에게 방해가 되지 않도록 게임 프로세스 동작 상태와 사용자 입력을 인터셉트하여 자동으로 Ready 상태로 전환해주는 헬퍼 스크립트를 실험했습니다.

### 4. [DXPractice](https://github.com/chzhxkd100/DXPractice) - C++ & DirectX 실무 연습
엔진 뒤에 숨겨진 그래픽스 라이프사이클을 깊이 있게 이해하기 위해 C++과 DirectX API를 연습한 저장소입니다.
*   GPU 렌더링 파이프라인의 핵심인 셰이더(Vertex/Pixel Shader)의 동작 방식을 직접 코딩하고, 버퍼 바인딩 및 그리기 호출(Draw Call) 단계를 추적했습니다.
*   C++ 메모리 누수를 감지하는 CRT 디버깅 라이브러리를 바인딩하여 실시간 그래픽스 리소스 관리 구조를 학습했습니다.

### 5. Network Programming & REST Architecture (Academic & Research)
컴퓨터 네트워크와 백엔드 아키텍처에 대한 이론을 코드로 옮기며 단단한 기초 체력을 다졌습니다.
*   **[DynamicRendering](https://github.com/chzhxkd100/DynamicRendering) / [orm](https://github.com/chzhxkd100/orm) / [httpdserver](https://github.com/chzhxkd100/httpdserver)**:
    *   FastAPI, Uvicorn, SQLAlchemy ORM을 연동하여 도커 컨테이너 환경에서 분리 구동되는 RESTful Pastebin 서비스를 구현했습니다.
    *   HTTP 요청 파싱부터 응답 헤더 조립까지 HTTP 프레임워크를 거치지 않고 **Vanilla Python 소켓 통신 수준에서 직접 httpd 웹 서버를 구현**(`httpdserver`)하며, HTTP 프로토콜 스펙과 TCP 3-way handshake 동작 원리를 몸소 체득했습니다.

---

## 📈 학습 철학과 미래의 방향성

*   **동작 원리에 대한 집요한 탐구**: 단순히 라이브러리를 가져다 쓰는 것에 그치지 않고, "어떻게 백엔드 프레임워크 없이 웹 서버를 구동할 것인가?", "어떻게 GCP 없이 로컬 데이터베이스를 Mocking할 것인가?" 와 같이 근본적인 원리를 파고듭니다.
*   **문제 해결을 위한 하이브리드 접근**: 웹, 서버리스, 시스템 프로그래밍, 게임 등 특정 분야의 경계에 갇히지 않고, 문제 상황에 가장 필요하고 적절한 도구를 빠르게 습득하여 적용합니다.
*   **품질을 높이는 정리와 리팩토링**: 프로젝트 완성 이후에도 기술적인 부채와 아쉬웠던 한계를 기록(GCP 배포 가이드, 세션 우회 기법 문서화 등)하여 타인과의 협업 및 유지보수성을 극대화합니다.

기술을 집요하게 탐구하며 단단한 아키텍처를 세워나가는 저의 여정에 동참할 팀을 찾고 있습니다. 

언제든 열려 있으니 편하게 연락해 주세요!

*   **Email**: chzhxkd100@gmail.com *(또는 실제 사용하는 이메일)*
*   **GitHub**: [github.com/chzhxkd100](https://github.com/chzhxkd100)
