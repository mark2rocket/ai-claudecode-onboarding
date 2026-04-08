---
name: ai-contents-week3
description: AI 컨텐츠 워크플로우 챌린지 3주차! 영상 제작 워크플로우 - 릴스부터 Remotion까지. "3주차", "Week 3", "ai-contents-week3", "영상", "릴스", "remotion" 요청에 사용.
---

# Week 3: 영상 제작 워크플로우

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

- **Session 0 (복습 + 기획)**: Phase A에서 Week 1~2 요약 + 영상 기획 중요성 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 1 (트랙 선택)**: Phase A에서 Track 1/Track 2 설명 + 선택 기준 안내 → Stop. **Phase B의 QUIZ가 트랙 선택** — 선택 결과에 따라 Track 1은 Session 2로, Track 2는 Session 6으로 이동.
- **Session 2 (코딩만으로 짧은 릴스)**: Track 1. Phase A에서 HTML 애니메이션 → 화면 녹화 방법 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 3 (GIF + 코딩으로 긴 릴스)**: Track 1. Phase A에서 GIF 배경 + 텍스트 오버레이 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 4 (GIF + 영상소스로 긴 릴스)**: Track 1. Phase A에서 FFmpeg 활용 + 영상 합성 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 5 (자막 + 음성 완성 릴스)**: Track 1. Phase A에서 SRT 자막 + 음성 합성 설명 → Stop. **퀴즈 없음.** 완성 영상이 증거.
- **Session 6 (홍보 영상 - Remotion)**: Track 2. Phase A에서 Remotion 기본 구조 + 홍보 영상 설계 안내 → Stop. Phase B에서 퀴즈 1개.
- **Session 7 (온보딩 영상 - Remotion)**: Track 2. Phase A에서 온보딩 구조 + Remotion 컴포넌트 설명 → Stop. Phase B에서 퀴즈 1개.
- **Session 8 (강의 영상 - Remotion)**: Track 2. Phase A에서 강의 영상 구조 + 슬라이드 애니메이션 설명 → Stop. **퀴즈 없음.** 완성 영상이 증거.
- **Session 9 (복습 + 템플릿)**: Phase A에서 Session 1~8 흐름 정리 + 영상 템플릿 3종 생성 안내 → Stop. Phase B에서 퀴즈 1개 + Week 3 마무리.

---

## References 파일 맵

| 세션 | 파일 |
|------|------|
| Session 0 | `references/session0-review.md` (복습 + 기획의 중요성) |
| Session 1 | `references/session1-track-select.md` (트랙 선택: 릴스 vs Remotion) |
| Session 2 | `references/session2-code-reels.md` (코딩만으로 짧은 릴스) |
| Session 3 | `references/session3-gif-reels.md` (GIF + 코딩으로 긴 릴스) |
| Session 4 | `references/session4-video-reels.md` (GIF + 영상소스로 긴 릴스) |
| Session 5 | `references/session5-full-reels.md` (자막 + 음성 완성 릴스) |
| Session 6 | `references/session6-promo-remotion.md` (홍보 영상 - Remotion) |
| Session 7 | `references/session7-onboarding-remotion.md` (온보딩 영상 - Remotion) |
| Session 8 | `references/session8-lecture-remotion.md` (강의 영상 - Remotion) |
| Session 9 | `references/session9-template.md` (복습 + 영상 템플릿 3종) |

> 파일 경로는 이 SKILL.md 기준 상대경로다.
> 각 reference 파일은 `## EXPLAIN`, `## EXECUTE`, `## QUIZ` 섹션으로 구성된다.

---

## 진행 규칙

- 한 번에 한 세션씩 진행한다
- "다음", "skip", 세션 번호/이름으로 이동한다
- **Track 1 경로**: Session 0 → 1 → 2 → 3 → 4 → 5 → 9
- **Track 2 경로**: Session 0 → 1 → 6 → 7 → 8 → 9
- Session 9는 두 트랙 모두의 마무리 세션이다
- Session 9 완료 후 → Week 4 예고 멘트를 출력한다

---

## 시작

스킬 시작 시 아래 순서로 진행한다:

**1. Week 1~2 핵심 요약을 먼저 출력한다 (항상)**

```
📌 Week 1~2 복습
─────────────────────────────────────────────────
Week 1  AX 마인드셋   AI는 실무자, 나는 디렉터
Week 1  Memory        CLAUDE.md + Auto Memory
Week 1  Skill         /명령어로 워크플로우 실행
Week 2  기획          스펙이 없으면 Claude가 추측한다
Week 2  프롬프트      한 줄 → 대상·분량·구조·디자인 진화
Week 2  파이프라인    브리프 → 스크립트 → HTML → 완성
Week 2  템플릿        완성형 예시 → 교체만 하면 새 작품
─────────────────────────────────────────────────
Week 3에서는 이것들을 영상 제작에 직접 적용합니다.
```

**2. 시작 세션을 선택한다**

### 전체 커리큘럼 (4주)

| Week | 주제 | 내용 |
|------|------|------|
| Week 1 | 기본 셋업 & 개념 | AX 마인드셋, 설치, 체험, 필수 기능 7개, CLI/git 기초 |
| Week 2 | 카드뉴스 워크플로우 | 기획 이론, 프롬프트 구체화, 파이프라인, 템플릿 |
| **Week 3** | 영상 제작 워크플로우 | 릴스·홍보·온보딩·강의 영상 제작 자동화 |
| Week 4 | 스킬 만들기 | 나만의 워크플로우를 Skill로 패키징 |

> 지금은 **Week 3**입니다.

---

### Week 3 세션 구성

| Session | 트랙 | 주제 | 핵심 체험 |
|-------|------|------|-----------|
| 0 | 공통 | 복습 + 기획의 중요성 | 영상은 카드뉴스보다 기획 요소가 많다 |
| 1 | 공통 | 트랙 선택 | 릴스(Track 1) vs Remotion(Track 2) |
| 2 | Track 1 | 코딩만으로 짧은 릴스 | HTML 애니메이션 → 화면 녹화 |
| 3 | Track 1 | GIF + 코딩으로 긴 릴스 | GIF 배경 + 텍스트 오버레이 |
| 4 | Track 1 | GIF + 영상소스로 긴 릴스 | FFmpeg으로 영상 합성 |
| 5 | Track 1 | 자막 + 음성 완성 릴스 | SRT + TTS + FFmpeg 최종 합성 |
| 6 | Track 2 | 홍보 영상 - Remotion | React 컴포넌트로 홍보 영상 |
| 7 | Track 2 | 온보딩 영상 - Remotion | 단계별 제품 설명 영상 |
| 8 | Track 2 | 강의 영상 - Remotion | 슬라이드 + 코드 애니메이션 |
| 9 | 공통 | 복습 + 영상 템플릿 | 재사용 가능한 영상 브리프 3종 |

```json
AskUserQuestion({
  "questions": [{
    "question": "Week 3 어디서부터 시작할까요?",
    "header": "시작 세션",
    "options": [
      {"label": "Session 0: 복습 + 기획의 중요성", "description": "Week 1~2 돌아보기 + 영상 기획이 왜 더 중요한지 — 처음이라면 여기서 시작"},
      {"label": "Session 1: 트랙 선택", "description": "릴스(Track 1) vs Remotion(Track 2) — 내 목적에 맞는 트랙 고르기"},
      {"label": "Track 1 - Session 2부터", "description": "코딩만으로 짧은 릴스 → GIF → 영상소스 → 자막/음성 순서로"},
      {"label": "Track 2 - Session 6부터", "description": "Remotion으로 홍보/온보딩/강의 영상 — 번호를 말해주세요"}
    ],
    "multiSelect": false
  }]
})
```

> 시작 세션 선택 후 → 해당 세션의 Phase A부터 진행한다.
