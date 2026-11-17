# AI 학습 노트

Claude Code와 나눈 대화를 정리한 문서 (2026-11-17)

## 1. AX 엔지니어가 하는 일

AX(AI Transformation) 엔지니어는 AI 모델을 직접 만드는 사람이 아니다.
**AI를 회사 업무와 시스템에 연결해서 일하는 방식을 바꾸는 사람**에 가깝다.

예시:
- "어제 들어온 주문 중 미처리 건 알려줘" → AI가 사내 주문 API를 조회해서 답변
- 사내 매뉴얼이나 도움말 PDF를 AI가 읽고 직원 질문에 답변
- 반복 업무(데이터 정리, 보고서 작성)를 AI 에이전트로 자동화

필요한 역량:
1. 기존 시스템(API, DB) 이해 → 실무로 이미 하고 있음
2. 그 시스템을 AI와 연결하는 기술 → 이번에 채울 부분

## 2. MCP란?

**MCP(Model Context Protocol)는 AI와 외부 도구를 연결하는 표준 규격이다.** 흔히 "AI용 USB-C"라고 부른다.

```
[AI 앱: Claude Code, Claude Desktop 등]  ← MCP 클라이언트
            │  (MCP 규격으로 대화)
            ▼
[MCP 서버]  ← 내가 만드는 부분
  - tools:     AI가 호출할 수 있는 기능 (예: 메모 검색, 메모 추가)
  - resources: AI가 읽을 수 있는 자료 (예: 문서, 코드표)
            │
            ▼
[실제 시스템: API, DB, 파일 등]
```

- Claude Code의 Google Drive, Gmail 연동도 MCP 서버다.
- MCP 서버가 "파일 검색", "파일 읽기" 같은 tool 목록을 AI에게 알려주면, AI가 필요할 때 골라서 호출한다.
- 결국 MCP 서버는 **함수 몇 개를 정해진 형식으로 노출하는 작은 서버**다. XData로 REST API를 만드는 것과 개념이 비슷하다.

## 3. 공부 순서

| 단계 | 내용 |
|---|---|
| 1. LLM 기본기 | 토큰, 컨텍스트, 프롬프트 작성법, 모델별 차이 |
| 2. LLM API 직접 호출 | Claude API로 대화하기, Tool Use(함수 호출) |
| 3. MCP | 공식 문서를 읽고 TypeScript SDK로 MCP 서버 만들기 |
| 4. RAG | 문서를 쪼개서 검색한 뒤 AI에게 넘기기 |
| 5. 에이전트 | 여러 tool을 조합해 AI가 스스로 단계를 밟게 하기 |

## 4. React 공부 방법

- 강의를 처음부터 끝까지 듣는 것보다 **직접 만들면서 배우는 게 빠르다.**
- 막히는 개념(상태관리, useEffect 등)만 골라서 강의나 문서로 보충한다.
- MCP나 AI 예제가 대부분 TypeScript 기반이라, 같이 공부하면 자연스럽게 익숙해진다.

## 5. 회사 프로젝트에 적용할 아이디어 (나중에)

- KOS XData의 주문조회 API를 감싸는 MCP 서버를 만든다.
- Claude에 연결해서 "이번 주 ○○ 거래처 주문 보여줘"를 처리하게 한다.
- 개발 서버와 테스트 데이터로 진행한다.
- 이 학습 프로젝트 3단계를 마친 뒤에 시도하면 좋다.

## 6. 참고 자료

- MCP 공식 문서: https://modelcontextprotocol.io ("Quickstart → Build a server"부터)
- Anthropic 문서: https://docs.anthropic.com (Tool use 항목)
- Anthropic Academy / Courses (무료): 프롬프트 엔지니어링, Tool use, MCP 과정
