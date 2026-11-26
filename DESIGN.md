---
version: alpha
name: Sookbak-design-analysis
description: 다방(dabangapp.com)의 매물 카드·필터 칩·가격 표기·회색 위계를 가져오고, 화면 구조는 당근마켓처럼 앱을 열면 바로 매물 목록이 나오는 피드형으로 바꾼 숙명여대 학생 전용 자취방·하숙 앱 디자인 시스템. 흰 캔버스, 회색 1px 헤어라인, Pretendard 한 서체, 18px 굵은 가격, 그리고 숙명 Royal Light Blue(#0072CE)와 하늘색 틴트로만 만든 파랑·하늘 팔레트(주황·노랑 없음). 찜 아이콘은 하트 대신 눈송이 결정. 그림자는 화면 위에 떠 있는 요소(글쓰기 버튼, 하단 바, 바텀시트)에만 쓴다.

colors:
  primary: "#0072CE"
  primary-hover: "#0063B8"
  primary-pressed: "#003087"
  primary-deep: "#003087"
  primary-ink: "#005BB0"
  accent: "#0072CE"
  accent-hover: "#005BB0"
  primary-tint: "#E8F4FD"
  primary-tint-strong: "#CDE7FB"
  sky: "#8FCBF5"
  focus-ring: "#A9D4F5"
  surface-selected: "#E8F4FD"
  ink: "#222222"
  ink-sub: "#434343"
  body: "#656565"
  body-muted: "#757575"
  placeholder: "#979797"
  icon-muted: "#979797"
  hairline: "#DFDFDF"
  divider-soft: "#EDEDED"
  disabled-border: "#CCCCCC"
  canvas: "#FFFFFF"
  surface-soft: "#F5F5F5"
  surface-pearl: "#FAFAFA"
  surface-chip-open: "#EDEDED"
  surface-dark: "#222222"
  snowflake: "#2B8FE6"
  women-tint: "#EEF0FF"
  women-ink: "#3D4FC4"
  status-reserved: "#157A4A"
  status-done: "#656565"
  success: "#1A9E5C"
  danger: "#E5484D"
  dim: "rgba(0, 0, 0, 0.4)"
  on-primary: "#FFFFFF"
  on-dark: "#FFFFFF"

typography:
  display:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 28px
    fontWeight: 700
    lineHeight: 1.36
    letterSpacing: -0.5px
  page-title:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 20px
    fontWeight: 700
    lineHeight: 1.6
    letterSpacing: 0
  price-lg:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 700
    lineHeight: 1.58
    letterSpacing: 0
  price:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 700
    lineHeight: 1.67
    letterSpacing: 0
  body-lg:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.63
    letterSpacing: 0
  body-lg-strong:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 700
    lineHeight: 1.63
    letterSpacing: 0
  body:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.71
    letterSpacing: 0
  body-strong:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 700
    lineHeight: 1.71
    letterSpacing: 0
  caption:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.67
    letterSpacing: 0
  caption-strong:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 700
    lineHeight: 1.67
    letterSpacing: 0
  micro:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 10px
    fontWeight: 700
    lineHeight: 1.6
    letterSpacing: 0

rounded:
  none: 0px
  xxs: 2px
  xs: 4px
  sm: 6px
  md: 8px
  lg: 12px
  sheet: 16px
  pill: 9999px
  full: 50%

spacing:
  xxs: 4px
  xs: 8px
  sm: 12px
  md: 16px
  lg: 20px
  xl: 24px
  xxl: 32px
  section: 48px

components:
  app-bar:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    height: 56px
    padding: 0 16px
  sell-want-toggle:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.body}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.pill}"
    height: 36px
    padding: 2px
  sell-want-toggle-selected:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.pill}"
    padding: 0 14px
  category-tab:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.body}"
    typography: "{typography.body-lg}"
    padding: 0 12px
    height: 44px
  category-tab-selected:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    typography: "{typography.body-lg-strong}"
  filter-chip:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.pill}"
    padding: 0 10px 0 12px
    height: 36px
  filter-chip-applied:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary-ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.pill}"
  interest-chip:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary-ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.pill}"
    padding: 0 12px
    height: 36px
  filter-reset-button:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    rounded: "{rounded.full}"
    size: 36px
  sort-selector:
    backgroundColor: transparent
    textColor: "{colors.body}"
    typography: "{typography.body}"
    height: 40px
  range-slider-knob:
    backgroundColor: "{colors.canvas}"
    rounded: "{rounded.full}"
    size: 24px
  range-slider-track-active:
    backgroundColor: "{colors.primary}"
    height: 4px
  listing-card:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.price}"
    rounded: "{rounded.none}"
    padding: 16px
  listing-card-done:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.placeholder}"
    rounded: "{rounded.none}"
  wanted-card:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.none}"
    padding: 16px
  listing-thumbnail:
    backgroundColor: "{colors.surface-soft}"
    rounded: "{rounded.md}"
    size: 112px
  status-badge-reserved:
    backgroundColor: "{colors.status-reserved}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 6px
    height: 20px
  status-badge-done:
    backgroundColor: "{colors.status-done}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 6px
    height: 20px
  status-badge-wanted:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    height: 20px
  status-badge-wanted-done:
    backgroundColor: "{colors.status-done}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    height: 20px
  photo-type-label:
    backgroundColor: "{colors.dim}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    height: 20px
  tag-verified:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary-ink}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 6px
    height: 20px
  tag-women-only:
    backgroundColor: "{colors.women-tint}"
    textColor: "{colors.women-ink}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 6px
    height: 20px
  tag-price-drop:
    backgroundColor: "{colors.primary-tint-strong}"
    textColor: "{colors.primary-deep}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 6px
    height: 20px
  tag-option:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.body}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 4px 8px
    height: 28px
  snowflake-toggle:
    backgroundColor: transparent
    textColor: "{colors.on-dark}"
    size: 24px
  snowflake-toggle-active:
    backgroundColor: transparent
    textColor: "{colors.snowflake}"
    size: 24px
  fab-write:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.pill}"
    padding: 0 20px
    height: 52px
  fab-write-locked:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.pill}"
  bottom-tab-bar:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.placeholder}"
    typography: "{typography.micro}"
    height: 56px
  bottom-tab-item-active:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.micro}"
  unread-badge:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-dark}"
    typography: "{typography.micro}"
    rounded: "{rounded.pill}"
    padding: 0 5px
    height: 16px
  detail-author-row:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    padding: 16px
  detail-price-block:
    backgroundColor: "{colors.surface-pearl}"
    textColor: "{colors.ink}"
    typography: "{typography.price-lg}"
    rounded: "{rounded.lg}"
    padding: 16px
  detail-mini-map:
    backgroundColor: "{colors.surface-soft}"
    rounded: "{rounded.lg}"
    height: 180px
  map-pin-area:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary}"
    rounded: "{rounded.full}"
  map-pin-campus:
    backgroundColor: "{colors.primary-deep}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.full}"
    size: 32px
  notice-banner:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.body}"
    typography: "{typography.caption}"
    rounded: "{rounded.md}"
    padding: 12px 16px
  detail-bottom-bar:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    height: 72px
    padding: 12px 16px
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.md}"
    padding: 0 16px
    height: 52px
  button-primary-pressed:
    backgroundColor: "{colors.primary-pressed}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.md}"
  button-primary-disabled:
    backgroundColor: "{colors.divider-soft}"
    textColor: "{colors.placeholder}"
    rounded: "{rounded.md}"
  button-primary-locked:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary-ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.md}"
  button-outline:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.md}"
    padding: 0 15px
    height: 44px
  text-link:
    backgroundColor: transparent
    textColor: "{colors.accent}"
    typography: "{typography.body}"
  verify-gate-sheet:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.page-title}"
    rounded: "{rounded.sheet} {rounded.sheet} 0 0"
    padding: 24px 20px
  signup-gate-sheet:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.page-title}"
    rounded: "{rounded.sheet} {rounded.sheet} 0 0"
    padding: 24px 20px
  verify-status-card:
    backgroundColor: "{colors.surface-pearl}"
    textColor: "{colors.ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.lg}"
    padding: 16px
  verify-step-indicator:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.full}"
    size: 24px
  bottom-sheet:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.page-title}"
    rounded: "{rounded.sheet} {rounded.sheet} 0 0"
    padding: 20px
  text-input:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.md}"
    padding: 0 16px
    height: 48px
  segmented-control:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.body}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.md}"
    height: 44px
  segmented-control-selected:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.sm}"
  chat-listing-header:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-strong}"
    height: 72px
    padding: 12px 16px
  chat-bubble-mine:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.lg}"
    padding: 10px 14px
  chat-bubble-theirs:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.lg}"
    padding: 10px 14px
  chat-transfer-warning:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.ink}"
    typography: "{typography.caption}"
    rounded: "{rounded.md}"
    padding: 8px 12px
---

## Overview

다방 웹은 지도와 400px 리스트를 나란히 놓는 **지도 중심** 구조입니다. 숙박숙박은 PRD에 따라 이 구조를 쓰지 않고, **당근마켓처럼 앱을 열면 바로 매물 카드 목록이 나오는 피드형**으로 갑니다. 학생끼리 올리는 단기임대·하숙·쉐어하우스는 매물 수가 적고 대부분 학교 근처에 몰려 있어, 지도를 훑는 것보다 최신 글을 위에서부터 보는 쪽이 빠르기 때문입니다. 지도는 매물 상세에서 대략적 위치를 확인하는 용도로만 씁니다.

다방에서 가져오는 것은 **매물 카드의 정보 구성과 시각 언어**입니다. 가격만 18px 굵게, 나머지 정보는 14px 보통 굵기로 회색 단계만 바꿔 위계를 만들고, 흰 캔버스와 1px 회색 헤어라인으로 면을 나누며, 파랑은 "선택됨"과 "누를 수 있음"에만 씁니다. 화면 구조(상단 바, 분류 탭, 필터 칩 줄, 카드 피드, 떠 있는 글쓰기 버튼, 하단 탭 바)는 당근마켓 방식을 따릅니다.

숙박숙박만의 요소는 네 가지입니다. (1) 다방 블루 `#326CF9` 자리에 숙명여대 공식 **Sookmyung Royal Light Blue `#0072CE`**와 하늘색 틴트로 만든 **파랑·하늘 팔레트**. 주황·노랑은 쓰지 않습니다. (2) 위치는 도보 시간 대신 **동네 이름 + 숙대 기준 위치**("청파동 · 도서관 후문 근처")로 표시. (3) **학생 인증 단계에 따라 버튼이 잠기는 UI**. 비회원은 목록만 구경하고, 이메일 인증 회원은 글 상세·찜·검색까지, 학생증 인증을 마친 정회원만 `+ 글쓰기`와 `채팅하기`를 쓸 수 있습니다. (4) 찜 아이콘은 하트 대신 **눈송이 결정** 모양입니다. 숙대생을 부르는 이름 "눈송이"에서 가져왔습니다.

**Key Characteristics:**
- 피드가 첫 화면입니다. 한 줄에 카드 하나, 무한 스크롤. 상단 바에서 `판매`(방 내놓기)와 `구함`(방 찾기) 목록을 바꿉니다.
- iOS·Android 모바일 앱을 기준으로 설계합니다.
- 하나의 블루(`{colors.primary}` — #0072CE)가 선택된 분류 탭, 적용된 필터, 주요 버튼, 글쓰기 버튼을 모두 담당하고, 배경은 하늘색 틴트(`{colors.primary-tint}` — #E8F4FD)로 부드럽게 받칩니다.
- 색은 파랑·하늘 계열만 씁니다. 주황·노랑 강조색은 없습니다.
- 찜은 하트가 아니라 눈송이 결정 아이콘(`{component.snowflake-toggle}`)입니다.
- 서체는 Pretendard 하나, 굵기는 400과 700 두 단계.
- 카드 안 위계는 회색 단계로: 가격 #222 → 정보 #656565 → 메타 #757575.
- 거래 상태(`예약중`·`거래완료`)는 가격 앞 작은 배지로, 거래가능은 배지 없음.
- 그림자는 화면 위에 떠 있는 요소(글쓰기 버튼, 하단 고정 바, 바텀시트)에만 씁니다.
- 인증이 필요한 버튼은 숨기지 않고 보여 준 뒤, 누르면 이유와 다음 단계를 안내합니다.

## Colors

> **분석한 페이지:** 다방 홈(`/`), 원/투룸 지도(`/map/onetwo`), 지도 안 매물 상세 패널, 방크기 필터 드롭다운, 모바일 지도(`/mobile/map/onetwo`). 2026-11-24, 데스크톱 1024px과 모바일 375px에서 계산된 CSS 값을 읽었습니다.
>
> **숙명여대 색 출처:** [숙명여자대학교 UI 가이드 Color Scheme](https://www.sookmyung.ac.kr/kr/intro/ui.do). Royal Blue Pantone 287C / RGB 0·48·135, Royal Light Blue Pantone 285C / RGB 0·114·206.

### Brand & Accent
- **Sookmyung Royal Light Blue** (`{colors.primary}` — #0072CE): 숙명여대 공식 색이자 앱의 메인 색. 다방의 `#326CF9`가 하던 일을 모두 맡습니다. 주요 버튼(`채팅하기`, `완료`, `적용하기`), 글쓰기 버튼, 선택된 분류 탭의 글자와 밑줄, 슬라이더 트랙, 내 채팅 말풍선, 안 읽은 수 배지. 남색보다 밝아 화면이 가볍고 귀엽게 보입니다. 흰 배경·흰 글자 대비 4.89:1(AA).
- **Primary Hover** (`{colors.primary-hover}` — #0063B8): 데스크톱 호버. 앱 전용 값입니다.
- **Sookmyung Royal Blue** (`{colors.primary-pressed}`, `{colors.primary-deep}` — #003087): 숙명여대 공식 메인 색. 눌림 상태, 로고 워드마크, 상세 미니 지도의 캠퍼스 마커, "가격 인하" 태그 글자. 다방이 `#0C1A53`을 쓰는 자리입니다.
- **Primary Ink** (`{colors.primary-ink}` — #005BB0): 하늘색 틴트 배경 위의 글자 전용(적용된 필터 칩, "내 관심 조건" 칩, "숙대생 인증" 태그, 잠긴 버튼). `#0072CE`는 틴트 위에서 4.37:1이라 한 단계 진한 파랑을 씁니다(6.02:1).
- **Accent** (`{colors.accent}` — #0072CE): 텍스트 링크, 카드의 위치 줄("청파동 · 도서관 후문 근처"). 메인 색과 같은 값입니다.
- **Sky Tint** (`{colors.primary-tint}` — #E8F4FD): 적용된 필터 칩, "숙대생 인증" 태그, 잠긴 버튼, 선택된 행의 배경. 다방의 `#EEF8FF` 자리.
- **Sky Tint Strong** (`{colors.primary-tint-strong}` — #CDE7FB): "가격 인하" 태그 배경, 진한 틴트가 필요할 때.
- **Sky** (`{colors.sky}` — #8FCBF5): 일러스트, 빈 화면 그림, 눈송이 장식. 대비가 낮아 글자·아이콘 단독으로는 쓰지 않습니다.
- **Focus Ring** (`{colors.focus-ring}` — #A9D4F5): 키보드 포커스 외곽선 전용.

### Surface
- **Canvas** (`{colors.canvas}` — #FFFFFF): 상단 바, 피드, 카드, 상세, 하단 탭 바 등 거의 모든 면.
- **Soft Gray** (`{colors.surface-soft}` — #F5F5F5): 옵션 태그, 사진 없는 썸네일, 상대 채팅 말풍선, 안내 문구 상자, 세그먼트 컨트롤 바탕.
- **Pearl** (`{colors.surface-pearl}` — #FAFAFA): 상세의 가격 블록, 인증 상태 카드.
- **Dark** (`{colors.surface-dark}` — #222222): 토스트 메시지 배경.

### Text
- **Ink** (`{colors.ink}` — #222222): 가격, 제목, 필터 칩 글자, 상세 정보 값.
- **Ink Sub** (`{colors.ink-sub}` — #434343): 강조가 필요한 보조 텍스트.
- **Body** (`{colors.body}` — #656565): 카드의 분류·방 종류, 층·면적·관리비, 옵션 태그 글자, 선택 안 된 분류 탭.
- **Body Muted** (`{colors.body-muted}` — #757575): 카드 맨 아래 메타 줄("2시간 전 · 채팅 3 · 찜 12"), 입주 가능일. 다방은 `#979797`을 쓰지만 흰 배경 대비 2.86:1로 AA에 못 미쳐 한 단계 진하게 바꿨습니다(4.61:1).
- **Placeholder** (`{colors.placeholder}` — #979797): 입력창 placeholder, `거래완료` 카드의 글자, 선택 안 된 하단 탭 아이콘. 본문 텍스트로는 쓰지 않습니다.

### Hairlines & Borders
- **Hairline** (`{colors.hairline}` — #DFDFDF): 필터 칩, 아웃라인 버튼, 입력창, 슬라이더 손잡이의 1px 테두리.
- **Divider Soft** (`{colors.divider-soft}` — #EDEDED): 카드 사이 구분선, 상단 바·분류 탭 아래 구분선, 하단 탭 바 위 구분선.
- **Disabled Border** (`{colors.disabled-border}` — #CCCCCC): 비활성 컨트롤.

### Status & Tags
- **예약중** (`{colors.status-reserved}` — #157A4A): 흰 글자 배지(5.36:1). 성공 색 `#1A9E5C`는 흰 글자 대비가 3.4:1이라 배지에는 한 단계 진한 초록을 씁니다.
- **거래완료** (`{colors.status-done}` — #656565): 흰 글자 배지. 카드 전체 글자도 `{colors.placeholder}`로 흐려집니다. 구함 글의 `구함완료`도 같은 색입니다.
- **구하는 중** (`{colors.primary}` — #0072CE): 구함 글 카드의 흰 글자 배지(4.89:1).
- **가격 인하** (`{colors.primary-tint-strong}` #CDE7FB + `{colors.primary-deep}` #003087): "가격 인하" 태그(9.26:1).
- **Snowflake** (`{colors.snowflake}` — #2B8FE6): 찜한 눈송이 아이콘을 채우는 하늘빛 파랑. 흰 배경 대비 3.4:1로 아이콘 기준(3:1)을 넘습니다. 글자색으로는 쓰지 않습니다.
- **Women Only** (`{colors.women-tint}` #EEF0FF + `{colors.women-ink}` #3D4FC4): "여성전용" 태그. 파랑 계열 안에서 인증 태그와 구분되도록 보랏빛이 살짝 도는 파랑을 씁니다(5.96:1).
- **Success / Danger** (`{colors.success}` #1A9E5C, `{colors.danger}` #E5484D): 인증 완료 체크, 입력 오류, 신고.

### Brand Gradient
**그라데이션은 쓰지 않습니다.** 다방도 UI에는 그라데이션 토큰이 없습니다. 다방 "플러스" 태그의 보라색(`#3E26FD`)이나 "새단장" 배지의 핑크(`#FF3478`) 같은 두 번째 강조색도 들이지 않고, 그 자리는 하늘색 틴트로 대신합니다. 숙명여대 공식 보조색인 Royal Yellow(`#FFB500`)와 Royal Orange(`#FF7D01`)도 파랑과 어울림이 맞지 않아 쓰지 않습니다.

## Typography

### Font Family
- **전체**: `Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif`. 다방과 같은 서체입니다. 한글·영문·숫자의 폭이 고르고 가격 숫자가 또렷합니다.
- **숫자**: 가격·면적·층수에는 `font-variant-numeric: tabular-nums`.
- **숙명눈꽃체**(숙명여대 전용서체)는 학교 로고·슬로건용이라 앱 UI에는 쓰지 않습니다.

### Hierarchy

| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `{typography.display}` | 28px | 700 | 1.36 | -0.5px | 앱 소개 화면 헤드라인 |
| `{typography.page-title}` | 20px | 700 | 1.6 (32px) | 0 | 화면 제목, 바텀시트 제목, 인증 안내 제목 |
| `{typography.price-lg}` | 24px | 700 | 1.58 (38px) | 0 | 상세 화면 가격 |
| `{typography.price}` | 18px | 700 | 1.67 (30px) | 0 | 피드 카드 가격 "월세 500/45" |
| `{typography.body-lg}` | 16px | 400 | 1.63 (26px) | 0 | 분류 탭, 상세 설명, 입력값, 채팅 메시지 |
| `{typography.body-lg-strong}` | 16px | 700 | 1.63 | 0 | 상단 바 판매/구함 전환, 선택된 분류 탭, 글쓰기 버튼, 구함 카드 제목 |
| `{typography.body}` | 14px | 400 | 1.71 (24px) | 0 | 카드 정보 줄, 필터 칩, 상세 정보 표 |
| `{typography.body-strong}` | 14px | 700 | 1.71 | 0 | 버튼 라벨, 적용된 필터 칩, 카드의 위치 줄 |
| `{typography.caption}` | 12px | 400 | 1.67 (20px) | 0 | 카드 메타 줄, 안내 문구, 슬라이더 눈금 |
| `{typography.caption-strong}` | 12px | 700 | 1.67 | 0 | 상태 배지, 태그, 사진 종류 라벨 |
| `{typography.micro}` | 10px | 700 | 1.6 | 0 | 하단 탭 라벨, 안 읽은 수 배지 |

### Principles

- **가격이 제일 크고 제일 굵다.** 피드에서 18px/700은 가격만 씁니다. 다른 정보는 모두 14px 이하입니다.
- **굵기는 400과 700 두 단계만.** 다방 전체에서 500·600은 나오지 않습니다.
- **자간은 거의 0.** 음수 자간은 28px 헤드라인에만 줍니다.
- **줄높이는 픽셀로 고정.** 다방처럼 12→20px, 14→24px, 16→26px, 18→30px, 20→32px, 24→38px. 위 표의 배수는 이 값을 나눈 것입니다.
- **회색 단계가 위계다.** #222(값) → #656565(정보) → #757575(메타) → #979797(비활성). 크기를 바꾸기 전에 색 단계부터 바꿉니다.

### Note on Font Substitutes
Pretendard는 무료 오픈 폰트이므로 앱에 Pretendard Variable을 넣어 씁니다. 로딩 전에는 `-apple-system`(iOS·macOS의 Apple SD Gothic Neo)과 `system-ui`(Android의 Noto Sans KR)로 대체되며, 두 서체 모두 글자 폭이 약간 넓어 카드 설명의 말줄임이 조금 일찍 생길 수 있습니다.

## Layout

### Spacing System
- **기본 단위:** 4px. 구조 간격은 8 / 12 / 16 / 20 / 24px에 맞춥니다.
- **토큰:** `{spacing.xxs}` 4px · `{spacing.xs}` 8px · `{spacing.sm}` 12px · `{spacing.md}` 16px · `{spacing.lg}` 20px · `{spacing.xl}` 24px · `{spacing.xxl}` 32px · `{spacing.section}` 48px.
- **화면 좌우 여백:** 16px.
- **카드 패딩:** 위아래 16px. 썸네일과 텍스트 사이 16px.
- **칩 사이 간격:** 필터 칩 8px, 태그 4px, 옵션 태그 8px.
- **상세 섹션 사이:** 24px, 섹션 사이 8px 회색 띠(`{colors.surface-soft}`)로 구분.

### Grid & Container
- **한 열 피드.** 휴대폰·태블릿 모두 카드는 한 줄에 하나입니다. 태블릿에서는 콘텐츠 폭을 최대 720px로 잡고 가운데 정렬합니다.
- **홈 구조 (위 → 아래):** 상단 바 56px → 분류 탭 44px → 필터 칩 줄 52px → 정렬 줄 40px → 카드 피드 → 하단 탭 바 56px. 상단 바·분류 탭·필터 칩은 스크롤 시 위에 붙어 있습니다(sticky).
- **떠 있는 글쓰기 버튼:** 오른쪽 아래, 하단 탭 바 위 16px, 오른쪽 16px.

```
홈 (375px 기준)
┌─────────────────────────────────┐
│ (●판매  구함)             🔍  🔔 │ 상단 바 56px
├─────────────────────────────────┤
│ 전체  원룸  투룸  오피스텔  쉐어하우스  하숙  단기임대  단기숙박 │ 분류 탭 44px (가로 스크롤)
│ ━━                              │
├─────────────────────────────────┤
│ [↻] (내 관심 조건) (가격 ⌄) (숙대 기준 위치 ⌄) (동네 ⌄) … │ 필터 칩 52px
│ 매물 128개                최신순 ⌄ │ 정렬 40px
├─────────────────────────────────┤
│ ┌──────┐ 월세 500/45             │
│ │ 112px│ 원룸 · 분리형             │
│ │   ❄  │ 3층 · 20㎡ · 관리비 5만     │
│ └──────┘ 청파동 · 도서관 후문 근처    │
│          12월 20일부터             │
│          [숙대생 인증] [여성전용]     │
│          2시간 전 · 채팅 3 · 찜 12   │
├─────────────────────────────────┤
│ ┌──────┐ [예약중] 하숙 월 65         │
│ │      │ 하숙 · 식사 포함            │
│ …                                │
│                       ┌─────────┐ │
│                       │ + 글쓰기 │ │ 떠 있는 버튼
│                       └─────────┘ │
├─────────────────────────────────┤
│   홈      찜      채팅(2)     마이   │ 하단 탭 56px
└─────────────────────────────────┘
```

### Whitespace Philosophy
피드는 다방 리스트처럼 **촘촘하게** 갑니다. 카드 사이에 여백을 두지 않고 1px 구분선으로만 나눠, 한 화면에 카드 4~5장이 보이게 합니다. 여백이 넉넉한 곳은 글 상세(섹션 사이 24px), 글쓰기 폼, 인증 화면입니다. 이 화면들은 한 번에 하나의 일만 하므로 숨 쉴 공간을 줍니다.

## Elevation & Depth

| Level | Treatment | Use |
|---|---|---|
| Flat | 그림자 없음 | 상단 바, 분류 탭, 피드 카드, 상세 본문 |
| Hairline | 1px `{colors.hairline}` 또는 `{colors.divider-soft}` | 필터 칩, 입력창, 아웃라인 버튼, 카드 구분선, 하단 탭 바 위쪽 |
| Knob | `rgba(0, 0, 0, 0.16) 0 1px 4px 0` | 범위 슬라이더 손잡이 (다방 실측값) |
| Floating button | `rgba(0, 0, 0, 0.2) 0 2px 4px 0` | 떠 있는 `+ 글쓰기` 버튼 (다방 모바일 플로팅 버튼 실측값) |
| Bottom bar | `rgba(0, 0, 0, 0.06) 0 -2px 4px 0` | 상세 하단 고정 바 |
| Sheet | `{colors.dim}` 전체 덮기 + 시트 | 필터 바텀시트, 가입 안내 시트, 인증 안내 시트, 정렬 시트, 글쓰기 종류 선택 시트 |

**그림자 원칙.** 그림자는 "콘텐츠 위에 떠 있다"는 뜻으로만 씁니다. 카드·상단 바·탭처럼 화면에 붙어 있는 요소는 구분선이나 배경색으로만 구분합니다.

### Decorative Depth
- 상세 화면의 섹션 사이 8px 회색 띠가 그림자 없이 층을 나눕니다.
- 앱 소개 화면에만 일러스트를 씁니다. 나머지 장식은 없습니다.

## Shapes

### Border Radius Scale

| Token | Value | Use |
|---|---|---|
| `{rounded.none}` | 0px | 피드 카드, 상단 바, 분류 탭, 상세 사진 캐러셀 |
| `{rounded.xxs}` | 2px | (다방 원본 버튼·칩 값. 숙박숙박에서는 쓰지 않음) |
| `{rounded.xs}` | 4px | 상태 배지, 태그, 사진 종류 라벨 |
| `{rounded.sm}` | 6px | 세그먼트 컨트롤 안쪽 선택 칸 |
| `{rounded.md}` | 8px | 썸네일, 버튼, 입력창, 안내 문구 상자 |
| `{rounded.lg}` | 12px | 상세 가격 블록, 미니 지도, 인증 상태 카드, 채팅 말풍선 |
| `{rounded.sheet}` | 16px | 바텀시트 위쪽 두 모서리 |
| `{rounded.pill}` | 9999px | 필터 칩, 떠 있는 글쓰기 버튼, 안 읽은 수 배지 |
| `{rounded.full}` | 50% | 슬라이더 손잡이, 필터 초기화 버튼, 프로필 사진, 캠퍼스 마커 |

다방은 버튼과 필터 칩을 2px로 각지게 쓰지만, 숙박숙박은 손가락으로 쓰는 모바일 피드이므로 버튼·썸네일 8px, 필터 칩 pill로 부드럽게 바꿨습니다.

### Photography Geometry
- **피드 썸네일:** 112 × 112px 정사각형, `{rounded.md}`, `object-fit: cover`. 오른쪽 위 6px에 흰 눈송이 아이콘(`{component.snowflake-toggle}`). 사진이 없으면 `{colors.surface-soft}`에 회색 집 아이콘.
- **상세 사진:** 화면 폭 꽉 차게 4:3, 좌우 스와이프, 오른쪽 아래 "1 / 8" 카운터, 왼쪽 아래 `{component.photo-type-label}`("방"·"화장실"). 탭하면 전체 화면.
- **판매 글쓰기 사진:** 80px 정사각형 그리드, 2~10장. 첫 장에 "대표" 라벨. 사진마다 왼쪽 아래 `{component.photo-type-label}`("방" / "화장실" / "기타")을 누르면 종류가 바뀝니다. 방 사진과 화장실 사진이 각각 1장 이상 있어야 `완료`가 켜지고, 모자라면 그리드 아래 `{typography.caption}` `{colors.danger}` "방 사진과 화장실 사진을 1장 이상 올려 주세요".
- **채팅 사진:** 한 번에 최대 10장. 말풍선 안에 `{rounded.lg}` 썸네일 그리드.
- 다방은 사진에 워터마크를 얹지만 숙박숙박은 넣지 않습니다.

## Components

### Top Bar & Navigation

**`app-bar`** — 높이 56px, 흰 배경, 좌우 16px, 아래 1px `{colors.divider-soft}`. 왼쪽은 `{component.sell-want-toggle}`, 오른쪽은 검색·알림 아이콘(24px, 터치 영역 44px).

**`sell-want-toggle`** — `판매` / `구함` 목록 전환. 높이 36px pill, `{colors.surface-soft}` 바탕 안에 두 칸. 선택된 칸은 `{component.sell-want-toggle-selected}` — 흰 배경 + `{colors.primary}` 700 글자. 분류 탭과 적용한 필터는 전환해도 그대로 유지됩니다. 비회원도 쓸 수 있습니다.

**`bottom-tab-bar`** — 높이 56px + safe area, 위 1px `{colors.divider-soft}`. 탭 네 개: 홈 · 찜 · 채팅 · 마이. 아이콘 24px 위 + 라벨 `{typography.micro}`. 선택 안 된 탭은 `{colors.placeholder}`, 선택된 탭은 `{component.bottom-tab-item-active}` — `{colors.ink}`에 채워진 아이콘. 찜 탭 아이콘은 눈송이 결정 모양입니다. 채팅 탭 아이콘 오른쪽 위에 `{component.unread-badge}`(높이 16px, `{colors.primary}` 배경, 흰 숫자).

### Category & Filters

**`category-tab`** — 가로 스크롤 분류 탭. 높이 44px, 좌우 패딩 12px, `{typography.body-lg}` `{colors.body}`. 선택되면 `{component.category-tab-selected}` — `{colors.primary}` 700 + 아래 2px `{colors.primary}` 밑줄. 판매·구함 공통 탭 목록(PRD 7.3). 아파트는 다루지 않습니다.

| 탭 | 보여 주는 글 |
|---|---|
| 전체 | 모든 글 |
| 원룸 | 방 하나 구조(오픈형·분리형·복층) |
| 투룸 | 방 두 개 이상(쓰리룸 이상 포함) |
| 오피스텔 | 오피스텔 건물의 호실 |
| 쉐어하우스 | 여러 명이 집을 나눠 쓰는 형태. 룸메이트 구인 포함 |
| 하숙 | 집주인 가정에 살거나 식사가 제공되는 형태 |
| 단기임대 | 1개월 이상 6개월 이하. 방학·교환학생 기간 양도 포함 |
| 단기숙박 | 1개월 미만(며칠~몇 주) |

**`filter-chip`** — 필터 칩 줄의 칩. 높이 36px, `{rounded.pill}`, 1px `{colors.hairline}`, 패딩 0 10px 0 12px, `{typography.body}` + 꺾쇠 아이콘. 칩 사이 8px, 가로 스크롤. 누르면 해당 항목이 펼쳐진 필터 바텀시트가 열립니다.
- 적용됨: `{component.filter-chip-applied}` — 배경 `{colors.primary-tint}`, 테두리 `{colors.primary}`, 글자 `{colors.primary-ink}` 700, 라벨이 값으로 바뀜("도서관 후문", "월세 50 이하") + ✕.
- 맨 앞에 `{component.filter-reset-button}` — 36px 원, 새로고침 아이콘. 적용된 필터가 있을 때만 보임.
- 칩 순서: (내 관심 조건) · 가격 · 숙대 기준 위치 · 동네 · 입주 가능일 · 여성전용 · 거래가능만.
- 비회원이 칩을 누르면 필터 대신 `{component.signup-gate-sheet}`가 열립니다.

**`interest-chip`** — 관심 매물 알림 조건(PRD 7.9a)을 저장한 회원에게만 필터 칩 줄 맨 앞(초기화 버튼 다음)에 보이는 "내 관심 조건" 칩. `{colors.primary-tint}` 배경, `{colors.primary-ink}` 700 글자, 앞에 작은 종 아이콘. 누르면 저장한 조건이 한 번에 필터로 적용되고 `{component.filter-chip-applied}` 모양으로 바뀝니다.

**필터 바텀시트** — `{component.bottom-sheet}` 안에 PRD 7.8의 필터를 위에서 아래로 나열. 섹션 제목 `{typography.body-lg-strong}`, 섹션 사이 24px.
- 거래 방식·기간(단기숙박 / 단기임대 / 장기): `{component.segmented-control}`(높이 44px, `{colors.surface-soft}` 바탕, 선택 칸 `{component.segmented-control-selected}` 흰 배경 + `{colors.primary}` 글자).
- 보증금·월세·전세금: 범위 슬라이더. 트랙 4px, 선택 구간 `{component.range-slider-track-active}`, 손잡이 `{component.range-slider-knob}` 24px. 위에 현재 값 "0 ~ 50만" `{typography.body-strong}`, 아래 눈금 `{typography.caption}` `{colors.placeholder}`.
- "관리비 포함해서 비교" 토글.
- 분류·숙대 기준 위치(1캠 정문 / 1캠 후문 / 도서관 후문 / 2캠 / 숙대입구역 / 효창공원앞역 / 남영역)·동네(청파동 / 효창동 / 남영동 / 용산동 / 기타): 여러 개 고르는 `{component.filter-chip}`.
- 조건(여성전용·반려동물·엘리베이터·주차·풀옵션): 여러 개 고르는 `{component.filter-chip}`.
- 하단 고정: `{component.button-outline}`(초기화) + `{component.button-primary}`("매물 128개 보기").

**`sort-selector`** — 필터 칩 아래 줄 오른쪽. "최신순 ⌄" `{typography.body}` `{colors.body}`. 왼쪽에는 "매물 128개". 정렬: 최신순 · 낮은 가격순 · 찜 많은순. 도보 시간을 계산하지 않으므로 거리순 정렬은 없습니다.

### Listing Feed

**`listing-card`** — 피드의 한 행. 패딩 16px, 흰 배경, 아래 1px `{colors.divider-soft}`. 왼쪽 `{component.listing-thumbnail}`(112px), 오른쪽 16px 띄우고 텍스트(PRD 7.2):
1. 가격 줄 — 상태 배지(있으면) + 가격 `{typography.price}` `{colors.ink}`. "월세 500/45"
2. 분류·방 종류 `{typography.body}` `{colors.body}` — "원룸 · 분리형", "하숙 · 식사 포함", "단기숙박 · 1박"
3. 층·면적·관리비 `{typography.body}` `{colors.body}` — "3층 · 20㎡ · 관리비 5만"
4. 위치 `{typography.body-strong}` `{colors.accent}` — 동네 이름 + 숙대 기준 위치 "청파동 · 도서관 후문 근처". 숙대 근처가 아니면 동네 이름만 "신수동". 도보 시간은 쓰지 않습니다.
5. 입주일·기간 `{typography.body}` `{colors.body-muted}` — "12월 20일부터", "1~2월 단기"
6. 태그 줄 — `{component.tag-verified}`, `{component.tag-women-only}`, `{component.tag-price-drop}` (최대 3개)
7. 메타 줄 `{typography.caption}` `{colors.body-muted}` — "2시간 전 · 채팅 3 · 찜 12"

- 거래완료: `{component.listing-card-done}` — 모든 글자 `{colors.placeholder}`, 썸네일 50% 불투명. 기본 정렬에서 목록 아래로 내려갑니다.
- 카드 전체가 상세로 가는 링크, 눈송이 찜 아이콘만 따로 눌림. 비회원이 카드나 찜 아이콘을 누르면 상세 대신 `{component.signup-gate-sheet}`가 열립니다.

**`wanted-card`** — 구함 목록의 한 행. 사진이 없는 글이 많으므로 썸네일 없이 텍스트만, 패딩 16px, 아래 1px `{colors.divider-soft}`. 글쓴이가 사진을 올렸으면 오른쪽에 64px 썸네일.
1. 상태 배지 + 제목 `{typography.body-lg-strong}` `{colors.ink}` — `{component.status-badge-wanted}` "구하는 중" 또는 `{component.status-badge-wanted-done}` "구함완료"
2. 원하는 분류·희망 위치 `{typography.body}` `{colors.body}` — "원룸 · 투룸 · 청파동 · 1캠 후문"
3. 예산 `{typography.body-strong}` `{colors.ink}` — "보증금 500 이하 · 월 60 이하"
4. 입주 희망일·기간 `{typography.body}` `{colors.body-muted}` — "3월 1일부터 · 1년"
5. 메타 줄 `{typography.caption}` `{colors.body-muted}` — "2시간 전 · 채팅 1 · 찜 4"

`구함완료` 카드는 `{component.listing-card-done}`처럼 글자를 `{colors.placeholder}`로 흐립니다.

**가격 표기 규칙** (PRD 8.3과 동일, 단위 만원)

| 거래 | 표기 | 예 |
|---|---|---|
| 월세 | `월세 {보증금}/{월세}` | 월세 500/45, 월세 1억2000/39 |
| 전세 | `전세 {전세금}` | 전세 1억5000 |
| 하숙 | `하숙 월 {금액}` + "식사 포함" 태그 | 하숙 월 65 |
| 단기임대 (주 단위) | `주 {금액}` | 주 15 |
| 단기숙박 | `1박 {금액}` / `1주 {금액}` | 1박 3, 1주 18 |
| 관리비 | `관리비 {금액}만` / `관리비 없음` | 관리비 5만 |

1억 이상은 `1억2000`처럼 억과 만을 붙여 씁니다. 쉐어하우스와 월 단위 단기임대는 월세 표기를 따릅니다.

**`status-badge-reserved` / `status-badge-done`** — 가격 앞 높이 20px 배지, `{rounded.xs}`, `{typography.caption-strong}` 흰 글자. `예약중`은 `{colors.status-reserved}`, `거래완료`는 `{colors.status-done}`. 거래가능은 배지 없음.

**`photo-type-label`** — 사진 왼쪽 아래의 "방" / "화장실" / "기타" 라벨. 높이 20px, `{colors.dim}` 반투명 검정 배경, 흰 `{typography.caption-strong}`, `{rounded.xs}`. 상세 캐러셀과 글쓰기 사진 그리드에 씁니다.

**`tag-verified`** — "숙대생 인증". 다방 "플러스" 태그 자리. 높이 20px, 패딩 0 × 6px, `{rounded.xs}`, `{colors.primary-tint}` 배경, `{colors.primary-ink}` 글자.

**`tag-women-only`** — "여성전용". `{colors.women-tint}` 배경, `{colors.women-ink}` 글자.

**`tag-price-drop`** — "가격 인하". 가격을 내린 뒤 3일간. `{colors.primary-tint-strong}` 배경, `{colors.primary-deep}` 글자.

**`snowflake-toggle`** — 찜 아이콘. 하트 대신 **눈송이 결정** 모양입니다.
- 모양: 가지 6개짜리 눈 결정. 각 가지 끝에 작은 V자 곁가지 한 쌍, 가운데는 작은 육각형. 24 × 24px 캔버스, 선 굵기 1.75px, 선 끝은 둥글게(`stroke-linecap: round`). 선이 둥글고 가지가 짧아 날카롭지 않고 동글동글하게 보이도록 그립니다.
- 기본: 사진 위에서는 흰 선 + `rgba(0, 0, 0, 0.24) 0 1px 2px` 그림자, 흰 배경 위(상세 하단 바, 찜 목록)에서는 `{colors.body}` 선.
- 찜함: `{component.snowflake-toggle-active}` — 가운데 육각형과 가지 사이를 `{colors.snowflake}`로 채우고 흰 1px 테두리. 누를 때 크기 1 → 1.2 → 1로 0.2초 튀어 오릅니다.
- 터치 영역 44 × 44px. 스크린 리더 이름은 "찜하기" / "찜 해제".
- 숙명여대 공식 심볼마크도 눈 결정을 바탕으로 하지만, 학교 UI 가이드상 심볼 무단 사용·변형이 금지되므로 **학교 심볼을 따라 그리지 않고** 앱 전용으로 새로 그린 단순한 결정 모양을 씁니다.

**`fab-write`** — 오른쪽 아래 떠 있는 `+ 글쓰기`. 높이 52px, `{rounded.pill}`, `{colors.primary}` 배경, 흰 `{typography.body-lg-strong}`, 패딩 0 × 20px, Floating button 그림자. 피드를 아래로 스크롤하면 "+" 아이콘만 남는 52px 원으로 줄어듭니다.
- 누르면 `{component.bottom-sheet}`에서 `판매`("방을 내놓아요") / `구함`("방을 찾고 있어요") 중 고릅니다.
- 학생증 미인증: `{component.fab-write-locked}` — 모양은 같고 "+" 앞에 작은 자물쇠 아이콘. 누르면 `{component.verify-gate-sheet}`. 비회원이 누르면 `{component.signup-gate-sheet}`.

### Listing Detail

화면 구성(PRD 7.5, 위 → 아래). 이메일 인증 회원부터 볼 수 있습니다.
1. 사진 캐러셀 (4:3, 화면 폭, 사진마다 `{component.photo-type-label}`)
2. **`detail-author-row`** — 프로필 사진 40px 원 + 닉네임 `{typography.body-lg-strong}` + `{component.tag-verified}`, 아래 "가입 8개월 · 매물 2개" `{typography.caption}` `{colors.body-muted}`. 실명·학번은 보이지 않습니다.
3. 제목 `{typography.page-title}`, 분류·올린 시각 `{typography.caption}`
4. **`detail-price-block`** — `{colors.surface-pearl}` 배경, `{rounded.lg}`, 패딩 16px. 가격 `{typography.price-lg}`, 아래 표: 보증금 · 월세(또는 전세금) · 관리비 · 관리비 포함 항목, 마지막 줄 **월 예상 비용**(월세 + 관리비) `{typography.body-strong}` `{colors.primary}`. "가격 협의 가능"이면 `{component.tag-verified}` 모양의 태그 추가.
5. 기본 정보 표 — 분류, 방 종류, 면적(㎡ · 평), 층, 방·욕실 수, 입주 가능일, 계약 기간. 라벨 `{typography.body}` `{colors.body}` 왼쪽 96px, 값 `{typography.body}` `{colors.ink}`.
6. 분류별 정보 — 하숙(식사 제공·1인실/2인실), 쉐어하우스(모집 인원·현재 거주 인원·1인실/다인실), 단기임대(임대 가능 기간), 단기숙박(숙박 가능 기간·1박/1주). 통금·하우스 규칙은 설명 본문에 씁니다.
7. 옵션·건물 — `{component.tag-option}` 아이콘+라벨 그리드
8. 설명 본문 `{typography.body-lg}`
9. 위치 — **`detail-mini-map`**(높이 180px, `{rounded.lg}`). 정확한 위치 대신 `{component.map-pin-area}`(반경 원, `{colors.primary}` 15% 채움 + 1px 테두리)와 `{component.map-pin-campus}`(32px 원, `{colors.primary-deep}`)를 함께 표시. 아래 "청파동 · 도서관 후문 근처".
10. "조회 120 · 찜 12 · 채팅 3" `{typography.caption}` `{colors.body-muted}`
11. **`notice-banner`** — "숙박숙박은 방을 보고 연결되는 데까지만 도와요. 앱 안에서는 송금할 수 없고, 계약 전에는 절대 송금하지 마세요. 반드시 직접 방문하고 등기부등본을 확인하세요." `{colors.surface-soft}` 상자, `{typography.caption}`, 앞에 ⓘ 아이콘.

섹션 사이는 24px + 8px 회색 띠.

**`detail-bottom-bar`** — 화면 아래 고정, 높이 72px + safe area, Bottom bar 그림자. 왼쪽 눈송이 찜 아이콘 + 세로 구분선 + 가격 요약(`{typography.body-lg-strong}`, 아래 줄 관리비 `{typography.caption}`), 오른쪽 `{component.button-primary}` "채팅하기"(폭 140px).
- 학생증 미인증: 버튼이 `{component.button-primary-locked}` — `{colors.primary-tint}` 배경 + `{colors.primary-ink}` 글자 + 자물쇠 아이콘 "인증하고 채팅하기". 누르면 `{component.verify-gate-sheet}`.
- 내 매물: 버튼 자리에 `{component.button-outline}` "채팅 3개 보기", 오른쪽 위 메뉴에 수정·상태 변경·삭제.

### Verification Gate

PRD 7.1의 권한표를 UI로 옮긴 부분입니다.

| 상태 | 목록 (판매/구함 전환·분류 탭) | 글 상세·찜·검색·필터 | `+ 글쓰기` | `채팅하기` |
|---|---|---|---|---|
| 비회원 (숙대생 아닌 일반인 포함) | 보임 | 누르면 `{component.signup-gate-sheet}` | 누르면 가입 안내 | — (상세를 못 엶) |
| 이메일 인증 완료 | 보임 | 됨 | 자물쇠 표시, 누르면 인증 안내 | 자물쇠 표시, 누르면 인증 안내 |
| 학생증 검수 대기 | 보임 | 됨 | 자물쇠, 안내에 "검수 중" | 자물쇠, 안내에 "검수 중" |
| 학생증 인증 완료 (정회원) | 보임 | 됨 | 사용 가능 | 사용 가능 |
| 재인증 미완료 · 졸업 1년 경과 | 보임 | 됨 | 자물쇠, 누르면 재인증 안내 | 기존 채팅은 읽기만, 새 채팅은 자물쇠 |

정회원은 재학생(졸업 예정자·대학원생 포함), 휴학생, 졸업 1년 이내 졸업생입니다.

**원칙:** 잠긴 버튼은 숨기지 않습니다. 같은 자리에 같은 모양으로 두고 자물쇠 아이콘만 더해, 무엇을 하면 열리는지 알 수 있게 합니다.

**`signup-gate-sheet`** — 비회원이 카드·찜·검색·필터 칩·`+ 글쓰기`를 누르면 올라오는 바텀시트. 모양은 `{component.verify-gate-sheet}`와 같습니다.
- 제목 `{typography.page-title}` "숙대생만 글을 볼 수 있어요"
- 설명 `{typography.body}` `{colors.body}` "학교 메일로 인증해 주세요"
- 하단 `{component.button-primary}` "학교 메일로 가입하기"(폭 100%) + `{component.text-link}` "계속 구경할게요"

**`verify-gate-sheet`** — 잠긴 버튼을 누르면 올라오는 바텀시트. `{rounded.sheet}` 위 모서리, 패딩 24px × 20px.
- 제목 `{typography.page-title}` "학생증 인증 후 이용할 수 있어요"
- 설명 `{typography.body}` `{colors.body}` "글쓰기와 채팅은 학생증 인증을 마친 눈송이만 할 수 있어요. 인증은 영업일 24시간 안에 끝나요."
- 단계 표시 — `{component.verify-step-indicator}` 24px 원 두 개를 선으로 연결: ① 학교 이메일(완료, `{colors.success}` 체크) ② 학생증(현재, `{colors.primary}`)
- 하단 `{component.button-primary}` "학생증 인증하기"(폭 100%) + `{component.text-link}` "다음에 할게요"
- 검수 대기 중이면 제목 "학생증 확인 중이에요", 설명 "영업일 24시간 안에 알려드릴게요", 버튼 대신 `{component.verify-status-card}`(접수 시각, 예상 완료 시각).

**`verify-status-card`** — 마이 화면 맨 위의 인증 상태 카드. `{colors.surface-pearl}`, `{rounded.lg}`, 패딩 16px. 상태(정회원 / 검수 중 / 반려됨 / 재인증 필요) + 다음 재인증일("2027년 3월"). 반려됐으면 사유와 "다시 올리기" 버튼.

**인증 화면 (S2·S3)** — 한 화면에 한 가지 일. 위에 `{component.verify-step-indicator}` 단계 표시, `{typography.page-title}` 제목, `{component.text-input}`(학교 이메일·인증번호 6자리) 또는 사진 업로드 상자(점선 1px `{colors.hairline}`, `{rounded.lg}`, 높이 160px), 하단 고정 `{component.button-primary}`. 인증번호 입력은 6칸 분리 입력, 남은 시간 "9:42" `{colors.danger}`.

### Forms (글쓰기)

**`text-input`** — 높이 48px, `{rounded.md}`, 1px `{colors.hairline}`, 좌우 16px, `{typography.body-lg}`. 포커스 시 테두리 `{colors.primary}`, 오류 시 `{colors.danger}` + 아래 `{typography.caption}` 오류 문구. 숫자 입력(보증금·월세·관리비)은 오른쪽에 단위 "만원" `{colors.body}`.

**판매 글쓰기 화면 (S8)** — 당근마켓 글쓰기처럼 한 화면 세로 스크롤. 섹션 순서는 PRD 7.4 표(사진 2~10장 → 분류 → 가격 → 관리비·관리비 포함 항목 → 주소 → 숙대 기준 위치 → 층 → 면적 → 분류별 항목 → 제목 → 일정 → 옵션·건물 → 글쓰기란 → 확인). 각 섹션 제목 `{typography.body-lg-strong}` + 필수 표시 `{colors.primary}` "*".
- 분류·거래 방식: `{component.segmented-control}`
- 가격: 거래 방식에 따라 보이는 입력칸이 바뀜(PRD 8.1). 월세면 보증금·월세·관리비, 전세면 전세금·관리비.
- 옵션·건물·관리비 포함 항목(수도·전기·가스·인터넷·TV·청소·없음): 여러 개 고르는 `{component.filter-chip}`
- 주소: 주소 검색으로 입력, 동네 이름은 자동으로 채워 회색 `{colors.body}`로 보여 줌. 숙대 기준 위치: `{component.bottom-sheet}` 목록에서 하나(1캠 정문 / 1캠 후문 / 도서관 후문 / 2캠 / 숙대입구역 / 효창공원앞역 / 남영역 / 숙대 근처 아님).
- 확인: "실제 거래는 앱 밖에서 당사자 간에 이루어지며, 앱 안 송금은 없습니다. 허위 매물은 제재됩니다" 동의 체크.

**구함 글쓰기 화면** — 같은 형식으로 더 짧게(PRD 7.4a): 원하는 분류(복수) → 희망 위치(숙대 기준 위치·동네, 복수) → 예산(보증금 상한·월 비용 상한) → 입주 희망일 → 희망 기간 → 제목 → 사진(선택, 최대 10장) → 글쓰기란. 복수 선택은 모두 `{component.filter-chip}`.
- 상단 바 오른쪽 `완료`: 필수 항목이 비면 `{colors.placeholder}`, 다 채우면 `{colors.primary}` 700.

### Buttons

**`button-primary`** — 주요 액션("채팅하기", "학생증 인증하기", "학교 메일로 가입하기", "매물 128개 보기"). `{colors.primary}` 배경, 흰 `{typography.body-strong}`, 높이 52px, 패딩 0 × 16px, `{rounded.md}`. 다방 "문자문의"(56px, 2px)보다 낮고 둥글게 바꿨습니다.
- 눌림: `{component.button-primary-pressed}` — `{colors.primary-pressed}`.
- 비활성(입력이 덜 됨): `{component.button-primary-disabled}` — `{colors.divider-soft}` 배경, `{colors.placeholder}` 글자.
- 잠김(인증 필요): `{component.button-primary-locked}` — `{colors.primary-tint}` 배경, `{colors.primary-ink}` 글자, 자물쇠 아이콘. 비활성과 달리 **누를 수 있고** 인증 안내를 엽니다.
- 포커스: `outline: 2px solid {colors.focus-ring}; outline-offset: 2px`.

**`button-outline`** — 보조 액션("초기화", "채팅 3개 보기"). 흰 배경, 1px `{colors.hairline}`, `{colors.ink}` `{typography.body-strong}`, 높이 44px, `{rounded.md}`.

**`text-link`** — `{colors.accent}` `{typography.body}`, 밑줄 없음. "다음에 할게요", "계속 구경할게요", "전체보기".

### Chat

**채팅 목록 (S10)** — 행마다 상대 프로필 40px + 닉네임 `{typography.body-strong}` + 마지막 메시지 `{typography.body}` `{colors.body}` 한 줄 + 시각 `{typography.caption}`, 오른쪽에 매물 썸네일 40px(`{rounded.xs}`)과 `{component.unread-badge}`.

**`chat-listing-header`** — 채팅방 맨 위에 고정된 매물 요약. 높이 72px, 아래 1px `{colors.divider-soft}`. 썸네일 48px + 상태 배지 + 가격 `{typography.body-strong}` + 제목 한 줄. 작성자에게는 오른쪽에 "예약중으로 변경" `{component.button-outline}`(높이 32px).

**`chat-bubble-mine` / `chat-bubble-theirs`** — 최대 폭 70%, `{rounded.lg}`, 패딩 10px × 14px, `{typography.body-lg}`. 내 말풍선 `{colors.primary}` + 흰 글자(오른쪽), 상대 `{colors.surface-soft}` + `{colors.ink}`(왼쪽). 시각·읽음 표시 `{typography.micro}` `{colors.body-muted}`.
- 사진은 한 번에 최대 10장까지 보낼 수 있습니다.
- 전화번호는 자유롭게 주고받을 수 있습니다. 따로 경고하지 않습니다.
- 계좌번호는 보낼 수 없습니다. 보내기를 누르면 메시지가 전송되지 않고 입력창 위에 `{colors.danger}` `{typography.caption}` "계좌번호는 보낼 수 없어요. 숙박숙박은 송금을 중개하지 않고, 계약 전에는 절대 송금하면 안 돼요"를 보여 줍니다. 사진에 계좌번호가 보이면 "계좌번호가 보이는 사진은 보낼 수 없어요".
- **`chat-transfer-warning`** — 상대 메시지에 송금 요청("입금", "계약금 먼저" 등)이 보이면 그 말풍선 바로 아래에 붙는 경고 상자. `{colors.surface-soft}`, `{rounded.md}`, 패딩 8px × 12px, 앞에 ⚠ 아이콘 `{colors.danger}`, `{typography.caption}` "계약 전에는 절대 송금하지 마세요". 오른쪽에 `{component.text-link}` 모양의 `{colors.danger}` "송금 요구 신고" 버튼. 받는 사람에게만 보입니다.
- 재인증 미완료 회원의 채팅방은 입력창 자리에 "재인증하면 다시 채팅할 수 있어요" + `{component.button-primary-locked}`가 보입니다.

### Sheets

**`bottom-sheet`** — 아래에서 올라오는 시트. 흰 배경, 위쪽 모서리 `{rounded.sheet}`(16px), 뒤에 `{colors.dim}`. 위 손잡이 36 × 4px `{colors.hairline}`, 제목 `{typography.page-title}`. 다방 모바일의 앱 설치 시트(위 모서리 16px)와 같은 모양입니다.

### Map (보조)

지도는 메인 탐색이 아닙니다(PRD 3.2). 쓰는 곳은 두 군데뿐입니다.
- 매물 상세의 `{component.detail-mini-map}` (P0)
- 목록 화면의 `지도로 보기`(P2). 이때는 다방의 클러스터 핀 문법(흰 pill + 왼쪽 `{colors.primary}` 숫자 원, 높이 30px)을 그대로 씁니다. 지도 안에서도 정확한 위치 대신 동 단위로 묶어 보여 줍니다.

## Do's and Don'ts

### Do
- 앱을 열면 바로 매물 피드를 보여 줍니다. 지도는 상세 안에서만.
- 선택·주요 액션에는 `{colors.primary}`(Sookmyung Royal Light Blue #0072CE) 하나만 쓰고, 배경 강조는 하늘색 틴트로 합니다.
- 숙명여대 공식 색 중 파랑 두 가지(#003087, #0072CE)만 HEX 그대로 씁니다. 학교 가이드가 색 임의 변경을 금지합니다.
- 찜은 언제나 눈송이 결정 아이콘으로 표시합니다.
- 피드 카드에서 18px/700은 가격에만 씁니다.
- 가격은 PRD 8.3 표기 규칙 그대로 씁니다. 자유 입력 가격을 그대로 노출하지 않습니다.
- 모든 판매 카드에 위치를 "동네 이름 · 숙대 기준 위치 근처"로 넣습니다.
- 인증이 필요한 버튼은 자물쇠와 함께 보여 주고, 누르면 이유와 다음 단계를 안내합니다.
- 상세와 채팅에 "앱 안 송금은 없고, 계약 전에는 송금하지 않는다"는 안내를 넣습니다.
- 그림자는 떠 있는 요소(글쓰기 버튼, 하단 고정 바, 바텀시트)에만 씁니다.

### Don't
- 지도를 첫 화면이나 메인 탐색으로 두지 않습니다.
- "도보 N분" 같은 도보 시간이나 거리순 정렬을 쓰지 않습니다.
- 아파트 분류 탭을 만들지 않습니다.
- 주황·노랑을 쓰지 않습니다. 숙명 Royal Yellow·Royal Orange, 다방의 보라 "플러스"·핑크 "새단장" 대신 하늘색 틴트를 씁니다.
- 찜에 하트 아이콘을 쓰지 않습니다.
- `{colors.placeholder}`(#979797), `{colors.snowflake}`(#2B8FE6), `{colors.sky}`(#8FCBF5)를 흰 바탕 위 본문 텍스트로 쓰지 않습니다.
- 500·600 굵기를 쓰지 않습니다. 400과 700뿐입니다.
- 잠긴 버튼을 숨기거나 회색 비활성처럼 보이게 만들지 않습니다. 비활성(`-disabled`)과 잠김(`-locked`)은 다른 상태입니다.
- 작성자의 실명·학번, 매물의 정확한 주소·호수를 화면에 보여 주지 않습니다.
- 숙명여대 로고·심볼을 앱 로고처럼 쓰지 않습니다.
- 피드 카드에 그림자나 둥근 카드 테두리를 넣지 않습니다.

## Responsive Behavior

### Breakpoints

| Name | Width | Key Changes |
|---|---|---|
| Phone | < 768px | 기준 화면. 한 열 피드, 하단 탭 바, 떠 있는 글쓰기 버튼, 필터·정렬은 바텀시트 |
| Tablet | ≥ 768px | 같은 구조, 콘텐츠 폭 720px 가운데 정렬. 썸네일 128px |
| Desktop (웹으로 만들 때만) | ≥ 1024px | 하단 탭 바를 위쪽 헤더 메뉴(홈·찜·채팅·마이)로 옮김. 콘텐츠 폭 720px 가운데. 글쓰기 버튼은 헤더 오른쪽 `{component.button-primary}`. 바텀시트는 가운데 모달(폭 480px, `{rounded.sheet}`)로 |

숙박숙박은 iOS·Android **모바일 우선 앱**입니다(PRD v0.2). 네이티브 앱으로 만들지 크로스플랫폼·웹앱으로 만들지는 아직 정하지 않았으므로(DEC-010), 데스크톱 행은 웹으로도 낼 때만 씁니다.

### Touch Targets
- 최소 44 × 44px(PRD 11 접근성).
- 필터 칩은 높이 36px이지만 위아래 4px 여백을 포함해 44px 터치 영역을 줍니다.
- 썸네일 위 눈송이 찜 아이콘은 24px, 터치 영역 44px.

### Collapsing Strategy
- **하단 탭 바:** 휴대폰·태블릿 하단 → (웹) 데스크톱 상단 헤더 메뉴.
- **글쓰기 버튼:** 휴대폰 떠 있는 pill(스크롤 시 원으로 축소) → (웹) 데스크톱 헤더 버튼.
- **바텀시트:** 휴대폰·태블릿 하단 시트 → (웹) 데스크톱 가운데 모달.
- **상세 하단 고정 바:** 모든 크기에서 유지, 데스크톱은 콘텐츠 폭(720px)에 맞춤.
- **분류 탭:** 모든 크기에서 가로 스크롤. 태블릿 이상에서는 8개(전체 + 7개 분류)가 한 줄에 다 보입니다.

### Image Behavior
- 피드 썸네일은 모든 크기에서 정사각형(모바일 112px, 태블릿 이상 128px).
- 상세 사진은 콘텐츠 폭에 꽉 차게 4:3.
- 썸네일은 lazy-load하고, 첫 화면 카드 10장의 썸네일만 먼저 불러옵니다(PRD 7.2: 2초 안에 카드 10개).

## Iteration Guide

1. 한 번에 컴포넌트 하나씩. YAML 키(`{component.listing-card}`, `{component.verify-gate-sheet}`)로 직접 가리킵니다.
2. 상태 변형(`-selected`, `-applied`, `-done`, `-pressed`, `-disabled`, `-locked`)은 `components:`에 별도 항목으로 둡니다.
3. HEX를 코드에 직접 쓰지 않고 `{token}` 참조만 씁니다.
4. 호버는 문서화하지 않습니다. 기본·선택·눌림·비활성·잠김 상태만 적습니다. (`{colors.primary-hover}`는 데스크톱 버튼용 토큰으로만 둠)
5. 가격은 언제나 `{typography.price}` 또는 `{typography.price-lg}`. 다른 글자를 18px/700 이상으로 키우지 않습니다.
6. 새 강조가 필요하면 색을 늘리기 전에 `{colors.primary-tint}` 배경이나 회색 단계로 먼저 해결합니다.
7. 권한이 걸린 기능을 새로 만들면 Verification Gate 표에 행을 추가하고 `-locked` 상태를 정의합니다.

## Known Gaps

- 다방은 지도 중심 앱이라 피드 화면 구조(상단 바·분류 탭·떠 있는 글쓰기 버튼·하단 탭 바)는 다방 실측값이 아니라 당근마켓식 구조를 숙박숙박에 맞게 설계한 값입니다. 다방에서 실측한 것은 색·서체·줄높이·카드 정보 구성·필터 칩·슬라이더·플로팅 그림자입니다.
- 당근마켓 화면은 이번에 직접 측정하지 않았습니다. 구조만 PRD의 설명을 따랐습니다.
- 입력 폼(글쓰기, 인증)의 오류·검증 상태는 다방 웹에서 확인하지 않았습니다. `{colors.danger}`는 앱 전용 값입니다.
- 관리자 화면(S14)은 이 문서에서 다루지 않습니다.
- 다크 모드는 정의하지 않았습니다.
- 파랑·하늘 팔레트 중 `#0063B8`, `#005BB0`, `#E8F4FD`, `#CDE7FB`, `#8FCBF5`, `#A9D4F5`, `#2B8FE6`, `#EEF0FF`, `#3D4FC4`는 숙명여대 공식 파랑 두 가지(`#003087`, `#0072CE`)를 기준으로 만든 앱 전용 값입니다. 공식 보조색 Royal Yellow(`#FFB500`)·Royal Orange(`#FF7D01`)는 사용자 요청(2026-11-25)으로 뺐습니다.
- 눈송이 찜 아이콘은 아직 SVG로 그리지 않았습니다. 위 모양 설명이 기준이며, 구현할 때 24px 아이콘 하나를 만들어 기본·찜함 두 상태로 씁니다.
- `{colors.status-reserved}`(초록)와 `{colors.danger}`(빨강)는 상태를 알리는 기능 색이라 파랑 계열로 바꾸지 않았습니다.
- 지도 타일 자체의 색(네이버/카카오 지도)은 지도 제공사 스타일이라 토큰으로 다루지 않습니다.
- 숙대 기준 위치 목록(1캠 정문, 1캠 후문, 도서관 후문, 2캠, 숙대입구역, 효창공원앞역, 남영역)은 PRD 14장에서 확인 중인 초안입니다. 바뀌면 필터 시트와 글쓰기 선택 목록을 같이 고칩니다.
- 구함 카드(`{component.wanted-card}`), 판매/구함 전환(`{component.sell-want-toggle}`), 채팅 송금 경고(`{component.chat-transfer-warning}`)는 다방에 없는 요소라 실측값 없이 기존 토큰으로 설계했습니다.
- 앱 구현 방식(네이티브 / 크로스플랫폼 / 웹앱)이 정해지면 Responsive Behavior와 폰트 불러오기 방법을 다시 맞춥니다.

## 변경 이력

### 2026-11-26 — PRD v0.2·SRS에 맞춤

요청: 변경 내역을 DESIGN.md 안에 합치고, 바뀐 기획(PRD v0.2)에 맞춰 고치기.

| 위치 | 변경 전 | 변경 후 |
|---|---|---|
| 상단 바 | `location-selector` "숙대 정문 ⌄" (도보 시간 기준 선택) | `sell-want-toggle` `판매` / `구함` 전환 |
| 분류 탭 | 전체·원룸·투룸+·오피스텔·아파트·단기임대·하숙·쉐어하우스 | 전체·원룸·투룸·오피스텔·쉐어하우스·하숙·단기임대·단기숙박 (아파트 없음) |
| 위치 표시 | "숙대 정문 도보 7분" | "청파동 · 도서관 후문 근처", 숙대 근처가 아니면 "신수동" |
| 필터 칩 | 가격 · 월세/전세 · 숙대까지 · 입주 가능일 · 여성전용 · 거래가능만 | (내 관심 조건) · 가격 · 숙대 기준 위치 · 동네 · 입주 가능일 · 여성전용 · 거래가능만 |
| 정렬 | 숙대에서 가까운순 포함 | 최신순 · 낮은 가격순 · 찜 많은순 |
| 글쓰기 버튼 | `+ 매물 올리기` | `+ 글쓰기` → 판매 / 구함 선택 |
| 가격 표기 | 단기숙박 없음 | `1박 3`, `1주 18` 추가 |
| 사진 | 3~10장 | 2~10장, 방·화장실 사진 각 1장 이상, 사진마다 `photo-type-label` 방/화장실/기타 |
| 인증 권한표 | 비회원 = 앱 소개 화면만 | 비회원도 목록 구경(카드·찜·검색·필터·글쓰기는 `signup-gate-sheet`), 재인증 미완료 행 추가 |
| 상세 안내 문구 | "매물 정보만 연결해요…" | "방을 보고 연결되는 데까지만 도와요. 앱 안에서는 송금할 수 없고, 계약 전에는 절대 송금하지 마세요…" |
| 채팅 | 전화번호·계좌번호 입력 시 안내 한 번 | 전화번호 허용, 계좌번호 전송 막음, 송금 요청에 `chat-transfer-warning` + "송금 요구 신고", 사진 최대 10장 |
| 반응형 | 모바일 우선 반응형 웹, 데스크톱 레이아웃 포함 | iOS·Android 모바일 우선 앱. 데스크톱은 웹으로도 낼 때만 |
| 새 컴포넌트 | — | `sell-want-toggle(-selected)`, `interest-chip`, `wanted-card`, `status-badge-wanted(-done)`, `photo-type-label`, `signup-gate-sheet`, `chat-transfer-warning` |

색·서체·간격·모서리·눈송이 찜 아이콘은 바뀌지 않았습니다.

### 2026-11-25 — 파랑·하늘 팔레트, 눈송이 찜

요청: 주황 계열을 빼고 파랑·하늘 계열 위주로 더 귀엽게, 찜 하트를 눈송이 결정 모양으로.

#### 1. 색상 토큰 (YAML `colors:`)

| 토큰 | 변경 전 | 변경 후 |
|---|---|---|
| `primary` (메인 색) | `#003087` Royal Blue (남색) | `#0072CE` Royal Light Blue (밝은 파랑) |
| `primary-hover` | `#00449B` | `#0063B8` |
| `primary-pressed` | `#00205C` | `#003087` |
| `primary-deep` | `#00205C` | `#003087` |
| `primary-ink` (새로 추가) | 없음 | `#005BB0` (하늘색 틴트 위 글자용) |
| `primary-tint` | `#EEF4FB` | `#E8F4FD` (하늘색 틴트) |
| `primary-tint-strong` | `#D6E4F5` | `#CDE7FB` |
| `sky` (새로 추가) | 없음 | `#8FCBF5` (일러스트·장식용 하늘색) |
| `focus-ring` | `#A9C8EC` | `#A9D4F5` |
| `surface-selected` | `#EEF4FB` | `#E8F4FD` |
| `highlight` / `highlight-tint` / `highlight-ink` | `#FFB500` / `#FFF4D6` / `#7A5600` (노랑) | 삭제 |
| `like` | `#FF7D01` (주황) | 삭제 → `snowflake` `#2B8FE6` (하늘빛 파랑) |
| `women-tint` / `women-ink` | `#FFF0E5` / `#B34F00` (주황 계열) | `#EEF0FF` / `#3D4FC4` (보랏빛 파랑) |

#### 2. 컴포넌트

| 컴포넌트 | 변경 전 | 변경 후 |
|---|---|---|
| 찜 아이콘 | `like-toggle` 하트, 찜하면 주황 `#FF7D01` | `snowflake-toggle` 눈송이 결정, 찜하면 하늘빛 파랑 `#2B8FE6`으로 채움 |
| "가격 인하" 태그 | 노랑 틴트 `#FFF4D6` + 갈색 글자 `#7A5600` | 진한 하늘 틴트 `#CDE7FB` + 남색 글자 `#003087` |
| "여성전용" 태그 | 주황 틴트 `#FFF0E5` + `#B34F00` | 보랏빛 파랑 틴트 `#EEF0FF` + `#3D4FC4` |
| 안 읽은 채팅 수 배지 | 주황 `#FF7D01` | 메인 파랑 `#0072CE` |
| 적용된 필터 칩·"숙대생 인증" 태그·잠긴 버튼의 글자 | `primary` (`#003087`) | `primary-ink` (`#005BB0`) |
| 하단 탭 바 `찜` 탭 아이콘 | (하트) | 눈송이 결정 |
| 홈 화면 그림의 카드 썸네일 | ♡ | ❄ |
| 상세 하단 고정 바 | 왼쪽 하트 | 왼쪽 눈송이 찜 아이콘 |

#### 3. 새로 추가한 눈송이 찜 아이콘 규칙

- 모양: 가지 6개짜리 눈 결정. 가지 끝마다 작은 V자 곁가지, 가운데는 작은 육각형. 24 × 24px, 선 굵기 1.75px, 선 끝은 둥글게. 가지를 짧고 둥글게 그려 귀엽게 보이게 합니다.
- 기본: 사진 위에서는 흰 선 + 옅은 그림자, 흰 배경 위에서는 회색 선.
- 찜함: 가운데를 `#2B8FE6`으로 채우고 흰 테두리. 누르면 1 → 1.2 → 1로 0.2초 튀어 오릅니다.
- 터치 영역 44 × 44px, 스크린 리더 이름 "찜하기" / "찜 해제".
- 숙명여대 공식 심볼도 눈 결정 모양이지만 학교 가이드상 무단 사용이 금지되므로, 학교 심볼을 따라 그리지 않고 앱 전용으로 새로 그립니다.

#### 4. 문장(설명) 변경

| 위치 | 변경 전 | 변경 후 |
|---|---|---|
| 맨 위 description | 선택·주요 액션에만 쓰는 숙명 Royal Blue(#003087) 하나 | 숙명 Royal Light Blue(#0072CE)와 하늘색 틴트로만 만든 파랑·하늘 팔레트(주황·노랑 없음). 찜 아이콘은 하트 대신 눈송이 결정 |
| Overview "숙박숙박만의 요소" | 세 가지. (1) Sookmyung Royal Blue `#003087` | 네 가지. (1) Royal Light Blue `#0072CE` + 하늘색 틴트, 주황·노랑 없음 … (4) 찜 아이콘은 눈송이 결정 |
| Key Characteristics | 하나의 블루(#003087) | 하나의 블루(#0072CE) + 하늘색 틴트 배경. "파랑·하늘 계열만", "찜은 눈송이" 두 줄 추가 |
| Brand Gradient | 블루 틴트와 숙명 옐로 틴트로 대신 | 하늘색 틴트로 대신. 숙명 Royal Yellow·Royal Orange도 쓰지 않음 |
| Do | 숙명 공식 색(#003087, #0072CE, #FFB500, #FF7D01)을 그대로 씀 | 공식 파랑 두 가지(#003087, #0072CE)만 그대로 씀. 찜은 언제나 눈송이 |
| Don't | 블루 틴트·옐로 틴트를 씀 / `#FF7D01`을 본문 글자로 쓰지 않음 | 주황·노랑을 쓰지 않음 / 찜에 하트를 쓰지 않음 / `#2B8FE6`, `#8FCBF5`를 본문 글자로 쓰지 않음 |
| Known Gaps | 앱 전용 값 목록에 `#00449B` 등, 공식 값에 `#FFB500`, `#FF7D01` 포함 | 새 앱 전용 값 목록으로 교체. 노랑·주황은 사용자 요청으로 뺐다고 기록. 눈송이 아이콘 SVG는 아직 없음. 초록(예약중)·빨강(오류)은 기능 색이라 유지 |

#### 5. 그대로 둔 것

- `#003087` Royal Blue는 없애지 않고 눌림 상태, 로고, 캠퍼스 마커, "가격 인하" 글자 같은 진한 파랑 자리로 옮겼습니다.
- `예약중` 배지 초록(`#157A4A`)과 오류 빨강(`#E5484D`)은 상태를 알리는 색이라 바꾸지 않았습니다.
- 서체, 크기, 간격, 모서리, 레이아웃은 바뀌지 않았습니다.
