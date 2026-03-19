# ai-contents-challenge 프로젝트 규칙

## 스킬 배포 규칙

새 스킬(week3, week4 등)을 만들 때는 반드시 `.agents/skills/`에 추가해야 한다.

- **배포용**: `.agents/skills/` — GitHub 클론 후 설치 시 이 경로를 기준으로 함
- **로컬 작업용**: `.claude/skills/` — 로컬에서만 사용되며 GitHub 설치 시 반영 안 됨

`.claude/skills/`에만 만들면 다른 사람이 설치해도 스킬이 보이지 않는다.

```bash
# 로컬에서 만든 경우 배포 전 반드시 복사
cp -r .claude/skills/ai-contents-weekN .agents/skills/
```
