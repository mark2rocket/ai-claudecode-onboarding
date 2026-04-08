---
name: ai-contents-week1
description: AI 컨텐츠 워크플로우 챌린지의 첫주! AX 마인드셋과 클로드코드 기본과 필수 기능에 대해 알아보기! "1주차", "Week 1", "ai-contents-week1" 요청에 사용.
---

# Week 1: AI 컨텐츠 워크플로우 챌린지

이 스킬이 호출되면 아래 **STOP PROTOCOL**을 반드시 따른다.

---

## STOP PROTOCOL — 절대 위반 금지

> 이 프로토콜은 이 스킬의 최우선 규칙이다.
> 아래 규칙을 위반하면 수업이 망가진다.

### 각 세션은 반드시 2턴에 걸쳐 진행한다

```
┌─ Phase A (첫 번째 턴) ──────────────────────────────┐
│ 1. references/에서 해당 세션 파일의 EXPLAIN 섹션을 읽는다    │
│ 2. 기능을 설명한다                                        │
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

### 공식 문서 URL 출력 (절대 누락 금지)

모든 세션의 Phase A 시작 시, 해당 reference 파일 상단의 `> 공식 문서:` URL을 **반드시 그대로 출력**한다.

```
📖 공식 문서: [URL]
```

- reference 파일에 URL이 여러 개 있으면 전부 출력한다
- URL을 요약하거나 생략하지 않는다
- 참가자가 직접 클릭해서 공식 문서를 볼 수 있어야 한다

### Phase A 종료 시 필수 문구

Phase A의 마지막에는 반드시 아래 형태의 문구를 출력하고 Stop한다:

```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

이 문구 이후에 어떤 도구 호출(AskUserQuestion 포함)이나 추가 텍스트도 출력하지 않는다.

### 세션 특수 규칙

- **Session 0 (AX 마인드셋)**: Phase A 설명 + 실행 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 1 (Setup)**: 퀴즈 없음. Phase A에서 설명+실행 안내 → Stop. Phase B에서 완료 확인만.
- **Session 2 (Experience)**: Phase A에서 3가지 데모 안내 → Stop. Phase B에서 체험 소감 확인.
- **Session 3 (Why)**: ⚠️ 특수 세션 — STOP PROTOCOL의 예외. Phase A에서 4컷 만화 보여준 뒤 AskUserQuestion으로 Quiz 1 출제 → 피드백 → Stop. Phase B에서 Quiz 2 + 영상 안내.
- **Session 4 (What)**: 4-1~4-4는 각각 독립 세션(Phase A → Phase B). 4-5는 간단 소개 세션(Phase A만).
- **Session 4-5 (Agent Teams · Hook · Plugin)**: Phase A만. 퀴즈 없음. 설명 + Session 4 전체 관계도 보여주고 Session 5로 이동.
- **Session 5 (Basics)**: Phase A에서 설명+실행 안내 → Stop. Phase B에서 퀴즈 2개 연속.

---

## References 파일 맵

| 세션 | 파일 |
|------|------|
| Session 0 | `references/session0-mindset.md` (AX 마인드셋) |
| Session 1 | `references/session1-setup.md` |
| Session 2 | `references/session2-experience.md` |
| Session 3 | `references/session3-why.md` |
| Session 4-1 ~ 4-4 | `references/session4-1-memory.md` ~ `references/session4-4-subagent.md` |
| Session 4-5 | `references/session4-5-advanced.md` (Agent Teams · Hook · Plugin 간단 소개 + 전체 관계도) |
| Session 5 | `references/session5-basics.md` |

> 파일 경로는 이 SKILL.md 기준 상대경로다.
> 각 reference 파일은 `## EXPLAIN`, `## EXECUTE`, `## QUIZ` 섹션으로 구성된다.

---

## 진행 규칙

- 한 번에 한 세션씩 진행한다
- "다음", "skip", 세션 번호/이름으로 이동한다
- Claude Code 관련 질문이 오면 claude-code-guide 에이전트(내장 도구)로 답변한다. 답변 후 사용자가 직접 따라할 수 있게 단계별로 안내하고, 질문할 때는 AskUserQuestion을 사용한다. 내장 에이전트 답변이 부정확하다고 판단되면, 공식 문서를 `curl`로 파일에 저장한 뒤 Read 툴로 꼼꼼히 읽고 정확한 정보로 다시 답한다 (WebFetch는 요약/손실 위험이 있으므로 사용하지 않는다)
- Session 3(Why) 완료 후 → Session 4(What)으로 이어진다
- Session 4-5 완료 후 → session4-5-advanced.md 하단의 전체 관계도를 보여주고 Session 5로 이동한다

---

## 시작

스킬 시작 시 **전체 커리큘럼 개요**를 먼저 보여주고, Week 1 세션 선택 질문을 한다.

### 전체 커리큘럼 (4주)

| Week | 주제 | 내용 |
|------|------|------|
| **Week 1** | 기본 셋업 & 개념 | AX 마인드셋, 설치, 체험, 필수 기능 7개, CLI/git 기초 |
| Week 2 | 카드뉴스 워크플로우 | Claude로 카드뉴스 기획·제작·배포 자동화 |
| Week 3 | 영상 워크플로우 | 스크립트·자막·섬네일·업로드 자동화 |
| Week 4 | 스킬 만들기 | 나만의 워크플로우를 Skill로 패키징 |

> 지금은 **Week 1**입니다. Week 2~4는 이후 스킬에서 진행합니다.

---

### Week 1 세션 구성

| Session | 주제 | 내용 |
|-------|------|------|
| 0 | AX 마인드셋 | AI는 실무자, 나는 디렉터 (퀴즈 1개) |
| 1 | Setup | 첫 실행 설정 + 에디터 |
| 2 | Experience | Working Backward 데모 3가지 |
| 3 | Why | 왜 CLI? 왜 터미널? (퀴즈 2개) |
| 4 | What | 7개 기능 소개 |
| 5 | Basics | CLI + git + GitHub (퀴즈 3개) |

```json
AskUserQuestion({
  "questions": [{
    "question": "Week 1 어디서부터 시작할까요?",
    "header": "시작 세션",
    "options": [
      {"label": "Session 0: AX 마인드셋", "description": "AI는 실무자, 나는 디렉터 — 처음이라면 여기서 시작"},
      {"label": "Session 1: Setup", "description": "첫 실행 설정 + 에디터"},
      {"label": "Session 2: Experience", "description": "Working Backward 데모 3가지"},
      {"label": "Session 3 이후부터", "description": "Session 3(Why), 4(What), 5(Basics) — 번호를 말해주세요"}
    ],
    "multiSelect": false
  }]
})
```

> "Session 3 이후부터" 선택 시: "어느 세션으로 이동할까요? Session 3(Why), Session 4-1(Memory), Session 4-2(Skill), Session 5(Basics) 중 말씀해주세요."

> 시작 세션 선택 후 → 해당 세션의 Phase A부터 진행한다.
