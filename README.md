## 안녕하세요, 백엔드 개발자 김재휘입니다

**드론 · AI · 서버를 하나의 서비스로 잇는 백엔드 개발자**입니다.
Java · Spring Boot로 서버를 만들고, 데이터가 서비스 안에서 끝까지 맞게 흐르도록 설계하는 일을 좋아합니다.

- 🤝 **함께 만드는 사람**: 팀의 서비스 경계와 API 규격을 먼저 맞추고, 결정은 문서로 남깁니다.
- 🚀 **새 기술을 두려워하지 않는 사람**: MQTT · DL4J · Spring AI(MCP) · 공간 DB까지, 필요하면 바로 배워 씁니다.
- ⏱️ **마감 안에 완성하는 사람**: 리뷰할 수 있는 단위로 PR을 나눠 정해진 시간 안에 끝냅니다.

## 포트폴리오

<a href="portfolio/saferoute-portfolio.pdf"><img src="portfolio/cover.png" width="640" alt="세잎지도 프로젝트 포트폴리오 표지"></a>

**[📄 세잎지도 프로젝트 포트폴리오 (PDF, 12쪽)](portfolio/saferoute-portfolio.pdf)**: 문제와 목표 · 데이터 구조 · 트러블슈팅 · 현장 검증 · 협업

## 프로젝트

| 프로젝트 | 기간 · 인원 | 맡은 일 | 결과 |
|---|---|---|---|
| **[세잎지도](https://github.com/Safe-Way/safe-route)**<br>보행 약자 안전 길찾기 | 2026.10 ~ 11 · 4인 | 데이터 · DB · PO | 공공데이터 약 550만 건 → 안전 시설 10만여 곳을 길에 연결<br>현장 비교 불편 **세잎지도 0 · 카카오 8 · 네이버 10**<br>[발표 영상·자료](https://github.com/Safe-Way/safe-route/tree/main/docs/presentation) |
| **InsightOn**<br>IoT 센서 · 액추에이터 코어 | 2026.07 ~ 09 · 8인 | Core (Sensor · Actuator) | MQTT → Redis → InfluxDB 파이프라인, 커밋 후 이벤트 반영으로 롤백 시 불일치 해결, 공급사별 어댑터(전략 패턴) |
| **[Mini Dooray](https://github.com/wognlrla/mini-dooray-gateway)**<br>팀 협업 관리 서비스 | 2026.05 · 5인 | Gateway (BFF) | Spring Security 세션 인증, Spring Session + Redis, 회원 데이터를 Account API로 위임해 서비스 경계 재설계 |

<details>
<summary><b>세잎지도에서 한 일 자세히</b></summary>

- 공공데이터 13종(가로등 · CCTV · 쉼터 · 화장실 · 비상벨 …)을 정제해 MySQL 공간 DB에 적재, OpenStreetMap 광주 도로망 81,709구간에 길별 점수로 연결
- 국토지리정보원 인도 데이터를 길 60,586개에 붙여 휠체어가 인도 없는 골목을 피하게 함 (골목 340m → 9m)
- 데이터 갱신 16단계를 명령 하나로 묶고, 끝나면 고아 참조 · 중복 · 표 줄 수를 자동 점검
- 가짜 JDBC로 DB 없이 적재 코드를 테스트해 커버리지 46% → 96% (서버 전체 82.9% → 89.0%)
- PO로 요구사항 · 결정 기록 59건 관리, GitHub Actions → Docker → 학교 서버 자동 배포
- 4명이 같은 코스를 각자 다른 앱으로 동시에 걸으며 녹화해 비교, 찾은 문제를 원인별로 나눠 고침 (5 → 2 → 0)

</details>

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

## 개인 프로젝트 · 연락

- 💻 개인 프로젝트 모음: [wognlrla/portfolio](https://github.com/wognlrla/portfolio)
- ✉️ wognlrla1@gmail.com
