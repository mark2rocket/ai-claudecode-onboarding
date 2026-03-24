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
| Week 4 | (예정) |

### Week 1 블록 구성

| 블록 | 주제 |
|------|------|
| Block 0 | AX 마인드셋 — AI 시대에 일하는 방식 |
| Block 1 | 설치 & 첫 실행 |
| Block 2 | 7일 후 모습 미리 체험 (`/oh-my-cardnews` 데모) |
| Block 2-Break | 터미널 꾸미기 & 상태바 설정 |
| Block 3 | 왜 터미널인가? |
| Block 4-1 | Memory — Claude가 나를 기억하게 하기 |
| Block 4-2 | Skill — 반복 작업 자동화 |
| Block 4-3 | MCP — 외부 도구 연결 |
| Block 4-4 | Subagent — 병렬 작업 위임 |
| Block 4-5 | Advanced Features 소개 |
| Block 5 | 터미널 & git 기초 |

---

## 설치 방법

### 방법 1: OMC 스킬 관리자 (권장)

Claude Code 터미널에서:

```
/skill add https://github.com/mark2rocket/claudecode-ai-contents-challenge
```

### 방법 2: 직접 복사

```bash
# 1. 저장소 클론
git clone https://github.com/mark2rocket/claudecode-ai-contents-challenge.git

# 2. 스킬 폴더를 내 Claude 설정으로 복사
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week1 ~/.claude/skills/
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week2 ~/.claude/skills/
cp -r claudecode-ai-contents-challenge/.agents/skills/ai-contents-week3 ~/.claude/skills/
```

### 설치 확인

Claude Code 터미널에서:

```
/skill list
```

`ai-contents-week1`, `ai-contents-week2`, `ai-contents-week3` 항목이 보이면 성공입니다.

---

## 사용 방법

Claude Code 터미널에서 아래 명령을 입력하면 수업이 시작됩니다:

```
/ai-contents-week1   # Week 1: AX 마인드셋 + Claude Code 기초
/ai-contents-week2   # Week 2: 카드뉴스 워크플로우
/ai-contents-week3   # Week 3: 영상 제작 워크플로우 (릴스 & Remotion)
```

Claude가 어느 블록부터 시작할지 물어보고, 설명 → 실습 → 퀴즈 순서로 진행합니다.

---

## 라이선스

MIT
