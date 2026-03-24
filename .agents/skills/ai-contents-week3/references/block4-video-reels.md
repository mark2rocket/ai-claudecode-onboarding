# Block 4: GIF + 영상소스로 긴 릴스 — "직접 찍은 영상을 FFmpeg으로 합친다"

> Track 1 전용 블록

---

## EXPLAIN

### 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 업그레이드     ║  ║  2. 영상 소스란?   ║
║                    ║  ║                    ║
║  ( ´▽`) 새암       ║  ║  (・∀・) 새암      ║
║  "GIF 릴스는 잘    ║  ║  "내가 직접 찍은   ║
║   됐어. 이번엔     ║  ║   화면이나 제품    ║
║   실제 영상도      ║  ║   영상을 넣으면    ║
║   넣어보자"        ║  ║   훨씬 진짜 같아!" ║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. FFmpeg 등장    ║  ║  4. Claude가        ║
║                    ║     명령어 생성       ║
║  (°□°!) 새암       ║  ║                    ║
║  "영상 합치려면    ║  ║  (≧▽≦) 새암       ║
║   FFmpeg이라는     ║  ║  "Claude한테 시키면║
║   툴이 필요한데... ║  ║   FFmpeg 명령어    ║
║   어떻게 쓰지?"   ║  ║   다 만들어줘!"    ║
╚════════════════════╝  ╚════════════════════╝
```

---

### FFmpeg이란?

```
FFmpeg = 영상 처리 CLI 도구 (무료, 오픈소스)

할 수 있는 것:
  - 영상 자르기, 합치기, 변환
  - 텍스트/이미지/GIF 오버레이
  - 자막 삽입 (SRT)
  - 음성 추가 / 분리
  - 비율 변환 (가로 → 세로)
  - 파일 형식 변환 (.mov → .mp4)

핵심 장점:
  - Claude가 명령어를 대신 작성해준다
  - 복잡한 GUI 편집 앱 없이 터미널 한 줄로 처리
  - 자동화 파이프라인에 넣기 좋음

설치 (Mac):
  brew install ffmpeg
```

---

### 영상 소스의 종류

```
1. 화면 녹화 (Screen Recording)
   → 앱, 웹사이트, Claude Code 작업 과정
   → Mac: Command+Shift+5
   → 제품 데모, 튜토리얼에 적합

2. 직접 촬영 (Camera)
   → 스마트폰으로 촬영한 영상
   → 손, 키보드, 제품 클로즈업
   → 생동감과 신뢰도 추가

3. 스톡 영상 (Stock Footage)
   → Pexels, Pixabay (무료)
   → "technology", "city", "office" 검색
```

---

### FFmpeg으로 합성하는 방법

```
기본 패턴 — 영상 위에 텍스트 오버레이:

ffmpeg -i input.mp4 \
  -vf "drawtext=fontfile=/path/to/font.ttf:\
       text='AI로 일 줄이기':\
       fontcolor=white:fontsize=80:\
       x=(w-text_w)/2:y=100" \
  -c:a copy output.mp4

기본 패턴 — 두 영상 세로로 합치기:

ffmpeg -i video1.mp4 -i video2.mp4 \
  -filter_complex "[0:v][1:v]concat=n=2:v=1:a=0" \
  output.mp4

기본 패턴 — 세로형으로 크롭:

ffmpeg -i input.mp4 \
  -vf "crop=ih*9/16:ih,scale=1080:1920" \
  vertical.mp4

→ 이 명령어들을 외울 필요 없다.
   Claude에게 원하는 결과를 설명하면 생성해준다.
```

---

### Claude에게 FFmpeg 명령어 맡기기

```
프롬프트 패턴:
"[파일명]을 [처리 방법]으로 처리해줘.
 결과 파일은 [파일명]으로 저장해줘.
 FFmpeg 명령어를 실행해줘."

예시:
"screen-recording.mov를 세로형(1080×1920)으로 변환하고
 상단에 '오늘의 AI 팁' 텍스트를 흰색으로 넣어줘.
 결과는 reels-v3.mp4로 저장해줘.
 FFmpeg 명령어 만들고 실행해줘."
```

---

## EXECUTE

**Step 1 — 영상 소스 준비**

아래 중 하나를 준비한다:

```
옵션 A: 화면 녹화 (가장 쉬움)
  Command+Shift+5로 15~30초짜리 화면 녹화
  (Claude Code 작업 모습, 앱 사용 화면 등)
  파일명: source.mov

옵션 B: 스마트폰 촬영
  30초 이내 짧은 영상 촬영
  Mac에 전송 (AirDrop 또는 USB)
  파일명: source.mp4

옵션 C: Pexels 무료 스톡 영상
  pexels.com → "technology" 검색 → 다운로드
  파일명: stock.mp4
```

---

**Step 2 — FFmpeg 설치 확인**

```
Claude에게 입력:
"ffmpeg가 설치돼 있는지 확인하고, 없으면 설치 방법 알려줘"
```

---

**Step 3 — 영상 합성**

```
영상 소스(source.mov)와 GIF 텍스트 오버레이를 합성해줘.

처리 순서:
1. source.mov를 세로형(1080×1920)으로 변환
2. 상단 20% 영역에 반투명 검정 바 추가
3. "AI로 일 줄이기" 텍스트를 상단에 흰색 굵게 추가
4. 결과를 reels-v3.mp4로 저장
5. 완료되면 파일 크기와 길이를 알려줘

FFmpeg 명령어를 만들고 실행해줘.
```

---

**Step 4 — 결과 확인 및 비교**

```
체크리스트:
□ FFmpeg이 설치됐나?
□ 영상 소스가 세로형으로 변환됐나?
□ 텍스트 오버레이가 잘 보이나?
□ Block 2(HTML만), Block 3(+GIF)와 비교했을 때 차이가 느껴지나?
□ reels-v3.mp4 파일이 생성됐나?
```

---

## QUIZ

```json
AskUserQuestion({
  "questions": [{
    "question": "FFmpeg를 쓸 때 Claude의 역할은?",
    "header": "Quiz 4",
    "options": [
      {"label": "FFmpeg 명령어를 대신 작성하고 실행해준다", "description": "원하는 결과를 설명하면 복잡한 명령어를 생성해줌"},
      {"label": "FFmpeg를 자동으로 설치해준다", "description": "설치는 brew로 직접 해야 한다"},
      {"label": "영상 편집 GUI를 제공한다", "description": "FFmpeg는 CLI 도구다"}
    ],
    "multiSelect": false
  }]
})
```

정답: 1번.
피드백: "맞아요! FFmpeg 명령어는 복잡하지만, Claude에게 '이 영상을 세로형으로 바꾸고 텍스트 넣어줘'처럼 설명하면 명령어를 직접 작성하고 실행까지 해줘요. FFmpeg 문법을 외울 필요가 없어요. Block 5에서는 여기에 SRT 자막과 음성을 추가해서 완전한 릴스를 완성해볼게요."
