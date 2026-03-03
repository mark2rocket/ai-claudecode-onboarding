# Block 3-2: Skill (자동화 레시피)

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/skills
> ```

## EXPLAIN

### Skill이란?

반복되는 업무를 **레시피처럼 저장**해두고, 필요할 때 한 줄로 실행하는 기능입니다.

매주 하는 "SNS 콘텐츠 정리 → 성과 분석 → 다음 주 계획" 같은 작업을 `/content-weekly` 한 줄로 실행할 수 있게 되는 겁니다.

---

### CLAUDE.md와 Skill의 차이

| 구분 | CLAUDE.md | Skill |
|------|-----------|-------|
| 불러오는 시점 | **매 대화마다** 항상 | **필요할 때만** 호출 시 |
| 용도 | 항상 적용되는 규칙 | 특정 작업용 레시피 |
| 비유 | 항상 켜진 기본 설정 | 필요할 때 꺼내 쓰는 요리책 |

Claude의 대화 기억 용량은 한정되어 있습니다. CLAUDE.md는 항상 불러오지만, Skill은 호출할 때만 불러오기 때문에 용량을 아낄 수 있습니다.

> 💡 **용어 정리**
> - **컨텍스트 윈도우(대화 기억 용량)**: Claude가 한 번에 기억할 수 있는 대화의 양. 가득 차면 앞의 내용을 잊기 시작합니다
> - **점진적 로딩**: 한 번에 다 불러오지 않고, 필요할 때만 꺼내 읽는 방식

---

### Skill 폴더 구조

```
my-skill/
├── SKILL.md          ← 필수: 이 파일만 있으면 Skill이 됩니다
├── scripts/          ← 선택: 실행할 코드
├── references/       ← 선택: 참고 문서
└── assets/           ← 선택: 이미지 등 리소스
```

지금 여러분이 실행하고 있는 이 온보딩도 Skill입니다!

---

## EXECUTE

새 대화창을 열고 아래를 입력해보세요:

```
/day1-test-skill
```

> Skill이 어떻게 동작하는지 직접 체험합니다.

> "위 내용을 직접 실행해보세요. 실행이 끝나면 **'완료'** 또는 **'다음'**이라고 입력해주세요."

---

## QUIZ

> Phase B에서만 실행한다.

```json
AskUserQuestion({
  "questions": [{
    "question": "Skill이 CLAUDE.md와 다른 핵심 이유는?",
    "header": "Quiz 3-2",
    "options": [
      {"label": "필요할 때만 불러와서 대화 기억 용량을 효율적으로 씀", "description": "CLAUDE.md는 항상 불러오지만 Skill은 호출 시에만"},
      {"label": "더 강력한 기능을 가져서", "description": "강력함보다는 효율성과 재사용성의 차이"},
      {"label": "무료라서", "description": "둘 다 Claude Code 안에 포함"}
    ],
    "multiSelect": false
  }]
})
```

정답: **1번**.
