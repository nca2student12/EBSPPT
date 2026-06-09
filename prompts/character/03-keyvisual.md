# 2단계 · 키비주얼 (캐릭터 실제 그림)

> 브리프를 이미지 생성 프롬프트로 옮겨 실제 캐릭터 그림을 만든다.

## 도구
- `generate_image` (힉스필드 MCP), 모델 **nano_banana_pro**
- 기본: `aspect_ratio` 1:1, `count` 2

## 루프
1. 브리프 기반 프롬프트로 **한 번에 2종** 생성.
2. 사용자 피드백 → 변경점만 반영해 재생성.
3. 마음에 든 컷이 나오면 그걸 **레퍼런스로 고정**하고 디테일만 수정.

## 일관성 유지 (중요)
- 확정하고 싶은 컷을 **레퍼런스 이미지**로 넣는다: `medias: [{ value: <job_id|url>, role: "image" }]`.
  - ⚠️ nano_banana_pro는 **role "image"만 허용** (reference 등은 자동 변환됨).
- 프롬프트에 "use the reference image, keep the EXACT same ... (눈·색·비율)" 명시 + **변경점만** 지시.

## 프롬프트 팁
- 바꾸고 싶은 것만 명확히: 불필요한 디테일 제거 / 비율 조정 / 포즈·소품 위치 등.
- **부정형도 명시**하면 잘 듣는다 (예: `NO sparkles`, `NO extra details`).
- 비율 강조는 대문자로 (예: `prop LARGER, character SMALLER`).

## 산출물 저장
- 확정 컷은 `outputs/` 에 역할이 드러나는 파일명으로 저장 (예: `<character>_keyvisual_main.png`).
- 캐릭터 시트(turnaround/emotion)·굿즈 목업도 같은 확정컷을 레퍼런스로 생성해 일관성 유지.
