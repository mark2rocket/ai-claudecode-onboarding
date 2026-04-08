# Session 4-5: Agent Teams · Hook · Plugin (간단 소개)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/agent-teams
> 📖 공식 문서: https://code.claude.com/docs/ko/hooks-guide
> 📖 공식 문서: https://code.claude.com/docs/ko/plugins
> ```

> ⚠️ 이 블록은 **Phase A만** 있다. 퀴즈와 Phase B 없음.
> 설명 후 block4-summary.md로 바로 이어진다.

---

## EXPLAIN

지금까지 배운 Memory, Skill, MCP, Subagent는 혼자서도 쓸 수 있는 기능들이다.
여기서는 "더 있다"는 것만 알고 넘어가는 3가지를 소개한다.

---

### Agent Teams — 팀 단위 협업

| 항목 | 내용 |
|------|------|
| 한 줄 요약 | 여러 Claude 에이전트가 팀처럼 협업 |
| Subagent와 차이 | Subagent는 1:1 보고. Teams는 에이전트끼리 직접 소통 + 공유 태스크 리스트 |
| 비유 | 팀장이 일 나누면 팀원들이 각자 작업하고 서로 대화하는 프로젝트 팀 |

```
Subagent: 리더 ← 보고만
Teams:    Agent A ↔ Agent B ↔ Agent C (공유 태스크 리스트)
```

> 지금 당장 쓸 일은 드물지만, 나중에 "큰 일을 자동화"하고 싶을 때 찾게 된다.

---

### Hook — 이벤트 자동 실행

| 항목 | 내용 |
|------|------|
| 한 줄 요약 | 특정 이벤트 발생 시 자동으로 코드(셸 스크립트) 실행 |
| AI와 차이 | AI는 확률적(가끔 까먹음). Hook은 결정론적(100% 실행) |
| 비유 | "작업 완료되면 자동으로 체크리스트 실행" 같은 자동 규칙 |

```
AI: "카드뉴스 완성되면 파일명 날짜로 정리해줘" → 가끔 까먹음
Hook: 파일 저장 이벤트 → 날짜 자동 정리 → 100%
```

> 지금은 몰라도 된다. "이런 게 있구나" 정도만.

---

### Plugin — 기능 묶음 패키지

| 항목 | 내용 |
|------|------|
| 한 줄 요약 | Skill + MCP + Hook + Agent를 하나의 패키지로 묶어 한 줄로 설치 |
| 비유 | 앱스토어에서 앱 설치하듯, `omc install 이름` 한 줄로 끝 |
| 예시 | `clarify` 플러그인 → 모호한 요청을 명확하게 만들어주는 기능 설치 |

```
개별 설정: Skill 복사 + MCP 설정 + Hook 설정 + ... (반복 작업)
Plugin:   omc install marketing-tools → 한 번에 끝
```

> oh-my-claudecode(`omc`)가 플러그인 관리자 역할을 한다.
> Week 2, 3에서 실제로 설치해볼 것이다. 지금은 개념만.

---

## EXECUTE

실습 없음. 아래 한 가지만 해본다:

Claude Code에 입력해보자:

```
Agent Teams, Hook, Plugin 중 내 업무(유튜버/1인 사업가/크리에이터)에 가장 유용할 것 같은 걸 하나 골라서 실제 활용 예시를 알려줘
```

> Claude의 답변을 읽고, 나중에 써볼 것이 있는지 느껴보는 것으로 충분하다.

---

## Session 4 마무리 — 전체 관계도

> 📖 전체 기능 개요: https://code.claude.com/docs/ko/features-overview

Session 4에서 배운 기능들의 관계를 정리해서 보여준다.

```
┌─ Memory ────── CLAUDE.md(내 지시문) + Auto Memory(Claude의 메모)
│
├─ Skill ─────── 반복 업무를 레시피로 저장
│   └─ MCP ───── Slack, Calendar 등 외부 도구 연결
│
├─ Subagent ──── 하나의 작업을 백그라운드에서 처리
│   └─ Agent Teams ── 여러 Subagent가 동시에 작업
│
├─ Hook ──────── 특정 이벤트 발생 시 자동 실행
│
└─ Plugin ────── 위의 모든 것을 묶어서 팀에 공유
```

전부 외울 필요 없다. 모르면 Claude에게 물어보면 된다.
