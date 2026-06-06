# Tracktory

> AI 기반 자율전공 학습경로 추천 시스템

Tracktory는 관심사와 경험은 있지만 아직 진로와 전공 선택이 명확하지 않은 학생에게 **직무 탐색 → 트랙 조합 추천 → 학기별 수강 로드맵**으로 이어지는 개인화 학습경로를 제안하는 모바일 서비스입니다.

한성대학교 트랙제와 교과목 구조를 기반으로 사용자의 온보딩 정보, 이수 과목, 관심 분야를 분석하고, 추천 결과를 앱에서 이해 가능한 리포트와 챗봇 경험으로 제공합니다.

![Tracktory app UI](./app-ui.svg)

## System Architecture

![Tracktory system architecture](./diagrams/01-system-architecture.svg)

앱은 Spring Boot 백엔드하고만 직접 통신하고, AI 연산은 Spring 이 내부 FastAPI 중계 서버로 위임합니다. FastAPI 서비스는 LangGraph 추천 그래프, 챗봇 그래프, RAGFlow/LightRAG 지식 베이스를 구동합니다.

## Repositories

| Repository | Role | Stack |
|---|---|---|
| [Tracktory/Frontend](https://github.com/Tracktory/Frontend) | 모바일 앱 클라이언트. 인증, 온보딩, 추천 결과, 분석 리포트, 챗봇, 마이페이지 화면을 제공합니다. | Expo · React Native · TypeScript · React Navigation · Zustand |
| [Tracktory/Backend](https://github.com/Tracktory/Backend) | 앱-facing 메인 백엔드. 인증, 프로필, 이수 과목, 추천 결과 저장, 추천 리포트 API, AI 중계 호출을 담당합니다. | Java 21 · Spring Boot · JPA · MySQL · JWT |
| [Tracktory/tracktory-ai](https://github.com/Tracktory/tracktory-ai) | AI 추천 중계 서버. LangGraph 추천 파이프라인, 챗봇 그래프, RAGFlow 검색, 설명 생성을 담당합니다. | Python 3.13 · FastAPI · LangGraph · RAGFlow · Pydantic |

## Tech Focus

- **Mobile UX**: Expo 기반 네이티브 앱, 온보딩 중심 입력 흐름, 추천 결과 탐색 UI, 챗봇 오버레이
- **Backend Boundary**: Spring Boot BFF, JWT 인증, 도메인 트랜잭션, 추천 결과 영속화, 내부 AI relay 인증
- **AI Workflow**: LangGraph state-first 추천 그래프, RAGFlow/LightRAG 검색, Pydantic 구조화 출력, LLM 설명 생성
- **Academic Data Modeling**: 한성대 단과대, 학부, 트랙, 과목, 직무, 기술스택, 선수과목 관계 모델링

## More Details

- Backend 설계와 앱-facing API: [Tracktory/Backend](https://github.com/Tracktory/Backend)
- AI 추천 파이프라인, 챗봇, RAGFlow, 트랙 조합 알고리즘: [Tracktory/tracktory-ai](https://github.com/Tracktory/tracktory-ai)

## Team

| Member | Focus |
|---|---|
| [@jwon0523](https://github.com/jwon0523) | Project lead, recommendation system, LangGraph pipeline, Spring Boot and FastAPI integration |
| [@ThreeeJ](https://github.com/ThreeeJ) | Chatbot agent, Spring Boot and FastAPI Integration |
| [@parkseonghun598](https://github.com/parkseonghun598) | Data processing, React Native frontend |
| [@J2H3233](https://github.com/J2H3233) | embedding/RAG optimization, Spring Boot |

| <img src="https://github.com/jwon0523.png" width="120" alt="jwon0523"> | <img src="https://github.com/ThreeeJ.png" width="120" alt="ThreeeJ"> | <img src="https://github.com/parkseonghun598.png" width="120" alt="parkseonghun598"> | <img src="https://github.com/J2H3233.png" width="120" alt="J2H3233"> |
|:---:|:---:|:---:|:---:|
| **이재원** | **정종진** | **박성훈** | **전종현** |
| Project Lead | AI Chatbot | Frontend | Research · RAG |
| 추천 시스템 · 백엔드/AI 연동 | 챗봇 에이전트 · 직무-역량 매핑 | React Native | 임베딩/RAG 최적화 |
| [@jwon0523](https://github.com/jwon0523) | [@ThreeeJ](https://github.com/ThreeeJ) | [@parkseonghun598](https://github.com/parkseonghun598) | [@J2H3233](https://github.com/J2H3233) |

</div>
