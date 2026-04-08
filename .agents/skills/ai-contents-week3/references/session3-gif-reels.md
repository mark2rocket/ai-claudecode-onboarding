# Session 3: GIF + 코딩으로 긴 릴스 — "움직이는 배경으로 시선을 잡는다"

> Track 1 전용 블록

---

## EXPLAIN

### 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. Session 2 복습   ║  ║  2. 한계 발견      ║
║                    ║  ║                    ║
║  ( ´▽`) 새암       ║  ║  (・・?) 새암      ║
║  "HTML만으로       ║  ║  "텍스트만 있으니  ║
║   릴스 완성!       ║  ║   좀 심심한데...   ║
║   근데 좀 심심해"  ║  ║   뭔가 배경에      ║
║                    ║  ║   움직임이 있으면?"║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. GIF 발견       ║  ║  4. 결과           ║
║                    ║  ║                    ║
║  (・∀・) 새암      ║  ║  (≧▽≦) 새암       ║
║  "GIPHY에서 GIF    ║  ║  "배경이 살아 움직 ║
║   받아서 HTML      ║  ║   이고 텍스트가    ║
║   배경으로 넣으면  ║  ║   위에 뜨는        ║
║   되잖아!"         ║  ║   릴스 완성!"      ║
╚════════════════════╝  ╚════════════════════╝
```

---

### GIF를 배경으로 쓰는 이유

```
GIF의 특성:
  - 움직이는 이미지 파일 (.gif)
  - 저작권 무료 소스가 많다 (GIPHY, Tenor)
  - HTML에서 배경 이미지로 바로 사용 가능
  - 다운로드만 하면 인터넷 없이도 사용

활용 방법:
  GIF (배경) + HTML 텍스트 오버레이 = 긴 릴스

  CSS:
    background: url(animation.gif) center/cover no-repeat;
    → GIF가 화면을 꽉 채우며 반복 재생

  텍스트는 z-index로 GIF 위에 올린다
    position: relative; z-index: 10;
```

---

### 긴 릴스 구조 (30~60초)

```
짧은 릴스 (Session 2): 단일 장면, 15초
긴 릴스 (Session 3~5): 여러 장면, 30~60초

장면 구성 예시 (60초 릴스):
┌─────────────────────────────────────────┐
│ 0~5초:   인트로 (Hook — 왜 봐야 하나?) │
│ 5~15초:  문제 제시                      │
│ 15~30초: 핵심 내용 1~3가지             │
│ 30~50초: 실전 예시 또는 팁             │
│ 50~60초: 마무리 + CTA                  │
└─────────────────────────────────────────┘

각 장면을 별도 HTML 섹션으로 만들고
scroll-snap 또는 JavaScript 타이머로 전환
```

---

### GIF 소스 찾는 법

```
추천 사이트:
  1. Klipy (klipy.com) ← 워크플로우 최적
     - GIF URL을 Claude Code가 curl로 직접 다운로드 가능
     - 검색 → GIF 선택 → 우클릭 URL 복사 → Claude에게 전달

  2. Pixabay (pixabay.com/gifs)
     - CC0 라이선스, 상업적 사용 가능
     - 검색: "technology", "ai", "data"

  3. Pexels (pexels.com)
     - 무료, 상업적 사용 가능

Claude Code에게 맡기는 방법:
  GIF URL을 알려주면 curl로 직접 다운로드해준다
  → 수동 다운로드 없이 파이프라인 연결 가능
```

---

### 텍스트 가독성 확보 방법

```
GIF 배경 위에 텍스트를 올릴 때 주의점:
  - 배경이 밝으면 텍스트가 안 보인다
  - 배경이 복잡하면 텍스트가 묻힌다

해결책:
  1. 반투명 검정 오버레이
     background: rgba(0,0,0,0.5);
     → GIF 위에 반투명 레이어 깔기

  2. 텍스트에 그림자 추가
     text-shadow: 2px 2px 8px rgba(0,0,0,0.8);

  3. 텍스트 배경 박스
     background: rgba(0,0,0,0.7); padding: 12px;
     border-radius: 8px;
```

---

## EXECUTE

**Step 1 — GIF 소스 준비**

Klipy(klipy.com)에서 아래 검색어로 GIF를 3개 찾아 URL을 복사한 뒤,
Claude Code에게 입력:

```
아래 GIF URL 3개를 curl로 다운로드해서
gif1.gif, gif2.gif, gif3.gif로 현재 프로젝트 폴더에 저장해줘.

URL 1: [Klipy에서 복사한 URL]  → gif1.gif  (인트로: 나만의 브랜드)
URL 2: [Klipy에서 복사한 URL]  → gif2.gif  (문제: 혼자 다 하는 고됨)
URL 3: [Klipy에서 복사한 URL]  → gif3.gif  (해결: 온라인 판매 시작)
```

> Klipy 검색어 참고: "small business" / "handmade craft" / "online shop"

---

**Step 2 — 멀티 장면 HTML 생성**

```
video_brief.md를 업데이트하고 아래 프롬프트로 HTML 생성:

다운로드한 GIF 3개(gif1.gif, gif2.gif, gif3.gif)를
배경으로 사용하는 60초짜리 세로형(1080×1920) 릴스 HTML을 만들어줘.

- 각 장면마다 다른 GIF 배경
- 반투명 검정 오버레이로 텍스트 가독성 확보
- 텍스트는 크고 굵게, Noto Sans KR
- JavaScript 타이머로 12초마다 장면 자동 전환
- reels-v2.html로 저장하고 브라우저로 열어줘
```

---

**Step 3 — Playwright로 영상 녹화**

```
Claude에게 입력:
"reels-v2.html을 Playwright로 열어서 60초 동안
 1080×1920 크기로 녹화하고 reels-v2.mp4로 저장해줘."

(Playwright 없을 때 백업:
 브라우저 전체화면 → Command+Shift+5 → 60초 녹화 → 중지)
```

체크리스트:
```
□ GIF 3개가 다운로드됐나?
□ 각 장면에 GIF 배경이 적용됐나?
□ 텍스트가 GIF 위에서 잘 보이나?
□ 장면 전환이 자연스럽나?
□ Session 2보다 시각적으로 풍성해졌나?
```

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "GIF 배경 위에 텍스트를 잘 보이게 하는 방법은?",
    "header": "Quiz 3",
    "options": [
      {"label": "텍스트를 더 크게 만든다", "description": "크기만 키우면 배경에 묻혀도 잘 보인다"},
      {"label": "반투명 검정 오버레이를 GIF와 텍스트 사이에 깐다", "description": "rgba(0,0,0,0.5) 레이어로 배경을 어둡게 눌러서 텍스트가 떠 보이게"},
      {"label": "GIF를 흑백으로 바꾼다", "description": "색상을 없애면 텍스트가 보인다"}
    ],
    "multiSelect": false
  }]
})
```

정답: 2번.
피드백: "맞아요! rgba(0,0,0,0.5) 같은 반투명 레이어를 GIF 위에 깔면, GIF의 움직임은 살리면서 텍스트 가독성을 확보할 수 있어요. Session 4에서는 GIF 대신 직접 촬영한 영상 소스를 쓰고, FFmpeg으로 오버레이를 합성해볼게요."
