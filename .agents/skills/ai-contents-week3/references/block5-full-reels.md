# Block 5: 자막 + 음성으로 완성 릴스 — "SRT + TTS + FFmpeg = 완성본"

> Track 1 전용 블록
> 이 블록은 퀴즈 없이 진행한다. EXECUTE 완료 후 완성 영상이 증거다.

---

## EXPLAIN

### 4컷 만화로 시작

```
╔════════════════════╗  ╔════════════════════╗
║  1. 뭔가 빠진 느낌 ║  ║  2. 자막의 힘      ║
║                    ║  ║                    ║
║  (・・?) 새암      ║  ║  (・∀・) 새암      ║
║  "영상은 좋은데... ║  ║  "소리 없이 봐도   ║
║   소리 없이 보면   ║  ║   내용이 전달되면  ║
║   무슨 말인지      ║  ║   훨씬 많은 사람이 ║
║   모르겠어"        ║  ║   끝까지 봐!"      ║
╚════════════════════╝  ╚════════════════════╝

╔════════════════════╗  ╔════════════════════╗
║  3. SRT + TTS      ║  ║  4. 완성           ║
║                    ║  ║                    ║
║  (≧▽≦) 새암       ║  ║  (≧▽≦) 새암       ║
║  "Claude가         ║  ║  "기획 → HTML →    ║
║   SRT 만들고       ║  ║   GIF → 영상 →     ║
║   TTS로 음성 생성  ║  ║   자막 + 음성      ║
║   FFmpeg로 합성!"  ║  ║   = 완성 릴스!"    ║
╚════════════════════╝  ╚════════════════════╝
```

---

### 자막(SRT)이 중요한 이유

```
소셜미디어 영상 시청 패턴:
  - 85%가 소리 없이 본다 (출근길, 공공장소)
  - 자막이 없으면 스크롤 통과
  - 자막이 있으면 내용 파악 후 소리 켜기

SRT 파일 구조:
  1
  00:00:00,000 --> 00:00:03,000
  직접 만든 걸 팔 수 있어요

  2
  00:00:03,000 --> 00:00:06,000
  재료비 + 시간 = 내 가격

  3
  00:00:06,000 --> 00:00:09,000
  인스타 DM 하나로 주문 받기

  → Claude가 스크립트를 받으면 SRT를 자동 생성한다
```

---

### TTS (Text-to-Speech) 옵션

```
옵션 1: Mac 내장 TTS (무료, 즉시 사용)
  say -v "Yuna" -r 200 -o audio.aiff "텍스트"
  → Yuna: 한국어 여성 음성
  → 품질: 보통 (빠르게 테스트할 때)

옵션 2: Claude Code에서 스크립트 실행
  Claude에게: "이 텍스트를 Mac say 명령어로
  음성 파일(audio.aiff)로 만들어줘"

옵션 3: ElevenLabs API (고품질, 유료)
  → 자연스러운 한국어 음성
  → 월 $5부터 사용 가능

옵션 4: 직접 녹음
  → QuickTime 오디오 녹음
  → 가장 자연스러운 음성

옵션 5: Qwen-TTS (고품질, API)
  → Alibaba의 TTS 모델, 한국어 지원
  → Claude에게: "Qwen-TTS API로 이 텍스트를
     음성 파일(audio.mp3)로 만들어줘"
  → ElevenLabs 대비 가격 경쟁력 높음
```

---

### 최종 합성 파이프라인

```
Step 1: 스크립트 작성 (Claude)
  ↓
Step 2: SRT 자막 생성 (Claude)
  ↓
Step 3: TTS 음성 생성 (Mac say / ElevenLabs)
  ↓
Step 4: FFmpeg으로 자막 burn-in + 오디오 합성 (Claude)
  ↓
Step 5: 최종 MP4 완성 → 업로드 준비

FFmpeg 자막 합성 예시:
  ffmpeg -i reels-v3.mp4 -i audio.mp3 \
    -vf "subtitles=subtitle.srt:\
         force_style='FontName=NotoSansKR,\
         FontSize=28,PrimaryColour=&Hffffff,\
         OutlineColour=&H000000,Outline=2'" \
    -c:v libx264 -c:a aac \
    reels-final.mp4
```

---

### Track 1 완성 — 무엇을 배웠나

```
Block 2: HTML 애니메이션 → 화면 녹화 (소스 제로)
Block 3: GIF 배경 + 텍스트 오버레이 (소스: GIF)
Block 4: 영상 소스 + FFmpeg 합성 (소스: 촬영)
Block 5: SRT 자막 + TTS 음성 + 최종 합성 (완성본)

각 블록마다 소스를 하나씩 더해서
가장 단순한 것에서 가장 완성된 것으로 진화했다.

이제 이 파이프라인을 video_brief.md에 정리해두면
다음 릴스는 같은 과정을 훨씬 빠르게 반복할 수 있다.
```

---

## EXECUTE

**Step 1 — 스크립트 + SRT 생성**

```
video_brief.md의 장면 구성을 보고
각 장면의 나레이션 스크립트를 써줘.
그 다음 SRT 자막 파일(subtitle.srt)도 만들어줘.

형식:
- 각 자막은 3초 이내
- 한 화면에 15자 이내 (모바일 가독성)
- 파일명: subtitle.srt
```

---

**Step 2 — TTS 음성 생성**

```
옵션 A (Mac 내장):
subtitle.srt의 텍스트 전체를
Mac say 명령어로 한국어 음성(Yuna)으로 만들어줘.
audio.aiff로 저장하고 mp3로 변환해줘.

옵션 B (직접 녹음):
QuickTime → 파일 → 새 오디오 녹음
스크립트 보면서 직접 읽기 → audio.mp3

옵션 C (Qwen-TTS):
subtitle.srt의 텍스트를 Qwen-TTS API로
한국어 음성 파일(audio.mp3)로 만들어줘.
```

---

**Step 3 — 최종 합성**

```
reels-v3.mp4 + subtitle.srt + audio.mp3를 합쳐서
최종 릴스(reels-final.mp4)를 만들어줘.

조건:
- 자막: 화면 하단 20% 위치, 흰색, 검정 외곽선
- 오디오: 영상 길이에 맞게 조절
- 출력: reels-final.mp4 (H.264, AAC)
- 완료 후 파일 크기와 길이 알려줘

FFmpeg 명령어를 생성하고 실행해줘.
```

---

**Step 4 — 최종 확인**

```
체크리스트:
□ subtitle.srt 파일이 생성됐나?
□ audio 파일이 생성됐나? (또는 직접 녹음 준비됐나?)
□ reels-final.mp4가 생성됐나?
□ 자막이 영상 위에 잘 보이나?
□ 오디오와 자막 타이밍이 맞나?
□ Block 2부터 비교했을 때 발전 과정이 느껴지나?
```

---

## Track 1 마무리

```
Track 1 완료!

Block 2~5에서 완성한 것:
┌──────────────────────────────────────────┐
│  Block 2: HTML 애니메이션 릴스           │
│  Block 3: GIF 배경 + 텍스트 오버레이    │
│  Block 4: 영상 소스 + FFmpeg 합성        │
│  Block 5: SRT 자막 + TTS 음성 완성본    │
└──────────────────────────────────────────┘

핵심 도구:
  video_brief.md → 기획 문서
  FFmpeg → 영상 합성 엔진
  Claude → 명령어 생성 + 스크립트 작성

Block 9에서 이 파이프라인을 템플릿으로 만든다.
Track 2(Remotion)도 경험해보고 싶다면 Block 6으로.
```
