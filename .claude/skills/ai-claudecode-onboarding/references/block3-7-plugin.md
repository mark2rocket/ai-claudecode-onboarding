# Block 3-7: Plugin (기능 묶음 패키지)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/plugins
> 📖 마켓플레이스: https://code.claude.com/docs/ko/discover-plugins
> ```

## EXPLAIN

### Plugin이란?

Skill, MCP, Hook, Agent 등 여러 기능을 **하나의 설치 패키지로 묶은 것**입니다.

팀 전체가 동일한 환경을 갖추게 하거나, 유용한 기능 모음을 한 번에 설치할 때 사용합니다.

> Plugin [쉬운 말: 기능 묶음 패키지] — 여러 기능을 하나로 묶어 한 줄 명령으로 설치할 수 있게 만든 것
> 패키징 [쉬운 말: 묶어서 배포] — 개별 파일들을 하나로 포장해서 쉽게 나눠 쓸 수 있게 만드는 것
> 배포 [쉬운 말: 나눠 주기] — 만든 기능을 다른 사람들도 쓸 수 있게 공유하는 것

---

### 개별 설치 vs Plugin 비교

```
Plugin 없이 (개별 설치)          Plugin 사용 (한 번에)
┌─────────┐                    ┌──────────────────────┐
│ Skill A │ ← 수동 복사         │ contents-creator-kit │
│ Skill B │ ← 수동 복사         │ ┌─ Skill A, B       │
│ MCP 설정 │ ← 수동 설정   vs   │ ├─ MCP 설정         │
│ Hook 설정│ ← 수동 설정         │ ├─ Hook 설정        │
│ Agent   │ ← 수동 설정         │ └─ Agent 설정       │
└─────────┘                    └──────────┬───────────┘
  팀원마다 반복                             │
                                claude plugin add
                                  한 줄이면 끝
```

---

### 컨텐츠 크리에이터 활용 예시

```
"콘텐츠 크리에이터 기본 Kit" Plugin 하나로:
- SNS 초안 작성 Skill
- 유튜브 성과 분석 MCP 연결
- 글쓰기 완료 알림 Hook
- 리서치 전담 Subagent 설정

→ 팀원 누구나 claude plugin add 한 줄로 동일 환경 구축
```

---

## EXECUTE

### 1단계: 플러그인 마켓플레이스 확인
```
/plugin
```

### 2단계: superpowers 플러그인 설치 (유용한 기능 모음)
```
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

### 3단계: clarify 플러그인 설치 (모호한 요청 명확화 도구)
```
/plugin marketplace add team-attention/plugins-for-claude-natives
/plugin install clarify
```

> clarify [쉬운 말: 명확화 도구] — "이번 달 SNS 전략 짜줘" 같은 모호한 요청을 Claude가 알아서 질문하며 구체화해주는 플러그인

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다.

```json
AskUserQuestion({
  "questions": [{
    "question": "Plugin의 핵심 역할은?",
    "header": "Quiz 3-7",
    "options": [
      {"label": "Skill + MCP + Hook + Agent 등을 하나의 패키지로 묶어 팀 공유", "description": "한 줄 설치로 팀 전체가 동일한 환경을 갖출 수 있음"},
      {"label": "새로운 AI 모델을 추가하는 것", "description": "모델 추가가 아닌 기능 묶음"},
      {"label": "Claude Code를 업데이트하는 것", "description": "업데이트와 무관"}
    ],
    "multiSelect": false
  }]
})
```

정답: **1번**.
