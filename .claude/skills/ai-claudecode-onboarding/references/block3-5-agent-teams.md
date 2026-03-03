# Block 3-5: Agent Teams (Claude 팀 협업)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/agent-teams
> ```

## EXPLAIN

### Agent Teams란?

여러 Claude가 **팀처럼 함께 일하는** 기능입니다.

Subagent가 "팀장 → 팀원(1:1 위임)" 이라면,
Agent Teams는 "팀원들이 서로 직접 소통하며 공유 할 일 목록을 함께 처리" 하는 방식입니다.

> Agent Teams [쉬운 말: Claude 팀 협업] — 여러 독립 Claude 인스턴스가 팀장 지휘 아래 서로 대화하며 협업하는 기능
> 인스턴스 [쉬운 말: 독립 실행 단위] — 각각 독립적으로 실행 중인 Claude 하나

---

### Subagent vs Agent Teams

| 구분 | Subagent | Agent Teams |
|------|----------|-------------|
| 구조 | 팀장 → 팀원 (1:1) | 팀장 + 여러 팀원들 (다:다) |
| 소통 | 팀원이 팀장에게만 보고 | 팀원들끼리도 직접 소통 |
| 할 일 목록 | 없음 | 공유 할 일 목록 있음 |
| 비유 | 심부름 보내기 | 실제 프로젝트 팀 운영 |

---

### 구조 시각화

```
              팀장 Claude
             /     |     \
            /      |      \
       Claude A  Claude B  Claude C
           \       |       /
            \      |      /
          공유 할 일 목록 (Task List)
```

각 Claude는 서로 메시지를 주고받으며 작업을 나눠서 처리합니다.

---

### 컨텐츠 크리에이터 활용 예시

```
이번 달 콘텐츠 캘린더를 만들어줘.
- Claude A: 트렌드 리서치
- Claude B: 경쟁사 분석
- Claude C: 초안 작성
```

세 작업이 동시에 진행되고 결과가 합쳐집니다.

---

## EXECUTE

Agent Teams를 활성화하는 설정을 추가합니다.

Claude Code에 이렇게 입력하세요:

```
내 settings.json에 Agent Teams를 활성화하는 설정을 추가해줘
```

Claude가 아래 내용을 `~/.claude/settings.json`에 추가해줄 겁니다:

```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

> `~/.claude/settings.json` [쉬운 말: Claude Code 전체 설정 파일] — 홈 폴더 안의 `.claude` 폴더에 있는 설정 파일입니다. `~`는 내 홈 폴더를 뜻합니다.

설정 후 확인:
```
~/.claude/settings.json 파일을 읽어서 CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS가 "1"로 설정됐는지 확인해줘
```

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다.

```json
AskUserQuestion({
  "questions": [{
    "question": "Agent Teams와 Subagent의 차이는?",
    "header": "Quiz 3-5",
    "options": [
      {"label": "각자 독립 공간에서 서로 소통하며 협업 (팀)", "description": "Subagent는 1:1 위임, Agent Teams는 팀원들끼리도 직접 소통"},
      {"label": "Agent Teams가 더 빠른 버전의 Subagent", "description": "속도 차이가 아니라 협업 방식의 차이"},
      {"label": "둘 다 같은 것", "description": "구조가 다름"}
    ],
    "multiSelect": false
  }]
})
```

정답: **1번**.
