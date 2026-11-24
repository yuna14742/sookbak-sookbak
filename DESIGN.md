---
version: alpha
name: Sookbak-design-analysis
description: 다방(dabangapp.com)의 지도 + 리스트 매물 탐색 구조를 그대로 가져오고, 브랜드 색을 숙명여대 공식 Sookmyung Royal Blue(#003087)로 바꾼 자취방·하숙 앱 디자인 시스템. 흰 캔버스, 회색 1px 헤어라인, Pretendard 한 서체, 18px 굵은 가격, 그리고 선택·액션·지도 핀에만 쓰는 하나의 블루. 그림자는 지도 위에 떠 있는 요소에만 쓴다.

colors:
  primary: "#003087"
  primary-hover: "#00449B"
  primary-pressed: "#00205C"
  primary-deep: "#00205C"
  accent: "#0072CE"
  accent-hover: "#005BB0"
  primary-tint: "#EEF4FB"
  primary-tint-strong: "#D6E4F5"
  focus-ring: "#A9C8EC"
  surface-selected: "#EEF4FB"
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
  footer-bg: "#373737"
  footer-text: "#AAAAAA"
  highlight: "#FFB500"
  highlight-tint: "#FFF4D6"
  highlight-ink: "#7A5600"
  like: "#FF7D01"
  women-tint: "#FFF0E5"
  women-ink: "#B34F00"
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
  section-title:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 400
    lineHeight: 1.58
    letterSpacing: -0.5px
  price-lg:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 24px
    fontWeight: 700
    lineHeight: 1.58
    letterSpacing: 0
  card-title:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 20px
    fontWeight: 700
    lineHeight: 1.6
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
  footer-link:
    fontFamily: "Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif"
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.23
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
  global-header:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    height: 80px
    padding: 0 20px
  nav-link:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.md}"
    padding: 8px 16px
    height: 42px
  nav-link-active:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.md}"
    padding: 8px 16px
  badge-new:
    backgroundColor: "{colors.highlight-tint}"
    textColor: "{colors.highlight-ink}"
    typography: "{typography.micro}"
    rounded: "{rounded.pill}"
    padding: 1px 5px
  search-input-hero:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.pill}"
    padding: 11px 23px 11px 56px
    height: 48px
  search-input-header:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.pill}"
    padding: 7px 37px 7px 15px
    height: 40px
  category-rail-item:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.body}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    size: 70px x 64px
  category-rail-item-selected:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
  filter-chip:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.xxs}"
    padding: 0 7px 0 11px
    height: 36px
  filter-chip-open:
    backgroundColor: "{colors.surface-chip-open}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.xxs}"
  filter-chip-applied:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.xxs}"
  filter-reset-button:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    rounded: "{rounded.xxs}"
    size: 42px x 36px
  filter-dropdown-panel:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.xxs}"
    padding: 24px
    width: 360px
  range-slider-knob:
    backgroundColor: "{colors.canvas}"
    rounded: "{rounded.full}"
    size: 24px
  range-slider-track-active:
    backgroundColor: "{colors.primary}"
    height: 4px
  list-tab-pill:
    backgroundColor: "{colors.surface-dark}"
    textColor: "{colors.on-dark}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.pill}"
    padding: 0 16px
    height: 32px
  listing-card:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.price}"
    rounded: "{rounded.none}"
    padding: 16px
    width: 400px
  listing-card-selected:
    backgroundColor: "{colors.surface-selected}"
    textColor: "{colors.ink}"
    rounded: "{rounded.none}"
  listing-card-visited:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.placeholder}"
    rounded: "{rounded.none}"
  listing-thumbnail:
    backgroundColor: "{colors.surface-soft}"
    rounded: "{rounded.xxs}"
    size: 140px
  tag-verified:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 4px
    height: 20px
  tag-women-only:
    backgroundColor: "{colors.women-tint}"
    textColor: "{colors.women-ink}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 4px
    height: 20px
  tag-option:
    backgroundColor: "{colors.surface-soft}"
    textColor: "{colors.body}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 4px 8px
    height: 28px
  tag-info-tint:
    backgroundColor: "{colors.primary-tint}"
    textColor: "{colors.primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 4px 8px
  like-toggle:
    backgroundColor: transparent
    textColor: "{colors.on-dark}"
    size: 24px
  like-toggle-active:
    backgroundColor: transparent
    textColor: "{colors.like}"
    size: 24px
  map-pin-cluster:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.caption}"
    rounded: "{rounded.pill}"
    height: 30px
  map-pin-cluster-count:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.pill}"
    padding: 6px
    height: 30px
  map-pin-listing:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 4px 8px
  map-pin-selected:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
  map-pin-campus:
    backgroundColor: "{colors.primary-deep}"
    textColor: "{colors.on-dark}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.full}"
    size: 32px
  map-location-label:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg-strong}"
    rounded: "{rounded.pill}"
    padding: 0 16px
    height: 40px
  map-control-button:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.caption}"
    rounded: "{rounded.sm}"
    size: 36px
  detail-panel:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.price-lg}"
    padding: 24px 20px
    width: 400px
  detail-id-bar:
    backgroundColor: "{colors.primary-deep}"
    textColor: "{colors.on-dark}"
    typography: "{typography.body}"
    padding: 8px 20px
    height: 40px
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.xxs}"
    padding: 0 16px
    height: 56px
  button-primary-pressed:
    backgroundColor: "{colors.primary-pressed}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.xxs}"
  button-primary-disabled:
    backgroundColor: "{colors.divider-soft}"
    textColor: "{colors.placeholder}"
    rounded: "{rounded.xxs}"
  button-outline:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-strong}"
    rounded: "{rounded.xxs}"
    padding: 0 15px
    height: 44px
  text-link:
    backgroundColor: transparent
    textColor: "{colors.accent}"
    typography: "{typography.body}"
  home-category-card:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.card-title}"
    rounded: "{rounded.lg}"
    padding: 20px
    height: 178px
  recent-visit-chip:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.pill}"
    padding: 0 7px
    height: 21px
  mobile-category-button:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.caption-strong}"
    rounded: "{rounded.xs}"
    padding: 0 8px
    size: 65px x 48px
  mobile-search-bar:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-lg}"
    rounded: "{rounded.xs}"
    height: 48px
  bottom-sheet:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.card-title}"
    rounded: "{rounded.sheet} {rounded.sheet} 0 0"
    padding: 20px
  footer:
    backgroundColor: "{colors.footer-bg}"
    textColor: "{colors.footer-text}"
    typography: "{typography.footer-link}"
    padding: 48px 20px
---

## Overview

다방 웹은 **"지도가 주인공이고, UI는 지도를 가리지 않는 얇은 틀"**이라는 원칙으로 만들어져 있습니다. 데스크톱 지도 화면은 80px 헤더 아래에 왼쪽 카테고리 레일(70px), 400px 매물 리스트, 나머지 전부를 차지하는 지도가 나란히 놓입니다. 매물을 누르면 지도 자리에 400px 상세 패널이 열려 리스트와 상세를 동시에 볼 수 있습니다. 화면 대부분은 흰색과 회색 헤어라인으로만 구분되고, 파랑은 "선택됨"과 "누를 수 있음"에만 씁니다.

밀도는 높은 편입니다. 카드 한 장에 가격, 방 종류, 층·면적·관리비, 한 줄 설명, 태그까지 다섯 줄이 들어가지만, 가격만 18px 굵게, 나머지는 14px 보통 굵기로 회색 단계만 바꿔서 위계를 만듭니다. 모서리는 거의 각져 있고(필터 칩·버튼 2px, 태그 4px), 둥근 형태는 검색창·지도 핀·"매물" 탭처럼 **떠 있거나 눌러서 이동하는 요소**에만 씁니다.

숙박숙박은 이 틀을 그대로 쓰고, 세 가지를 바꿉니다. (1) 다방 블루 `#326CF9` 자리에 숙명여대 공식 **Sookmyung Royal Blue `#003087`**을 넣습니다. (2) 지도의 기준점을 숙명여대 캠퍼스(청파동)로 두고, 카드에 "숙대 정문 도보 N분"을 넣습니다. (3) 카테고리를 원룸·투룸·하숙·쉐어하우스·양도·룸메이트로 바꿉니다.

**Key Characteristics:**
- 지도 + 리스트 분할 화면. 리스트와 상세는 각각 400px 고정 폭, 지도가 나머지를 모두 차지합니다.
- 하나의 블루(`{colors.primary}` — #003087)가 선택 상태, 주요 버튼, 지도 클러스터 핀을 모두 담당합니다.
- 가장 짙은 블루(`{colors.primary-deep}` — #00205C)는 매물번호 바와 캠퍼스 마커에만 씁니다. 다방은 같은 자리에 `#0C1A53`을 씁니다.
- 서체는 Pretendard 하나. 굵기는 400과 700 두 단계만 씁니다.
- 각진 컨트롤(2px)과 둥근 플로팅 요소(pill)의 두 가지 모양 문법.
- 그림자는 지도 위에 떠 있는 요소(모바일 버튼, 지도 컨트롤, 위치 라벨, 슬라이더 손잡이)에만 씁니다.
- 회색 단계로 위계를 만듭니다: 제목 #222 → 정보 #656565 → 설명 #757575(다방은 #979797).

## Colors

> **분석한 페이지:** 홈(`/`), 원/투룸 지도(`/map/onetwo`), 지도 안 매물 상세 패널, 방크기 필터 드롭다운, 모바일 지도(`/mobile/map/onetwo`). 2026-11-24, 데스크톱 1024px과 모바일 375px에서 계산된 CSS 값을 읽었습니다.
>
> **숙명여대 색 출처:** [숙명여자대학교 UI 가이드 Color Scheme](https://www.sookmyung.ac.kr/kr/intro/ui.do). Royal Blue Pantone 287C / RGB 0·48·135, Royal Light Blue Pantone 285C / RGB 0·114·206.

### Brand & Accent
- **Sookmyung Royal Blue** (`{colors.primary}` — #003087): 숙명여대 공식 메인 색. 다방의 `#326CF9`가 하던 일을 모두 맡습니다. 주요 버튼("문의하기", "적용하기"), 선택된 카테고리, 적용된 필터 칩, 지도 클러스터 숫자 원, 슬라이더 트랙. 흰 배경 대비 11.85:1.
- **Royal Blue Hover** (`{colors.primary-hover}` — #00449B): 데스크톱 호버. 공식 색 사이를 나눈 앱 전용 값입니다.
- **Royal Blue Pressed / Deep** (`{colors.primary-pressed}`, `{colors.primary-deep}` — #00205C): 눌림 상태, 그리고 상세 패널의 매물번호 바와 캠퍼스 마커. 다방이 `#0C1A53`(blue-900)을 쓰는 자리입니다.
- **Sookmyung Royal Light Blue** (`{colors.accent}` — #0072CE): 숙명여대 공식 보조 색. 텍스트 링크, 필터 패널의 "전체" 같은 보조 액션, 카드의 "숙대 도보 N분" 정보. 흰 배경 대비 4.89:1(AA).
- **Primary Tint** (`{colors.primary-tint}` — #EEF4FB): 선택된 레일 항목, 적용된 필터 칩, 파란 정보 태그의 배경. 다방의 `#EEF8FF` 자리.
- **Focus Ring** (`{colors.focus-ring}` — #A9C8EC): 키보드 포커스 외곽선 전용.

### Surface
- **Canvas** (`{colors.canvas}` — #FFFFFF): 헤더, 리스트, 상세 패널, 카드, 버튼 등 거의 모든 면.
- **Selected Row** (`{colors.surface-selected}` — #EEF4FB): 상세가 열려 있는 매물 카드의 배경. 다방은 `#F0F4FA`.
- **Soft Gray** (`{colors.surface-soft}` — #F5F5F5): 옵션 태그(신축·주차·풀옵션), 사진이 없을 때의 썸네일.
- **Pearl** (`{colors.surface-pearl}` — #FAFAFA): 섹션 배경을 아주 옅게 나눌 때.
- **Chip Open** (`{colors.surface-chip-open}` — #EDEDED): 드롭다운이 열려 있는 필터 칩의 배경.
- **Dark** (`{colors.surface-dark}` — #222222): 리스트 상단 "매물" 탭 알약.
- **Footer** (`{colors.footer-bg}` — #373737): 푸터 전용 진회색.

### Text
- **Ink** (`{colors.ink}` — #222222): 가격, 제목, 필터 칩 글자, 상세 정보 값.
- **Ink Sub** (`{colors.ink-sub}` — #434343): 강조가 필요한 보조 텍스트.
- **Body** (`{colors.body}` — #656565): 카드의 방 종류, 층·면적·관리비, 옵션 태그 글자.
- **Body Muted** (`{colors.body-muted}` — #757575): 카드의 한 줄 설명, 조회수·찜 수. 다방은 `#979797`을 쓰지만 흰 배경 대비 2.86:1로 AA에 못 미쳐 한 단계 진하게 바꿨습니다(4.61:1).
- **Placeholder** (`{colors.placeholder}` — #979797): 입력창 placeholder, 이미 본 매물 카드 글자, 슬라이더 눈금. 본문 텍스트로는 쓰지 않습니다.

### Hairlines & Borders
- **Hairline** (`{colors.hairline}` — #DFDFDF): 필터 칩, 아웃라인 버튼, 드롭다운 패널, 슬라이더 손잡이의 1px 테두리.
- **Divider Soft** (`{colors.divider-soft}` — #EDEDED): 검색창 테두리, 홈 카테고리 카드 테두리, 헤더 아래 구분선.
- **Disabled Border** (`{colors.disabled-border}` — #CCCCCC): 비활성 컨트롤, "최근 방문" 칩 테두리.

### Status & Tags
- **Highlight** (`{colors.highlight}` — #FFB500, Sookmyung Royal Yellow): 별점, 일러스트 포인트. 텍스트로 쓸 때는 `{colors.highlight-tint}` 배경 + `{colors.highlight-ink}`(#7A5600) 글자(6.07:1). 다방의 핑크 "새단장" 배지(`#FF3478` / `#FFF2F6`) 자리.
- **Like** (`{colors.like}` — #FF7D01, Sookmyung Royal Orange): 찜 하트가 채워졌을 때만. 흰 배경 대비 2.57:1이라 텍스트로는 쓰지 않습니다.
- **Women Only** (`{colors.women-tint}` #FFF0E5 + `{colors.women-ink}` #B34F00): "여성전용" 태그(4.67:1).
- **Success / Danger** (`{colors.success}` #1A9E5C, `{colors.danger}` #E5484D): 학교 메일 인증 완료, 입력 오류.

### Brand Gradient
**그라데이션은 쓰지 않습니다.** 다방도 UI에는 그라데이션 토큰이 없고, 홈 배너의 색감은 이미지 자체에 들어 있습니다. 다방 "플러스" 태그의 보라색(`#3E26FD` / `#F5F3FE`)처럼 두 번째 강조색을 들이지 않고, 그 자리는 `{component.tag-verified}`(블루 틴트)로 대신합니다.

## Typography

### Font Family
- **전체**: `Pretendard Variable, Pretendard, -apple-system, system-ui, sans-serif`. 다방과 같은 서체입니다. 한글·영문·숫자의 폭이 고르고 가격 숫자가 또렷합니다.
- **숫자**: 가격·면적·층수처럼 숫자가 세로로 정렬되어야 하는 곳은 `font-variant-numeric: tabular-nums`.
- **숙명눈꽃체**(숙명여대 전용서체)는 학교 로고·슬로건용이라 앱 UI에는 쓰지 않습니다.

### Hierarchy

| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `{typography.display}` | 28px | 700 | 1.36 | -0.5px | 홈 첫 화면 헤드라인 (다방에는 없음, 앱 전용) |
| `{typography.section-title}` | 24px | 400 | 1.58 (38px) | -0.5px | 홈 섹션 제목 "관심있는 청파동 주변, …". 강조 단어만 `{colors.primary}` 700 |
| `{typography.price-lg}` | 24px | 700 | 1.58 (38px) | 0 | 상세 패널 가격 |
| `{typography.card-title}` | 20px | 700 | 1.6 (32px) | 0 | 홈 카테고리 카드 제목, 바텀시트 제목 |
| `{typography.price}` | 18px | 700 | 1.67 (30px) | 0 | 리스트 카드 가격 "월세 300/43" |
| `{typography.body-lg}` | 16px | 400 | 1.63 (26px) | 0 | 헤더 메뉴, 검색 입력, 상세 설명 |
| `{typography.body-lg-strong}` | 16px | 700 | 1.63 | 0 | 드롭다운 패널 제목, 지도 위치 라벨 |
| `{typography.body}` | 14px | 400 | 1.71 (24px) | 0 | 카드 정보 줄, 필터 칩, 상세 정보 표 |
| `{typography.body-strong}` | 14px | 700 | 1.71 | 0 | 버튼 라벨, "매물" 탭, 적용된 필터 칩 |
| `{typography.footer-link}` | 13px | 400 | 1.23 | 0 | 푸터 링크 |
| `{typography.caption}` | 12px | 400 | 1.67 (20px) | 0 | 슬라이더 눈금, 지도 핀 지역명 |
| `{typography.caption-strong}` | 12px | 700 | 1.67 | 0 | 태그, 레일 라벨, 핀 숫자 |
| `{typography.micro}` | 10px | 700 | 1.6 | 0 | "NEW" 배지 |

### Principles

- **가격이 제일 크고 제일 굵다.** 리스트에서 18px/700은 가격만 씁니다. 방 종류·면적·설명은 모두 14px/400이고 색만 다릅니다.
- **굵기는 400과 700 두 단계만.** 다방 전체에서 500·600은 나오지 않습니다. 강조가 필요하면 700, 아니면 400.
- **자간은 거의 0.** 다방은 24px 섹션 제목에만 -0.5px을 주고 나머지는 `normal`입니다. 작은 글자에 음수 자간을 넣지 않습니다.
- **줄높이는 픽셀로 고정.** 다방은 12→20px, 14→24px, 16→26px, 18→30px, 20→32px, 24→38px로 줄높이를 고정해 카드 줄 간격이 일정합니다. 위 표의 배수는 이 값을 나눈 것입니다.
- **회색 단계가 위계다.** #222(값) → #656565(정보) → #757575(설명) → #979797(비활성). 크기를 바꾸기 전에 색 단계부터 바꿉니다.

### Note on Font Substitutes
Pretendard는 무료 오픈 폰트이므로 대체할 필요는 거의 없습니다. CDN이나 `next/font/local`로 Pretendard Variable을 불러오고, 로딩 전에는 `-apple-system`(iOS·macOS의 Apple SD Gothic Neo)과 `system-ui`(Android의 Noto Sans KR)로 대체됩니다. 두 대체 서체 모두 Pretendard보다 글자 폭이 약간 넓으니 카드 설명 줄의 말줄임이 조금 일찍 생길 수 있습니다.

## Layout

### Spacing System
- **기본 단위:** 4px. 구조 간격은 8 / 12 / 16 / 20 / 24px에 맞춥니다.
- **토큰:** `{spacing.xxs}` 4px · `{spacing.xs}` 8px · `{spacing.sm}` 12px · `{spacing.md}` 16px · `{spacing.lg}` 20px · `{spacing.xl}` 24px · `{spacing.xxl}` 32px · `{spacing.section}` 48px.
- **카드 패딩:** 리스트 카드 `{spacing.md}`(16px), 홈 카테고리 카드 `{spacing.lg}`(20px).
- **패널 패딩:** 상세 패널 24px(위아래) × 20px(좌우), 드롭다운 패널 24px.
- **칩 사이 간격:** 필터 칩 8px, 옵션 태그 8px, 태그 안 아이콘-글자 4px.
- **헤더 좌우 여백:** 20px.

### Grid & Container
- **데스크톱 지도 화면:** `헤더 80px` 아래로 `카테고리 레일 70px | 리스트 400px | 지도 (나머지)`. 필터바는 리스트+지도 위에 걸쳐 높이 약 56px.
- **상세 열림:** `레일 | 리스트 400px | 상세 패널 400px | 지도`. 상세는 지도를 밀어내고 그 왼쪽에 붙습니다.
- **홈:** 최대 폭 1200px, 가운데 정렬. 카테고리 카드는 3열 그리드(카드 폭 약 333px), 오른쪽에 배너 열.
- **모바일:** 지도가 전체 화면을 차지하고, 상단에 카테고리 버튼 + 검색창, 오른쪽에 세로로 지도 컨트롤 버튼, 아래에서 바텀시트가 올라옵니다.

```
데스크톱 지도 화면 (≥ 1024px)
┌──────────────────────────────────────────────────────────────┐
│ 로고  [ 숙대입구역, 청파동, 효창공원앞역…  🔍 ]   지도 양도 관심목록 로그인 │ 80px
├──────┬───────────────────────────────────────────────────────┤
│ 원룸 │ [월세·전세 ⌄][보증금 ⌄][방크기 ⌄][숙대까지 ⌄][추가필터 ⌄][↻]   │ 56px
│ 투룸 ├──────────────────┬────────────────────────────────────┤
│ 하숙 │ (매물)            │                                    │
│ 쉐어 │ ┌────┐ 월세 300/43│      (52 청파동)    (14 효창동)      │
│ 양도 │ │140 │ 원룸 · 단기 │              ◉ 숙명여대              │
│ 룸메 │ │ px │ 3층, 20㎡…  │      (8 원효로)                      │
│ 70px │ └────┘ 🚶 정문 7분 │                         [⌖]        │
│      │ 400px             │                                    │
└──────┴──────────────────┴────────────────────────────────────┘
```

### Whitespace Philosophy
다방은 여백보다 **정보 밀도**를 택합니다. 카드 사이에 간격 없이 패딩 16px만으로 이어 붙이고, 리스트에는 구분선도 거의 없습니다. 대신 지도 영역에는 아무 UI도 얹지 않아 지도가 시원하게 보입니다. 숙박숙박도 리스트는 촘촘하게, 지도는 비워 두는 이 대비를 유지합니다. 여백이 넉넉한 곳은 홈(섹션 사이 48px)과 상세 패널뿐입니다.

## Elevation & Depth

| Level | Treatment | Use |
|---|---|---|
| Flat | 그림자 없음, 테두리 없음 | 헤더, 리스트 카드, 상세 패널, 푸터 |
| Hairline | 1px `{colors.hairline}` 또는 `{colors.divider-soft}` | 필터 칩, 드롭다운 패널, 검색창, 홈 카테고리 카드, 아웃라인 버튼 |
| Chip lift | `rgba(0, 0, 0, 0.06) 0 2px 4px 0` | 홈 카테고리 카드 안 "최근 방문" 칩 |
| Knob | `rgba(0, 0, 0, 0.16) 0 1px 4px 0` | 범위 슬라이더 손잡이 |
| Map control | `rgba(0, 0, 0, 0.12) 0 0 8px -1px` | 지도 위 36px 컨트롤 버튼(필터, 현재 위치) |
| Floating bar | `rgba(0, 0, 0, 0.2) 0 2px 4px 0` | 모바일 상단 카테고리 버튼, 검색창 |
| Floating label | `rgba(0, 0, 0, 0.1) 0 10px 20px 0` | 지도 하단 위치 라벨 "청파동" |
| Dim | `{colors.dim}` 전체 덮기 | 바텀시트·모달 뒤 |

**그림자 원칙.** 그림자는 "지도 위에 떠 있다"는 뜻으로만 씁니다. 리스트·패널·카드처럼 화면에 붙어 있는 요소는 테두리나 배경색으로만 구분합니다. 드롭다운 패널도 그림자 없이 1px 헤어라인만 씁니다.

### Decorative Depth
- **지도 자체가 깊이를 만듭니다.** 컬러 지도 위에 흰 핀과 파란 숫자 원이 놓이면서 자연스럽게 층이 생깁니다.
- **선택된 행 배경**(`{colors.surface-selected}`)이 "지금 이 매물을 보고 있다"를 그림자 없이 표시합니다.
- 홈 배너만 사진·일러스트를 쓰고, 나머지 장식은 없습니다.

## Shapes

### Border Radius Scale

| Token | Value | Use |
|---|---|---|
| `{rounded.none}` | 0px | 리스트 카드, 상세 패널, 헤더, 매물번호 바 |
| `{rounded.xxs}` | 2px | 필터 칩, 드롭다운 패널, 주요·아웃라인 버튼, 매물 썸네일 |
| `{rounded.xs}` | 4px | 태그, 카테고리 레일 항목, 모바일 카테고리 버튼·검색창 |
| `{rounded.sm}` | 6px | 지도 컨트롤 버튼 |
| `{rounded.md}` | 8px | 헤더 메뉴 호버 영역 |
| `{rounded.lg}` | 12px | 홈 카테고리 카드 |
| `{rounded.sheet}` | 16px | 바텀시트 위쪽 두 모서리 |
| `{rounded.pill}` | 9999px | 검색창(데스크톱), 지도 클러스터 핀, "매물" 탭, 위치 라벨, NEW 배지, "최근 방문" 칩 |
| `{rounded.full}` | 50% | 슬라이더 손잡이, 캠퍼스 마커 |

### Photography Geometry
- **리스트 썸네일:** 140 × 140px 정사각형, `{rounded.xxs}`, `object-fit: cover`. 오른쪽 위 8px에 흰 하트(`{component.like-toggle}`). 다방은 사진에 워터마크를 얹지만 숙박숙박은 넣지 않습니다.
- **상세 사진:** 상세 패널 폭(400px) 꽉 차게, 가로로 넘기는 캐러셀. 바로 아래에 `{component.detail-id-bar}`가 붙습니다.
- **사진이 없을 때:** `{colors.surface-soft}` 배경에 회색 집 아이콘.
- **홈 카드 일러스트:** 오른쪽 아래 약 56px, 평면 일러스트, 블루 계열 + 옐로 포인트.

## Components

### Top Navigation

**`global-header`** — 높이 80px, 흰 배경, 좌우 20px. 왼쪽에 로고(숙박숙박 워드마크, `{colors.primary}`), 그 옆에 `{component.search-input-header}`, 오른쪽에 메뉴. 아래 1px `{colors.divider-soft}` 구분선.

**`nav-link`** — `{typography.body-lg}`(16px/400) `{colors.ink}`, 패딩 8px × 16px, 높이 42px, 호버 영역 `{rounded.md}`. 현재 페이지는 `{component.nav-link-active}` — 글자 `{colors.primary}` 700. 새 메뉴 옆에는 `{component.badge-new}`(10px/700, pill, 패딩 1px × 5px).

**`search-input-header`** — 지도 화면 헤더의 검색창. 폭 320px, 높이 40px, `{rounded.pill}`, 1px `{colors.divider-soft}` 테두리, 패딩 7px 37px 7px 15px, 오른쪽 돋보기 아이콘. Placeholder "숙대입구역, 청파동, 효창공원앞역, 매물번호".

**`search-input-hero`** — 홈 가운데의 큰 검색창. 높이 48px, `{rounded.pill}`, 왼쪽 패딩 56px(돋보기 아이콘 자리), 16px 글자.

### Category Rail & Filters

**`category-rail-item`** — 지도 화면 왼쪽 세로 레일의 항목. 70 × 64px, 아이콘 24px 위 + 라벨 `{typography.caption-strong}` 아래, 글자 `{colors.body}`. 선택되면 `{component.category-rail-item-selected}` — 배경 `{colors.primary-tint}`, 1px `{colors.primary}` 테두리, 글자 `{colors.primary}`. 항목: 원룸 · 투룸 · 하숙 · 쉐어하우스 · 양도 · 룸메이트.

**`filter-chip`** — 드롭다운을 여는 칩. 높이 36px, 1px `{colors.hairline}` 테두리, `{rounded.xxs}`(2px), 패딩 0 7px 0 11px, 라벨 `{typography.body}` + 오른쪽 꺾쇠 아이콘. 칩 사이 8px.
- 열림: `{component.filter-chip-open}` — 배경 `{colors.surface-chip-open}`, 테두리 `{colors.primary}`, 꺾쇠가 위로.
- 적용됨: `{component.filter-chip-applied}` — 배경 `{colors.primary-tint}`, 글자 `{colors.primary}` 700, 라벨이 값으로 바뀜("도보 10분 이내").
- 맨 끝에 `{component.filter-reset-button}` — 42 × 36px, 새로고침 아이콘만.
- 숙박숙박 전용 필터: 숙대까지(도보 5·10·15분, 정문/후문 기준), 여성전용 건물, 단기(1~6개월), 방학 양도.

**`filter-dropdown-panel`** — 칩 바로 아래에 붙어 열리는 패널. 폭 360px, 흰 배경, 1px `{colors.hairline}`, `{rounded.xxs}`, 패딩 24px, 그림자 없음. 맨 위 제목 `{typography.body-lg-strong}`, 그 아래 라벨 `{typography.body}` + 오른쪽 "전체" `{component.text-link}`.

**`range-slider`** — 보증금·월세·면적 범위. 트랙 4px, 선택 구간 `{component.range-slider-track-active}`(`{colors.primary}`), 손잡이 `{component.range-slider-knob}` 24px 원, 1px `{colors.hairline}`, 손잡이 그림자. 아래 눈금 `{typography.caption}` `{colors.placeholder}`("최소 · 10평 · 20평 … 최대").

### Listing List

**`list-tab-pill`** — 리스트 맨 위 "매물" 탭. 배경 `{colors.surface-dark}`, 흰 글자 `{typography.body-strong}`, 높이 32px, 패딩 0 × 16px, `{rounded.pill}`. 숙박숙박에서는 "매물 · 양도 · 룸메" 세그먼트로 늘릴 수 있습니다.

**`listing-card`** — 리스트의 한 행. 폭 400px, 패딩 16px, 흰 배경, 테두리·그림자 없음. 왼쪽 `{component.listing-thumbnail}`(140px 정사각형), 오른쪽 16px 띄우고 텍스트 다섯 줄:
1. 가격 `{typography.price}`(18px/700) `{colors.ink}` — "월세 300/43"
2. 방 종류 `{typography.body}` `{colors.body}` — "원룸 · 단기"
3. 층·면적·관리비 `{typography.body}` `{colors.body}` — "3층, 20㎡, 관리비 5만"
4. 학교 거리 `{typography.body-strong}` `{colors.accent}` — "숙대 정문 도보 7분" (숙박숙박 추가)
5. 설명 `{typography.body}` `{colors.body-muted}`, 한 줄 말줄임
6. 태그 줄 — `{component.tag-verified}`, `{component.tag-women-only}`

- 상세가 열린 카드: `{component.listing-card-selected}` — 배경 `{colors.surface-selected}`.
- 이미 본 카드: `{component.listing-card-visited}` — 모든 글자 `{colors.placeholder}`.

**가격 표기 규칙** — 다방과 같이 만원 단위. 월세 `월세 {보증금}/{월세}`(예: 월세 1억2000/39), 전세 `전세 {금액}`, 하숙 `하숙 {월 금액}` + "식사 포함" 태그.

**`tag-verified`** — 다방 "플러스" 태그 자리. 높이 20px, 패딩 0 × 4px, `{rounded.xs}`, `{typography.caption-strong}`, 배경 `{colors.primary-tint}`, 글자 `{colors.primary}`. "학교메일 인증", "직거래".

**`tag-women-only`** — 같은 모양, 배경 `{colors.women-tint}`, 글자 `{colors.women-ink}`. "여성전용".

**`like-toggle`** — 썸네일 위 24px 하트. 기본은 흰 아웃라인, 찜하면 `{component.like-toggle-active}` — `{colors.like}`로 채움.

### Map

**`map-pin-cluster`** — 줌 아웃 상태의 지역 핀. 높이 30px, `{rounded.pill}`, 1px `{colors.primary}` 테두리, 흰 배경. 왼쪽에 `{component.map-pin-cluster-count}`(`{colors.primary}` 배경, 흰 `{typography.caption-strong}`, 패딩 6px), 오른쪽에 지역명 `{typography.caption}` `{colors.ink}` 좌우 8px. 예: `(52) 청파동`.

**`map-pin-listing`** — 줌 인 상태의 개별 매물 핀. 흰 배경, 1px `{colors.primary}` 테두리, `{rounded.xs}`, 가격 `{typography.caption-strong}` `{colors.primary}`, 아래 6px 꼬리. 선택되면 `{component.map-pin-selected}` — 배경 `{colors.primary}`, 흰 글자.

**`map-pin-campus`** — 숙명여대 위치. 32px 원, `{colors.primary-deep}` 배경, 흰 2px 테두리, 항상 표시되고 다른 핀보다 위. 정문 기준 도보 10분 반경을 `{colors.accent}` 10% 채움 + 1px 점선 원으로 표시.

**`map-control-button`** — 지도 오른쪽 세로 버튼(필터, 현재 위치, 숙대로 이동). 36 × 36px, 흰 배경, `{rounded.sm}`(6px), Map control 그림자.

**`map-location-label`** — 지도 하단 가운데에 지금 보이는 동네 이름("청파동"). 높이 40px, `{rounded.pill}`, 패딩 0 × 16px, Floating label 그림자.

### Listing Detail

**`detail-panel`** — 리스트 오른쪽에 열리는 400px 패널. 맨 위 "매물 {번호}" 제목줄, 사진 캐러셀, `{component.detail-id-bar}`, 그 아래 본문 패딩 24px × 20px.
- 가격 `{typography.price-lg}`(24px/700)
- 한 줄 소개 `{typography.body-lg}`
- 정보 표(방 종류 · 면적 · 층 · 관리비) `{typography.body}` `{colors.ink}`
- 옵션 태그 줄 `{component.tag-option}` — 배경 `{colors.surface-soft}`, 글자 `{colors.body}` 12px/700, 패딩 4px × 8px, `{rounded.xs}`, 간격 8px
- 조회·찜 수 `{typography.body}` `{colors.body-muted}`
- 숙박숙박 추가: 위치 지도 + "숙대 정문 도보 N분 · 후문 도보 N분"
- 하단 고정 CTA: `{component.button-outline}`(찜) + `{component.button-primary}`(채팅 문의)

**`detail-id-bar`** — 사진 바로 아래 40px 띠. 배경 `{colors.primary-deep}`, 흰 글자 "매물번호 59916787" + 복사 아이콘, 오른쪽에 "6일 전". 패딩 8px × 20px.

### Buttons

**`button-primary`** — 주요 액션("채팅 문의", "적용하기", "매물 등록"). 배경 `{colors.primary}`, 흰 글자 `{typography.body-strong}`, 높이 56px, 패딩 0 × 16px, `{rounded.xxs}`(2px). 다방의 "문자문의"·"적용하기"와 같은 치수입니다.
- 눌림: `{component.button-primary-pressed}` — `{colors.primary-pressed}`.
- 비활성: `{component.button-primary-disabled}` — 배경 `{colors.divider-soft}`, 글자 `{colors.placeholder}`.
- 포커스: `outline: 2px solid {colors.focus-ring}; outline-offset: 2px`.

**`button-outline`** — 보조 액션("더보기", "단지 정보 보러가기", "찜하기"). 흰 배경, 1px `{colors.hairline}`, 글자 `{colors.ink}` `{typography.body-strong}`, 높이 44px, 패딩 0 × 15px, `{rounded.xxs}`. 패널 폭에 꽉 차게(360px) 씁니다.

**`text-link`** — `{colors.accent}` `{typography.body}`, 밑줄 없음. "전체", "전체보기".

### Home

**`home-category-card`** — 홈 첫 화면 카테고리 타일. 흰 배경, 1px `{colors.divider-soft}`, `{rounded.lg}`(12px), 패딩 20px, 높이 178px. 제목 `{typography.card-title}`(20px/700), 설명 두 줄 `{typography.body}` `{colors.body-muted}`, 오른쪽 아래 일러스트. 방금 본 카테고리에는 `{component.recent-visit-chip}`(높이 21px, pill, 1px `{colors.disabled-border}`, Chip lift 그림자, "최근 방문" 12px/700). 3열 그리드, 간격 12px. 숙박숙박 카드: 원룸·투룸 / 하숙 / 쉐어하우스 / 양도 / 룸메이트.

**섹션 제목** — `{typography.section-title}`(24px/400, -0.5px). 지역명만 `{colors.primary}` 700. 예: "숙대 근처 **청파동**, 새로 올라온 방".

### Mobile

**`mobile-category-button`** — 지도 왼쪽 위 65 × 48px 버튼. 배경 `{colors.primary}`, 흰 아이콘 + "원룸" `{typography.caption-strong}`, `{rounded.xs}`, Floating bar 그림자. 누르면 카테고리 바텀시트.

**`mobile-search-bar`** — 카테고리 버튼 오른쪽, 높이 48px, 흰 배경, `{rounded.xs}`, Floating bar 그림자. 데스크톱의 pill 검색창과 달리 각진 모양입니다.

**`bottom-sheet`** — 아래에서 올라오는 시트. 흰 배경, 위쪽 모서리 `{rounded.sheet}`(16px), 뒤에 `{colors.dim}`. 상단 손잡이 36 × 4px `{colors.hairline}`. 리스트 시트는 세 단계(손잡이만 96px / 절반 / 전체), 필터 시트는 하단에 꽉 찬 `{component.button-primary}`("적용하기", 335 × 56px).

### Footer

**`footer`** — 배경 `{colors.footer-bg}`(#373737), 링크 `{typography.footer-link}` `{colors.footer-text}`(#AAAAAA, 대비 5.12:1). "개인정보처리방침"만 흰색 700. 패딩 48px × 20px.

## Do's and Don'ts

### Do
- 선택·주요 액션·지도 핀에는 `{colors.primary}`(Sookmyung Royal Blue #003087) 하나만 씁니다.
- 숙명여대 공식 색(#003087, #0072CE, #FFB500, #FF7D01)은 HEX 그대로 씁니다. 가이드가 색 임의 변경을 금지합니다.
- 리스트 카드에서 18px/700은 가격에만 씁니다.
- 정보 위계는 크기보다 회색 단계(#222 → #656565 → #757575)로 먼저 만듭니다.
- 필터 칩·버튼·패널은 2px 각진 모양, 떠 있는 요소(검색창·핀·라벨·탭)는 pill로 구분합니다.
- 그림자는 지도 위에 떠 있는 요소에만 씁니다.
- 지도 첫 화면은 숙명여대를 중심에 두고, 캠퍼스 마커를 항상 보이게 합니다.
- 카드와 상세에 "숙대 정문 도보 N분"을 넣습니다.

### Don't
- 두 번째 강조색을 들이지 않습니다. 다방의 보라 "플러스"나 핑크 "새단장" 대신 블루 틴트·옐로 틴트를 씁니다.
- `{colors.placeholder}`(#979797)와 `{colors.like}`(#FF7D01)를 본문 텍스트에 쓰지 않습니다. 대비가 AA에 못 미칩니다.
- 500·600 굵기를 쓰지 않습니다. 400과 700뿐입니다.
- 리스트 카드나 상세 패널에 그림자·둥근 모서리를 넣지 않습니다.
- 숙명여대 로고·심볼을 앱 로고처럼 쓰지 않습니다. 학교 승인 전까지는 앱 자체 워드마크를 씁니다.
- 지도 위에 배너나 광고를 얹지 않습니다. 지도는 비워 둡니다.
- 작은 글자(16px 이하)에 음수 자간을 주지 않습니다.

## Responsive Behavior

### Breakpoints

| Name | Width | Key Changes |
|---|---|---|
| Mobile | < 768px | 다방은 `/mobile/map`으로 따로 보냄. 전체 화면 지도 + 플로팅 카테고리 버튼·검색창 + 오른쪽 컨트롤 + 바텀시트 리스트 |
| Tablet | 768–1023px | 헤더 유지, 카테고리 레일을 숨기고 헤더 아래 가로 탭으로. 리스트 360px + 지도 |
| Desktop | ≥ 1024px | 레일 70px + 리스트 400px + 지도. 상세는 리스트 옆 400px 패널 |
| Wide | ≥ 1440px | 지도만 넓어지고 레일·리스트·상세 폭은 고정 |

다방은 모바일을 별도 라우트(`/mobile/...`)로 나누지만, 숙박숙박은 한 라우트에서 CSS 브레이크포인트로 바꿉니다.

### Touch Targets
- 최소 44 × 44px. 다방의 지도 컨트롤(36px)은 데스크톱 기준이라, 모바일에서는 44px로 키웁니다.
- 모바일 카테고리 버튼(65 × 48px), 검색창(48px), 하단 CTA(56px)는 그대로 충분합니다.
- 필터 칩은 모바일에서 높이 36 → 40px.

### Collapsing Strategy
- **헤더:** 데스크톱 80px 헤더 → 모바일에서는 없애고 지도 위 플로팅 검색창으로.
- **카테고리 레일:** 세로 레일 → 태블릿 가로 탭 → 모바일 `{component.mobile-category-button}` + 바텀시트.
- **필터바:** 가로 칩 줄 → 모바일에서는 오른쪽 필터 버튼 하나 + 필터 바텀시트(하단 "적용하기").
- **리스트:** 400px 왼쪽 패널 → 모바일 바텀시트(3단계).
- **상세:** 리스트 옆 400px 패널 → 모바일 전체 화면 페이지, 하단 고정 CTA.
- **푸터:** 모바일 지도 화면에서는 숨기고 마이 탭 안으로.

### Image Behavior
- 리스트 썸네일은 모든 크기에서 정사각형. 모바일 바텀시트에서는 112px로 줄입니다.
- 상세 사진은 패널(또는 화면) 폭에 꽉 차게, 4:3.
- `next/image`로 lazy-load, 첫 화면 썸네일 몇 장만 eager.

## Iteration Guide

1. 한 번에 컴포넌트 하나씩. YAML 키(`{component.listing-card}`, `{component.filter-chip-applied}`)로 직접 가리킵니다.
2. 상태 변형(`-open`, `-applied`, `-selected`, `-visited`, `-pressed`, `-disabled`)은 `components:`에 별도 항목으로 둡니다.
3. HEX를 코드에 직접 쓰지 않고 `{token}` 참조만 씁니다.
4. 호버는 문서화하지 않습니다. 기본·선택·눌림·비활성 상태만 적습니다. (예외: `{colors.primary-hover}`는 데스크톱 버튼용 토큰으로만 둠)
5. 가격은 언제나 `{typography.price}` 또는 `{typography.price-lg}`. 다른 글자를 18px/700 이상으로 키우지 않습니다.
6. 새 강조가 필요하면 색을 늘리기 전에 `{colors.primary-tint}` 배경이나 회색 단계로 먼저 해결합니다.
7. 학교 관련 정보(거리·인증)는 `{colors.accent}` 또는 `{colors.primary}` 계열로 통일합니다.

## Known Gaps

- 다방 매물 상세의 아래쪽 섹션(가격 상세표, 관리비 내역, 중개사 정보)은 한 개 매물에서만 확인했고 구조만 적었습니다.
- 입력 폼(매물 등록, 로그인)의 오류·검증 상태는 다방 웹에서 확인하지 않았습니다. `{colors.danger}`는 앱 전용 값입니다.
- 줌 인 상태의 개별 매물 핀은 이번 분석 줌 레벨(11)에서 나오지 않아 다방 실측값이 아닌 앱 설계값입니다.
- 태블릿 브레이크포인트는 다방에서 측정하지 않았고, 모바일 전환은 다방이 사용자 에이전트로 `/mobile` 라우트에 보내는 방식이라 정확한 너비 기준은 알 수 없습니다.
- 다크 모드는 다방 웹에 없어 정의하지 않았습니다.
- Primary 스케일 중 `#00449B`, `#00205C`, `#EEF4FB`, `#D6E4F5`, `#A9C8EC`, `#005BB0`은 숙명여대 공식 색 사이를 나눈 앱 전용 값입니다. 공식 값은 `#003087`, `#0072CE`, `#636569`, `#97999B`, `#FFB500`, `#FF7D01`, `#D9D9D6`입니다.
- 지도 타일 자체의 색(네이버/카카오 지도)은 지도 제공사 스타일이라 토큰으로 다루지 않습니다.
