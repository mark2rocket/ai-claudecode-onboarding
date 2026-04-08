---
name: ai-contents-week2
description: AI 컨텐츠 워크플로우 챌린지 2주차! 카드뉴스 기획부터 파이프라인·템플릿 완성까지. "2주차", "Week 2", "ai-contents-week2", "카드뉴스" 요청에 사용.
---

# Week 2: 카드뉴스 워크플로우

이 스킬이 호출되면 아래 **STOP PROTOCOL**을 반드시 따른다.

---

## STOP PROTOCOL — 절대 위반 금지

> 이 프로토콜은 이 스킬의 최우선 규칙이다.
> 아래 규칙을 위반하면 수업이 망가진다.

### 각 세션은 반드시 2턴에 걸쳐 진행한다

```
┌─ Phase A (첫 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 세션 파일의 EXPLAIN 섹션을 읽는다    │
│ 2. 내용을 설명한다                                        │
│ 3. references/에서 해당 세션 파일의 EXECUTE 섹션을 읽는다    │
│ 4. "지금 직접 실행해보세요"라고 안내한다                     │
│ 5. ⛔ 여기서 반드시 STOP. 턴을 종료한다.                    │
│                                                          │
│ ❌ 절대 하지 않는 것: 퀴즈 출제, QUIZ 섹션 읽기             │
│ ❌ 절대 하지 않는 것: AskUserQuestion 호출                  │
│ ❌ 절대 하지 않는 것: "실행해봤나요?" 질문                   │
└──────────────────────────────────────────────────────────┘

  ⬇️ 사용자가 돌아와서 "했어", "완료", "다음" 등을 입력한다

┌─ Phase B (두 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 세션 파일의 QUIZ 섹션을 읽는다       │
│ 2. AskUserQuestion으로 퀴즈를 출제한다                     │
│ 3. 정답/오답 피드백을 준다                                 │
│ 4. 다음 세션으로 이동할지 AskUserQuestion으로 묻는다         │
│ 5. ⛔ 다음 세션을 시작하면 다시 Phase A부터.                │
└──────────────────────────────────────────────────────────┘
```

### 핵심 금지 사항 (절대 위반 금지)

1. **Phase A에서 AskUserQuestion을 호출하지 않는다** — 설명 + 실행 안내 후 바로 Stop
2. **Phase A에서 퀴즈를 내지 않는다** — QUIZ 섹션은 Phase B에서만 읽는다
3. **Phase A에서 "실행해봤나요?"를 묻지 않는다** — 사용자가 먼저 말할 때까지 기다린다
4. **한 턴에 EXPLAIN + QUIZ를 동시에 하지 않는다** — 반드시 2턴으로 나눈다

### Phase A 종료 시 필수 문구

Phase A의 마지막에는 반드시 아래 형태의 문구를 출력하고 Stop한다:

```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

이 문구 이후에 어떤 도구 호출(AskUserQuestion 포함)이나 추가 텍스트도 출력하지 않는다.

### 세션 특수 규칙

- **Session Recap (Week 1 복습)**: Phase A만. 퀴즈 없음. 7줄 요약 + Week 1→2 연결 설명 후 자동으로 Session HTML로 이동.
- **Session HTML (왜 HTML인가?)**: Phase A 설명 + 실행 안내 → Stop. Phase B에서 퀴즈 1개. 완료 후 Session 0으로 이동.
- **Session 0 (기획 = 추측 통제)**: Phase A 설명 + 실행 안내 → Stop. Phase B에서 퀴즈 1개. 완료 후 Session 1로 이동.
- **Session 1 (주제 + 대상 + 분량)**: Phase A에서 2단계 프롬프트 비교 실행 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 2 (스토리구조 + 후킹)**: Phase A에서 스토리 구조 틀 + 후킹 기법 설명 + 실행 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 3 (디자인 스펙 + 레이아웃)**: Phase A에서 스펙 4요소 + 레이아웃 3요소 설명 + 실행 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 4 (HTML 생성)**: Phase A에서 content_brief.md → HTML 변환 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 5 (PNG 저장)**: Phase A에서 HTML → PNG 변환 안내 → Stop. **퀴즈 없음.** PNG 파일이 증거.
- **Session 6 (전체 흐름 실행)**: Phase A에서 5단계 순서대로 실행 안내 → Stop. **퀴즈 없음.** 완성 결과물로 마무리.
- **Session 7 (재사용 템플릿)**: Phase A에서 3종 생성 + 교체 체험 안내 → Stop. Phase B에서 퀴즈 1개 + Week 2 마무리.

---

## References 파일 맵

| 세션 | 파일 |
|------|------|
| Session Recap | `references/session-recap.md` (Week 1 복습 + Week 2 연결) |
| Session HTML | `references/session-html-osmu.md` (왜 HTML인가? OSMU 개념) |
| Session 0 | `references/session0-planning.md` (기획 = 추측 통제) |
| Session 1 | `references/session1-brief.md` (주제 + 대상 + 분량) |
| Session 2 | `references/session2-story.md` (스토리구조 + 후킹) |
| Session 3 | `references/session3-design.md` (디자인 스펙 + 레이아웃) |
| Session 4 | `references/session4-html.md` (HTML 생성) |
| Session 5 | `references/session5-png.md` (PNG 저장) |
| Session 6 | `references/session6-pipeline.md` (전체 흐름 실행) |
| Session 7 | `references/session7-template.md` (재사용 템플릿 3종) |

> 파일 경로는 이 SKILL.md 기준 상대경로다.
> 각 reference 파일은 `## EXPLAIN`, `## EXECUTE`, `## QUIZ` 섹션으로 구성된다.

---

## 진행 규칙

- 한 번에 한 세션씩 진행한다
- "다음", "skip", 세션 번호/이름으로 이동한다
- 각 세션의 프롬프트는 이전 세션에서 쌓인 스펙이 누적되는 방식으로 진화한다
- 실습 결과물(HTML, PNG 파일)은 이후 세션 비교에 활용한다
- Session 5 완료 후 → Session 6(전체 흐름)으로 자연스럽게 이어진다
- Session 6 완료 후 → Session 7(템플릿)으로 자연스럽게 이어진다
- Session 7 완료 후 → Week 3 예고 멘트를 출력한다

---

## 시작

스킬 시작 시 아래 순서로 진행한다:

**1. Week 1 핵심 요약을 먼저 출력한다 (항상)**

```
📌 Week 1 복습
─────────────────────────────────────────────────
AX 마인드셋  AI는 실무자, 나는 디렉터
Memory      CLAUDE.md(내가 씀) + Auto Memory(Claude)
Skill       /명령어 하나로 워크플로우 실행
MCP         외부 도구(Slack·Notion 등) 연결
Subagent    탐색·분석을 에이전트에 위임
Agent Teams 여러 에이전트가 협업해서 결과물 생성
Hook/Plugin 자동 실행·기능 확장
─────────────────────────────────────────────────
Week 2에서는 이것들을 카드뉴스 제작에 직접 적용합니다.
```

**2. 복습 세션 여부를 묻는다**

```json
AskUserQuestion({
  "questions": [{
    "question": "Week 1 복습 세션을 볼까요?",
    "header": "Week 1 복습",
    "options": [
      {"label": "복습 세션 보기", "description": "Week 1 → Week 2 연결을 4컷 만화로 확인 (5분)"},
      {"label": "바로 시작", "description": "Session HTML(왜 HTML인가?) → Session 0 순서로 시작"}
    ],
    "multiSelect": false
  }]
})
```

> "복습 세션 보기" 선택 시 → `references/session-recap.md` 읽고 내용 출력 → 자동으로 Session HTML로 이동
> "바로 시작" 선택 시 → 자동으로 Session HTML로 이동 → Session HTML 완료 후 아래 세션 선택 질문으로 이동

**3. 세션 선택 질문**

### 전체 커리큘럼 (4주)

| Week | 주제 | 내용 |
|------|------|------|
| Week 1 | 기본 셋업 & 개념 | AX 마인드셋, 설치, 체험, 필수 기능 7개, git 기초 |
| **Week 2** | 카드뉴스 워크플로우 | 기획, 스토리+후킹, 디자인, HTML, PNG, 템플릿 |
| Week 3 | 영상 워크플로우 | 릴스·Remotion 영상 제작 자동화 |
| Week 4 | 스킬 만들기 | 나만의 워크플로우를 Skill로 패키징 |

> 지금은 **Week 2**입니다.

---

### Week 2 세션 구성

| Session | 주제 | 핵심 체험 |
|---------|------|-----------|
| 0 | 기획 = 추측 통제 | 스펙이 없으면 Claude가 전부 결정한다 |
| 1 | 주제 + 대상 + 분량 | 세 가지 정보가 결과물 전체를 바꾼다 |
| 2 | 스토리구조 + 후킹 | 읽히는 흐름 + 클릭하게 만드는 제목 |
| 3 | 디자인 스펙 + 레이아웃 | 수치가 디자이너 역할을 한다 |
| 4 | HTML 생성 | 스펙 → 브라우저 카드 시각화 |
| 5 | PNG 저장 | HTML → SNS 업로드용 이미지 |
| 6 | 전체 흐름 실행 | 5단계를 한 번에 순서대로 실행 |
| 7 | 재사용 템플릿 | 완성형 HTML 3종 → 다음번엔 교체만 |

```json
AskUserQuestion({
  "questions": [{
    "question": "Week 2 어디서부터 시작할까요?",
    "header": "시작 세션",
    "options": [
      {"label": "Session 0: 기획 = 추측 통제", "description": "처음이라면 여기서 시작 — Claude의 추측을 줄이는 것이 기획"},
      {"label": "Session 1: 주제 + 대상 + 분량", "description": "세 가지 정보만으로 결과물이 얼마나 달라지는지 체험"},
      {"label": "Session 2: 스토리구조 + 후킹", "description": "읽히는 흐름 + 클릭하게 만드는 제목 기법"},
      {"label": "Session 4 이후부터", "description": "Session 4(HTML), 5(PNG), 6(전체 흐름), 7(템플릿) — 번호를 말해주세요"}
    ],
    "multiSelect": false
  }]
})
```

> 시작 세션 선택 후 → 해당 세션의 Phase A부터 진행한다.
