## 안녕하세요, 백엔드 개발자 김재휘입니다

**IoT · AI · 데이터를 하나의 서비스로 잇는 백엔드 개발자**입니다.
Java · Spring Boot로 서버를 만들고, 데이터가 서비스 안에서 끝까지 맞게 흐르도록 설계하는 일을 좋아합니다.

- **함께 만드는 사람**: 팀의 서비스 경계와 API 규격을 먼저 맞추고, 결정은 문서로 남깁니다.
- **새 기술을 두려워하지 않는 사람**: MQTT · DL4J · Spring AI(MCP) · 공간 DB까지, 필요하면 바로 배워 씁니다.
- **마감 안에 완성하는 사람**: 리뷰할 수 있는 단위로 PR을 나눠 정해진 시간 안에 끝냅니다.

## 포트폴리오

<table>
<tr>
<td width="50%"><a href="portfolio/saferoute-portfolio.pdf"><img src="portfolio/cover.png" alt="세잎지도 프로젝트 포트폴리오 표지"></a></td>
<td width="50%"><a href="portfolio/backend-portfolio.pdf"><img src="portfolio/backend-cover.png" alt="백엔드 개발자 포트폴리오 표지"></a></td>
</tr>
<tr>
<td><b><a href="portfolio/saferoute-portfolio.pdf">세잎지도 프로젝트 포트폴리오</a></b> (PDF, 12쪽)<br>문제와 목표 · 데이터 구조 · 트러블슈팅 · 현장 검증 · 협업</td>
<td><b><a href="portfolio/backend-portfolio.pdf">백엔드 개발자 포트폴리오</a></b> (PDF, 11쪽)<br>InsightOn · Mini Dooray — 구조 · 트러블슈팅 · 서비스 경계</td>
</tr>
</table>

**[이력서 · 자기소개서 (Word)](resume/이력서_자기소개서_김재휘.docx)**: 기술 스택 · 교육 · 프로젝트(세잎지도 · InsightOn · AI-fly-schedule · Mini Dooray) · 자기소개서

## 프로젝트

### 팀 프로젝트

| 프로젝트 | 기간 · 인원 | 맡은 일 | 결과 |
|---|---|---|---|
| **[세잎지도](https://github.com/Safe-Way/safe-route)**<br>보행 약자 안전 길찾기 | 2026.10 ~ 11 · 4인 | 데이터 · DB | 공공데이터 약 550만 건 → 안전 시설 10만여 곳을 길에 연결<br>현장 비교 불편 **세잎지도 0 · 카카오 8 · 네이버 10**<br>[발표 영상·자료](https://github.com/Safe-Way/safe-route/tree/main/docs/presentation) |
| **[InsightOn](portfolio/backend-portfolio.pdf)**<br>IoT 센서 · 액추에이터 코어 | 2026.07 ~ 09 · 8인 | Core (Sensor · Actuator) | MQTT → Redis → InfluxDB 파이프라인, 커밋 후 이벤트 반영으로 롤백 시 불일치 해결, 공급사별 어댑터(전략 패턴) |
| **[Mini Dooray](https://github.com/wognlrla/mini-dooray-gateway)**<br>팀 협업 관리 서비스 | 2026.05 · 5인 | Gateway (BFF) | Spring Security 세션 인증, Spring Session + Redis, 회원 데이터를 Account API로 위임해 서비스 경계 재설계 |
| **[AI-fly-schedule](https://github.com/wognlrla/portfolio/tree/main/ai-fly-schedule)**<br>자연어 항공편 조회 | 2026.06 · 팀 | Multi-Agent · MCP Tool | 자연어 한 줄로 항공편 검색 · 필터 · 추천, 단일 프롬프트를 파싱 → 조회 → 필터 → 추천 Agent로 나눠 정확도 개선, MCP Tool 입출력 스키마를 정해 잘못된 도구 호출 해결 |

**교육 과정 팀 실습 (team2)**: [MQTT 시계열 추론](https://github.com/wognlrla/MQTT-timeseries-inference) (교육장 센서 데이터 60분 예측 · 이상 탐지, Jetson 상시 추론) · [Jetson 멀티모달 임베딩](https://github.com/wognlrla/LLM-model) (EmbeddingGemma로 텍스트 · 이미지 · 영상 검색)

<details>
<summary><b>세잎지도에서 한 일 자세히</b></summary>

- 공공데이터 13종(가로등 · CCTV · 쉼터 · 화장실 · 비상벨 …)을 정제해 MySQL 공간 DB에 적재, OpenStreetMap 광주 도로망 81,709구간에 길별 점수로 연결
- 국토지리정보원 인도 데이터를 길 60,586개에 붙여 휠체어가 인도 없는 골목을 피하게 함 (골목 340m → 9m)
- 데이터 갱신 16단계를 명령 하나로 묶고, 끝나면 고아 참조 · 중복 · 표 줄 수를 자동 점검
- 가짜 JDBC로 DB 없이 적재 코드를 테스트해 커버리지 46% → 96% (서버 전체 82.9% → 89.0%)
- 요구사항 · 결정 기록 59건 관리, GitHub Actions → Docker → 학교 서버 자동 배포
- 4명이 같은 코스를 각자 다른 앱으로 동시에 걸으며 녹화해 비교, 찾은 문제를 원인별로 나눠 고침 (5 → 2 → 0)

</details>

<details>
<summary><b>InsightOn에서 한 일 자세히</b></summary>

- Sensor · Actuator 도메인을 Controller → UseCase(인가 · 권한) → Service → Repository 계층으로 설계, CRUD · 검색 API
- LoRaWAN 센서 데이터를 MQTT 패킷 파싱 → 센서 자동 등록 → Redis 최신값 → InfluxDB 시계열로 저장하는 파이프라인
- 저장소 역할 분리: Redis 최신값 · MySQL 메타 · InfluxDB 시계열, 캐시 · RDB · 시계열 DB 3중 저장소 정합성 설계
- 캐시를 먼저 갱신하면 DB 실패 시 불일치 → `@TransactionalEventListener(AFTER_COMMIT)`로 커밋 이후에만 캐시 · InfluxDB 반영
- 실행 주체를 쿼리 파라미터로 받아 위장 가능 → 서버가 검증한 서비스 인증 헤더에서 호출 주체를 매핑
- 액추에이터 명령 프리셋 · 값 검증, 실행 로그 설계, RabbitMQ로 룰엔진 이벤트 발행 · 그룹 기반 권한 검증
- 공급사별 어댑터를 자동 등록하는 `ActuatorControlAdapterRegistry`(전략 패턴) → 새 공급사는 구현체 추가만, 값 변환 책임은 코어 한 곳에
- Front · Core · Simulator 3개 서비스를 설계 · 구현, LG ThinQ · SmartThings를 모사한 시뮬레이터로 실기기 없이 통합 테스트
- PR 리뷰 반영 리팩터링, SonarQube 커버리지 보완

</details>

### 개인 프로젝트

| 프로젝트 | 설명 | 기술 |
|---|---|---|
| **[블라인드 코너](https://claude.ai/artifact/NSwtNNgZnMxrBat4QgNFUk)**<br>[저장소](https://github.com/wognlrla/making-game) · 2026.10 | 위에서 내려다보지만 내가 바라보는 부채꼴(90°)만 보이는 2D 공격/수비 전술 슈터 웹 게임. 난이도별 AI 대전(5대5), 방 만들기 · 참여 멀티플레이, 판마다 새로 만들어지는 건물 맵 | TypeScript, Phaser 3, Vite, WebSocket(ws) |
| **[헬다이버즈 작전 사령부](https://claude.ai/artifact/LnkYXP8kAcBWVBfhdMqtzd)**<br>2026.11 | 헬다이버즈 2 로드아웃 도우미 웹앱. 장비마다 물량 · 장갑 · 대전차 · 철거 · 생존 역할을 매겨 내 로드아웃의 빈틈을 보여 주고, 무작위 로드아웃 · 티어 메이커 · 보유 장비 관리, 버튼 한 번으로 장비 데이터 최신화 | HTML · JavaScript, Claude Artifact(DB · 루틴 연동) |
| [hotel-reservation-system](https://github.com/wognlrla/portfolio/tree/main/hotel-reservation-system) | JWT 인증과 계층형 예외 처리를 적용한 호텔 객실 예약 REST API | Spring Boot 3, JPA, QueryDSL, JWT |
| [fbp-engine](https://github.com/wognlrla/portfolio/tree/main/fbp-engine) | Flow-Based Programming 기반 Java 메시지 스트리밍 엔진 | Java 17, MQTT |
| [iris-classifier](https://github.com/wognlrla/portfolio/tree/main/iris-classifier) | DL4J 다층 퍼셉트론을 Spring Boot에 붙인 붓꽃 품종 분류 웹서비스 | DL4J, Spring Boot |
| [breakout-game](https://github.com/wognlrla/portfolio/tree/main/breakout-game) | JavaFX로 만든 벽돌깨기 게임 | Java, JavaFX |

## 기술 스택

| 구분 | 사용 |
|---|---|
| Backend | Java, Spring Boot, Spring Security, JPA, QueryDSL, Spring AI (MCP) |
| Database | MySQL (공간 인덱스), Redis, InfluxDB, H2 |
| IoT · MQ | MQTT (Paho · LoRaWAN), RabbitMQ, Node-RED, DL4J |
| Data · DevOps | Python, OpenStreetMap, GitHub Actions, Docker |
| Tools | Git · GitHub, JUnit5, SonarQube, IntelliJ, Maven |

## 학력 · 교육

- 조선대학교 인공지능공학과 편입 재학 (2027.08 졸업 예정)
- 호남대학교 로봇드론공학과
- NHN Academy 인공지능 기반 IoT 웹서비스 개발자 과정 (2025.12 ~ 2026.09)
- 스마트그리드 기반 IoT융합 SW전문가과정 (2020.11 ~ 2021.03)

## 연락

- wognlrla1@gmail.com
