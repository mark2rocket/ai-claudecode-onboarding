# Block 6: 홍보 영상 - Remotion — "React 컴포넌트가 영상이 된다"

> Track 2 전용 블록

---

## EXPLAIN

### 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 홍보 영상 필요 ║  ║  2. 기존 방식의    ║
║                    ║     한계             ║
║  ( ´▽`) 새암       ║  ║                    ║
║  "제품 홍보 영상을 ║  ║  (╥﹏╥) 새암       ║
║   만들어야 하는데  ║  ║  "애프터이펙트는   ║
║   어떻게 하지?"   ║  ║   너무 어렵고      ║
║                    ║  ║   비싸고 배울 게   ║
║                    ║  ║   너무 많아..."    ║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. Remotion 발견  ║  ║  4. React = 영상   ║
║                    ║  ║                    ║
║  (・∀・) 새암      ║  ║  (≧▽≦) 새암       ║
║  "React로 영상을   ║  ║  "내가 아는        ║
║   만든다고?        ║  ║   컴포넌트 방식으로║
║   코드가 곧        ║  ║   영상을 만들 수   ║
║   영상 파일?!"     ║  ║   있다!"           ║
╚════════════════════╝  ╚════════════════════╝
```

---

### Remotion이란?

```
Remotion = React 기반 영상 제작 프레임워크

핵심 개념:
  - React 컴포넌트 = 영상의 장면
  - props = 애니메이션 파라미터
  - useCurrentFrame() = 현재 프레임 번호
  - interpolate() = 값을 부드럽게 변환

일반 영상 편집과의 차이:
  편집 앱:    타임라인 드래그 → 렌더링
  Remotion:  컴포넌트 코드 작성 → npx remotion render

장점:
  - 버전 관리 가능 (git)
  - 데이터 기반 영상 (API 연동 가능)
  - 재사용 가능한 컴포넌트
  - Claude가 컴포넌트 전체를 생성해준다
```

---

### Remotion 설치 및 시작

```
# 새 Remotion 프로젝트 생성
npx create-video@latest

# 프로젝트 이름: my-promo-video
# 템플릿: Hello World (기본)

# 개발 서버 실행
cd my-promo-video
npm run dev
# → 브라우저에서 영상 미리보기 가능

# 렌더링 (최종 MP4 출력)
npx remotion render src/index.ts MyComp out/video.mp4
```

---

### Remotion 핵심 API

```javascript
// useCurrentFrame: 현재 프레임 번호 (0부터 시작)
const frame = useCurrentFrame();

// interpolate: 프레임에 따라 값을 부드럽게 변환
const opacity = interpolate(frame, [0, 30], [0, 1]);
// → 0프레임(불투명도 0) → 30프레임(불투명도 1)

// spring: 물리 기반 스프링 애니메이션
const scale = spring({ frame, fps, config: { damping: 20 }});

// Sequence: 특정 프레임부터 컴포넌트 시작
<Sequence from={60}>  {/* 60프레임 = 2초(30fps 기준) */}
  <TextSlide text="핵심 기능 소개" />
</Sequence>
```

> 위 코드를 이해할 필요 없다.
> Claude에게 "홍보 영상 Remotion 컴포넌트 만들어줘"라고 하면
> useCurrentFrame, interpolate를 포함한 전체 코드를 생성해준다.
> 코드에 에러가 나면 에러 메시지만 그대로 Claude에게 붙여넣으면 된다.

---

### 홍보 영상 구조 (Hook → 문제 → 해결 → CTA)

```
효과적인 홍보 영상 4단계:
┌──────────────────────────────────────────┐
│ 0~5초:   Hook — 타깃 고객의 문제 한 줄  │
│ 5~15초:  문제 — 현재 상황의 고통 구체화 │
│ 15~40초: 해결 — 내 제품/서비스의 가치  │
│ 40~60초: CTA — 지금 해야 하는 이유     │
└──────────────────────────────────────────┘

각 단계를 Remotion 컴포넌트로:
  <HookScene />      → 0~150프레임 (5초, 30fps)
  <ProblemScene />   → 150~450프레임 (10초)
  <SolutionScene />  → 450~1200프레임 (25초)
  <CTAScene />       → 1200~1800프레임 (20초)
```

---

## EXECUTE

**Step 0 — Node.js 설치 확인**

```
Claude에게 입력:
"node --version 과 npm --version을 확인해줘.
 없으면 Mac에 Node.js 설치하는 방법 알려줘."
```

Node.js가 설치되어 있어야 npx 명령어가 실행된다.
Remotion의 필수 전제 조건이다.

---

**Step 1 — Remotion 프로젝트 생성**

```
Claude에게 입력:
"npx create-video@latest로 Remotion 프로젝트를 만들어줘.
 프로젝트 이름: my-promo-video
 설치가 완료되면 개발 서버(npm run dev)를 실행해줘."
```

---

**Step 2 — 홍보 영상 브리프 작성**

```
promo_brief.md를 만들어줘.

---
# 홍보 영상 브리프

## 제품/서비스
[내 제품 또는 서비스 이름]

## 타깃
[어떤 사람을 위한 제품인가?]

## 핵심 가치
[이 제품으로 고객이 얻는 것]

## 영상 길이
60초

## 구조
0~5초:   Hook - "[타깃]을 위한 한 줄 질문"
5~15초:  문제 - 현재 상황의 고통
15~40초: 해결 - 제품이 해결하는 방법 (3가지)
40~60초: CTA - "지금 [행동] 하세요"

## 스타일
배경: 다크 (어두운 남색 또는 검정)
포인트 컬러: [브랜드 색상]
폰트: 굵고 깔끔하게
---
```

---

**Step 3 — Remotion 컴포넌트 생성**

```
promo_brief.md를 읽고
Remotion으로 60초 홍보 영상 컴포넌트를 만들어줘.

- HookScene, ProblemScene, SolutionScene, CTAScene 컴포넌트 분리
- useCurrentFrame + interpolate로 fadeIn 애니메이션
- spring 애니메이션으로 텍스트 등장 효과
- 1920×1080 (16:9) 기준
- src/Promo.tsx에 저장하고 미리보기 알려줘
```

---

**Step 4 — 렌더링**

```
Claude에게 입력:
"Remotion으로 promo_brief.md 기반 홍보 영상을 렌더링해줘.
 출력 파일: out/promo-video.mp4"
```

체크리스트:
```
□ Remotion 프로젝트가 생성됐나?
□ 브라우저에서 미리보기가 열리나?
□ HookScene, ProblemScene 등 4개 장면이 구분되나?
□ 애니메이션이 부드럽게 작동하나?
□ out/promo-video.mp4가 렌더링됐나?
```

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "Remotion에서 useCurrentFrame()의 역할은?",
    "header": "Quiz 6",
    "options": [
      {"label": "영상의 현재 재생 시간(초)을 반환한다", "description": "초 단위로 값이 나온다"},
      {"label": "현재 프레임 번호를 반환해서 애니메이션 값을 계산하는 기준이 된다", "description": "interpolate()와 함께 써서 프레임에 따라 opacity, position 등을 변환"},
      {"label": "컴포넌트를 자동으로 렌더링한다", "description": "렌더링은 npx remotion render 명령어로 한다"}
    ],
    "multiSelect": false
  }]
})
```

정답: 2번.
피드백: "맞아요! useCurrentFrame()은 현재 프레임 번호(0, 1, 2...)를 반환해요. 이 값을 interpolate()에 넣으면 '0프레임일 때 opacity 0, 30프레임일 때 opacity 1'처럼 애니메이션을 부드럽게 만들 수 있어요. Block 7에서는 같은 방식으로 온보딩 영상을 만들어볼게요."
