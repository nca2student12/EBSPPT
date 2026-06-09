# 3단계 · 키비주얼 생성 — `character` 모드 (Soul)

> 입력: 1단계 브리프(character.*) + 2단계 구성표(캐릭터 등장 슬라이드 목록)
> 흐름: **컨셉 컷 생성 → Soul 학습 → 슬라이드별 캐릭터 컷 생성**
> 캐릭터는 Soul로 학습해 모든 슬라이드에서 일관된 모습으로 재사용한다.

---

## 0. 입력 변수
- `{{DESIGN_BRIEF}}` : 1단계 출력 (colors / typography / tone / **character.***)
- `{{SLIDE_VISUALS}}` : 2단계 "캐릭터 등장 = O" 슬라이드 목록 (슬라이드# / 포즈·표정 / 비주얼 메모)

---

## 1. 프롬프팅 영역  ⟵ 직접 작성 (이미지 프롬프트 공식)

### 1-1. 캐릭터 컨셉 프롬프트 공식
<!--
Soul 학습용 레퍼런스를 만들 때 쓰는 공식.
브리프의 character.appearance / outfit / colors / style 을 항상 주입하도록 작성.
예) "[appearance], [outfit], [colors], clean studio background, [style], professional, high detail"
-->
(작성)

### 1-2. 슬라이드 컷 프롬프트 공식
<!--
학습된 Soul로 각 슬라이드 컷을 만들 때 쓰는 공식.
슬라이드별 {{포즈·표정}} 과 {{비주얼 메모}} 를 끼워넣는 자리 포함.
예) "{{포즈·표정}}, {{비주얼 메모}}, [colors], [layout 구도], consistent character"
-->
(작성)

---

## 2. 생성 설정
- 컨셉 컷 모델: `soul_cast` 또는 `nano_banana_pro` (레퍼런스 5~20장 생성)
- Soul 학습: `show_characters(action='train')` — 위 컨셉 컷을 레퍼런스로 (※ 최대 ~10분)
- 슬라이드 컷 모델: `soul_2` + `soul_id`
- aspect_ratio: (작성) · count: (작성)

---

## 3. 실행 절차
1. **컨셉 컷 생성** — `1-1 공식` + `character.soul_refs` 방향대로 다양한 각도·표정 5~20장 생성
2. **Soul 학습** — 생성한 컷으로 `show_characters(action='train')` → `soul_id` 확보
3. **슬라이드 컷 생성** — `{{SLIDE_VISUALS}}` 각 행마다:
   - `1-2 공식`에 슬라이드 `포즈·표정` + `비주얼 메모` 주입
   - `soul_2` + `soul_id`로 생성
4. **매핑 수집** — `슬라이드# → 이미지 URL` 표로 정리

---

## 4. 산출물 (다음 단계로)
| 슬라이드# | 캐릭터 컷 URL | 비고 |
|-----------|---------------|------|
| | | |

- → 4단계 NotebookLM 초안에 슬라이드별로 삽입
- → 5단계 Canva에서 배치·보정
