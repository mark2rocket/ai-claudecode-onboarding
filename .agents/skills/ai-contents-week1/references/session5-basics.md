# Session 5: Basics

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/cli-usage
> ```

---

## EXPLAIN

### 🎬 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 새암의 걱정    ║  ║  2. 실수해버렸다   ║
║                    ║  ║                    ║
║  (╥﹏╥) 새암       ║  ║  (°□°!) 새암       ║
║  "git... GitHub... ║  ║  "어제 만든 파일   ║
║   다 외워야        ║  ║   실수로 지웠어!"  ║
║   하나?"           ║  ║                    ║
║                    ║  ║    ╔═══════╗       ║
║  [git 명령어 보고  ║  ║    ║ ★   ★ ║       ║
║   머리 아픈 새암]  ║  ║    ║  ▲▲▲  ║       ║
║                    ║  ║    ╚═══╦═══╝       ║
║                    ║  ║  "git으로 복구할게요"║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. Claude가 해결  ║  ║  4. 깨달음         ║
║                    ║  ║                    ║
║    ╔═══════╗       ║  ║  (≧▽≦) 새암       ║
║    ║ ★   ★ ║       ║  ║  "세이브 포인트    ║
║    ║  ▲▲▲  ║       ║  ║   가 있었던 거야!  ║
║    ╚═══╦═══╝       ║  ║   외울 필요 없이   ║
║  새암: "최근 커밋  ║  ║   Claude한테       ║
║   3개 보여줘"      ║  ║   시키면 되고!"    ║
║  > git log 실행    ║  ║                    ║
║  > 복구 완료 ✓     ║  ║    ╔═══════╗       ║
║                    ║  ║    ║ ★   ★ ║       ║
║                    ║  ║    ╚═══╦═══╝       ║
║                    ║  ║  "말로 시키면 돼요"║
╚════════════════════╝  ╚════════════════════╝
```

**git과 GitHub — Claude가 다 해준다. 개념만 알면 된다.**
이 블록의 목표는 "세이브 포인트가 있구나" 하는 감각이면 충분하다.

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

**1. git 체험**
```
이 폴더가 git으로 관리되고 있는지 확인해줘. 최근 커밋 3개도 보여줘
```

**2. GitHub 체험**
```
GitHub의 Pull Request가 뭔지 비개발자한테 설명하듯 알려줘
```

---

## QUIZ

> 사용자가 돌아오면 먼저 칭찬한다:
> "잘하셨습니다! 방금 git과 GitHub를 Claude Code를 통해 직접 체험한 겁니다. 명령어를 몰라도 말로 시키면 됩니다."
> 그다음 퀴즈 2개를 순서대로 출제한다.

### Quiz A: git

```json
AskUserQuestion({
  "questions": [{
    "question": "git에서 '게임 세이브'에 해당하는 동작은?",
    "header": "Quiz A",
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

### Quiz B: GitHub

```json
AskUserQuestion({
  "questions": [{
    "question": "내 파일을 인터넷(클라우드)에 백업하는 동작은?",
    "header": "Quiz B",
    "options": [
      {"label": "git commit", "description": "로컬에 세이브"},
      {"label": "git push", "description": "클라우드(GitHub)에 업로드"},
      {"label": "git clone", "description": "클라우드에서 다운로드"},
      {"label": "git branch", "description": "A안, B안 분기"}
    ],
    "multiSelect": false
  }]
})
```

정답: 2번 git push. 피드백: "완벽합니다! commit = 로컬 세이브, push = 클라우드 백업. 이 두 가지만 알면 충분합니다. 명령어는 Claude한테 시키면 되니까요."
