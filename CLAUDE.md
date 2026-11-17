# AI 학습 프로젝트: 메모·할 일 관리 앱

AX(AI Transformation) 역량을 쌓으려고 처음부터 만드는 개인 학습 프로젝트다.
앱 하나를 단계별로 키우면서 React, API 서버, MCP, Claude API, RAG를 차례로 익힌다.

학습 배경과 개념 정리는 [docs/study-plan.md](docs/study-plan.md)에 있다.

## 사용자 정보
- 실무: Delphi / TMS Web Core 기반 웹 프로그램, TMS XData REST 서버 개발
- REST API, 인증·세션 처리 경험이 있다.
- React, TypeScript, MCP, LLM API는 처음 배운다.

## 작업 규칙 (반드시 지킬 것)
- **항상 한국어로 답변한다.**
- **실행 전에 먼저 설명한다.** 무엇을 만들지, 결과가 어떻게 될지 설명하고, 사용자가 확인한 뒤에 구현한다.
- **학습이 목적이다.** 코드를 한 번에 다 작성해 주지 않는다.
  1. 단계마다 개념과 구조를 먼저 설명한다.
  2. 사용자가 직접 코드를 작성한다. 막히는 부분만 도와준다.
  3. 완성되면 리뷰하면서 더 나은 방법과 그 이유를 알려준다.
- 사용자가 "이 코드 왜 이렇게 써?"라고 물으면, 실무 경험(Delphi, XData)에 빗대어 설명하면 이해가 빠르다.

## 기술 스택
- 화면: Vite + React + TypeScript
- 서버: Node.js + Express (또는 Hono)
- DB: SQLite
- MCP: 공식 TypeScript SDK (`@modelcontextprotocol/sdk`)
- AI: Claude API (4단계부터)

전부 TypeScript로 통일해서 언어 학습 부담을 줄인다.

## 단계별 계획
| 단계 | 만드는 것 | 배우는 것 | 상태 |
|---|---|---|---|
| 1. 화면 | 메모 추가·수정·삭제 화면 (데이터는 브라우저에만 저장) | React, TypeScript, 컴포넌트, useState | 진행 중 |
| 2. 서버 | 메모를 저장하는 API 서버 + DB | Node.js, REST API, SQLite, 화면↔서버 통신 | 시작 전 |
| 3. MCP 서버 | Claude Code / Claude Desktop에서 "회의 관련 메모 찾아줘"가 되게 하기 | MCP 개념, tool 정의, AI의 tool 호출 흐름 | 시작 전 |
| 4. 앱 내 AI 채팅 | 앱 화면에서 AI와 대화하며 메모 조작 | Claude API, Tool Use, 스트리밍 | 시작 전 |
| 5. RAG | 메모가 많아도 의미가 비슷한 메모를 찾아 AI가 답변 | 임베딩, 벡터 검색, RAG 구조 | 시작 전 |

- 1~3단계는 무료다. MCP는 Claude Code나 Claude Desktop에 연결하면 되기 때문이다.
- 4~5단계는 Claude API 키가 필요하고 사용량만큼 과금된다.
- 단계를 마칠 때마다 위 표의 "상태"를 갱신한다.

## 개발 환경 메모
- 화면 프로젝트는 `client/` 폴더에 있다. `npm run dev`는 반드시 `client/`에서 실행한다. (루트에는 package.json이 없다)
- 새 컴퓨터에서 처음 시작할 때: `git clone` → `cd client` → `npm install` → `npm run dev`
- 회사·집 컴퓨터를 오가며 작업한다. 대화 기록은 컴퓨터끼리 공유되지 않으므로, 작업을 마칠 때 아래 "진행 상황"과 "다음 할 일"을 갱신하고 push한다.

## 진행 상황 (1단계)
- [x] Node.js 확인 (v22.17.0, npm 10.9.2)
- [x] GitHub 레포 연결 (`origin` → peesechizza/ai-memo-app, 브랜치 `main`)
- [x] Vite 프로젝트 생성 (`client/`, React + TypeScript, ESLint)
- [x] 생성된 파일 구조 설명 (index.html → main.tsx → App.tsx, useState 카운터 예제)
- [x] App.tsx 템플릿 정리 (`<h1>내 메모 앱</h1>`만 남김)
- [x] `src/types.ts`의 `Memo` 타입 작성 (id·title·content·createdAt, 모두 string)
- [ ] MemoForm (메모 추가)
- [ ] MemoList, MemoItem (목록 표시)
- [ ] 삭제
- [ ] 수정
- [ ] localStorage 저장

## 다음 할 일
1. MemoForm 컴포넌트: 제목·내용 입력 + [추가] 버튼. `useState`로 입력값 다루기 개념 설명부터 시작
