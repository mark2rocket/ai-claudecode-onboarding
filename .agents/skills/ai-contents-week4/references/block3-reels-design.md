# Block 3: 릴스 스킬 설계

---

## EXPLAIN

```
┌─────────────────────────────────────────────────────────┐
│ 1컷: 새암이 Week 3 릴스와 카드뉴스를 비교해서 본다.    │
│ 카드뉴스는 PNG 한 장. 릴스는 영상+자막+음성+GIF.      │
│                                                         │
│  (´-ω-`) 새암                                           │
│  "카드뉴스랑 구조가 완전히 다르네."                     │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ 2컷: 릴스 스킬 폴더를 펼쳐보니 style.md가 두껍다.      │
│ 영상소스 / 자막 / 음성 / 애니메이션 옵션이 가득하다.  │
│                                                         │
│  ( ´▽`) 새암                                            │
│  "한 번만 설정해두면 매번 물어볼 필요가 없겠다."        │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ 3컷: style.md를 보면 영상소스 항목이 있다.              │
│ "HTML 애니메이션 + GIF 배경 + 촬영 영상 복합"          │
│                                                         │
│  (^ω^) 새암                                             │
│  "여러 소스를 섞을 수 있다는 걸 스킬이 알고 있다."      │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ 4컷: `/my-reels 신제품 소개`를 입력하자               │
│ Claude가 style.md를 읽고 정확히 그 형식으로 만든다.   │
│                                                         │
│  (≧▽≦) 새암                                             │
│  "이제 매번 '자막 넣어줘' 안 해도 되잖아."              │
└─────────────────────────────────────────────────────────┘
```

---

### 카드뉴스 vs 릴스 — 스킬 구조 차이

| 항목 | 카드뉴스 (my-cardnews) | 릴스 (my-reels) |
|------|----------------------|----------------|
| 산출물 | PNG 이미지 | MP4 영상 |
| 소스 | HTML → 스크린샷 | HTML + GIF + 촬영 영상 복합 가능 |
| 자막 | 없음 | HTML 내 텍스트 or SRT 파일 |
| 음성/음악 | 없음 | 배경음악 / AI TTS / 직접 녹음 |
| 핵심 스펙 파일 | design.md | **style.md** (더 많은 옵션) |

---

### 릴스 스킬 폴더 구조

```
my-reels/
├── SKILL.md          ← 실행 순서 지시 (소스 유형 분기 포함)
└── references/
    ├── brand.md      ← my-cardnews에서 복사 (동일)
    ├── brief.md      ← 릴스 브리프 프롬프트
    ├── style.md      ← 릴스 스타일 스펙 (소스·자막·음성 포함)
    └── workflow.md   ← 소스 유형별 제작 단계 + 금지 목록
```

---

### style.md — 릴스 전용 확장 스펙

카드뉴스의 design.md보다 훨씬 많은 옵션을 담는다.

**영상 소스 옵션 (복수 선택 가능)**

| 소스 유형 | 설명 | 준비물 |
|----------|------|--------|
| HTML 애니메이션 | CSS 장면 전환, 순수 코드로 생성 | 없음 |
| GIF 배경 | Klipy/Pexels 무료 GIF 오버레이 | GIF 파일 URL |
| 촬영 영상 (MP4) | 직접 찍은 영상 파일을 배경으로 | 로컬 MP4 파일 |
| 복합 | 위 소스들을 혼합 사용 | 각 소스 준비물 |

**자막 옵션**

| 방식 | 설명 |
|------|------|
| 없음 | 자막 미사용 |
| HTML 내 텍스트 | 디자인에 포함된 텍스트 (편집 쉬움) |
| SRT 파일 (FFmpeg) | 별도 자막 파일 → FFmpeg으로 합성 |

**음성/음악 옵션**

| 방식 | 설명 |
|------|------|
| 없음 (무음) | 음악·음성 미사용 |
| 배경음악 | 로컬 MP3 파일을 영상에 합성 |
| AI 음성 (TTS) | Claude가 스크립트 작성 → 별도 TTS 변환 |
| 직접 녹음 | 미리 녹음한 MP3/M4A 파일 사용 |

---

### brand.md 공유 전략

Week 4에서는 **방법 A(복사)**를 쓴다. 단순하고 안전하다.

```bash
cp ~/.claude/skills/my-cardnews/references/brand.md \
   ~/.claude/skills/my-reels/references/brand.md
```

---

## EXECUTE

**AskUserQuestion으로 릴스 스타일 스펙을 수집한 후 폴더·파일을 자동 생성한다.**

### Step 1 — 릴스 스타일 4개 질문 수집

```json
AskUserQuestion({
  "questions": [
    {
      "question": "릴스에서 사용할 영상 소스를 모두 선택하세요.",
      "header": "영상 소스",
      "options": [
        { "label": "HTML 애니메이션", "description": "CSS 장면 전환, 코드만으로 생성 (기본)" },
        { "label": "GIF 배경", "description": "Klipy / Pexels 무료 GIF 오버레이" },
        { "label": "촬영 영상 (MP4)", "description": "직접 찍은 영상을 배경으로 사용" },
        { "label": "직접 입력 (Other)", "description": "그 외 소스 방식" }
      ],
      "multiSelect": true
    },
    {
      "question": "자막 방식을 선택하세요.",
      "header": "자막",
      "options": [
        { "label": "HTML 내 텍스트 (추천)", "description": "디자인에 자막 포함, 편집 쉬움" },
        { "label": "SRT 파일 (FFmpeg 합성)", "description": "별도 자막 파일로 후편집" },
        { "label": "자막 없음", "description": "텍스트 없이 영상만" }
      ],
      "multiSelect": false
    },
    {
      "question": "음성 / 음악 방식을 선택하세요.",
      "header": "음성/음악",
      "options": [
        { "label": "배경음악 (MP3)", "description": "로컬 MP3 파일을 영상에 합성" },
        { "label": "AI 음성 합성 (TTS)", "description": "스크립트 작성 → TTS로 변환" },
        { "label": "직접 녹음 파일", "description": "미리 녹음한 MP3/M4A 사용" },
        { "label": "없음 (무음)", "description": "음성·음악 미사용" }
      ],
      "multiSelect": false
    },
    {
      "question": "텍스트 등장 애니메이션을 선택하세요.",
      "header": "애니메이션",
      "options": [
        { "label": "fade-in (천천히 등장)", "description": "안정적이고 읽기 편함" },
        { "label": "slide-up (아래서 위로)", "description": "역동적인 느낌" },
        { "label": "typewriter (타이핑 효과)", "description": "긴장감, 텍스트 집중" },
        { "label": "없음 (정적)", "description": "애니메이션 없이 바로 표시" }
      ],
      "multiSelect": false
    }
  ]
})
```

### Step 2 — 폴더 생성 + brand.md 복사

Bash로 폴더를 만들고 brand.md를 복사한다:
```bash
mkdir -p ~/.claude/skills/my-reels/references
cp ~/.claude/skills/my-cardnews/references/brand.md \
   ~/.claude/skills/my-reels/references/brand.md
```

### Step 3 — style.md 작성 (Step 1 답변 반영)

Write 툴로 `~/.claude/skills/my-reels/references/style.md`를 생성한다:

```
# 릴스 스타일 스펙

크기: 1080×1920 (9:16 세로)
영상소스: [Step 1 영상 소스 선택값 — 복수 가능]
배경: [영상소스 선택값 기반 자동 결정]
메인 텍스트 크기: 80px 이상
서브 텍스트 크기: 48px 이상
애니메이션: [Step 1 애니메이션 선택값], 장면 전환 2초 간격
자막 방식: [Step 1 자막 선택값]
자막 위치: 화면 하단 20%
자막 색상: 흰색 (#FFFFFF), 검은 테두리 2px
음성/음악: [Step 1 음성/음악 선택값]
장면 수: 5~8장면
총 재생 시간: 15~30초

금지 사항:
- 40px 미만 텍스트 (모바일에서 안 보임)
- 복잡한 배경 (텍스트 가독성 저하)
- 5초 이상 아무 움직임 없는 장면
- 확인 없이 바로 녹화 안내 (Human-in-the-loop 필수)
```

### Step 4 — 생성 확인

폴더 구조를 출력해서 보여준다:
- `my-reels/references/brand.md` (복사 완료)
- `my-reels/references/style.md` (생성 완료 — 영상소스·자막·음성 포함)

**체크리스트**
- [ ] `my-reels/references/` 폴더 생성
- [ ] brand.md 복사 완료 (my-cardnews에서)
- [ ] 영상 소스 방식 선택 완료 (복수 가능)
- [ ] 자막 방식 선택 완료
- [ ] 음성/음악 방식 선택 완료
- [ ] 애니메이션 스타일 선택 완료
- [ ] style.md 생성 — 모든 선택값 반영 확인

---

## QUIZ

**퀴즈: 릴스 스킬에서 카드뉴스 스킬과 가장 크게 다른 점은?**

1. 릴스는 HTML을 사용하지 않는다
2. 릴스는 영상 소스(GIF, 촬영 영상, HTML 애니메이션), 자막, 음성/음악 옵션이 추가되어 style.md가 훨씬 풍부하다
3. 릴스는 brand.md를 공유할 수 없다

정답: 2번. 카드뉴스는 HTML → PNG 한 가지 경로지만, 릴스는 HTML 애니메이션·GIF·촬영 영상을 복합으로 쓸 수 있고 자막과 음성까지 얹을 수 있어요. 이 옵션들을 style.md에 한 번 저장해두면 매번 다시 설정할 필요가 없어요.
