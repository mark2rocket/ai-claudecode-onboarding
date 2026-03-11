# Block 4-3: MCP

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/mcp
> ```

---

## EXPLAIN

### 🎬 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 새암의 요청    ║  ║  2. Claude의 한계  ║
║                    ║  ║                    ║
║  (´-ω-`) 새암      ║  ║    ╔═══════╗       ║
║  "오늘 슬랙에서    ║  ║    ║ X   X ║       ║
║   온 메시지 중     ║  ║    ║  ~~~  ║ Claude║
║   중요한 거 요약   ║  ║    ╚═══╦═══╝       ║
║   해줘"            ║  ║      ══╩══         ║
║                    ║  ║  "슬랙에 접근할    ║
║                    ║  ║   권한이 없어요... ║
║                    ║  ║   저는 여기 안에만"║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. MCP 연결       ║  ║  4. 연결 후        ║
║                    ║  ║                    ║
║  ( ´▽`) 새암       ║  ║    ╔═══════╗       ║
║  "MCP로 슬랙을     ║  ║    ║ ★   ★ ║       ║
║   Claude에          ║  ║    ║  ▲▲▲  ║ Claude║
║   연결하면 된다고?"║  ║    ╚═══╦═══╝       ║
║                    ║  ║      ══╩══         ║
║  Claude ══MCP══▶   ║  ║  "슬랙 메시지      ║
║  [Slack] [Notion]  ║  ║   읽어올게요!      ║
║  [Calendar] [...]  ║  ║   오늘 핵심 3개:"  ║
╚════════════════════╝  ╚════════════════════╝
```

**Claude는 기본적으로 터미널 안에 갇혀 있다.**
MCP는 Claude가 외부 세계(Slack, Notion, Calendar 등)와 연결되는 플러그다.

---

### MCP란?

```
기본 Claude:
  새암 ─────────▶ Claude ─────────▶ 터미널 안에서만

MCP 연결 후:
  새암 ─────────▶ Claude ══MCP══▶ Slack
                              ══MCP══▶ Notion
                              ══MCP══▶ Calendar
                              ══MCP══▶ ...
```

MCP(Model Context Protocol)는 Anthropic이 만든 **오픈 표준**.
어떤 서비스든 MCP 서버만 있으면 Claude에 연결할 수 있다.

---

### 내가 쓸 수 있는 MCP 예시

| MCP 서버 | 하는 일 |
|----------|---------|
| Slack MCP | 메시지 읽기/쓰기 |
| Google Calendar MCP | 일정 확인/추가 |
| Notion MCP | 페이지 읽기/편집 |
| GitHub MCP | 코드 관리 |
| 브라우저 MCP | 웹페이지 읽기/자동화 |

---

## EXECUTE

Claude에게 직접 물어보자:

```
MCP가 뭔지 쉽게 설명해줘.
내가 유튜버/1인 사업자라면 유용하게 쓸 수 있는 MCP 서버 예시 3개도 알려줘
```

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "MCP를 한 마디로 말하면?",
    "header": "Quiz 4-3",
    "options": [
      {"label": "Claude 안에 내장된 기능", "description": "MCP는 외부 연결이지 내장이 아님"},
      {"label": "프로그래밍 언어의 일종", "description": "언어가 아니라 연결 프로토콜"},
      {"label": "Claude와 외부 도구를 연결하는 플러그", "description": "Slack, Calendar 등을 Claude에 꽂는 표준 방식"}
    ],
    "multiSelect": false
  }]
})
```

정답: 3번.
피드백: "맞아요! Claude는 기본적으로 터미널 안에서만 일하는데, MCP를 연결하면 Slack도 읽고, 캘린더도 보고, Notion도 편집할 수 있어요. 외부 세계로 연결되는 플러그라고 생각하면 됩니다."
