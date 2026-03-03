# Block 3-1: Memory (기억 시스템)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/memory
> ```

## EXPLAIN

Claude Code의 기억 시스템은 두 가지로 이루어져 있습니다.

---

### ① CLAUDE.md — 내가 써주는 지시문 파일

**시스템 프롬프트** [쉬운 말: 대화 시작 전 AI에게 주는 사전 지시서] 역할을 하는 파일입니다.
새 대화를 시작할 때마다 Claude가 이 파일을 먼저 읽고 시작합니다.

예를 들어:
```
# 나의 Claude 지시문

- 나는 뷰티 유튜버입니다
- 모든 답변은 한국어로, 친근한 말투로 해주세요
- SNS 글은 항상 이모지를 포함해주세요
```

이 파일에 적어두면 매번 설명하지 않아도 됩니다.

---

### ② Auto Memory — Claude가 스스로 쓰는 기억 노트

Claude가 작업하면서 발견한 패턴, 선호도, 해결책을 **자동으로 파일에 기록**합니다.
다음 대화에서 자동으로 불러와 이전 맥락을 기억하는 것처럼 동작합니다.

> Auto Memory [쉬운 말: Claude의 자동 기억 노트] — Claude가 "이 사람은 이런 걸 좋아하는구나"라고 스스로 메모해두는 시스템

---

### 두 가지 비교

| 구분 | CLAUDE.md | Auto Memory |
|------|-----------|-------------|
| 누가 씀 | 내가 직접 | Claude가 자동으로 |
| 내용 | 규칙, 선호도, 역할 | 패턴, 디버깅 해결책, 발견한 것들 |
| 저장 위치 | 프로젝트 최상위 폴더 | `~/.claude/projects/.../memory/` |
| 불러오기 | 매 대화마다 자동 | 매 대화마다 자동 (첫 200줄) |

---

## EXECUTE

세 가지를 순서대로 해보세요:

**1단계:** 아래 명령으로 CLAUDE.md를 자동 생성합니다
```
/init
```
> `/init` [쉬운 말: 초기화 명령] — 현재 폴더를 분석해서 CLAUDE.md를 자동으로 만들어줍니다

**2단계:** 메모리 현황을 확인합니다
```
/memory
```

**3단계:** Claude에게 개인 정보를 알려주고, Auto Memory에 기록되는지 확인합니다
```
나는 뷰티 콘텐츠 크리에이터야. 인스타그램 팔로워가 2만명이고 유튜브도 운영 중이야.
```

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다.

```json
AskUserQuestion({
  "questions": [{
    "question": "CLAUDE.md와 Auto Memory의 차이는?",
    "header": "Quiz 3-1",
    "options": [
      {"label": "CLAUDE.md는 내가 쓰는 지시문, Auto Memory는 Claude가 자동으로 쓰는 메모", "description": "둘 다 매 대화마다 자동으로 불러와진다"},
      {"label": "CLAUDE.md는 임시 저장, Auto Memory는 영구 저장", "description": "둘 다 파일로 저장됨"},
      {"label": "차이 없이 같은 것이다", "description": "역할이 다름"}
    ],
    "multiSelect": false
  }]
})
```

정답: **1번**.
