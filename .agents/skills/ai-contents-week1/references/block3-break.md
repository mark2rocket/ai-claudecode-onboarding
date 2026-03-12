# Block 3-Break: 쉬어가기 — 터미널 & Status Line

> 이 블록은 퀴즈 없이 가볍게 진행한다. Phase A만 있고 Phase B는 없다.
> 사용자가 "완료" 또는 "다음"이라고 하면 Block 4로 넘어간다.

---

## EXPLAIN

### 🎬 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 새암의 터미널  ║  ║  2. 강사의 터미널  ║
║                    ║  ║                    ║
║  (´-ω-`) 새암      ║  ║  (≧▽≦) 강사       ║
║                    ║  ║                    ║
║  $ claude          ║  ║  [Ghostty - 색상,  ║
║  > 흰 바탕에       ║  ║   폰트, 분할 창]   ║
║    검은 글자       ║  ║                    ║
║    밋밋하다...     ║  ║  [claude-opus-4]   ║
║                    ║  ║  ▓▓▓░░░░░░░ 32%   ║
║  "이게 전부야?"    ║  ║  "환경도 실력이에요"║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. Status Line    ║  ║  4. 새암의 터미널  ║
║     설정           ║  ║     (이후)         ║
║                    ║  ║                    ║
║    ╔═══════╗       ║  ║  (≧▽≦) 새암       ║
║    ║ ★   ★ ║       ║  ║                    ║
║    ║  ▲▲▲  ║ Claude║  ║  [claude-sonnet]   ║
║    ╚═══╦═══╝       ║  ║  ▓▓▓▓░░░░░░ 41%   ║
║      ══╩══         ║  ║                    ║
║  "스크립트 만들고  ║  ║  "이제 내 터미널   ║
║   설정까지 완료!   ║  ║   같은 느낌이다!"  ║
║   [Opus] ▓▓░ 25%"  ║  ║                    ║
╚════════════════════╝  ╚════════════════════╝
```

**여기까지 왜 Claude Code를 쓰는지(Block 3)를 배웠다.**
본격적인 기능 탐구 전, 잠깐 작업 환경을 꾸미고 가자.

---

### 터미널 추천

Claude Code는 터미널에서 돌아간다. 어떤 터미널을 쓰느냐에 따라 경험이 달라진다.

| 터미널 | 특징 | 설치 |
|--------|------|------|
| **Warp** | AI 내장. 자동완성·설명 기능. 비개발자 친화적 | [warp.dev](https://warp.dev) |
| **Ghostty** | 빠르고 가벼움. GPU 가속. 오픈소스 | [ghostty.org](https://ghostty.org) |
| **iTerm2** | macOS 대표 터미널. 풍부한 기능 | [iterm2.com](https://iterm2.com) |
| **WezTerm** | 크로스플랫폼. Lua로 설정 | [wezfurlong.org/wezterm](https://wezfurlong.org/wezterm) |

> 기본 Terminal.app도 쓸 수 있다. 지금 당장 바꿀 필요는 없다.

---

### Claude Code Alias 설정

매번 `claude --dangerously-skip-permissions` 를 타이핑하기 귀찮다.
**단축 alias**를 만들면 두 글자로 실행할 수 있다.

**Claude에게 시키기:**

```
zsh나 PowerShell 터미널에 다음 alias 만들어줘

- cc: claude (기본 실행)
- ccd: claude --dangerously-skip-permissions (바이패스 모드)
- ccr: claude --resume --dangerously-skip-permissions (이전 세션 재개 + 바이패스)
```

> Claude가 `~/.zshrc` (또는 PowerShell profile)에 자동으로 추가해준다.
> 이후 `cc` 만 쳐도 Claude Code가 실행된다.

---

### Claude Code Status Line

Claude Code 화면 맨 아래에 **상태 표시줄**을 커스터마이즈할 수 있다.
지금 쓰는 모델, 컨텍스트 사용량 등을 실시간으로 보여준다.

**가장 쉬운 방법 — Claude에게 시키기:**

```
/statusline 모델 이름과 컨텍스트 사용률을 프로그레스 바로 보여줘
```

> 이 한 줄이면 Claude가 스크립트를 만들고 설정까지 해준다.
> 결과: `[claude-sonnet-4-6] ▓▓▓░░░░░░░ 32%`

---

## EXECUTE

두 가지를 해보자:

1. **Status Line 설정**: Claude Code에 위 `/statusline ...` 명령 입력
2. **터미널 구경**: 위 터미널 중 하나의 공식 사이트를 방문해서 스크린샷 구경

> 실습 후 "완료" 또는 "다음"이라고 입력하면 Block 4로 넘어간다.
