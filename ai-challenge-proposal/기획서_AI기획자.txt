# AI 기획자 제안서: 5일 AI 비서 챌린지 기술 설계

> 작성일: 2026-03-29
> 목적: 비개발자 한국 직장인을 위한 Claude Code AI 비서 5일 챌린지 기술 설계 제안

---

## 기술 설계 원칙

1. **로컬 우선 (Local-First)** — Claude Code는 로컬에서 실행된다. 파일·데이터가 외부 서버로 전송되지 않는다는 점을 Day 1부터 명시한다.
2. **복붙 가능한 구체성** — 모든 실습 파일은 "복사해서 붙여넣으면 즉시 동작"하는 수준으로 작성한다.
3. **실패 포인트 사전 차단** — MCP 설정(Day 3)이 최대 이탈 지점이다. 사전 설치 가이드 + 폴백 시나리오를 필수로 제공한다.
4. **No New Concepts on Day 5** — Day 5는 기존 개념의 조합만으로 완성한다. 새 개념(웹훅 등)은 선택형 확장으로만 제공한다.
5. **비개발자 언어** — 터미널 명령어에 반드시 "이 명령어는 ~를 하는 명령어입니다" 주석을 병기한다.

---

## 1. 기술 실현 가능성 검토

### Day 1: Claude Code 설치 + CLAUDE.md + 기본 개념

| 항목 | 가능 여부 | 선결 조건 | 비개발자 난이도 | 막힐 포인트 & 해결법 |
|------|---------|---------|-------------|-----------------|
| Claude Code 설치 (macOS) | 가능 | Anthropic 계정, Pro/Max 플랜, Node.js | ★★☆ | Node.js 버전 문제 → `brew install node` 또는 nodejs.org 직접 설치 |
| Warp 터미널 설치 | 가능 | macOS 12 이상 | ★☆☆ | 없음. DMG 다운로드-설치로 완료 |
| CLAUDE.md 작성 | 가능 | Claude Code 설치 완료 | ★☆☆ | 빈 파일 공포증 → 템플릿 제공으로 해결 |
| 자연어로 폴더 구조 생성 | 가능 | Claude Code 실행 상태 | ★☆☆ | 없음 |
| 엑셀 파일 요약 (WOW) | 가능 | xlsx 파일이 로컬에 존재 | ★☆☆ | Claude Code는 xlsx 직접 파싱 가능. 단, 암호화된 파일은 불가 |
| 에이전트/MCP/스킬 개념 교육 | 가능 | 없음 | 개념 전달만 | 추상적 개념 → 비유(신입사원/아답터/버튼) 사용 |

**Day 1 주요 전제조건:**
- Claude Pro ($20/월) 또는 Max ($100/월) 플랜 필수 — Free 플랜은 Claude Code 미지원
- Node.js 18 이상 설치 필요
- macOS 기준 설명. Windows 참여자는 WSL2 필요하여 난이도 급상승 → 별도 가이드 제공 권장

---

### Day 2: 스킬 문법 + 리서치 자동화

| 항목 | 가능 여부 | 선결 조건 | 비개발자 난이도 | 막힐 포인트 & 해결법 |
|------|---------|---------|-------------|-----------------|
| SKILL.md 파일 작성 | 가능 | Claude Code 설치 | ★★☆ | 마크다운 미숙 → 템플릿 제공 |
| 슬래시 명령어 등록 | 가능 | `~/.claude/skills/` 경로에 파일 저장 | ★★☆ | 경로 오타 → 절대경로 복붙 명령어 제공 |
| 스킬 스토어 활용 | 가능 | 인터넷 연결 | ★☆☆ | oh-my-claudecode 설치 여부 확인 필요 |
| 웹 리서치 자동화 | 가능 | Claude Code 기본 제공 | ★★☆ | 한국어 검색 시 네이버 결과 미반영 가능 → 사이트 URL 지정 프롬프트 사용 |
| 보고서 마크다운 자동 저장 | 가능 | 없음 | ★☆☆ | 없음 |

---

### Day 3: Gmail MCP + mail-briefing 스킬

| 항목 | 가능 여부 | 선결 조건 | 비개발자 난이도 | 막힐 포인트 & 해결법 |
|------|---------|---------|-------------|-----------------|
| Gmail MCP 설치 | 가능 | Google 계정, OAuth 앱 설정 | ★★★ | OAuth 설정이 가장 어려움 → 단계별 스크린샷 가이드 필수 |
| MCP 설정 파일 작성 | 가능 | `~/.claude.json` 수정 | ★★★ | JSON 문법 오류 → jsonlint.com 검증 안내 |
| mail-briefing 스킬 동작 | 가능 | Gmail MCP 연결 완료 | ★★☆ | MCP 연결 실패 시 전체 Day 3가 막힘 → 폴백: 로컬 txt 파일 사용 |
| Outlook 연동 | 조건부 가능 | Outlook MCP 별도 설치 | ★★★★ | 이 챌린지에서는 Gmail만 지원 권장 |

**Day 3 폴백 시나리오 (MCP 설정 실패 시):**
메일 내용을 복사해서 `~/ai-assistant/inbox/mail_today.txt`에 붙여넣고 아래 프롬프트 사용:
```
inbox/mail_today.txt 파일을 읽고, 긴급/협력사/정기보고/필터링 4가지로 분류해서 브리핑해줘.
```

---

### Day 4: 서브에이전트 병렬 실행 + Slack/Notion/Calendar MCP

| 항목 | 가능 여부 | 선결 조건 | 비개발자 난이도 | 막힐 포인트 & 해결법 |
|------|---------|---------|-------------|-----------------|
| Slack MCP 설치 | 가능 | Slack 워크스페이스, Bot Token | ★★★ | Bot Token 생성 과정 복잡 → 단계별 안내 필수 |
| Notion MCP 설치 | 가능 | Notion Integration 생성 | ★★★ | Integration을 특정 페이지에 연결하는 단계 실수 多 |
| Google Calendar MCP | 가능 | Day 3 Gmail과 동일 OAuth | ★★☆ | Day 3 완료 시 추가 작업 거의 없음 |
| Task 도구로 서브에이전트 스폰 | 가능 | Claude Code Pro/Max 플랜 | ★★★ | SKILL.md에 Task 문법 직접 작성 필요 → 완성 템플릿 제공 |

---

### Day 5: 스킬 체이닝 or 외부 발행

| 항목 | 가능 여부 | 선결 조건 | 비개발자 난이도 | 막힐 포인트 & 해결법 |
|------|---------|---------|-------------|-----------------|
| /start 스킬 체이닝 | 가능 | Day 2~4 스킬 모두 완성 | ★★☆ | SKILL.md에서 다른 스킬 호출 문법 → 템플릿 제공 |
| /friday 주간 정리 스킬 | 가능 | Notion MCP 연결 완료 | ★★☆ | 없음 |
| Slack Incoming Webhook | 가능 | Slack 앱 설정 권한 | ★★★★ | 웹훅 URL 생성 → curl 테스트 → Claude 실행 3단계. 선택형 확장으로 제공 권장 |
| 뉴스레터 자동화 (Stibee API) | 조건부 가능 | Stibee 유료 플랜, API 키 | ★★★★★ | 챌린지 범위 초과 가능. Day 5 이후 보너스 트랙으로 별도 제공 권장 |

---

## 2. Day별 실습 파일 설계

### Day 1: 폴더 구조 + CLAUDE.md

#### 폴더 구조 (참여자가 만들 구조)

```
~/ai-assistant/
├── CLAUDE.md              # 오늘의 핵심 파일 — AI 비서 설명서
├── inbox/                 # 처리할 파일 넣는 곳
│   └── .gitkeep
├── output/                # Claude 결과물 저장
│   └── .gitkeep
├── research/              # 리서치 결과 저장
│   └── .gitkeep
└── skills/                # 나만의 스킬 저장 (Day 2부터 사용)
    └── .gitkeep
```

**Claude에게 입력하는 생성 프롬프트:**
```
~/ai-assistant 폴더를 만들고, 그 안에 inbox, output, research, skills 폴더를 만들어줘.
각 폴더 안에 .gitkeep 빈 파일도 만들어줘.
```

#### CLAUDE.md 실제 예시 전체 내용

`~/ai-assistant/CLAUDE.md`로 저장. 대괄호 부분을 자신의 정보로 채운다.

```markdown
# 나의 AI 비서 설정

## 역할
당신은 15년 경력의 꼼꼼한 시니어 비서입니다.
보고서는 반드시 '결론 → 근거 → 다음 액션' 순서로 작성합니다.
한국어로 대화하고, 격식체(~입니다/~합니다)를 유지합니다.

## 내 정보
- 이름: [이름 입력]
- 직책: [직책 입력] (예: 마케팅팀 AE, PM, 경영지원 대리)
- 회사 유형: [회사 설명] (예: 직원 50명 뷰티 이커머스 스타트업)
- 주요 업무:
  - [업무1] (예: 퍼포먼스 마케팅 운영)
  - [업무2] (예: SNS 콘텐츠 기획 및 업로드)
  - [업무3] (예: 월간 성과 보고서 작성)

## 협업 툴
- 슬랙: [주 사용 채널] (예: #marketing, #general)
- 노션: [주 사용 DB] (예: 콘텐츠 캘린더, OKR 트래커)
- 이메일: [Gmail / Outlook 중 선택]
- 기타: [Google Sheets, Linear 등 사용하는 툴]

## 출력 스타일
- 길이: 핵심만, 불필요한 감탄사 없이
- 형식: 불릿포인트 우선, 숫자는 원화(₩) 표기
- 보고서: 3줄 요약 먼저, 그다음 상세 내용
- 이메일 초안: 수신자 직급에 맞는 존댓말 수준 자동 조정

## 절대 하지 않는 것
- 확인되지 않은 정보를 사실처럼 말하지 않기
- "~인 것 같아요" 등 추측성 표현 금지 (모를 때는 "확인이 필요합니다" 사용)
- 내부 데이터를 외부 서비스로 전송하지 않기
- 파일 삭제 작업은 반드시 확인 후 실행

## 현재 진행 중인 프로젝트
- [프로젝트명]: [한 줄 설명]
- [프로젝트명]: [한 줄 설명]

## 나의 글쓰기 스타일
[내가 쓴 실제 보고서 문장 하나를 여기에 붙여넣기]
(예: "전월 대비 CTR 0.3%p 상승하였으며, 주요 원인은 소재 교체로 판단됩니다.")
```

**WOW 실습 프롬프트 (Day 1 마지막):**
```
inbox 폴더에 있는 파일들을 열어서,
각 파일의 핵심 내용을 3줄로 요약해줘.
요약 후 '공통적으로 개선이 필요한 부분'이 있다면 알려줘.
결과는 output/day1-summary.md 파일로 저장해줘.
```

---

### Day 2: 스킬 파일 설계

#### 스킬 파일 저장 위치 및 등록 방법

```bash
# Step 1: 스킬 디렉토리 생성 (터미널에서 한 번만 실행)
# 이 명령어는 홈 폴더 아래 .claude/skills/research-skill 폴더를 만드는 명령어입니다
mkdir -p ~/.claude/skills/research-skill

# Step 2: SKILL.md 파일 생성 (아래 내용 복붙)
# 이 명령어는 현재 위치를 research-skill 폴더로 이동하는 명령어입니다
cd ~/.claude/skills/research-skill
```

#### research-skill SKILL.md 전체 내용

`~/.claude/skills/research-skill/SKILL.md`로 저장:

```markdown
---
name: research-skill
description: 경쟁사 분석, 시장 조사, 업계 뉴스를 자동으로 리서치하고 보고서를 만든다.
  "리서치", "조사해줘", "/research" 요청에 사용한다.
---

# 리서치 자동화 스킬

## 사용법
/research [주제]
예시: /research 올리브영 신규 브랜드 입점 현황
예시: /research 경쟁사 A사 최근 업데이트
예시: /research HR테크 스타트업 요금제 비교

## 실행 순서

1. 사용자가 입력한 [주제]를 파악한다.
2. 웹 검색으로 최신 정보를 수집한다. 검색 시 아래를 참고한다:
   - 국내 뉴스: IT조선, 블로터, 바이라인네트워크, 한국경제 검색
   - 공식 사이트나 보도자료 우선 참조
   - 지난 30일 이내 정보에 집중
3. 수집한 정보를 아래 형식으로 정리한다:

---
## [주제] 리서치 결과
작성일: [오늘 날짜]
담당: AI 리서치 어시스턴트

### 핵심 요약 (3줄)
-
-
-

### 현재 상황
[2~3문단 설명]

### 주요 플레이어 동향
| 회사/브랜드 | 최근 변화 | 의미 |
|------------|---------|------|

### 최근 변화사항 (지난 30일)
-
-

### 수치 및 데이터
-
-

### 액션 권장사항
1.
2.
3.
---

4. 결과를 ~/ai-assistant/research/[주제 축약]-[YYYYMMDD].md 파일로 저장한다.
5. "리서치 완료! ~/ai-assistant/research/ 에 저장했습니다." 라고 알린다.
```

#### 스킬 작동 확인 방법

Claude Code를 열고 아래를 입력한다:
```
/research 올리브영 최근 신규 브랜드
```

---

### Day 3: Gmail MCP 설치 및 mail-briefing 스킬

#### Gmail MCP 설치 단계별 가이드

**Step 1: Google Cloud Console에서 OAuth 앱 만들기**

1. https://console.cloud.google.com 접속 (Google 계정으로 로그인)
2. 상단 프로젝트 선택 → "새 프로젝트" → 이름: `claude-assistant` → 만들기
3. 좌측 메뉴 → "API 및 서비스" → "라이브러리"
4. 검색창에 `Gmail API` → 클릭 → "사용 설정"
5. 좌측 메뉴 → "사용자 인증 정보" → "+ 사용자 인증 정보 만들기" → "OAuth 클라이언트 ID"
6. 처음이면 "동의 화면 구성" 먼저 진행:
   - User Type: 외부 → 만들기
   - 앱 이름: `Claude Assistant`, 이메일 입력 → 저장 후 계속
7. 애플리케이션 유형: "데스크톱 앱" → 이름: `Claude Desktop` → 만들기
8. JSON 다운로드 → 파일 이름을 `google-credentials.json`으로 변경
9. 터미널에서 실행: `mv ~/Downloads/google-credentials.json ~/ai-assistant/`

**Step 2: Gmail MCP 패키지 설치**

```bash
# 이 명령어는 Gmail MCP 서버 패키지를 전역으로 설치하는 명령어입니다
npm install -g @modelcontextprotocol/server-gmail

# 설치 확인 (버전 번호가 나오면 성공)
npx @modelcontextprotocol/server-gmail --version
```

**Step 3: Claude Code MCP 설정 파일 수정**

먼저 현재 사용자 이름 확인:
```bash
# 이 명령어는 현재 사용자의 홈 폴더 경로를 보여주는 명령어입니다
echo $HOME
# 출력 예시: /Users/jieun  ← 이 부분이 사용자 이름입니다
```

`~/.claude.json` 파일을 아래 내용으로 만든다. (`[사용자이름]` 부분을 실제 이름으로 교체)

```json
{
  "mcpServers": {
    "gmail": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-gmail",
        "--credentials-file",
        "/Users/[사용자이름]/ai-assistant/google-credentials.json"
      ]
    }
  }
}
```

저장 방법 (터미널):
```bash
# 이 명령어는 nano 텍스트 편집기로 파일을 여는 명령어입니다
nano ~/.claude.json
# 위 내용 붙여넣기 → Ctrl+X → Y → Enter
```

**Step 4: 인증 실행 및 확인**

```bash
# Claude Code 재시작
claude
# 자동으로 브라우저 인증 창이 열림 → Google 계정 로그인 → 권한 허용
```

연결 확인 방법 (Claude Code 내에서):
```
오늘 받은 Gmail 메일이 몇 통인지 알려줘.
```
숫자가 나오면 연결 성공.

#### mail-briefing SKILL.md 전체 내용

`~/.claude/skills/mail-briefing/SKILL.md`로 저장:

```markdown
---
name: mail-briefing
description: Gmail을 읽어서 오늘 받은 메일을 우선순위별로 브리핑한다.
  "메일 브리핑", "메일 요약", "오늘 메일", "/mail-briefing" 요청에 사용한다.
---

# 메일 브리핑 스킬

## 실행 순서

1. Gmail MCP를 통해 오늘 받은 메일(최근 24시간)을 모두 읽는다.
2. 각 메일을 아래 4가지 분류 기준으로 나눈다:

   분류 기준:
   - 긴급·액션 필요: 상사/임원 발신, 마감 언급("~까지", "D-", "긴급"), 계약/법무 관련
   - 협력사·파트너: 외부 파트너 발신, 검토 요청, 회신 필요
   - 정기 보고·참고: 자동 발송 리포트, 사내 공지, FYI 성격
   - 필터링 권장: 광고, 뉴스레터 구독, 수신 동의 없는 외부 발신

3. 아래 형식으로 출력한다:

---
메일 브리핑 ([오늘 날짜] 기준, 총 [N]통)

긴급·액션 필요 ([N]건)
- [발신자] "[제목 요약]" → 마감: [날짜 또는 "오늘"] / 액션: [해야 할 일 한 줄]

협력사·파트너 ([N]건)
- [발신자] "[제목 요약]" → [요청 내용 한 줄]

정기 보고·참고 ([N]건)
- [제목들 나열, 쉼표 구분]

필터링 권장 ([N]건)
- [간략 설명]

오늘 반드시 처리할 메일: [긴급 건 번호 나열]
예상 소요 시간: 약 [N]분
---

4. 출력 후: "특정 메일에 대해 답장 초안이 필요하시면 번호를 말씀해 주세요." 안내한다.
```

---

### Day 4: 서브에이전트 daily-briefing 스킬

#### MCP 설치 요약 및 .claude.json 최종 파일

**Slack Bot Token 발급 방법:**
1. https://api.slack.com/apps → "Create New App" → "From scratch"
2. App Name: `Claude Assistant`, 워크스페이스 선택 → 만들기
3. 좌측 "OAuth & Permissions" → "Bot Token Scopes" → 아래 4개 추가:
   - `channels:history` (채널 메시지 읽기)
   - `channels:read` (채널 목록 읽기)
   - `chat:write` (메시지 보내기)
   - `users:read` (사용자 정보 읽기)
4. 상단 "Install to Workspace" → 허용
5. "Bot User OAuth Token" (`xoxb-`로 시작) 복사

**Notion Integration 발급 방법:**
1. https://www.notion.so/my-integrations → "+ New integration"
2. Name: `Claude Assistant`, 워크스페이스 선택 → Submit
3. "Internal Integration Token" (`secret_`로 시작) 복사
4. **중요:** Notion에서 연결할 페이지 열기 → 우상단 "..." → "Connections" → "Claude Assistant" 추가
   (이 단계를 빠뜨리면 아무것도 읽지 못함)

**MCP 패키지 설치:**
```bash
# Slack MCP 설치
npm install -g @modelcontextprotocol/server-slack

# Notion MCP 설치
npm install -g @modelcontextprotocol/server-notion

# Google Calendar MCP 설치
npm install -g @modelcontextprotocol/server-google-calendar
```

**~/.claude.json 최종 전체 파일 (Day 4 완성본):**

아래 내용을 `~/.claude.json`에 저장한다. 모든 `[사용자이름]`, `[토큰]` 부분을 교체한다.

```json
{
  "mcpServers": {
    "gmail": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-gmail",
        "--credentials-file",
        "/Users/[사용자이름]/ai-assistant/google-credentials.json"
      ]
    },
    "google-calendar": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-google-calendar",
        "--credentials-file",
        "/Users/[사용자이름]/ai-assistant/google-credentials.json"
      ]
    },
    "slack": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-slack"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-여기에-봇-토큰-붙여넣기"
      }
    },
    "notion": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "secret_여기에-인테그레이션-키-붙여넣기"
      }
    }
  }
}
```

#### daily-briefing SKILL.md 전체 내용 (서브에이전트 병렬 실행)

`~/.claude/skills/daily-briefing/SKILL.md`로 저장:

```markdown
---
name: daily-briefing
description: Slack, Notion, Google Calendar를 동시에 분석해서 오늘의 데일리 브리핑을 만든다.
  "데일리 브리핑", "오늘 브리핑", "/daily-briefing" 요청에 사용한다.
---

# 데일리 브리핑 스킬

## 개요
3개의 서브에이전트가 동시에(병렬로) 각각의 정보원을 분석한다.
각 에이전트는 독립된 컨텍스트에서 작동하므로 서로의 정보에 방해받지 않는다.
결과를 취합해서 하나의 브리핑으로 출력한다.

## 실행 방법

아래 3개 Task를 동시에 실행한다. (병렬 실행 — 순서 없이 동시 시작)

**Task 1 — Slack 요약 에이전트:**
Slack MCP를 사용한다.
지난 16시간 동안 활동이 있었던 주요 채널(#general, #marketing, #product 등)을 확인한다.
읽지 않은 메시지와 나(@사용자)에게 직접 언급된 메시지를 가져온다.
채널별로 핵심 내용을 1~2줄로 요약하고, 멘션된 항목은 별도 표시한다.
아래 형식으로 반환한다:
[슬랙 요약]
- #채널명: 핵심 내용 한 줄
- (멘션) #채널명: 내용

**Task 2 — Notion 현황 에이전트:**
Notion MCP를 사용한다.
접근 가능한 데이터베이스(콘텐츠 캘린더, OKR, 태스크 목록 등)를 확인한다.
오늘 날짜 기준으로 마감이 임박한 항목(오늘 또는 내일)을 찾는다.
진행 중이거나 검토 중인 항목 중 업데이트가 필요한 것을 표시한다.
아래 형식으로 반환한다:
[노션 현황]
- 오늘 마감: [항목명] / [담당자]
- 검토 필요: [항목명]
- 이번 주 예정: [항목명]

**Task 3 — 캘린더 에이전트:**
Google Calendar MCP를 사용한다.
오늘의 일정을 시간순으로 가져온다.
각 일정의 제목, 시간, 참석자(있는 경우)를 정리한다.
아래 형식으로 반환한다:
[오늘 일정]
- HH:MM [일정 제목] ([소요 시간]) — 참석자: [있으면 표시]

## 출력 형식

3개 에이전트 결과를 취합해서 아래 형식으로 최종 출력한다:

---
데일리 브리핑 ([오늘 날짜 요일 포함])

[슬랙 요약]
(Task 1 결과 삽입)

[노션 업무 현황]
(Task 2 결과 삽입)

[오늘 일정]
(Task 3 결과 삽입)

[오늘의 액션 Top 3]
1. (슬랙+노션+캘린더 정보를 종합해서 오늘 가장 중요한 3가지 도출)
2.
3.
---
```

#### 병렬 실행 확인 방법

Claude Code에서 `/daily-briefing` 입력 후, 터미널에서 "Agent 1 started", "Agent 2 started", "Agent 3 started" 메시지가 거의 동시에 나타나면 병렬 실행 성공.

---

### Day 5: 스킬 체이닝 /start, /friday

#### /start SKILL.md 전체 내용

`~/.claude/skills/start-skill/SKILL.md`로 저장:

```markdown
---
name: start-skill
description: 출근 시 실행하는 모닝 루틴 스킬. mail-briefing과 daily-briefing을 순서대로 실행하고 오늘의 작전 계획을 만든다.
  "출근", "시작", "/start", "오늘 시작" 요청에 사용한다.
---

# 출근 루틴 스킬 (/start)

## 실행 순서

오늘 날짜와 현재 시각을 확인한다.

**Step 1 — 메일 브리핑**
/mail-briefing 스킬을 실행한다.
(Gmail에서 오늘 받은 메일을 긴급/협력사/정기/필터링으로 분류)

**Step 2 — 데일리 브리핑**
/daily-briefing 스킬을 실행한다.
(Slack, Notion, 캘린더를 병렬로 읽어서 종합 현황 제공)

**Step 3 — 오늘의 작전 계획 생성**
Step 1과 Step 2 결과를 종합해서 아래 형식으로 오늘의 작전 계획을 만든다:

---
오늘의 작전 계획 ([날짜] [요일])

지금 당장 해야 할 것
1. [메일/슬랙에서 파악한 긴급 액션]
2. [노션/캘린더에서 파악한 마감 임박 항목]
3. [오늘 미팅 전 준비사항]

오후에 처리할 것
- [중요하지만 급하지 않은 항목들]

오늘 넘겨도 되는 것
- [D+1 이상 여유 있는 항목들]

오늘의 주요 일정
[캘린더 일정 요약]

어제 미완료 항목 (있다면)
- [어제 날짜의 output 폴더에 미완료 메모가 있으면 표시]
---

**Step 4 — 결과 저장**
작전 계획을 ~/ai-assistant/output/start-[YYYYMMDD].md 파일로 저장한다.
"출근 루틴 완료! 오늘도 좋은 하루 되세요." 라고 인사한다.
```

#### /friday SKILL.md 전체 내용

`~/.claude/skills/friday-skill/SKILL.md`로 저장:

```markdown
---
name: friday-skill
description: 금요일 퇴근 전 실행하는 주간 마무리 스킬. 이번 주 실적을 정리하고 다음 주를 준비한다.
  "금요일", "주간 정리", "/friday", "주간 마무리" 요청에 사용한다.
---

# 금요일 마무리 스킬 (/friday)

## 실행 순서

오늘 날짜(금요일 기준)를 확인한다.

**Step 1 — 이번 주 실적 취합**
~/ai-assistant/output/ 폴더에서 이번 주(월~금) start-*.md 파일을 모두 읽는다.
각 날의 완료 항목과 미완료 항목을 파악한다.

Notion MCP를 통해 이번 주에 업데이트된 태스크/프로젝트 항목을 확인한다.

**Step 2 — 주간 보고서 초안 생성**
아래 형식으로 주간 보고서 초안을 만든다:

---
주간 업무 보고서
기간: [이번 주 월요일] ~ [금요일]
작성: [CLAUDE.md의 이름]

이번 주 완료한 주요 업무
1.
2.
3.

진행 중 (다음 주 이어서)
-
-

다음 주 주요 일정
(Google Calendar에서 다음 주 일정 가져오기)
-
-

이번 주 잘한 것 3가지
1. (완료 항목 기반으로 성과 표현)
2.
3.

건의사항 또는 이슈
-
---

**Step 3 — 미완료 항목 이월 처리**
이번 주 미완료 항목 목록을 보여주고:
"위 항목 중 다음 주로 이월할 항목을 번호로 알려주세요. 나머지는 취소 처리합니다." 라고 묻는다.

사용자 응답을 받아 ~/ai-assistant/output/carry-over-[다음주월요일].md 파일로 저장한다.

**Step 4 — 결과 저장**
주간 보고서를 ~/ai-assistant/output/weekly-[YYYYMMDD].md 파일로 저장한다.
"주간 마무리 완료! 수고하셨습니다. 편안한 주말 보내세요." 라고 인사한다.
```

#### (선택형 확장) Slack Webhook 자동 포스팅

기본 캡스톤 완료 후 시간이 남는 참여자를 위한 보너스 실습.

**Step 1: Slack Incoming Webhook URL 발급**
1. https://api.slack.com/apps → 자신의 앱 선택
2. 좌측 "Incoming Webhooks" → 활성화(ON)
3. "Add New Webhook to Workspace" → 포스팅할 채널 선택
4. Webhook URL 복사 (`https://hooks.slack.com/services/...`)

**Step 2: 작동 테스트 (터미널에서)**
```bash
# 이 명령어는 Slack에 테스트 메시지를 보내는 명령어입니다
# [WEBHOOK_URL] 부분을 실제 URL로 교체하세요
curl -X POST -H 'Content-type: application/json' \
  --data '{"text":"안녕하세요! Claude AI 비서 연결 테스트입니다."}' \
  [WEBHOOK_URL]
```
터미널에 `ok`가 출력되고 Slack 채널에 메시지가 오면 성공.

**Step 3: /start 스킬에 Slack 포스팅 추가**

/start SKILL.md의 Step 4 뒤에 아래 내용을 추가:

```markdown
**Step 5 — 슬랙 공유 (선택)**
사용자가 "슬랙에 공유해줘"라고 하면:
Bash 도구로 아래 curl 명령어를 실행해서 오늘의 작전 계획 요약을 슬랙에 포스팅한다.

curl -X POST -H 'Content-type: application/json' \
  --data '{"text":"[오늘의 브리핑 요약 3줄]"}' \
  https://hooks.slack.com/services/[여기에-웹훅-URL]
```

---

## 3. 기술 난이도 매핑

### Day별 기술 난이도 (비개발자 기준 1~5점)

| Day | 주요 내용 | 난이도 | 핵심 근거 |
|-----|---------|--------|---------|
| Day 1 | 설치 + CLAUDE.md | ★★☆☆☆ (2점) | 설치 과정에서 Node.js 버전 이슈 가능성 있으나 구글 검색으로 해결 가능 수준 |
| Day 2 | 스킬 문법 + 리서치 | ★★☆☆☆ (2점) | 파일 경로와 마크다운 규칙만 익히면 됨. 실수해도 다시 저장하면 됨 |
| Day 3 | Gmail MCP 설치 | ★★★★☆ (4점) | OAuth 설정 복잡. JSON 문법 오류 시 전체 Claude Code가 시작 안 됨 |
| Day 4 | 서브에이전트 + 멀티 MCP | ★★★☆☆ (3점) | MCP 추가 설치는 Day 3 방법과 동일. SKILL.md Task 문법은 템플릿 복붙으로 해결 가능 |
| Day 5 | 스킬 체이닝 | ★★☆☆☆ (2점) | 기존 스킬을 조합하는 것이므로 새 개념 없음. 이전 스킬들이 잘 작동하면 쉽게 완성 |

### 가장 위험한 탈락 포인트 Top 3 및 탈출구

**1위 — Day 3 Gmail MCP OAuth 설정 실패**
- 위험 신호: `Error: Could not load credentials` 또는 브라우저 인증 창이 안 열림
- 탈출구 A (권장): "Day 2.5 사전 과제"로 Day 2 당일 저녁에 MCP 설치만 먼저 진행. Day 3 본 수업은 스킬 제작에 집중.
- 탈출구 B (폴백): Gmail 대신 로컬 텍스트 파일(mail_today.txt)로 동일 실습 진행. MCP 없이도 분류 로직은 배울 수 있음.
- 탈출구 C: 챌린지 운영자가 사전에 녹화한 3분 설치 영상 제공. "따라만 하면 되는" 영상이 FAQ보다 효과적.

**2위 — Day 1 Node.js / Claude Code 설치 실패**
- 위험 신호: `claude: command not found` 또는 `npm ERR!` 메시지
- 탈출구 A: Node.js 버전 확인 (`node --version`). 18 미만이면 `brew upgrade node` 또는 nodejs.org에서 재설치.
- 탈출구 B: Windows 사용자는 WSL2 설치가 필요. Day 0에 "운영체제 확인 + 사전 설치 안내" 별도 발송.
- 탈출구 C: Claude Code 설치 전 사전 설치 체크리스트(Node.js 버전, Anthropic 플랜 확인) 배포.

**3위 — Day 4 ~/.claude.json JSON 문법 오류**
- 위험 신호: Claude Code 실행 시 `JSON parse error` 또는 MCP 도구가 안 보임
- 탈출구 A: https://jsonlint.com 에서 파일 내용 붙여넣어 검증. 빨간 줄 표시된 곳 수정.
- 탈출구 B: 완성된 ~/.claude.json 예시 파일을 챌린지 자료로 배포. 참여자는 토큰만 교체.
- 탈출구 C: Claude Code 내에서 `claude config`로 설정 확인 방법 안내.

---

## 4. Day 5 기술 권고

### 옵션 비교

| 비교 항목 | 옵션 1: 스킬 체이닝 (/start + /friday) | 옵션 2: 웹훅 + 외부 발행 |
|---------|--------------------------------------|----------------------|
| 새 개념 필요 여부 | 없음 (기존 스킬 조합) | 있음 (HTTP, Webhook, curl) |
| 구현 난이도 | ★★☆☆☆ | ★★★★☆ |
| 에러 발생 가능성 | 낮음 (내부 스킬 호출만) | 높음 (외부 서비스 연결, 토큰 만료 등) |
| 비개발자 성공률 | 85% 이상 예상 | 50% 이하 예상 |
| 완성 후 성취감 | 높음 — "내가 만든 아침 루틴 시스템" | 매우 높음 — "슬랙에 내가 만든 메시지가 자동으로 올라감" |
| 실제 사용 빈도 | 매일 (출근/퇴근 트리거) | 주 1~2회 (필요 시 트리거) |
| 실패 시 파급 | Day 5 일부 실패, 복구 쉬움 | Day 5 전체 막힘 가능, 복구 어려움 |

### 권고: 옵션 1을 필수 캡스톤, 옵션 2를 선택형 확장으로 운영

**기술적 근거:**

1. **학습 설계 원칙 충족** — Day 5는 새 개념 없이 기존 학습을 통합하는 날이어야 한다. 웹훅은 HTTP 엔드포인트, 인증 헤더, JSON 페이로드 개념을 새로 도입하므로 인지 부하가 급증한다.

2. **실패 허용 구조** — 웹훅 연결에서 에러가 나면 `curl: (7) Failed to connect` 또는 `invalid_payload` 같은 추상적 오류 메시지가 나온다. 비개발자에게 이 오류는 해결 경로를 찾기 어렵다. 스킬 체이닝 실패는 대부분 SKILL.md 파일 경로 문제로, 수정이 직관적이다.

3. **일상 사용성이 학습 유지를 결정한다** — 챌린지 종료 후 도구를 매일 쓰게 만드는 것이 최종 목표다. `/start`는 출근 트리거가 있어 매일 사용한다. 웹훅 기반 자동화는 유지보수(토큰 만료, 채널 변경)가 필요하고 한 번 깨지면 방치하기 쉽다.

4. **한국 리서치의 인사이트 반영** — 한국 리서처 보고서는 "슬랙 자동 포스팅이 더 강한 성취감을 준다"고 제안했다. 이를 완전히 버리지 않되, 기본 캡스톤 완성 후 보너스로 제공하면 두 가지 이점을 모두 취할 수 있다. 빠르게 완성한 참여자는 웹훅 확장을 하고, 나머지는 스킬 체이닝으로 성공 경험을 만든다.

**권장 Day 5 진행 구조:**

```
0:00 ~ 0:15  아침 복습 — Days 1~4 전체 아키텍처를 그림으로 그려보기
0:15 ~ 0:35  스킬 체이닝 개념 (5분) + /start 파일 작성 (15분)
0:35 ~ 1:00  /friday 파일 작성 + 두 스킬 연결 테스트
1:00 ~ 1:20  /start 실행 → 결과 스크린샷 → 카카오톡 오픈채팅에 공유
1:20 ~ 1:40  (선택형) Slack Webhook 추가 — 빠른 참여자만
1:40 ~ 2:00  수료 정리 + "이제 무엇을 자동화할지" 개인 계획 작성
```

---

## 5. 보안·데이터 가이드

### 한국 직장인 보안 우려에 대한 기술적 답변

**Q: "회사 내부 데이터를 Claude Code에 입력하면 Anthropic 서버로 전송되나요?"**

A: Claude Code는 로컬 컴퓨터에서 실행되는 도구다. 파일을 읽고 분석하는 작업은 내 컴퓨터 안에서 이루어진다. 단, Claude에게 질문을 입력할 때 그 텍스트는 Anthropic API를 통해 처리된다. 따라서:

- 파일 경로, 폴더 구조: 로컬에서만 처리
- 파일 내용 중 Claude에게 "요약해줘"라고 보낸 부분: API로 전송됨
- API 전송 데이터는 Anthropic의 Privacy Policy에 따라 처리되며, 훈련 데이터로 사용하지 않도록 설정 가능 (API 사용 시 기본 비훈련)

실무 권고:
- 민감도가 높은 개인정보(주민등록번호, 계좌번호 등)는 Claude에게 직접 입력하지 말고, 익명화된 버전 사용
- CLAUDE.md에 `내부 기밀 데이터를 외부로 전송하지 않기` 규칙 명시 (AI 자체 제어)
- 회사 IT 정책 확인 후 사용. 개인 업무 효율화 용도는 대부분 허용 범위

---

**Q: "Gmail MCP를 연결하면 모든 메일이 자동으로 어딘가에 저장되나요?"**

A: 아니다. Gmail MCP는 Claude가 요청할 때만 Gmail API를 호출해서 메일을 읽는다. 자동 수집·저장 기능은 없다. `/mail-briefing`을 실행할 때만 읽고, 결과를 로컬 파일로 저장하는 것은 내가 명령한 경우에만 일어난다.

Gmail API 권한 범위(scope) 확인 방법:
1. https://myaccount.google.com/permissions 접속
2. `Claude Assistant` 항목 클릭 → 부여된 권한 목록 확인
3. 언제든 여기서 권한 취소 가능

---

**Q: "Slack Bot이 연결되면 모든 채널을 볼 수 있나요?"**

A: Bot이 추가된 채널만 볼 수 있다. 기본적으로 Bot은 초대받은 채널에만 접근 가능하다. 민감한 채널(인사, 급여 등)은 Bot을 초대하지 않으면 된다.

최소 권한 설정 권장:
- `channels:history`: 공개 채널 메시지 읽기만 허용
- Private 채널은 별도 초대 없으면 접근 불가
- Bot 초대 전 팀장 또는 Slack 관리자에게 공유 권장

---

### 참여자에게 Day 1에 알려야 할 보안 사항 (체크리스트)

아래 내용을 Day 1 오리엔테이션에서 명확히 전달한다:

```
Claude Code 보안 설정 체크리스트

[필수]
- CLAUDE.md에 "내부 기밀 데이터를 외부로 전송하지 않기" 규칙 추가 완료
- 개인정보(주민번호, 계좌번호, 비밀번호)는 Claude에 직접 입력 금지
- MCP 연결 전 회사 IT 정책 또는 팀장 확인 (특히 보안 정책이 있는 중견/대기업)

[권장]
- Gmail MCP 권한을 "읽기 전용(Read Only)"으로 제한
- Slack Bot은 업무 채널에만 초대 (인사, 급여 채널 제외)
- 실습 후 Google 계정 권한 관리 페이지에서 부여된 권한 목록 확인

[참고]
- Claude Code 자체는 오프라인으로도 실행 가능 (파일 읽기/쓰기 등)
- 웹 검색, MCP 도구 사용 시에만 외부 연결 발생
- Anthropic API는 SOC 2 Type II 인증, 기업용 데이터 비훈련 정책 적용
```

---

## 6. 즉시 실행 권고사항

챌린지 시작 전 운영팀이 준비해야 할 항목 (우선순위 순):

### 즉시 실행 (런칭 전 필수)

1. **Day 3 MCP 설치 영상 녹화** — Gmail MCP OAuth 설정을 Mac에서 실제로 따라하면서 녹화한 3분 영상. 텍스트 가이드보다 10배 효과적. 이것이 없으면 Day 3 이탈률이 40%를 넘을 수 있다.

2. **Day 1 사전 설치 체크리스트 배포** — 챌린지 시작 하루 전 참여자에게 발송:
   - Node.js 설치 및 버전 확인 방법
   - Warp 터미널 설치
   - Anthropic 플랜 확인
   - macOS / Windows 여부 확인

3. **완성된 SKILL.md 파일 4개 zip 배포** — research-skill, mail-briefing, daily-briefing, start-skill의 완성본 파일을 미리 배포. 참여자는 빈칸 채우기 방식으로 진행.

4. **~/.claude.json 최종 예시 파일 배포** — 4개 MCP 설정이 모두 포함된 예시 파일. 참여자는 토큰 값만 교체하면 됨.

### 런칭 후 운영

5. **카카오톡 오픈채팅 개설** — 매일 인증샷 공유 채널. Day 3 MCP 오류 Q&A는 여기서 실시간 지원. 다른 사람 오류와 해결 사례가 쌓이면 자연스러운 FAQ가 됨.

6. **Day 3 라이브 세션 (30분) 제공** — MCP 설치가 가장 어려운 날이다. 비동기 자료만으로는 이탈을 막기 어렵다. Zoom 또는 구글 미트로 짧은 라이브 Q&A 제공 시 완료율이 유의미하게 상승한다.

7. **Day 5 인증샷 포맷 제공** — 최종 결과물을 공유할 때 쓸 수 있는 간단한 카드 이미지 템플릿. "5일 챌린지 수료 + /start 실행 화면 + 한 줄 소감" 형식. LinkedIn이나 인스타그램 공유로 바이럴 효과 기대.

---

*작성: AI 기획자 | 기반 데이터: 한국 리서처 보고서, 해외 리서처 보고서 1·2 (2026-03-29)*
