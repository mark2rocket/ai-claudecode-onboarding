# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## 프로젝트 개요

비개발자 1인 크리에이터·사업가를 위한 **Claude Code AI 컨텐츠 워크플로우 챌린지** 스킬 모음.
슬라이드 강의가 아니라 Claude가 직접 설명·질문·실습을 안내하는 인터랙티브 커리큘럼이다.

빌드, 테스트, 린트 명령어 없음 — 순수 콘텐츠(Markdown) 저장소.

---

## 스킬 배포 규칙 (핵심)

새 스킬을 만들 때 **반드시** `.agents/skills/`에 추가해야 한다.

| 경로 | 용도 |
|------|------|
| `.agents/skills/` | 배포용 — GitHub 클론 후 설치 시 이 경로 기준 |
| `.claude/skills/` | 로컬 전용 — GitHub 설치 시 반영 안 됨 |

```bash
# 로컬에서 만든 경우 배포 전 반드시 복사
cp -r .claude/skills/ai-contents-weekN .agents/skills/

# 로컬 설치 (개발 중 테스트용)
cp -r .agents/skills/ai-contents-weekN ~/.claude/skills/
```

`.claude/skills/`에만 만들면 다른 사람이 설치해도 스킬이 보이지 않는다.

---

## 스킬 파일 구조

각 스킬은 아래 구조를 따른다:

```
.agents/skills/<skill-name>/
├── SKILL.md              # 오케스트레이터 — 진행 규칙 + 블록 맵
└── references/
    ├── block0-*.md       # 각 블록의 교육 콘텐츠
    ├── block1-*.md
    └── ...
```

### SKILL.md 구조

```markdown
---
name: skill-name
description: 트리거 설명. "키워드1", "키워드2" 요청에 사용.
---

# STOP PROTOCOL         ← 최우선 규칙 (절대 위반 금지)
## References 파일 맵   ← 블록 → 파일 매핑 테이블
## 진행 규칙            ← 블록 순서, 트랙 분기 등
## 시작                 ← 스킬 호출 시 첫 번째 동작
```

### references/block*.md 구조

모든 블록 파일은 아래 3개 섹션으로 구성된다:

```markdown
## EXPLAIN   ← 4컷 만화 + 개념 설명 (Phase A에서만 읽음)
## EXECUTE   ← 실습 프롬프트 + 체크리스트 (Phase A에서만 읽음)
## QUIZ      ← AskUserQuestion (Phase B에서만 읽음)
```

---

## STOP PROTOCOL — 스킬의 핵심 교육 패턴

모든 스킬은 블록당 **반드시 2턴**으로 진행한다. 이를 위반하면 수업 구조가 망가진다.

```
Phase A (첫 번째 턴):
  EXPLAIN 읽기 → 설명 → EXECUTE 읽기 → "직접 해보세요" 안내 → ⛔ STOP
  ❌ 금지: AskUserQuestion 호출, 퀴즈 출제, "해봤나요?" 질문

  ↓ 사용자가 "완료" / "다음" 입력

Phase B (두 번째 턴):
  QUIZ 읽기 → AskUserQuestion으로 퀴즈 → 피드백 → 다음 블록 이동 확인
```

Phase A 종료 시 필수 출력 문구:
```
---
👆 위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

---

## 현재 커리큘럼

| Week | 스킬명 | 주제 |
|------|--------|------|
| Week 1 | `ai-contents-week1` | AX 마인드셋 + Claude Code 기초 |
| Week 2 | `ai-contents-week2` | 카드뉴스 워크플로우 |
| Week 3 | `ai-contents-week3` | 영상 제작 워크플로우 (릴스 + Remotion) |
| Week 4 | `ai-contents-week4` | 나만의 카드뉴스·릴스 제작 스킬 만들기 |

Week 3은 듀얼 트랙 구조:
- **Track 1** (Block 2~5): 릴스 — HTML 애니메이션 → GIF → FFmpeg → 자막+음성
- **Track 2** (Block 6~8): Remotion — 홍보/온보딩/강의 영상
- **Block 9**: 두 트랙 공통 마무리

---

## 새 Week 스킬 추가 방법

1. `.agents/skills/ai-contents-weekN/` 디렉토리 생성
2. `SKILL.md` 작성 — 기존 Week 2/3의 STOP PROTOCOL 섹션을 그대로 복사하고 블록 특수 규칙만 수정
3. `references/block*.md` 파일 작성 — EXPLAIN / EXECUTE / QUIZ 3섹션 필수
4. 로컬 설치 테스트: `cp -r .agents/skills/ai-contents-weekN ~/.claude/skills/`
5. 커밋 + 푸시
6. README.md의 커리큘럼 표, 설치 명령어, 사용 방법 업데이트

---

## 콘텐츠 작성 규칙

- **4컷 만화**: EXPLAIN 섹션 첫 부분에 항상 포함. ASCII 박스 형식, 주인공 이름 "새암"
- **퀴즈**: 선택지 3개, 정답은 항상 명확하게 `정답: N번.` + 피드백 문장으로 마무리
- **퀴즈 없는 블록**: 파일 상단에 `> 이 블록은 퀴즈 없이 진행한다. EXECUTE 완료 후 결과물이 증거다.` 명시
- **GIF 소스**: GIPHY/Tenor는 저작권 주의. 안전 소스는 Klipy, Pixabay GIF, Pexels Video (CC0)
- **영상 스펙**: 릴스 = 1080×1920 (9:16), Remotion = 1920×1080 (16:9)
