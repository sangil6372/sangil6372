### 결제처럼 틀리면 안 되는 흐름을, 검증 기준부터 세워 만듭니다

웹과 Android 서비스를 설계부터 배포까지 직접 만들어 왔습니다.
동시에 들어온 요청, 원 단위 계산, 장애 뒤 재시도처럼 결제 시스템에서 문제가 되는 상황을 테스트로 먼저 재현하고, 확인된 구조만 남깁니다.

<br>

## How I Work

- **정합성은 DB가 보장하게** : 조건부 UPSERT, 유니크 제약, `FOR UPDATE SKIP LOCKED`
- **재전송과 장애를 전제로** : Idempotency-Key 멱등 API, 아웃박스 워커, 교착 재현과 잠금 순서 통일
- **금액은 정수로, 근거는 테스트로** : 끝전 배분 규칙을 비교해 선택하고 속성 기반 테스트로 합계 보존 확인
- **배포는 처음부터 자동으로** : GitHub Actions → Docker → AWS EC2 / RDS

<br>

## Projects

| 프로젝트 | 내용 | 기술 |
|---|---|---|
| **ReceiPie** · 영수증 정산 앱 | 사용 한도 동시성, 원 단위 정산, 멱등 API, 교착 해소를 중심으로 앱과 서버를 다시 설계 | Kotlin, Jetpack Compose, Spring Boot, PostgreSQL |
| **MoneyBunny** · 청년 정책 추천·알림 웹 서비스 | 6인 팀 PM 겸 백엔드. 정책 데이터 수집, 추천 REST API, 알림, CI/CD 구축 | Java, Spring, MyBatis, MySQL, Redis, Vue 3, FCM, AWS |
| **MoneyBunny S2** · 알림 시스템 재설계 | 알림을 결제 승인 통지처럼 다뤄, 누락과 중복 발송을 DB 수준에서 차단 | Spring Boot, PostgreSQL, Docker, GitHub Actions |
| **AI 학습 데이터 정제 공정** · 인턴 | AI가 실패하면 원문을 지키는 규칙과 OCR 대체 흐름으로 정제 공정 자동화 | Python, GPT API, OCR, AWS S3 |
| **TCP 소켓 서버** | 기본 소켓 서버를 TLS, 비동기, Pub/Sub까지 단계적으로 확장 | Python |

<sub>2026년 개인 프로젝트는 AI 코딩 도구로 구현했고, 설계 결정과 검증 기준은 직접 정했습니다.</sub>

<br>

## Tech Stack

| 분야 | 기술 |
|---|---|
| Language | Java · Kotlin · JavaScript / TypeScript · Python |
| Backend | Spring Boot · Spring MVC · MyBatis · RESTful API |
| Web / App | Vue 3 · Pinia · Android (Jetpack Compose) · PWA |
| Data | PostgreSQL · MySQL · Redis |
| Infra | AWS (EC2 · RDS · S3) · Docker · GitHub Actions · Linux |
