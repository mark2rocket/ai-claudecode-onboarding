# Block 3-3: MCP (외부 앱 연결 플러그)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/mcp
> ```

## EXPLAIN

### MCP란?

**외부 앱을 Claude에 꽂는 플러그**입니다.

기본 Claude는 텍스트만 읽고 쓸 수 있습니다.
MCP를 연결하면 Slack 메시지를 읽거나, 구글 캘린더 일정을 확인하거나, 노션 문서를 편집하는 것을 Claude가 직접 할 수 있게 됩니다.

> MCP [쉬운 말: 외부 앱 연결 플러그] — Model Context Protocol의 약자. Claude가 외부 서비스와 대화할 수 있게 연결해주는 표준 규격
> 프로토콜 [쉬운 말: 통신 규격] — 서로 다른 서비스가 대화하기 위한 약속된 방식

---

### 비유로 이해하기

| 비유 | 의미 |
|------|------|
| Claude = 스마트폰 | 기본 기능만 있는 상태 |
| MCP = 앱 | 기능을 추가하는 것 |
| Slack MCP 설치 | 슬랙 앱을 추가한 것 |

---

### 작동 방식

> 툴 콜링 [쉬운 말: 도구 호출] — Claude가 텍스트를 생성하는 것에 그치지 않고, 실제로 외부 서비스에 "이 작업 해줘"라는 명령을 보내는 것

```
Claude ───── "Slack에서 오늘 메시지 읽어줘"
  │
  ▼ 도구 호출(툴 콜링)
┌──────────┐    MCP 연결 규격    ┌──────────┐
│ Claude   │ ◀════════════════▶ │  Slack   │
│ Code     │    표준 약속        │  서버    │
└──────────┘                   └──────────┘
  내 컴퓨터                      외부 서비스
```

---

### 컨텐츠 크리에이터에게 유용한 MCP 예시

| MCP | 가능한 일 |
|-----|----------|
| Slack MCP | 팀 채널 메시지 자동 수집 |
| Google Calendar MCP | 촬영·업로드 일정 확인 |
| Notion MCP | 콘텐츠 캘린더 자동 업데이트 |
| YouTube MCP | 영상 성과 데이터 가져오기 |

---

## EXECUTE

Claude에게 직접 물어보세요:

```
MCP가 뭔지 쉽게 설명해줘. 내가 콘텐츠 크리에이터인데 쓸 수 있는 MCP 서버 예시 3개도 알려줘
```

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다.

```json
AskUserQuestion({
  "questions": [{
    "question": "MCP를 한 마디로 말하면?",
    "header": "Quiz 3-3",
    "options": [
      {"label": "Claude와 외부 앱을 연결하는 표준 플러그", "description": "Slack, 노션 등을 Claude에 꽂는 것"},
      {"label": "Claude의 내장 기능", "description": "MCP는 외부 연결이지 내장이 아님"},
      {"label": "프로그래밍 언어", "description": "도구 연결 규격임"}
    ],
    "multiSelect": false
  }]
})
```

정답: **1번**.
