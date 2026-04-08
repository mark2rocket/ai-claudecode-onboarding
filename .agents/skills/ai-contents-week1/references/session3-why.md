# Session 3: Why

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/how-claude-code-works#에이전트-루프
> ```

> Session 3는 설명 없이 바로 퀴즈로 진행하는 특수 블록이다.
> Phase A에서 4컷 만화 + 퀴즈 1을 진행하고, Phase B에서 퀴즈 2 + 영상을 안내한다.

---

## EXPLAIN

### 🎬 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 새암의 일상    ║  ║  2. 한계           ║
║                    ║  ║                    ║
║  (´-ω-`) 새암      ║  ║  (╥﹏╥) 새암       ║
║  [chat.claude.ai]  ║  ║  "파일은 내가 저장 ║
║  매번 복붙...      ║  ║   매번 같은 설명   ║
║  매번 설명...      ║  ║   반복하고...      ║
║  매번 저장...      ║  ║   자동화는 꿈도    ║
║                    ║  ║   못 꾸겠어"       ║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. Claude Code    ║  ║  4. 새암의 깨달음  ║
║     발견           ║  ║                    ║
║  ( ´▽`) 새암       ║  ║  (≧▽≦) 새암       ║
║  "파일 직접 접근   ║  ║  "AI가 내 컴퓨터  ║
║   + Skill로        ║  ║   에서 직접 일하   ║
║   자동화된다고?!"  ║  ║   는 거구나!"      ║
║                    ║  ║                    ║
║    ╔═══════╗       ║  ║    ╔═══════╗       ║
║    ║ ★   ★ ║ Claude║  ║    ║ ★   ★ ║ Claude║
║    ╚═══╦═══╝ Code  ║  ║    ╚═══╦═══╝       ║
║  [파일][Skill][MCP]║  ║  "뭐든 시키면 돼요"║
╚════════════════════╝  ╚════════════════════╝
```

---

## QUIZ-1

### Quiz 1: claude.ai vs Claude Code

```json
AskUserQuestion({
  "questions": [{
    "question": "claude.ai 웹과 Claude Code의 가장 큰 차이는?",
    "header": "Quiz 1",
    "options": [
      {"label": "Claude Code가 더 똑똑한 AI를 쓴다", "description": "같은 Claude 모델을 씀"},
      {"label": "claude.ai는 무료, Claude Code는 유료", "description": "요금제는 다르지만 그게 핵심 차이는 아님"},
      {"label": "Claude Code는 내 컴퓨터 파일과 프로그램을 직접 제어할 수 있다", "description": "파일 읽기/쓰기, Skill 자동화, MCP 연결 등"},
      {"label": "Claude Code는 개발자만 쓸 수 있다", "description": "지금 여기서 비개발자가 쓰고 있음"}
    ],
    "multiSelect": false
  }]
})
```

정답: 3번. 해설로 아래 도식을 보여준다:

```
claude.ai:    대화 → AI 답변 → 내가 복붙·저장
Claude Code:  대화 → AI가 직접 파일 편집·저장·실행
```

---

## QUIZ-2

### Quiz 2: 왜 비개발자용 툴이 아니라 Claude Code인가?

```json
AskUserQuestion({
  "questions": [{
    "question": "왜 Claude CoWork 같은 비개발자용 툴이 아니라 Claude Code를 써야 할까요?",
    "header": "Quiz 2",
    "options": [
      {"label": "비개발자용 도구가 별로라서", "description": "CoWork도 좋지만 Claude Code가 자유도의 끝판왕"},
      {"label": "Claude Code가 무료라서", "description": "유료"},
      {"label": "개발자만 쓸 수 있어서", "description": "비개발자도 씀. 지금 여기서."},
      {"label": "모두가 코딩으로 새로운 차원의 일을 하게 될 것이라서", "description": "코딩 = 개발자 전유물이 아니라 모든 지식노동의 도구가 된다"}
    ],
    "multiSelect": false
  }]
})
```

정답: 4번. 해설:

```
비개발자용 툴  → 정해진 UI 안에서의 생산성
Claude Code   → 코딩이라는 새로운 차원의 일

토큰을 많이 쓸 수 있다
= 엄청나게 많은 노동력을 가진 사람이 된다
```

오늘만 지나면 출발선에 서게 된다.

### 영상 시청

아래 영상을 시청하라고 안내한다:

https://youtu.be/JI8S9T7r2SQ?si=aGYqNMqklAeL9pZs&t=23

> "AI 분야가 지식 노동보다 더 큰 규모가 될 수 있는 '소프트웨어 공장 카테고리'라고 보고 있다."
