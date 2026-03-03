# Block 4: 터미널 & git 기초

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/cli-usage
> ```

## EXPLAIN

### 왜 배워야 하나요?

Claude Code를 쓸 때 가끔 터미널 명령어와 git을 직접 입력해야 합니다.
**딱 5가지**만 알면 됩니다. 나머지는 Claude에게 물어보면 됩니다.

---

### 터미널 필수 명령어 5가지

> 터미널 [쉬운 말: 명령어 창] — 글자를 입력해서 컴퓨터에 직접 명령하는 프로그램

| 명령어 | 기능 | 예시 |
|--------|------|------|
| `cd 폴더명` | 폴더 이동 | `cd Documents` |
| `ls` | 현재 폴더 목록 보기 | `ls` |
| `pwd` | 현재 내 위치 확인 | `pwd` |
| `cat 파일명` | 파일 내용 보기 | `cat SKILL.md` |
| `open 파일명` | 파일/폴더 열기 (Mac) | `open .` |

> `cd` [쉬운 말: 폴더 이동] — Change Directory의 약자. 다른 폴더로 이동하는 명령
> `ls` [쉬운 말: 목록 보기] — List의 약자. 현재 폴더에 뭐가 있는지 보여줌
> `pwd` [쉬운 말: 현재 위치 확인] — Print Working Directory의 약자

---

### git 기초

> git [쉬운 말: 파일 변경 기록기] — 누가 언제 무엇을 바꿨는지 기록하고, 이전 상태로 되돌릴 수 있는 도구

컨텐츠 제작으로 비유하면:
- 글을 고칠 때마다 **자동 저장 + 버전 기록**
- 잘못 수정해도 **이전 버전으로 즉시 복구**
- 팀원과 **같은 파일을 충돌 없이 편집**

| 명령어 | 기능 | 비유 |
|--------|------|------|
| `git clone 주소` | 저장소 다운로드 | 구글 드라이브 폴더 내 컴퓨터에 복사 |
| `git commit -m "메모"` | 현재 상태 저장 | 게임 세이브 포인트 만들기 |
| `git branch` | 여러 버전 동시 작업 | 원본 건드리지 않고 임시 복사본에서 작업 |
| `git push` | 변경사항 업로드 | 구글 드라이브에 동기화 |

> 저장소 [쉬운 말: git이 관리하는 프로젝트 폴더] — repository의 번역. 파일과 변경 기록이 모두 담긴 폴더
> commit [쉬운 말: 저장 시점 기록] — "지금 이 상태를 저장해둬"라는 명령
> branch [쉬운 말: 작업 가지] — 원본을 건드리지 않고 새 버전을 시도할 수 있는 공간
> push [쉬운 말: 업로드] — 내 컴퓨터의 변경사항을 원격 저장소(GitHub)에 올리는 것

---

### GitHub 기초

> GitHub [쉬운 말: 파일 공유 & 협업 플랫폼] — git으로 관리하는 파일을 인터넷에 올리고 팀과 함께 작업하는 사이트

| 개념 | 쉬운 말 |
|------|---------|
| **Pull Request (PR)** | "이렇게 바꿨는데 괜찮아?" 팀원에게 검토 요청 |
| **Merge** | 검토 통과 후 실제 반영 |
| **Repository** | 프로젝트 폴더 (온라인 버전) |

---

### 에디터 추천 (복습)

| 에디터 | 추천 대상 |
|--------|----------|
| **Antigravity** | 처음 시작하는 분 (무료, 가장 쉬움) |
| **Cursor** | AI 기능을 적극 활용하고 싶은 분 |
| **VSCode** | 이미 사용 중인 분 |

---

## EXECUTE

3가지를 순서대로 해보세요:

**1단계:** 터미널에서 현재 위치 확인
```
pwd
ls
```

**2단계:** Claude Code가 있는 폴더로 이동
```
cd ~/.claude
ls
```

**3단계:** Claude에게 git에 대해 물어보기
```
git이 뭔지 컨텐츠 크리에이터 입장에서 설명해줘
```

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다. 3개의 퀴즈를 순서대로 낸다.

```json
AskUserQuestion({
  "questions": [
    {
      "question": "현재 폴더의 파일 목록을 보는 터미널 명령어는?",
      "header": "Quiz 4-1",
      "options": [
        {"label": "ls", "description": "List — 현재 폴더 내용 보기"},
        {"label": "cd", "description": "Change Directory — 폴더 이동"},
        {"label": "pwd", "description": "현재 위치 확인"},
        {"label": "cat", "description": "파일 내용 보기"}
      ],
      "multiSelect": false
    }
  ]
})
```

정답: **ls**. 해설 후 다음 퀴즈:

```json
AskUserQuestion({
  "questions": [
    {
      "question": "git commit은 어떤 역할을 하나요?",
      "header": "Quiz 4-2",
      "options": [
        {"label": "현재 상태를 게임 세이브처럼 저장", "description": "'지금 이 시점'을 기록해두는 것"},
        {"label": "파일을 삭제하는 것", "description": "삭제가 아닌 저장"},
        {"label": "인터넷에 업로드", "description": "업로드는 git push"}
      ],
      "multiSelect": false
    }
  ]
})
```

정답: **1번**. 해설 후 마지막 퀴즈:

```json
AskUserQuestion({
  "questions": [
    {
      "question": "GitHub에서 Pull Request(PR)란?",
      "header": "Quiz 4-3",
      "options": [
        {"label": "변경사항을 팀원에게 검토 요청하는 것", "description": "\"이렇게 바꿨는데 괜찮아?\" 확인 받는 절차"},
        {"label": "파일을 다운로드하는 것", "description": "다운로드는 git clone 또는 git pull"},
        {"label": "계정을 만드는 것", "description": "계정 생성과 무관"}
      ],
      "multiSelect": false
    }
  ]
})
```

정답: **1번**.

---

## 마무리

3개 퀴즈 완료 후 아래 메시지로 Day 1 온보딩을 마무리한다:

```
🎉 Day 1 완료!

오늘 배운 것:
✅ Claude Code 설치 & 첫 실행
✅ 7일 후 모습 미리 체험
✅ 왜 터미널인가?
✅ 7가지 핵심 기능 (Memory, Skill, MCP, Subagent, Agent Teams, Hook, Plugin)
✅ 터미널 & git 기초

다음 단계:
→ MCP를 연결해서 슬랙·노션과 Claude를 이어보세요
→ 첫 번째 나만의 Skill을 만들어보세요
→ 모르는 건 언제든 Claude에게 물어보세요

수고하셨습니다! 🚀
```
