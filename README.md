# ai-claudecode-onboarding

비개발자 1인 사업가·크리에이터를 위한 **Claude Code Day 1 온보딩 스킬**입니다.

슬라이드 강의가 아닙니다. Claude가 직접 설명하고, 질문하고, 실습을 안내합니다.

---

## 대상

- 코딩 경험 없는 1인 크리에이터 (인스타그램·유튜브 운영자)
- Claude Code를 처음 접하는 비개발자
- AI 도구로 콘텐츠 워크플로우를 자동화하고 싶은 분

---

## 커리큘럼

| 블록 | 주제 | 중요도 |
|------|------|--------|
| Block 0 | 설치 & 첫 실행 | 필수 |
| Block 1 | 7일 후 모습 미리 체험 | 필수 |
| Block 2 | 왜 터미널인가? | 필수 |
| Block 3-필수 | Memory · Skill · MCP | **오늘 당장 쓸 것** |
| Block 3-심화 | Subagent · Agent Teams · Hook · Plugin | 나중에 |
| Block 4 | 터미널 & git 기초 | 선택 (협업 시) |

---

## 설치 방법

### 방법 1: OMC 스킬 관리자 (권장)

Claude Code 터미널에서:

```
/skill add https://github.com/mark2rocket/ai-claudecode-onboarding
```

### 방법 2: 직접 복사

```bash
# 1. 저장소 클론
git clone https://github.com/mark2rocket/ai-claudecode-onboarding.git

# 2. 스킬 폴더를 내 Claude 설정으로 복사
cp -r ai-claudecode-onboarding/.claude/skills/ai-claudecode-onboarding ~/.claude/skills/
```

### 설치 확인

Claude Code 터미널에서:

```
/skill list
```

`ai-claudecode-onboarding` 항목이 보이면 성공입니다.

---

## 사용 방법

Claude Code 터미널에서 아래 명령을 입력하면 온보딩이 시작됩니다:

```
/ai-claudecode-onboarding
```

Claude가 어느 블록부터 시작할지 물어보고, 설명 → 실습 → 퀴즈 순서로 진행합니다.

---

## 라이선스

MIT
