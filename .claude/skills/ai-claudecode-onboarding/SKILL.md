# Day 1: Claude Code 온보딩 — 1인 크리에이터를 위한 워크플로우 챌린지

> 비개발자 1인 사업가·크리에이터를 위한 Claude Code 온보딩.
> 슬라이드를 보는 강의가 아닙니다. Claude가 직접 가르치고, 질문하고, 실습을 안내합니다.

---

## 진행 규칙 (반드시 따를 것)

이 스킬은 **2단계 블록 시스템**으로 진행된다.

- **Phase A**: 기능 설명 + 실행 안내 → 그 자리에서 멈춘다 (퀴즈 금지, 추가 질문 금지)
- **Phase B**: 사용자가 "완료" 또는 "다음"이라고 돌아오면 → AskUserQuestion으로 퀴즈 → 피드백 → 다음 블록 안내

### 엄격한 규칙
1. Phase A에서 절대 AskUserQuestion을 호출하지 않는다
2. Phase A에서 퀴즈를 내지 않는다 — QUIZ 섹션은 Phase B 전용이다
3. Phase A에서 "해보셨나요?", "어떠셨나요?" 같은 질문을 하지 않는다
4. 각 블록 시작 시 반드시 공식 문서 URL을 출력한다
5. 모든 Phase A는 반드시 이 문장으로 끝낸다:
   > "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## 블록 구성

| 블록 | 주제 | 형식 | 중요도 |
|------|------|------|--------|
| 0 | 설치 & 첫 실행 | Phase A만 (퀴즈 없음) | 필수 |
| 1 | 7일 후 미리 체험 | 데모 3개 + Phase B 소감 | 필수 |
| 2 | 왜 터미널인가? | 퀴즈 1(Phase A) + 퀴즈 2(Phase B) | 필수 |
| 3-필수 | 핵심 기능 3가지 (Memory·Skill·MCP) | 각 Phase A + B | **오늘 당장 쓸 것** |
| 3-심화 | 심화 기능 4가지 (Subagent·Teams·Hook·Plugin) | 각 Phase A + B | 나중에 필요할 때 |
| 4 | 터미널 & git 기초 | Phase A + Phase B 퀴즈 3개 | **선택 (협업·버전관리 필요 시)** |

---

## 시작

아래 안내를 보여주고, AskUserQuestion으로 어디서 시작할지 물어본다.

```
📋 오늘의 여정

⭐ 필수 코스 (모든 분께 추천)
  Block 0 → 설치가 안 되어 있다면 여기서 시작
  Block 1 → 7일 후 모습을 먼저 체험
  Block 2 → 왜 터미널을 써야 하는가?
  Block 3-필수 → 오늘 당장 쓸 핵심 기능 3가지 (Memory·Skill·MCP)

🔧 심화 코스 (여유 있을 때)
  Block 3-심화 → Subagent·Agent Teams·Hook·Plugin
  Block 4 → 터미널 & git 기초 (협업·버전관리 필요 시, 선택)
```

```json
AskUserQuestion({
  "questions": [{
    "question": "어느 블록부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0: 설치 & 첫 실행", "description": "Claude Code를 처음 설치하는 분"},
      {"label": "Block 1: 7일 후 미리 체험", "description": "설치는 됐고 바로 체험하고 싶은 분"},
      {"label": "Block 3-필수: 핵심 기능 3가지", "description": "오늘 당장 쓸 Memory·Skill·MCP부터"},
      {"label": "Block 2: 왜 터미널인가?", "description": "철학적 이유가 먼저 궁금한 분"}
    ],
    "multiSelect": false
  }]
})
```

선택에 따라 해당 references/ 파일을 읽고 그대로 진행한다.

- Block 0 → `references/block0-setup.md`
- Block 1 → `references/block1-experience.md`
- Block 2 → `references/block2-why.md`
- Block 3 필수 → `references/block3-1-memory.md` → `block3-2-skill.md` → `block3-3-mcp.md` → `block3-summary.md`
- Block 3 심화 → `references/block3-4-subagent.md` → `block3-5-agent-teams.md` → `block3-6-hook.md` → `block3-7-plugin.md`
- Block 4 (선택) → `references/block4-basics.md`
