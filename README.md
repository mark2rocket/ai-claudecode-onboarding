# claudecode-ai-contents-challenge

비개발자 1인 사업가·크리에이터를 위한 **Claude Code AI 컨텐츠 워크플로우 챌린지** 스킬 모음입니다.

슬라이드 강의가 아닙니다. Claude가 직접 설명하고, 질문하고, 실습을 안내합니다.

---

## 대상

- 코딩 경험 없는 1인 크리에이터 (인스타그램·유튜브 운영자)
- Claude Code를 처음 접하는 비개발자
- AI 도구로 콘텐츠 워크플로우를 자동화하고 싶은 분

---

## 커리큘럼

| 주차 | 주제 |
|------|------|
| Week 1 | AX 마인드셋 + Claude Code 기본 & 필수 기능 |
| Week 2 | 카드뉴스 워크플로우 — 기획·프롬프트 구체화·파이프라인·템플릿 |
| Week 3 | 영상 제작 워크플로우 — 릴스(HTML+FFmpeg) & Remotion(홍보/온보딩/강의) |
| Week 4 | 나만의 콘텐츠 제작 스킬 만들기 — `/my-cardnews` & `/my-reels` 자동화 스킬 패키징 |

---

## 설치 방법

```bash
# 1. 저장소 클론
git clone https://github.com/mark2rocket/claudecode-ai-contents-challenge.git

# 2. 스킬 폴더를 내 Claude 설정으로 복사
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week1 ~/.claude/skills/
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week2 ~/.claude/skills/
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week3 ~/.claude/skills/
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week4 ~/.claude/skills/
```

---

## 사용 방법

Claude Code 터미널에서 아래 명령을 입력하면 수업이 시작됩니다:

```
/ai-contents-week1   # Week 1: AX 마인드셋 + Claude Code 기초
/ai-contents-week2   # Week 2: 카드뉴스 워크플로우
/ai-contents-week3   # Week 3: 영상 제작 워크플로우 (릴스 & Remotion)
/ai-contents-week4   # Week 4: 나만의 카드뉴스·릴스 스킬 만들기
```

Claude가 어느 세션부터 시작할지 물어보고, 설명 → 실습 → 퀴즈 순서로 진행합니다.

---

## 라이선스

MIT
