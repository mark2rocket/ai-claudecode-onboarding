# Block 5: Basics

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/cli-usage
> ```

---

## EXPLAIN

### 🎬 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 새암의 걱정    ║  ║  2. 실제로 해보니  ║
║                    ║  ║                    ║
║  (╥﹏╥) 새암       ║  ║  (°□°!) 새암       ║
║  "CLI, git,        ║  ║  "Claude한테       ║
║   GitHub...        ║  ║   '현재 위치       ║
║   다 외워야        ║  ║   알려줘' 했더니   ║
║   하나?"           ║  ║                    ║
║                    ║  ║    ╔═══════╗       ║
║  [명령어 목록 보고  ║  ║    ║ ★   ★ ║       ║
║   머리 아픈 새암]  ║  ║    ║  ▲▲▲  ║       ║
║                    ║  ║    ╚═══╦═══╝       ║
║                    ║  ║  pwd 실행해서 보여줌║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. git도 마찬가지 ║  ║  4. 깨달음         ║
║                    ║  ║                    ║
║  (´-ω-`) 새암      ║  ║  (≧▽≦) 새암       ║
║  "git commit이     ║  ║  "외울 필요가      ║
║   뭔지 몰라도      ║  ║   없었던 거잖아!   ║
║   되나?"           ║  ║   Claude가 다      ║
║                    ║  ║   해주는데!"       ║
║  새암: "최근 커밋  ║  ║                    ║
║   3개 보여줘"      ║  ║    ╔═══════╗       ║
║                    ║  ║    ║ ★   ★ ║       ║
║    ╔═══════╗       ║  ║    ║  ▲▲▲  ║       ║
║    ║ ★   ★ ║ git   ║  ║    ╚═══╦═══╝       ║
║    ║  ▲▲▲  ║ log   ║  ║  "말로 시키면 돼요"║
║    ╚═══╦═══╝ 실행  ║  ║                    ║
╚════════════════════╝  ╚════════════════════╝
```

**명령어를 외울 필요 없다. Claude에게 말로 시키면 된다.**
이 블록의 목표는 "아, 이런 게 있구나" 정도면 충분하다.

---

### CLI 기초 — 알아두면 좋은 5개

| 명령어 | 의미 | 비유 |
|--------|------|------|
| `cd 폴더명` | 폴더 이동 | Finder에서 폴더 더블클릭 |
| `ls` | 목록 보기 | 폴더 열어서 뭐 있나 보기 |
| `pwd` | 현재 위치 | 주소창 보기 |
| `cat 파일명` | 파일 내용 보기 | 메모장으로 파일 열기 |
| `open ./` | 폴더 열기 | Finder로 열기 (Mac) |

> 이 5개면 충분하다. Claude가 나머지는 다 해준다.

---

### git 기초 — 실행 취소의 끝판왕

"보고서_최종.docx → 최종_진짜.docx → 찐최종.docx" — git을 쓰면 이런 일이 없다.

| 동작 | 비유 |
|------|------|
| `git commit` | 게임 세이브 |
| `git clone` | Google Drive에서 폴더 다운로드 |
| `git push` | Google Drive에 업로드 |
| `git branch` | A안, B안 동시 작업 |

> 더 배우고 싶다면: [git 간편 안내서](https://rogerdudler.github.io/git-guide/index.ko.html)

---

### GitHub 기초

| 개념 | 비유 |
|------|------|
| Pull Request (PR) | "이렇게 바꿨는데 괜찮아?" 리뷰 요청 |
| Merge | "오케이, 합치자" 리뷰 통과 후 반영 |

---

## EXECUTE

Claude에게 말로 시켜보는 체험이다:

**1. CLI 체험**
```
지금 내가 어느 폴더에 있는지 알려줘
```

**2. CLI 직접 체험** — `!`를 붙이면 터미널 명령어를 직접 실행:
```
!ls .claude/skills/
```

**3. git 체험**
```
이 폴더가 git으로 관리되고 있는지 확인해줘. 최근 커밋 3개도 보여줘
```

**4. GitHub 체험**
```
GitHub의 Pull Request가 뭔지 비개발자한테 설명하듯 알려줘
```

---

## QUIZ

> 사용자가 돌아오면 먼저 칭찬한다:
> "잘하셨습니다! 방금 CLI와 git을 Claude Code를 통해 직접 사용한 겁니다. 명령어를 몰라도 말로 시키면 됩니다."
> 그다음 퀴즈 3개를 순서대로 출제한다.

### Quiz A: CLI

```json
AskUserQuestion({
  "questions": [{
    "question": "Claude가 현재 폴더 위치를 알려줄 때 사용한 명령어는?",
    "header": "Quiz A",
    "options": [
      {"label": "ls", "description": "목록 보기"},
      {"label": "cd", "description": "폴더 이동"},
      {"label": "pwd", "description": "Print Working Directory — 현재 위치 출력"},
      {"label": "where", "description": "이런 명령어는 없음"}
    ],
    "multiSelect": false
  }]
})
```

정답: 3번 pwd. 피드백: "맞습니다! 외울 필요는 없지만, Claude가 뒤에서 뭘 하는지 알면 더 똑똑하게 시킬 수 있습니다."

### Quiz B: git

```json
AskUserQuestion({
  "questions": [{
    "question": "git에서 '게임 세이브'에 해당하는 동작은?",
    "header": "Quiz B",
    "options": [
      {"label": "git clone", "description": "폴더 다운로드"},
      {"label": "git push", "description": "업로드"},
      {"label": "git save", "description": "이런 명령어는 없음"},
      {"label": "git commit", "description": "현재 상태를 저장"}
    ],
    "multiSelect": false
  }]
})
```

정답: 4번 git commit. 피드백: "정확합니다! commit = 세이브. 뭘 해도 돌아갈 수 있으니 실험을 두려워하지 마세요."

### Quiz C: GitHub

```json
AskUserQuestion({
  "questions": [{
    "question": "GitHub에서 '이렇게 바꿨는데 괜찮아?' 하고 리뷰를 요청하는 것은?",
    "header": "Quiz C",
    "options": [
      {"label": "Merge", "description": "리뷰 통과 후 합치기"},
      {"label": "Pull Request (PR)", "description": "변경사항 리뷰 요청"},
      {"label": "git push", "description": "업로드"},
      {"label": "Issue", "description": "버그/기능 요청 등록"}
    ],
    "multiSelect": false
  }]
})
```

정답: 2번 Pull Request (PR). 피드백: "훌륭합니다! CLI, git, GitHub — 이 세 가지를 직접 체험했습니다. 앞으로 Claude에게 말로 시키면 되니까, 명령어 자체를 외울 필요는 전혀 없습니다."
