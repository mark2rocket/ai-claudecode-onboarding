---
name: ai-contents-week4
description: AI 컨텐츠 워크플로우 챌린지 4주차! 나만의 카드뉴스·릴스 제작 스킬 완성. "4주차", "Week 4", "ai-contents-week4", "스킬 만들기" 요청에 사용.
---

# Week 4: 나만의 콘텐츠 제작 스킬 만들기

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

- **Session 0 (복습 + 구조 이해)**: Phase A에서 Week 1~3 요약 + 스킬 구조 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 1 (카드뉴스 스킬 설계)**: Phase A에서 스킬 폴더 구조 + brand.md 역할 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 2 (카드뉴스 스킬 완성)**: Phase A에서 Human-in-the-loop 구조 + SKILL.md 작성 → Stop. Phase B에서 퀴즈 1개.
- **Session 3 (릴스 스킬 설계)**: Phase A에서 릴스 스킬 폴더 구조 + style.md 작성 → Stop. Phase B에서 퀴즈 1개.
- **Session 4 (릴스 스킬 완성)**: Phase A에서 릴스 Human-in-the-loop 체크리스트 + SKILL.md 작성 → Stop. Phase B에서 퀴즈 1개.
- **Session 5 (스킬 최적화)**: Phase A만. **퀴즈 없음.** 최적화 팁 6가지 안내 + 실습 → Stop.
- **Session 6 (배포 + 마무리)**: Phase A에서 배포 명령어 + 4주 마무리 정리 → Stop. Phase B에서 4주 마무리 퀴즈 1개.

---

## References 파일 맵

| 세션 | 파일 |
|------|------|
| Session 0 | `references/session0-review.md` (복습 + 스킬 구조 이해) |
| Session 1 | `references/session1-cardnews-design.md` (카드뉴스 스킬 설계) |
| Session 2 | `references/session2-cardnews-build.md` (카드뉴스 스킬 완성) |
| Session 3 | `references/session3-reels-design.md` (릴스 스킬 설계) |
| Session 4 | `references/session4-reels-build.md` (릴스 스킬 완성) |
| Session 5 | `references/session5-optimize.md` (스킬 최적화) |
| Session 6 | `references/session6-deploy.md` (배포 + 마무리) |

> 파일 경로는 이 SKILL.md 기준 상대경로다.
> 각 reference 파일은 `## EXPLAIN`, `## EXECUTE`, `## QUIZ` 섹션으로 구성된다.

---

## 진행 규칙

- 한 번에 한 세션씩 진행한다
- "다음", "skip", 세션 번호/이름으로 이동한다
- **기본 경로**: Session 0 → 1 → 2 → 3 → 4 → 5 → 6
- Session 6 완료 후 → "4주 챌린지 완주" 축하 메시지를 출력한다

---

## 시작

스킬 시작 시 아래 순서로 진행한다:

**1. Week 1~3 핵심 요약을 먼저 출력한다 (항상)**

```
📌 Week 1~3 복습
─────────────────────────────────────────────────
Week 1  AX 마인드셋   AI는 실무자, 나는 디렉터
Week 1  Memory        CLAUDE.md + Auto Memory
Week 1  Skill         /명령어로 워크플로우 실행
Week 2  카드뉴스      브리프→스크립트→HTML→PNG 파이프라인
Week 2  템플릿        완성형 예시 → 교체만 하면 새 작품
Week 3  릴스          HTML 애니메이션 → 화면녹화 → MP4
Week 3  Track 1       GIF+텍스트, FFmpeg, 자막+음성
─────────────────────────────────────────────────
Week 4에서는 이것들을 내 자동화 스킬로 만듭니다.
```

**2. 시작 세션을 선택한다**

### 전체 커리큘럼 (4주)

| Week | 주제 | 내용 |
|------|------|------|
| Week 1 | 기본 셋업 & 개념 | AX 마인드셋, 설치, 체험, 필수 기능 7개, CLI/git 기초 |
| Week 2 | 카드뉴스 워크플로우 | 기획 이론, 프롬프트 구체화, 파이프라인, 템플릿 |
| Week 3 | 영상 제작 워크플로우 | 릴스·홍보·온보딩·강의 영상 제작 자동화 |
| **Week 4** | 스킬 만들기 | 나만의 워크플로우를 Skill로 패키징 |

> 지금은 **Week 4**입니다.

---

### Week 4 세션 구성

| Session | 주제 | 핵심 체험 |
|-------|------|-----------|
| 0 | 복습 + 스킬 구조 이해 | 스킬 = 내 콘텐츠 공장 구조 파악 |
| 1 | 카드뉴스 스킬 설계 | brand.md + 폴더 구조 설계 |
| 2 | 카드뉴스 스킬 완성 | Human-in-the-loop + 첫 실행 |
| 3 | 릴스 스킬 설계 | style.md + 릴스 폴더 구조 설계 |
| 4 | 릴스 스킬 완성 | 체크리스트 + 화면녹화 완성 |
| 5 | 스킬 최적화 | 금지 목록, CSS 변수, Plan mode |
| 6 | 배포 + 마무리 | .agents/skills/ 배포 + 4주 완주 |

```json
AskUserQuestion({
  "questions": [{
    "question": "Week 4 어디서부터 시작할까요?",
    "header": "시작 세션",
    "options": [
      {"label": "Session 0: 복습 + 스킬 구조 이해", "description": "처음이라면 여기서 시작 — 기존 스킬 파일 열어보기"},
      {"label": "Session 1: 카드뉴스 스킬 설계", "description": "내 브랜드 정보 저장 + 파일 구조 설계"},
      {"label": "Session 3: 릴스 스킬 설계", "description": "카드뉴스 스킬 완성 후 여기로"},
      {"label": "Session 5: 스킬 최적화", "description": "스킬 만들었는데 결과가 마음에 안 들 때"}
    ],
    "multiSelect": false
  }]
})
```

> 시작 세션 선택 후 → 해당 세션의 Phase A부터 진행한다.
