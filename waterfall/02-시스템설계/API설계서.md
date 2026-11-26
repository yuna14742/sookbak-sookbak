# API 설계서

> 숙박숙박 Phase 2 시스템 설계 산출물이다. [SRS](../01-요구사항분석/요구사항명세서-SRS.md) v0.1 5.2의 엔드포인트 초안을 요청·응답 규격, 권한, 오류 코드, 요청 제한 수치까지 정했다. 근거는 SRS·[RTM](../01-요구사항분석/요구사항추적매트릭스-RTM.md)·[유스케이스 명세서](../01-요구사항분석/유스케이스명세서.md) v0.1, PRD.md v0.2, [시스템 아키텍처 설계서](시스템아키텍처설계서-SAD.md)(ADR-001~008), [데이터베이스 설계서](데이터베이스설계서.md), [화면 설계서](화면설계서.md), 2026-11-26 사용자 결정이다. 확인되지 않은 수치는 "초안", 결정되지 않은 사항은 "미결"로 표시하고 부록 C에 모았다.

| 항목 | 내용 |
|------|------|
| **프로젝트명** | 숙박숙박 (SookbakSookbak) |
| **문서 번호** | API-SOOKBAK-v0.1 |
| **문서 버전** | v0.1 (초안) |
| **작성일** | 2026-11-26 |
| **작성자** | 이유나 (기획) / Claude (초안 작성 지원) |
| **승인자** | 이유나 (기획 책임자) |
| **문서 상태** | 초안 (G2 검토 전) |

---

## 1. API 설계 원칙

API는 Next.js Route Handlers(`/api/v1`)로 만들고 Vercel 서울 리전에서 실행한다 (SAD ADR-002). 클라이언트는 숙박숙박 모바일 웹앱(PWA, SAD ADR-001) 하나다. 나중에 앱으로 포장해도 같은 API를 쓴다.

### 1.1 RESTful 설계 규칙

| 규칙 | 설명 | 예시 |
|------|------|------|
| 자원 중심 URL | URL은 자원(명사), 행위는 HTTP Method | `GET /posts` (O), `GET /getPosts` (X) |
| 복수형 사용 | 컬렉션 자원은 복수형 | `/posts`, `/chat-rooms`, `/interest-conditions` |
| 소문자 + 하이픈 | 경로는 소문자, 단어는 하이픈 | `/chat-rooms` (O), `/chatRooms` (X) |
| 계층 관계 표현 | 부모-자식은 경로로 | `/chat-rooms/{roomId}/messages` |
| 내 자원 | 로그인한 본인 자원은 `me` | `/users/me`, `/drafts/me`, `/verifications/me` |
| 필터/정렬/페이징 | Query Parameter | `?type=SALE&category=ONE_ROOM&sort=PRICE_ASC&cursor=…` |
| 행위 자원 | 상태 전이처럼 동사가 자연스러우면 하위 경로 | `POST /auth/kakao`, `PATCH /posts/{id}/status`, `POST /admin/verifications/{id}/approve` |
| 멱등한 토글 | 찜처럼 켜고 끄는 것은 `PUT`/`DELETE` | `PUT /posts/{id}/favorite` |
| 슬래시 규칙 | 후행 슬래시 미사용 | `/posts` (O), `/posts/` (X) |
| 서버가 최종 판단 | 권한·필수 항목·한도·계좌번호 차단은 화면에서 먼저 막아도 API에서 다시 검사 | SAD 2.2 |

### 1.2 버저닝 전략

| 항목 | 내용 |
|------|------|
| 방식 | URL Path 버저닝 (SRS NFR-010) |
| 현재 버전 | `v1` |
| URL 패턴 | `/api/v1/{resource}` (화면과 같은 도메인. 도메인은 미결 SAD-Q1) |
| 하위 호환성 | 필드 추가·선택 파라미터 추가는 같은 버전 유지, Breaking Change(8.2) 때만 `v2` |
| 지원 정책 | 웹앱이라 배포하면 모든 사용자가 새 화면을 받는다. 다만 열려 있던 화면·서비스 워커 캐시를 고려해 이전 버전은 새 버전 배포 후 최소 30일 유지 (초안) |

### 1.3 네이밍 규칙

| 대상 | 규칙 | 예시 |
|------|------|------|
| URL 경로 | kebab-case, 복수형 명사 | `/chat-rooms`, `/notification-settings` |
| Query Parameter | camelCase | `?monthlyCostMax=60&moveInBy=2027-03-01` |
| Request/Response Body | camelCase. DB 컬럼(snake_case)은 서버에서 변환 | `{ "dealStatus": "AVAILABLE", "publishedAt": "…" }` |
| 열거형 값 | UPPER_SNAKE_CASE, DB 설계서 4.2와 같은 값 | `ONE_ROOM`, `SHORT_STAY`, `EMAIL_VERIFIED` |
| 금액 | 만 원 단위 정수 (SRS 5.2.1) | `"deposit": 500`, `"monthlyRent": 45` |
| 날짜·시각 | 날짜는 `YYYY-MM-DD`, 시각은 ISO 8601 UTC(`Z`). KST 표시는 클라이언트 또는 서버의 표시용 문자열(`…Text`) | `"moveInDate": "2027-03-01"`, `"createdAt": "2026-11-26T01:20:00Z"` |
| 표시용 문자열 | `…Text` 접미사. 서버가 만들고 화면은 그대로 보여 준다 | `priceText`, `locationText` |
| Header | 표준 헤더 + `Idempotency-Key`, `X-Request-Id` | |
| 에러 코드 | UPPER_SNAKE_CASE | `VERIFICATION_REQUIRED`, `ACCOUNT_NUMBER_BLOCKED` |

### 1.4 변경 이력

| 버전 | 날짜 | 작성자 | 변경 내용 |
|------|------|--------|-----------|
| v0.1 | 2026-11-26 | 이유나 / Claude | 초안 작성. SRS 5.2 엔드포인트 확장(사용자·인증·글·임시 저장·업로드·주소·찜·채팅·차단·신고·관심 조건·알림·관리자), 카카오 로그인 + 자체 토큰(ADR-003), 인증 단계별 권한, 계좌번호 차단 오류, 요청 제한 수치, 웹앱(PWA) 웹 푸시 토큰 |
| v1.0 | [미정] | 이유나 | G2 검토 후 최종 승인 |

---

## 2. 인증/인가

### 2.1 인증 방식

| 방식 | 용도 | 전달 |
|------|------|------|
| Bearer Token (JWT) | 사용자 API 호출, Supabase Realtime 구독 | `Authorization: Bearer {accessToken}` |
| Refresh Token 쿠키 | 로그인 유지 (Access Token 재발급) | `sb_refresh` 쿠키 (HttpOnly, Secure, SameSite=Lax, Path=`/api/v1/auth`) |
| 카카오 OAuth 2.0 | 로그인·가입 (카카오 회원번호만 받음) | 2.3 |
| 가입 대기 토큰 | 카카오 확인 후 닉네임·약관 입력까지 (10분) | `POST /auth/signup` 본문 `signupToken` |
| 내부 작업 키 | pg_cron이 내부 작업 API 호출 | `Authorization: Bearer {CRON_SECRET}` (환경 변수, 저장소에 올리지 않음, SAD 4.5) |

비밀번호는 받지도 저장하지도 않는다 (AC-002-2). 외부 시스템용 API Key는 발급하지 않는다.

### 2.2 JWT 토큰 구조

#### Access Token

| 항목 | 내용 |
|------|------|
| 알고리즘 | HS256, 서명 키 `SUPABASE_JWT_SECRET` (환경 변수). 같은 토큰으로 Realtime 구독 시 RLS `auth.uid()`가 동작 (ADR-003) |
| 만료 | 1시간 (초안, NFR-004) |
| 저장 | 웹앱 메모리에만. localStorage·쿠키에 두지 않음 |
| Payload | `sub`(회원 ID, UUID), `role`(`authenticated` 고정, Supabase 규칙), `aud`(`authenticated`), `sid`(로그인 세션 ID), `iat`, `exp` |
| 넣지 않는 것 | 닉네임·이메일·인증 단계·관리자 여부. 인증 단계와 정지 여부는 요청마다 DB `users.status`로 판단 (승인·정지가 바로 반영되도록) |

```json
{
  "sub": "3f1c2a90-6c1e-4d8e-9b55-2f7a0d1e8c44",
  "role": "authenticated",
  "aud": "authenticated",
  "sid": "b7a5e3d2-0f4c-4a61-8f0e-1d2c3b4a5e6f",
  "iat": 1795656000,
  "exp": 1795659600
}
```

#### Refresh Token

| 항목 | 내용 |
|------|------|
| 형식 | 무작위 256비트 문자열 (JWT 아님). DB `auth_sessions`에는 SHA-256 해시만 저장 |
| 만료 | 마지막 사용 후 30일 (초안, NFR-004) |
| 전달 | `Set-Cookie: sb_refresh=…; HttpOnly; Secure; SameSite=Lax; Path=/api/v1/auth; Max-Age=2592000`. 화면 코드(JavaScript)가 읽을 수 없음 |
| 갱신 정책 | 쓸 때마다 새 토큰으로 교체(Rotation). 이미 교체된 토큰이 다시 오면 탈취로 보고 그 세션 계열 전체를 폐기 → `REFRESH_TOKEN_REUSED` |
| 폐기 | 로그아웃, 탈퇴, 영구 정지, 7일 정지 시작 시 해당 회원 세션 전부 |

### 2.3 카카오 로그인 플로우

```
웹앱                       숙박숙박 API                      카카오
  |  1. state 생성(세션 저장소)  |                               |
  |---- 2. 카카오 인가 화면으로 이동 (client_id, redirect_uri, state) ---->|
  |<--- 3. /start/callback?code&state ----------------------------------|
  |  4. state 일치 확인            |                               |
  |-- 5. POST /auth/kakao {code, redirectUri} -->|                 |
  |                              |-- 6. 토큰 교환 (REST 키·Client Secret) -->|
  |                              |<- 7. 카카오 토큰 ----------------|
  |                              |-- 8. GET /v2/user/me (회원번호만) ------>|
  |                              |<- 9. id ------------------------|
  |                              | 10. 카카오 토큰 버림              |
  |                              | 11. 가입된 회원번호인지 확인        |
  |<- 12a. LOGGED_IN + accessToken + Set-Cookie(refresh) --|       |
  |<- 12b. SIGNUP_REQUIRED + signupToken(10분) -------------|       |
  |-- 13. POST /auth/signup {signupToken, nickname, agreements} -->|
  |<- 14. 201 + accessToken + Set-Cookie(refresh) ---------|       |
```

- 카카오 앱 키(REST API 키, Client Secret)는 서버 환경 변수에만 둔다. 웹앱에 들어가는 키는 도메인 제한된 JavaScript 키(`NEXT_PUBLIC_KAKAO_JS_KEY`, 지도용)뿐이다 (SAD 4.5).
- 카카오에서 받는 정보는 회원번호로 제한한다 (FR-001-2). 카카오 토큰은 DB에 저장하지 않는다.
- 탈퇴 후 30일이 안 된 카카오 계정, 영구 정지된 카카오 계정은 11단계에서 막는다 (`SIGNUP_BLOCKED`).
- 홈 화면에서 실행한 PWA(iOS)에서 카카오 로그인 후 돌아오는 동작은 상세 설계에서 실제 기기로 시험한다 (SAD-Q3).

### 2.4 인가 (Authorization)

권한은 Access Token의 `sub`로 DB에서 읽은 `users.status`와 `users.role`로 판단한다. 아래 "최소 단계"보다 낮으면 403 `VERIFICATION_REQUIRED`와 `requiredLevel`을 돌려주어 화면이 알맞은 안내(학교 메일 인증 / 학생증 인증)를 띄우게 한다 (SRS 5.2.3).

| 단계 (`requiredLevel`) | 해당 `users.status` | 할 수 있는 것 (FR-004) |
|------------------------|---------------------|------------------------|
| `GUEST` | 로그인 안 함 | 홈 목록 구경(첫 화면, 최신순, 필터 없음) |
| `LOGGED_IN` | `UNVERIFIED` 이상 | 비회원과 같음 + 내 정보, 학교 메일 인증 요청 |
| `EMAIL_VERIFIED` | `EMAIL_VERIFIED`, `PENDING_REVIEW`, `MEMBER`, `RESTRICTED` | 글 상세, 찜, 검색·필터·정렬, 관심 조건, 알림, 글 신고, 차단, 채팅 목록 |
| `MEMBER` | `MEMBER` | 글쓰기·수정, 채팅방 열기, 메시지 보내기, 채팅 상대 신고 |
| `ADMIN` | `role = ADMIN` | `/admin/*` |

| 규칙 | 내용 |
|------|------|
| 정지 | `SUSPENDED`는 모든 API에서 403 `ACCOUNT_SUSPENDED` (정지 종료 시각 포함). 로그아웃·내 정보 조회·탈퇴만 허용 |
| 권한 제한 | `RESTRICTED`는 기존 채팅방 읽기만 가능. 메시지 전송·글쓰기는 403 `VERIFICATION_REQUIRED`(`requiredLevel: MEMBER`, `reason: REVERIFY`) |
| 탈퇴 | `WITHDRAWN`은 로그인 불가 (401 `ACCOUNT_WITHDRAWN`) |
| 자원 소유 | 글 수정·삭제·상태 변경은 작성자만. 다른 사람이면 403 `NOT_RESOURCE_OWNER` |
| 채팅방 | 참여자(작성자·문의자)만 조회. 아니면 404 `CHAT_ROOM_NOT_FOUND` (존재 여부를 숨김) |
| 비공개 글 | `HIDDEN`·`PRIVATE`·`DELETED` 글은 작성자·관리자 외에는 404 `POST_NOT_FOUND` |
| 차단 | 차단 관계에서는 채팅방 열기·메시지 전송이 403 `USER_BLOCKED` |
| 관리자 | 일반 가입 경로로 만들 수 없고, 운영자가 DB에서 `role`을 지정 (NFR-004) |

---

## 3. 공통 규격

### 3.1 요청 포맷

#### 공통 요청 헤더

| 헤더 | 필수 | 설명 | 예시 |
|------|------|------|------|
| `Content-Type` | 본문이 있을 때 | `application/json` 또는 `multipart/form-data`(업로드·학생증) | `application/json; charset=utf-8` |
| `Authorization` | 인증 API | Bearer Access Token | `Bearer eyJhbGciOi…` |
| `Accept-Language` | 아니요 | 메시지 언어. MVP는 `ko`만 | `ko` |
| `X-Request-Id` | 아니요 | 클라이언트 요청 ID(UUID). 없으면 서버가 만들고 응답 헤더와 로그에 남김 | `5b0e…` |
| `Idempotency-Key` | 글 등록에 필수 | 같은 요청 중복 방지. 24시간 동안 같은 키는 첫 응답을 그대로 돌려줌 (FR-007-6) | UUID |

### 3.2 응답 포맷

SRS 5.2.3 형식을 따른다.

#### 단일 자원 응답

```json
{
  "success": true,
  "data": {
    "id": "8d2e4b10-…",
    "type": "SALE",
    "title": "숙대입구역 3분 원룸 양도해요"
  }
}
```

#### 목록 응답 (커서 기반 페이지네이션)

무한 스크롤에 맞춰 커서 기반을 기본으로 쓴다 (SRS 5.2.3). 전체 개수가 필요한 화면("매물 N개")은 `GET /posts/count`를 따로 부른다.

```json
{
  "success": true,
  "data": [ { "id": "…" }, { "id": "…" } ],
  "meta": {
    "nextCursor": "eyJwIjoiMjAyNi0xMS0yNlQwMToyMDowMFoiLCJpIjoiOGQyZSJ9",
    "limit": 20
  }
}
```

#### 페이지네이션 요청 파라미터

| 파라미터 | 타입 | 기본값 | 설명 |
|----------|------|--------|------|
| `cursor` | String | 없음 | 이전 응답의 `meta.nextCursor`. 없으면 첫 페이지 |
| `limit` | Integer | 20 | 1~50. 채팅 메시지는 기본 30 |

- 커서는 정렬 키와 ID를 묶은 불투명 문자열(Base64url JSON)이다. 클라이언트는 해석하지 않는다.
- `nextCursor`가 `null`이면 마지막 페이지다.
- 커서가 망가졌거나 정렬·필터가 바뀐 뒤의 커서면 400 `INVALID_CURSOR`.
- 관리자 대기열처럼 페이지 번호가 필요한 화면도 MVP는 커서로 통일한다.

#### 정렬

| 값 | 의미 | 기준 (DB 설계서 3.5 인덱스) |
|----|------|------------------------------|
| `LATEST` (기본) | 최신순 | `published_at DESC, id DESC`. 거래완료·구함완료는 아래로 (FR-006-2) |
| `PRICE_ASC` | 낮은 가격순 | `monthly_cost ASC`. 단기숙박 탭(`category=SHORT_STAY`)은 `stay_price ASC` (DB-Q4) |
| `FAVORITES` | 찜 많은순 | `favorite_count DESC, id` |

거리순은 없다 (EX-005). 비회원·인증 전 회원은 `LATEST`만 쓸 수 있다.

#### 필터링

필터 파라미터는 이메일 인증 회원 이상만 쓸 수 있다. 비회원이 보내면 403 `VERIFICATION_REQUIRED`(`requiredLevel: EMAIL_VERIFIED`) (AC-004-2). 목록은 5.3 참조.

### 3.3 에러 응답 포맷

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "입력 내용을 다시 확인해 주세요",
    "requiredLevel": null,
    "details": [
      { "field": "photos", "message": "화장실 사진을 1장 이상 올려 주세요" },
      { "field": "floor", "message": "해당 층은 전체 층보다 높을 수 없어요" }
    ],
    "retryAfter": null,
    "requestId": "5b0e9c7a-…"
  }
}
```

| 필드 | 설명 |
|------|------|
| `code` | 6장 오류 코드. 화면은 이 값으로 분기한다 |
| `message` | 사용자에게 그대로 보여 줄 수 있는 한국어 문장 (해요체, DESIGN.md 문구 규칙) |
| `requiredLevel` | 권한 부족(403)일 때 필요한 단계 (`EMAIL_VERIFIED` / `MEMBER`) |
| `details` | 필드별 오류 (`field`는 요청 본문의 camelCase 경로, 배열은 `photos[2]`) |
| `retryAfter` | 429일 때 다시 요청할 수 있는 시각 (ISO 8601). `Retry-After` 헤더(초)도 함께 보냄 |
| `requestId` | 문의·로그 추적용 |

- 서버 내부 오류(500)에는 스택·SQL·외부 업체 응답을 넣지 않는다. Sentry에만 남긴다 (SAD 6.2).
- 개인정보(실명·학번·학교 이메일·주소·카카오 회원번호)는 오류 메시지에도 넣지 않는다.

### 3.4 HTTP 상태 코드 사용 규칙

| 코드 | 의미 | 사용 상황 |
|------|------|-----------|
| 200 OK | 성공 | 조회, 수정, 로그인(`POST /auth/kakao`) |
| 201 Created | 생성 성공 | 가입, 글 등록, 채팅방 새로 열기, 메시지 전송, 신고 |
| 204 No Content | 성공, 본문 없음 | 삭제, 로그아웃, 찜 해제, 차단 해제 |
| 400 Bad Request | 형식·필드 오류 | 필수 누락, 범위 초과, 인증번호 불일치 |
| 401 Unauthorized | 인증 실패 | 토큰 없음·만료·위조, 가입 대기 토큰 만료 |
| 403 Forbidden | 권한 없음 | 인증 단계 부족, 정지, 작성자 아님, 차단 관계 |
| 404 Not Found | 자원 없음 | 없는 글, 숨김 글(다른 사람), 참여하지 않은 채팅방 |
| 409 Conflict | 상태·한도 충돌 | 닉네임 중복, 공개 글 한도, 이미 신고함, 허용되지 않는 상태 전이 |
| 413 Content Too Large | 파일 크기 초과 | 사진 10MB 초과 |
| 415 Unsupported Media Type | 파일 형식 | JPG·PNG·HEIC·WebP 외 |
| 422 Unprocessable Content | 정책 위반 내용 | 계좌번호가 든 메시지·사진, 금지 표현 |
| 429 Too Many Requests | 요청 제한 | 7장 수치 초과, 인증번호 60초·5회 잠금 |
| 500 Internal Server Error | 서버 오류 | 예상하지 못한 오류 |
| 502 Bad Gateway | 외부 서비스 오류 | 카카오·메일·OCR·주소 API 실패 (SRS 5.3 대체 동작 안내) |
| 503 Service Unavailable | 점검·과부하 | DB 연결 실패, 점검 중 |

---

## 4. API 엔드포인트 목록

Base URL: `https://{도메인}/api/v1` (도메인 미결). "최소 권한"은 2.4의 단계다.

### 4.1 인증 API (Auth)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| POST | `/auth/kakao` | 카카오 인가 코드로 로그인. 처음이면 가입 대기 토큰 (5.1) | 없음 | FR-001, FR-002 |
| POST | `/auth/signup` | 닉네임·약관 동의로 가입 (5.2) | 가입 대기 토큰 | FR-001 |
| POST | `/auth/refresh` | Access Token 재발급, Refresh Token 교체 | Refresh 쿠키 | FR-002 |
| POST | `/auth/logout` | 이 기기 세션 폐기, 이 기기 푸시 토큰 삭제 | 로그인 | FR-002 |

### 4.2 사용자·인증 API (Users, Verifications)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| GET | `/users/me` | 내 정보 (닉네임, 인증 단계, 학적 상태, 재인증 마감일, 공개 글 수·한도) | 로그인 | FR-002, FR-022 |
| PATCH | `/users/me` | 닉네임 변경 (30일 1회, 초안) | 로그인 | FR-022 |
| DELETE | `/users/me` | 탈퇴 (카카오 연결 끊기 포함, 글 숨김, 30일 후 파기) | 로그인 | FR-002 |
| GET | `/users/nickname-availability?nickname=` | 닉네임 사용 가능 여부 | 없음 (가입 화면) | FR-001 |
| GET | `/users/me/posts?status=` | 내 글 (공개·비공개·숨김 사유 포함) | 로그인 | FR-022 |
| POST | `/verifications/email-codes` | 학교 메일 인증번호 발송 (5.6) | 로그인 | FR-001 |
| POST | `/verifications/email-codes/verify` | 인증번호 확인 → `EMAIL_VERIFIED` (5.6) | 로그인 | FR-001 |
| POST | `/verifications` | 학생증·증명서 제출 (multipart, 첫 인증·재인증) | 이메일 인증 | FR-003, FR-005 |
| GET | `/verifications/me` | 내 인증 상태·반려 사유·재제출 가능 여부 | 이메일 인증 | FR-003, FR-022 |

### 4.3 게시글 API (Posts)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| GET | `/posts` | 판매·구함 목록·검색·필터·정렬 (5.3) | 없음 (필터·검색·정렬은 이메일 인증) | FR-006, FR-017 |
| GET | `/posts/count` | 같은 조건의 개수 ("매물 N개 보기") | 없음 (필터는 이메일 인증) | FR-017 |
| GET | `/posts/{postId}` | 글 상세 (5.8). 조회 수 집계 | 이메일 인증 | FR-013, FR-024 |
| POST | `/posts` | 판매·구함 글 등록 (5.4) | 정회원 | FR-007~011 |
| PATCH | `/posts/{postId}` | 글 수정 (부분 수정, 같은 검증) | 작성자 (정회원) | FR-007, FR-011 |
| PATCH | `/posts/{postId}/status` | 거래 상태 변경 | 작성자 | FR-012 |
| DELETE | `/posts/{postId}` | 글 삭제 (soft delete) | 작성자 | FR-007, FR-011 |
| POST | `/posts/{postId}/keep` | "아직 거래 가능해요" (방치 글 확인 응답, 60일 연장) | 작성자 | FR-012 |

### 4.4 임시 저장·업로드·주소·설정 API

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| GET | `/drafts/me?type=` | 임시 저장본 (판매·구함 각 1개) | 정회원 | FR-007 |
| PUT | `/drafts/me?type=` | 임시 저장 (덮어쓰기, 30일 보관) | 정회원 | FR-007 |
| DELETE | `/drafts/me?type=` | 임시 저장본 삭제 | 정회원 | FR-007 |
| POST | `/uploads/photos` | 사진 1장 업로드 (5.5). `purpose`: `POST`/`CHAT`/`PROFILE` | 정회원 | FR-007, FR-011, FR-015 |
| POST | `/addresses/resolve` | 주소 → 동네 이름(법정동) 확인. 좌표·주소는 응답에 안 넣음 | 정회원 | FR-010 |
| GET | `/settings/public` | 화면용 공개 설정 (숙대 기준 위치 목록, 분류, 옵션 코드, 한도 수치) | 없음 | FR-010-5, DEC-012 |

### 4.5 찜 API (Favorites)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| PUT | `/posts/{postId}/favorite` | 찜 (이미 찜이면 그대로 200) | 이메일 인증 | FR-014 |
| DELETE | `/posts/{postId}/favorite` | 찜 해제 | 이메일 인증 | FR-014 |
| GET | `/favorites?cursor=` | 찜 목록 (거래완료·숨김 글은 흐리게 표시용 상태 포함) | 이메일 인증 | FR-014 |

### 4.6 채팅 API (Chat)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| POST | `/chat-rooms` | 채팅방 열기 `{postId}`. 이미 있으면 기존 방 200, 새로 열면 201 | 정회원 | FR-015 |
| GET | `/chat-rooms?cursor=` | 채팅 목록 (상대 닉네임, 글 요약, 마지막 메시지, 안 읽은 수) | 이메일 인증 | FR-015 |
| GET | `/chat-rooms/{roomId}` | 채팅방 정보 (글 요약·상태, 상대, 차단 여부, 비개입 안내 표시 여부) | 참여자 | FR-015, FR-023 |
| GET | `/chat-rooms/{roomId}/messages?before=&after=&limit=` | 메시지 조회. `before`는 과거 더 보기, `after`는 재연결 후 놓친 메시지 동기화 | 참여자 | FR-015, NFR-003 |
| POST | `/chat-rooms/{roomId}/messages` | 메시지 전송 (텍스트 또는 사진, 5.7) | 참여자 + 정회원 | FR-015 |
| PATCH | `/chat-rooms/{roomId}/read` | 읽음 처리 `{lastReadMessageId}` | 참여자 | FR-015 |
| (WSS) | Supabase Realtime `postgres_changes` on `chat_messages` (`room_id=eq.{roomId}`) | 새 메시지 수신. Access Token으로 구독, RLS가 참여자만 허용 (ADR-004) | 참여자 | FR-015, NFR-001 |

### 4.7 차단·신고 API (Blocks, Reports)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| GET | `/blocks` | 차단 목록 | 이메일 인증 | FR-016 |
| POST | `/blocks/{userId}` | 차단 (이미 차단이면 200) | 이메일 인증 | FR-016 |
| DELETE | `/blocks/{userId}` | 차단 해제 | 이메일 인증 | FR-016 |
| POST | `/reports` | 글 신고 / 채팅 상대 신고 / 송금 요구 신고 (5.9) | 이메일 인증 (채팅 상대는 정회원·참여자) | FR-018 |

### 4.8 관심 조건·알림 API (Interest, Notifications)

| Method | Endpoint | 설명 | 최소 권한 | 관련 FR |
|--------|----------|------|-----------|---------|
| GET | `/interest-conditions` | 내 관심 조건 (최대 5개) | 이메일 인증 | FR-021 |
| POST | `/interest-conditions` | 관심 조건 저장. 이름이 없으면 서버가 자동 생성 | 이메일 인증 | FR-021 |
| PATCH | `/interest-conditions/{id}` | 이름·조건·알림 켜기 수정 | 이메일 인증 | FR-021 |
| DELETE | `/interest-conditions/{id}` | 삭제 | 이메일 인증 | FR-021 |
| GET | `/notifications?cursor=` | 알림 목록 (90일, 초안) + 안 읽은 수 | 이메일 인증 | FR-020 |
| PATCH | `/notifications/read` | 읽음 처리 `{ids}` 또는 `{all: true}` | 이메일 인증 | FR-020 |
| GET | `/notification-settings` | 알림 설정 | 이메일 인증 | FR-020, FR-021 |
| PUT | `/notification-settings` | 알림 설정 저장 (채팅·찜한 글·관심 매물, 야간 관심 매물 끄기) | 이메일 인증 | FR-020, FR-021 |
| PUT | `/devices/push-token` | 웹 푸시 토큰 등록·갱신 `{token, platform: "WEB"}` | 로그인 | FR-020 |
| DELETE | `/devices/push-token` | 이 기기 푸시 토큰 삭제 (알림 끄기) | 로그인 | FR-020 |

웹앱(PWA, SAD ADR-001)이므로 지금은 `platform`이 항상 `WEB`이다. 토큰은 Firebase JS SDK가 서비스 워커로 발급한다. iOS는 홈 화면에 추가한 뒤에만 토큰을 받을 수 있다 (화면 설계서 1.3).

### 4.9 관리자 API (Admin)

모든 관리자 API는 `role = ADMIN`만 호출할 수 있고, 처리 결과는 `audit_logs`에 남긴다 (NFR-006).

| Method | Endpoint | 설명 | 관련 FR |
|--------|----------|------|---------|
| GET | `/admin/verifications?status=PENDING&cursor=` | 인증 대기열 (오래된 순) | FR-019 |
| GET | `/admin/verifications/{id}` | 제출 자료 (학생증 이미지는 5분짜리 서명 URL) | FR-019 |
| POST | `/admin/verifications/{id}/approve` | 승인 `{academicStatus, studentNo, graduatedAt?}`. 학번은 HMAC만 저장 후 원본 파일 즉시 삭제 | FR-003, FR-019 |
| POST | `/admin/verifications/{id}/reject` | 반려 `{reason, memo?}`. 원본 파일 즉시 삭제 | FR-003, FR-019 |
| GET | `/admin/reports?status=RECEIVED&cursor=` | 신고 대기열 | FR-019 |
| GET | `/admin/reports/{id}` | 신고 상세 (글 스냅샷, 송금 요구 신고면 해당 메시지 앞뒤 20개) | FR-019 |
| POST | `/admin/reports/{id}/resolve` | 처리 `{result: ACTIONED / NO_ACTION, memo}` | FR-019 |
| POST | `/admin/posts/{id}/hide` | 글 숨김 `{reason}` | FR-019 |
| POST | `/admin/posts/{id}/restore` | 숨김 해제 (신고 수 초기화) | FR-019 |
| GET | `/admin/users/{id}` | 회원 정보 (닉네임, 상태, 신고·제재 이력. 실명·학번 원문 없음) | FR-019 |
| POST | `/admin/users/{id}/sanctions` | 제재 `{type: WARNING / SUSPEND_7D / PERMANENT, reason}` | FR-019 |
| GET | `/admin/settings/{key}` | 운영 설정값 조회 | FR-010-5, NFR-009 |
| PUT | `/admin/settings/{key}` | 운영 설정값 변경 (숙대 기준 위치, 한도, 계좌번호 패턴 등) | FR-010-5, NFR-009 |

### 4.10 내부·상태 확인 API

외부에 공개하지 않는 경로다. 목록은 SAD 7장 예약 작업 표를 따른다.

| Method | Endpoint | 설명 | 인증 |
|--------|----------|------|------|
| POST | `/api/internal/jobs/{jobName}` | 예약 작업 실행 (푸시 발송, 관심 매물 묶음, 재인증 안내·만료, 방치 글, 완료 30일 숨김, 파기) | `CRON_SECRET` |
| GET | `/api/health` | 앱 상태 (업타임 모니터) | 없음 |
| GET | `/api/health/db` | DB 연결 확인 (버전·시각만, 데이터 없음) | 없음 |

---

## 5. API 상세 명세

대표 API만 상세히 적는다. 나머지는 같은 규칙(3장)을 따르며, 구현 시 Zod 스키마에서 OpenAPI 문서를 만든다 (부록 A).

### 5.1 POST /api/v1/auth/kakao - 카카오 로그인

| 항목 | 내용 |
|------|------|
| **설명** | 카카오 인가 코드로 본인 확인. 가입된 회원이면 로그인, 처음이면 가입 대기 토큰을 준다 |
| **인증** | 불필요 |
| **관련 요구사항** | FR-001, FR-002, AC-002-2, NFR-004 |
| **Rate Limit** | IP당 10회/분 (7.2) |

#### Request Body

```json
{
  "code": "카카오가 돌려준 인가 코드",
  "redirectUri": "https://{도메인}/start/callback"
}
```

| 필드 | 타입 | 필수 | 검증 규칙 | 설명 |
|------|------|------|-----------|------|
| `code` | String | Y | 1~512자 | 카카오 인가 코드 (1회용) |
| `redirectUri` | String | Y | 서버에 등록된 값과 정확히 일치 | 카카오 토큰 교환에 필요 |

`state` 값은 웹앱이 인가 화면으로 보내기 전에 만들어 두고 콜백에서 직접 비교한다. 일치하지 않으면 이 API를 부르지 않는다.

#### Response Body - 성공, 기존 회원 (200 OK)

`Set-Cookie: sb_refresh=…; HttpOnly; Secure; SameSite=Lax; Path=/api/v1/auth; Max-Age=2592000`

```json
{
  "success": true,
  "data": {
    "result": "LOGGED_IN",
    "accessToken": "eyJhbGciOiJIUzI1NiIs…",
    "expiresIn": 3600,
    "user": {
      "id": "3f1c2a90-…",
      "nickname": "청파동눈송이",
      "status": "EMAIL_VERIFIED",
      "role": "USER"
    }
  }
}
```

#### Response Body - 성공, 처음 온 카카오 계정 (200 OK)

```json
{
  "success": true,
  "data": {
    "result": "SIGNUP_REQUIRED",
    "signupToken": "eyJ…",
    "signupTokenExpiresIn": 600
  }
}
```

`signupToken`은 카카오 회원번호를 담아 서버 키로 서명한 10분짜리 토큰이다. 회원번호 자체는 응답에 넣지 않는다.

#### Response Body - 실패

| 상황 | 상태 | `code` | `message` |
|------|------|--------|-----------|
| 코드 만료·재사용 | 400 | `KAKAO_CODE_INVALID` | 카카오 로그인을 완료하지 못했어요. 다시 시도해 주세요 |
| 탈퇴 30일 이내 / 영구 정지 계정 | 403 | `SIGNUP_BLOCKED` | 지금은 이 카카오 계정으로 가입할 수 없어요 |
| 카카오 서버 오류 | 502 | `KAKAO_UNAVAILABLE` | 카카오 로그인이 잠시 안 돼요. 잠시 후 다시 시도해 주세요 |

---

### 5.2 POST /api/v1/auth/signup - 가입

| 항목 | 내용 |
|------|------|
| **설명** | 닉네임과 약관 동의로 계정을 만든다. 상태는 `UNVERIFIED` |
| **인증** | `signupToken` (본문) |
| **관련 요구사항** | FR-001, AC-001-6, BP-DEAL-004 |
| **Rate Limit** | IP당 10회/시간 |

#### Request Body

```json
{
  "signupToken": "eyJ…",
  "nickname": "청파동눈송이",
  "agreements": {
    "terms": true,
    "privacy": true,
    "ageOver14": true,
    "marketing": false
  }
}
```

| 필드 | 타입 | 필수 | 검증 규칙 | 설명 |
|------|------|------|-----------|------|
| `signupToken` | String | Y | 서명·만료(10분) 확인 | `POST /auth/kakao` 응답 |
| `nickname` | String | Y | 2~10자, 한글·영문·숫자, 중복 불가, 금지어 아님 | 다른 사용자에게 보이는 이름. 카카오 프로필 이름 사용 안 함 |
| `agreements.terms` | Boolean | Y | `true` | 이용약관 ("회사는 거래 당사자가 아니며 중개하지 않는다" 포함) |
| `agreements.privacy` | Boolean | Y | `true` | 개인정보 수집·이용 |
| `agreements.ageOver14` | Boolean | Y | `true` | 만 14세 이상 |
| `agreements.marketing` | Boolean | N | - | 선택 |

#### Response Body - 성공 (201 Created)

`Set-Cookie: sb_refresh=…` (5.1과 같음)

```json
{
  "success": true,
  "data": {
    "accessToken": "eyJhbGciOiJIUzI1NiIs…",
    "expiresIn": 3600,
    "user": {
      "id": "3f1c2a90-…",
      "nickname": "청파동눈송이",
      "status": "UNVERIFIED",
      "role": "USER",
      "createdAt": "2026-11-26T01:20:00Z"
    },
    "next": "EMAIL_VERIFICATION"
  }
}
```

#### Response Body - 실패

| 상황 | 상태 | `code` | `details` |
|------|------|--------|-----------|
| 가입 대기 토큰 만료 | 401 | `SIGNUP_TOKEN_EXPIRED` | - (화면은 S1로 돌아가 다시 카카오 로그인) |
| 닉네임 형식 | 400 | `VALIDATION_ERROR` | `{ "field": "nickname", "message": "닉네임은 2~10자 한글·영문·숫자로 정해 주세요" }` |
| 닉네임 중복 | 409 | `NICKNAME_TAKEN` | `{ "field": "nickname", "message": "이미 쓰고 있는 닉네임이에요" }` |
| 필수 약관 미동의 | 400 | `VALIDATION_ERROR` | `{ "field": "agreements.terms", … }` |
| 같은 카카오 계정 동시 가입 | 409 | `ALREADY_REGISTERED` | - (화면은 로그인으로 처리) |

---

### 5.3 GET /api/v1/posts - 판매·구함 목록

| 항목 | 내용 |
|------|------|
| **설명** | 홈 목록, 분류 탭, 검색, 필터, 정렬. 공개(`PUBLIC`) 글만, 차단한·차단당한 사용자 글 제외 |
| **인증** | 선택 (필터·검색·정렬은 이메일 인증 회원 이상) |
| **관련 요구사항** | FR-006, FR-017, AC-004-2, AC-006-1~5, AC-017-1~4 |
| **응답 시간 목표** | p95 500ms 이하 (NFR-001) |
| **캐싱** | 비회원 첫 페이지(필터 없음)만 CDN 30초 캐시 (`s-maxage=30, stale-while-revalidate=60`). 로그인 응답은 `private, no-store` |

#### Query Parameters

| 파라미터 | 타입 | 필수 | 기본값 | 설명 | 권한 |
|----------|------|------|--------|------|------|
| `type` | Enum | N | `SALE` | `SALE` / `WANTED` | 전체 |
| `category` | Enum | N | 전체 | `post_category` 7개 중 하나. 구함은 `wanted_categories`에 포함된 글 | 전체 |
| `cursor` | String | N | - | 3.2 | 전체 |
| `limit` | Integer | N | 20 | 1~50 | 전체 |
| `sort` | Enum | N | `LATEST` | `LATEST` / `PRICE_ASC` / `FAVORITES` | 이메일 인증 |
| `q` | String | N | - | 키워드 2~30자. 제목·본문·동네·하숙 이름 부분 일치 (`pg_trgm`) | 이메일 인증 |
| `priceType` | Enum | N | - | `MONTHLY` / `JEONSE` / `STAY` | 이메일 인증 |
| `depositMax` | Integer | N | - | 보증금 상한 (만 원) | 이메일 인증 |
| `monthlyCostMin` / `monthlyCostMax` | Integer | N | - | 월 예상 비용 범위 (월세 + 관리비, 주 단위는 4.3배) | 이메일 인증 |
| `jeonseMax` | Integer | N | - | 전세금 상한 | 이메일 인증 |
| `stayPriceMax` | Integer | N | - | 숙박비 상한 | 이메일 인증 |
| `landmarks` | String (쉼표 구분) | N | - | 숙대 기준 위치 코드 (`app_settings.campus_landmarks`) | 이메일 인증 |
| `neighborhoods` | String (쉼표 구분) | N | - | 동네 이름 | 이메일 인증 |
| `moveInBy` | Date | N | - | 이 날짜까지 입주 가능 (즉시 입주 포함) | 이메일 인증 |
| `period` | Enum | N | - | `SHORT_STAY`(1~29일) / `SHORT_TERM`(30~183일) / `LONG` | 이메일 인증 |
| `features` | String (쉼표 구분) | N | - | `WOMEN_ONLY`, `PET_OK`, `ELEVATOR`, `PARKING`, `SECURITY`, `FULL_OPTION` (모두 만족) | 이메일 인증 |
| `roomStructure` | Enum | N | - | `OPEN` / `SEPARATED` / `DUPLEX` (원룸) | 이메일 인증 |
| `availableOnly` | Boolean | N | false | 거래가능·구하는 중만 | 이메일 인증 |

도보 시간·거리 파라미터는 없다 (EX-005). 알 수 없는 파라미터는 무시하고, 값이 잘못되면 400 `VALIDATION_ERROR`.

#### Response Body - 성공 (200 OK), 판매

```json
{
  "success": true,
  "data": [
    {
      "id": "8d2e4b10-…",
      "type": "SALE",
      "category": "ONE_ROOM",
      "title": "숙대입구역 근처 분리형 원룸 양도해요",
      "dealStatus": "AVAILABLE",
      "coverPhoto": {
        "url": "https://…/post-photos/8d2e…/0_thumb.webp",
        "width": 336,
        "height": 336
      },
      "priceText": "월세 500/45",
      "subPriceText": "관리비 7만",
      "categoryText": "원룸 · 분리형",
      "specText": "3층 / 5층 · 6.2평",
      "locationText": "청파동 · 도서관 후문 근처",
      "moveInText": "즉시 입주",
      "metaText": "2시간 전 · 채팅 3 · 찜 12",
      "badges": ["PRICE_CUT"],
      "isFavorited": false,
      "isMine": false,
      "publishedAt": "2026-11-26T01:20:00Z"
    }
  ],
  "meta": {
    "nextCursor": "eyJwIjoi…",
    "limit": 20
  }
}
```

| 필드 | 설명 |
|------|------|
| `priceText` | 월세 `월세 {보증금}/{월세}`, 주 단위 `주 {금액}만`, 전세 `전세 {금액}`(1억 이상은 `1억 2,000`), 숙박비 `1박 {금액}만` / `1주 {금액}만`, 협의 가능이면 끝에 ` · 협의` (FR-009) |
| `subPriceText` | 관리비 `관리비 {N}만` / `관리비 없음`. 하숙은 `식사 포함` 등 |
| `locationText` | `{동네} · {숙대 기준 위치} 근처`. 숙대 근처가 아니면 `{동네}`만. **건물 주소·도보 시간은 절대 넣지 않는다** (AC-006-4·5, AC-010-1) |
| `metaText` | 상대 시간 + 0이 아닌 채팅·찜 수 (FR-024) |
| `badges` | `PRICE_CUT`(인하 후 3일), `NEW`(24시간), `WOMEN_ONLY` |
| `isFavorited` / `isMine` | 로그인 사용자 기준. 비회원은 `false` |

표시용 문자열을 서버에서 만드는 이유: 가격 표기 규칙(FR-009)과 위치 공개 규칙(FR-010)을 한곳에서 지키고, 화면 설계서 5.4 카드 구성을 그대로 쓰기 위해서다. 원래 값(`deposit`, `monthlyRent` 등)은 상세(5.8)에만 준다.

#### Response Body - 성공 (200 OK), 구함

```json
{
  "success": true,
  "data": [
    {
      "id": "c41a…",
      "type": "WANTED",
      "title": "3월부터 1년 살 원룸 구해요",
      "dealStatus": "SEEKING",
      "categoryText": "원룸 · 투룸",
      "locationText": "청파동 · 1캠 후문",
      "budgetText": "보증금 500 이하 · 월 60 이하",
      "moveInText": "3월 1일부터 · 1년",
      "metaText": "2시간 전 · 채팅 1 · 찜 4",
      "isFavorited": false,
      "isMine": false,
      "publishedAt": "2026-11-26T01:20:00Z"
    }
  ],
  "meta": { "nextCursor": null, "limit": 20 }
}
```

#### Response Body - 실패 (403 Forbidden)

비회원이 필터·검색·정렬을 보냈을 때:

```json
{
  "success": false,
  "error": {
    "code": "VERIFICATION_REQUIRED",
    "message": "학교 메일 인증을 하면 검색과 필터를 쓸 수 있어요",
    "requiredLevel": "EMAIL_VERIFIED",
    "details": []
  }
}
```

---

### 5.4 POST /api/v1/posts - 판매·구함 글 등록

| 항목 | 내용 |
|------|------|
| **설명** | 판매 또는 구함 글을 등록한다. 사진은 먼저 `POST /uploads/photos`로 올리고 `uploadId`로 붙인다 |
| **인증** | 정회원 (`MEMBER`) |
| **관련 요구사항** | FR-007~FR-011, FR-023, AC-007-1~6, AC-008-1~4, AC-010-1~3, AC-011-3 |
| **Rate Limit** | 사용자당 10회/시간, 30회/일 |

#### Request Headers

| 헤더 | 값 | 필수 |
|------|-----|------|
| `Authorization` | `Bearer {accessToken}` | Y |
| `Content-Type` | `application/json` | Y |
| `Idempotency-Key` | UUID (글쓰기 화면을 열 때 만들고, 다시 보내도 같은 값) | Y |

#### Request Body - 판매 (원룸 예시)

```json
{
  "type": "SALE",
  "category": "ONE_ROOM",
  "title": "숙대입구역 근처 분리형 원룸 양도해요",
  "body": "2월 말 졸업이라 계약 승계할 분 찾아요. 집주인 동의 받았어요.",
  "price": {
    "priceType": "MONTHLY",
    "rentUnit": "MONTH",
    "deposit": 500,
    "monthlyRent": 45,
    "maintenanceFee": 7,
    "maintenanceIncludes": ["WATER", "INTERNET"],
    "negotiable": false
  },
  "location": {
    "roadAddress": "서울 용산구 청파로47길 00",
    "detailAddress": "302호",
    "campusLandmark": "LIB_BACK"
  },
  "room": {
    "floor": 3,
    "totalFloors": 5,
    "isRooftop": false,
    "areaM2": 20.5,
    "roomStructure": "SEPARATED",
    "options": ["AIRCON", "WASHER", "FRIDGE", "BED", "DESK"],
    "buildingFeatures": ["WOMEN_ONLY", "SECURITY"]
  },
  "moveIn": { "date": null, "immediate": true },
  "contract": {
    "form": "SUCCESSION",
    "landlordConsent": "YES",
    "endDate": "2027-08-31"
  },
  "photos": [
    { "uploadId": "u-01…", "kind": "ROOM" },
    { "uploadId": "u-02…", "kind": "ROOM" },
    { "uploadId": "u-03…", "kind": "BATHROOM" }
  ],
  "nonInterventionAgreed": true
}
```

| 필드 | 타입 | 필수 | 검증 규칙 | 설명 |
|------|------|------|-----------|------|
| `type` | Enum | Y | `SALE` / `WANTED` | |
| `category` | Enum | 판매 Y | 7개 분류 (아파트 없음, AC-008-1) | |
| `title` | String | Y | 1~40자, 연락처·계좌번호 패턴 금지 | |
| `body` | String | N | 0~2,000자, 연락처·계좌번호 패턴 금지 | |
| `price.priceType` | Enum | 판매 Y | 분류별 허용값 (DB `ck_posts_price_by_category`) | 하숙·쉐어·단기임대 `MONTHLY`, 단기숙박 `STAY` |
| `price.deposit` | Integer | 월세·전세 Y | 0~99,999 | 만 원 |
| `price.monthlyRent` | Integer | 월세 Y | 1~999 | 주 단위면 1주 금액 |
| `price.jeonsePrice` | Integer | 전세 Y | 1~99,999 | |
| `price.stayPrice` / `price.stayUnit` | Integer / Enum | 숙박비 Y | 1~999 / `NIGHT`·`WEEK` | |
| `price.maintenanceFee` | Integer | 판매 Y | 0~99 | "없음"은 0 + `["NONE"]` |
| `location.roadAddress` | String | 판매 Y | 우편번호 검색 화면에서 고른 도로명 주소 | **비공개.** `post_private_locations`에만 저장, 어떤 응답에도 안 나감 (ADR-005) |
| `location.detailAddress` | String | N | 0~30자 | 비공개 |
| `location.campusLandmark` | String | 판매 Y | `app_settings.campus_landmarks` 코드 또는 `NOT_NEAR` | |
| `room.floor` / `room.totalFloors` | Integer | 판매 Y | 반지하 -1, `floor <= totalFloors` | |
| `room.areaM2` | Number | 판매 Y | 1~200 | 평은 서버가 계산해 표시 |
| `room.roomStructure` | Enum | 원룸 Y | `OPEN`/`SEPARATED`/`DUPLEX` | |
| `room.roomCount` | Integer | 투룸 Y | 2 이상 | |
| `share` / `boarding` / `period` | Object | 분류별 Y | FR-008 표 (쉐어 인원, 하숙 이름·식사, 단기 기간 30~183일 / 1~29일) | |
| `selfResidenceConfirmed` | Boolean | 단기숙박 Y | `true` | 본인이 사는 방의 빈 기간 (FR-008-4a) |
| `contract.landlordConsent` | Enum | 승계·전대·단기 Y | `YES`/`NO`/`CHECKING` | |
| `photos` | Array | 판매 Y | 판매 2~10장, `ROOM` 1장 이상, `BATHROOM` 1장 이상 (AC-007-1·2). 구함 0~10장. 각 `uploadId`는 본인이 올린 `POST` 용도, 미사용 | 배열 순서 = 노출 순서, 첫 장이 대표 |
| `nonInterventionAgreed` | Boolean | 판매 Y | `true` | 거래 비개입 고지 동의 (FR-023) |

구함 글은 `wantedCategories`(1개 이상), `wantedLandmarks`·`wantedNeighborhoods`(합쳐 1개 이상), `budget.depositMax`·`budget.monthlyCostMax`(하나 이상), `moveIn`(날짜 또는 즉시), `wantedPeriodText`를 보낸다 (FR-011, DB `ck_posts_wanted_required`).

#### 서버 처리 순서

1. Zod 스키마로 형식·분류별 필수 항목 검사 → 필드별 오류를 한 번에 모아 400.
2. `Idempotency-Key`가 24시간 안에 쓰였으면 첫 응답을 그대로 돌려준다.
3. 주소를 카카오 로컬 API로 확인해 법정동(`neighborhood`)과 좌표를 얻는다. 좌표는 `post_private_locations`에만 저장하고, 무작위로 옮긴 표시 중심(`display_lat/lng`)을 한 번 정한다 (AC-010-3).
4. 트랜잭션: 작성자 행 잠금(`FOR UPDATE`) → 공개 판매 글 3건·구함 1건·단기숙박 1건 한도 확인 → 글·사진·위치 저장 → 업로드 상태 `ATTACHED`.
5. 커밋 후 관심 조건 매칭을 알림 대기열에 넣는다 (ADR-006).

#### Response Body - 성공 (201 Created)

`Location: /api/v1/posts/8d2e4b10-…`

```json
{
  "success": true,
  "data": {
    "id": "8d2e4b10-…",
    "type": "SALE",
    "dealStatus": "AVAILABLE",
    "visibility": "PUBLIC",
    "neighborhood": "청파동",
    "locationText": "청파동 · 도서관 후문 근처",
    "publishedAt": "2026-11-26T01:20:00Z",
    "publicPostCount": { "sale": 1, "saleLimit": 3 }
  }
}
```

#### Response Body - 실패

| 상황 | 상태 | `code` | 예시 `details` / 비고 |
|------|------|--------|----------------------|
| 필수 누락·범위 | 400 | `VALIDATION_ERROR` | `{ "field": "photos", "message": "화장실 사진을 1장 이상 올려 주세요" }` |
| 학생증 인증 전 | 403 | `VERIFICATION_REQUIRED` | `requiredLevel: MEMBER` |
| 재인증 미완료 | 403 | `VERIFICATION_REQUIRED` | `requiredLevel: MEMBER`, `details: [{ "field": "reason", "message": "REVERIFY" }]` |
| 판매 3건 초과 | 409 | `POST_LIMIT_EXCEEDED` | "공개 중인 판매 글은 3개까지예요. 다른 글을 거래완료로 바꾸거나 삭제해 주세요" |
| 구함 1건·단기숙박 1건 초과 | 409 | `POST_LIMIT_EXCEEDED` | `details`에 한도 종류 |
| 다른 사람의 업로드·이미 쓴 업로드 | 400 | `UPLOAD_INVALID` | `{ "field": "photos[1].uploadId" }` |
| 주소 확인 실패 | 400 | `ADDRESS_NOT_FOUND` | "주소를 다시 골라 주세요" |
| 주소 API 장애 | 502 | `ADDRESS_SERVICE_UNAVAILABLE` | 임시 저장 안내 (SRS 5.3) |
| 제목·본문에 연락처·계좌번호 | 422 | `CONTACT_INFO_NOT_ALLOWED` | 연락은 채팅으로 (BP) |

---

### 5.5 POST /api/v1/uploads/photos - 사진 업로드

| 항목 | 내용 |
|------|------|
| **설명** | 사진 1장을 올린다. 서버가 EXIF(위치 등)를 지우고 목록용(336px)·상세용(1280px) WebP를 만든다. 채팅 사진은 OCR로 계좌번호를 검사한다 |
| **인증** | 정회원 |
| **관련 요구사항** | FR-007, FR-011, FR-015, AC-015-5, NFR-005 |
| **Rate Limit** | 사용자당 60장/시간 |

Vercel 함수 실행 시간 제한 때문에 여러 장을 한 요청에 묶지 않고 1장씩 올린다 (ADR-002). 화면은 최대 3장을 동시에 올린다.

#### Request Headers

| 헤더 | 값 | 필수 |
|------|-----|------|
| `Authorization` | `Bearer {accessToken}` | Y |
| `Content-Type` | `multipart/form-data` | Y |

#### Request Body (multipart/form-data)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| `file` | File | Y | 사진 1장 |
| `purpose` | String | Y | `POST` / `CHAT` / `PROFILE` |
| `roomId` | String | `CHAT`이면 Y | 채팅방 ID (참여자 확인) |

#### 파일 제한

| 항목 | 제한 |
|------|------|
| 최대 크기 | 10MB |
| 허용 형식 | JPG, PNG, HEIC/HEIF, WebP (내용의 매직 바이트로 확인, 확장자만 믿지 않음) |
| 최소 해상도 | 짧은 변 400px 이상 (글 사진) |
| 저장 | `post-photos`·`chat-photos` 버킷, 추측할 수 없는 경로 (UUID). 원본은 저장하지 않고 변환본만 |
| 미사용 정리 | 24시간 안에 글·메시지에 붙지 않으면 삭제 (DB `media_uploads`) |

#### Response Body - 성공 (201 Created)

```json
{
  "success": true,
  "data": {
    "uploadId": "u-01…",
    "thumbUrl": "https://…/post-photos/…/thumb.webp",
    "detailUrl": "https://…/post-photos/…/detail.webp",
    "width": 1280,
    "height": 960,
    "expiresAt": "2026-11-27T01:20:00Z"
  }
}
```

#### Response Body - 실패

| 상황 | 상태 | `code` | `message` |
|------|------|--------|-----------|
| 10MB 초과 | 413 | `FILE_TOO_LARGE` | 사진은 한 장에 10MB까지 올릴 수 있어요 |
| 형식 | 415 | `UNSUPPORTED_FILE_TYPE` | JPG, PNG, HEIC 사진만 올릴 수 있어요 |
| 해상도 부족 | 400 | `IMAGE_TOO_SMALL` | 사진이 너무 작아요. 더 큰 사진을 골라 주세요 |
| 채팅 사진에 계좌번호 | 422 | `ACCOUNT_NUMBER_BLOCKED` | 사진에 계좌번호가 보여서 보낼 수 없어요. 숙박숙박은 앱 안에서 돈을 주고받지 않아요 |
| OCR 장애 | (통과) | - | 사진은 보내고 "송금 요구" 신고로 보완 (SAD 2.3, 초안). 서버 로그에 경고 |

---

### 5.6 학교 메일 인증 (POST /verifications/email-codes, /verify)

| 항목 | 내용 |
|------|------|
| **설명** | `@sookmyung.ac.kr` 메일로 6자리 인증번호를 보내고 확인한다. 성공하면 `EMAIL_VERIFIED` |
| **인증** | 로그인 (`UNVERIFIED`) |
| **관련 요구사항** | FR-001, AC-001-3·4, NFR-004 |

#### 발송 Request Body

```json
{ "email": "snow2026@sookmyung.ac.kr" }
```

| 필드 | 검증 규칙 |
|------|-----------|
| `email` | 이메일 형식, 도메인이 `sookmyung.ac.kr` (DB `ck_users_school_email`), 다른 계정에 연결되지 않음, 차단 식별자 아님 |

#### 발송 Response (200 OK)

```json
{
  "success": true,
  "data": {
    "expiresAt": "2026-11-26T01:30:00Z",
    "resendAvailableAt": "2026-11-26T01:21:00Z"
  }
}
```

#### 확인 Request Body / Response (200 OK)

```json
{ "email": "snow2026@sookmyung.ac.kr", "code": "482913" }
```

```json
{ "success": true, "data": { "status": "EMAIL_VERIFIED", "next": "STUDENT_ID_VERIFICATION" } }
```

#### 실패

| 상황 | 상태 | `code` | 비고 |
|------|------|--------|------|
| 학교 메일 아님 | 400 | `SCHOOL_EMAIL_REQUIRED` | "숙명여대 메일(@sookmyung.ac.kr)만 쓸 수 있어요" |
| 이미 다른 계정에 연결 | 409 | `EMAIL_ALREADY_USED` | 1이메일 1계정 |
| 60초 안에 재발송 | 429 | `RESEND_TOO_SOON` | `retryAfter` |
| 인증번호 불일치 | 400 | `INVALID_CODE` | `details: [{ "field": "code", "message": "인증번호가 맞지 않아요 (남은 횟수 3회)" }]` |
| 만료·재발송 전 번호 | 400 | `CODE_EXPIRED` | "인증번호가 만료됐어요. 다시 받아 주세요" |
| 5회 실패 잠금 | 429 | `CODE_LOCKED` | 30분, `retryAfter` (AC-001-4) |
| 메일 발송 실패 | 502 | `MAIL_UNAVAILABLE` | "메일을 보내지 못했어요. 잠시 후 다시 시도해 주세요" |

인증번호 원문은 DB·로그에 남기지 않는다. HMAC만 저장한다 (DB `email_verification_codes`).

---

### 5.7 POST /api/v1/chat-rooms/{roomId}/messages - 메시지 전송

| 항목 | 내용 |
|------|------|
| **설명** | 텍스트 또는 사진 메시지를 보낸다. 받는 쪽은 Realtime 구독으로 1초 안에 받는다 (NFR-001) |
| **인증** | 참여자 + 정회원 (`RESTRICTED`는 읽기만) |
| **관련 요구사항** | FR-015, FR-016, AC-015-3~7, NFR-003, ADR-004, ADR-007 |
| **Rate Limit** | 사용자당 30개/분, 방당 600개/일 |

#### Request Body

```json
{
  "clientMsgId": "0b6e8f3a-4c2d-4e1f-9a7b-1c2d3e4f5a6b",
  "kind": "TEXT",
  "body": "안녕하세요, 혹시 이번 주말에 방 볼 수 있을까요?"
}
```

```json
{
  "clientMsgId": "2a1f…",
  "kind": "PHOTO",
  "uploadIds": ["u-11…", "u-12…"]
}
```

| 필드 | 타입 | 필수 | 검증 규칙 |
|------|------|------|-----------|
| `clientMsgId` | UUID | Y | 화면이 만든 ID. 같은 값으로 다시 보내면 저장된 메시지를 그대로 돌려줌 (재전송 중복 방지) |
| `kind` | Enum | Y | `TEXT` / `PHOTO` |
| `body` | String | TEXT Y | 1~1,000자 |
| `uploadIds` | Array | PHOTO Y | 1~10개, 본인이 이 방에 올린 `CHAT` 업로드(이미 OCR 통과) |

#### 서버 처리

1. 참여자·정회원·차단 관계 확인.
2. 텍스트를 `app_settings.account_number_pattern` 규칙으로 검사 → 걸리면 **저장하지 않고** 422 (AC-015-4).
3. 송금 요청 표현(`app_settings.remittance_words`: "입금", "선입금", "계약금 먼저" 등)이 있으면 저장하되 `remittanceWarning: true` (AC-015-6).
4. 저장 → 채팅방 마지막 메시지 갱신 → 상대에게 `CHAT_MESSAGE` 알림 대기열 (같은 방 묶음).

#### Response Body - 성공 (201 Created)

```json
{
  "success": true,
  "data": {
    "id": "m-901…",
    "roomId": "r-55…",
    "senderId": "3f1c2a90-…",
    "kind": "TEXT",
    "body": "안녕하세요, 혹시 이번 주말에 방 볼 수 있을까요?",
    "photos": [],
    "remittanceWarning": false,
    "clientMsgId": "0b6e8f3a-…",
    "createdAt": "2026-11-26T01:20:00.412Z"
  }
}
```

#### Response Body - 실패 (422 Unprocessable Content)

```json
{
  "success": false,
  "error": {
    "code": "ACCOUNT_NUMBER_BLOCKED",
    "message": "계좌번호는 채팅으로 보낼 수 없어요. 돈은 직접 만나 계약할 때 주고받아 주세요",
    "requiredLevel": null,
    "details": [{ "field": "body", "message": "계좌번호로 보이는 숫자가 있어요" }]
  }
}
```

| 상황 | 상태 | `code` |
|------|------|--------|
| 권한 제한·인증 전 | 403 | `VERIFICATION_REQUIRED` |
| 차단 관계 | 403 | `USER_BLOCKED` |
| 참여하지 않은 방 | 404 | `CHAT_ROOM_NOT_FOUND` |
| 글이 삭제·숨김됨 | 409 | `POST_NOT_AVAILABLE` (기존 메시지 읽기는 가능) |
| 너무 빠름 | 429 | `RATE_LIMITED` |

#### 실시간 수신 (Supabase Realtime)

| 항목 | 내용 |
|------|------|
| 연결 | `supabase.realtime.setAuth(accessToken)` 후 채널 `room:{roomId}` 구독, `postgres_changes` `INSERT` on `public.chat_messages` filter `room_id=eq.{roomId}` |
| 권한 | RLS SELECT 정책이 참여자만 허용 (DB 설계서 `chat_messages`) |
| 토큰 만료 | Access Token 재발급 시 `setAuth`로 바꿈 |
| 놓친 메시지 | 재연결·앱 복귀 시 `GET …/messages?after={마지막 메시지 ID}` (NFR-003) |
| 순서 | `createdAt`, `id` 순. 내가 보낸 메시지는 `clientMsgId`로 낙관적 표시를 교체 |

---

### 5.8 GET /api/v1/posts/{postId} - 글 상세

| 항목 | 내용 |
|------|------|
| **인증** | 이메일 인증 회원 이상 (비회원·인증 전은 403 `VERIFICATION_REQUIRED`, 화면은 S1-a·S3 안내) |
| **관련 요구사항** | FR-013, FR-010, FR-024, AC-010-1~3, AC-013-1~4 |
| **조회 수** | 같은 사용자 하루 1회만 (DB `post_views`), 본인 글 제외 |

#### Response Body - 성공 (200 OK, 판매 일부)

```json
{
  "success": true,
  "data": {
    "id": "8d2e4b10-…",
    "type": "SALE",
    "category": "ONE_ROOM",
    "title": "숙대입구역 근처 분리형 원룸 양도해요",
    "body": "2월 말 졸업이라 …",
    "dealStatus": "AVAILABLE",
    "price": {
      "priceType": "MONTHLY", "rentUnit": "MONTH",
      "deposit": 500, "monthlyRent": 45,
      "maintenanceFee": 7, "maintenanceIncludes": ["WATER", "INTERNET"],
      "negotiable": false, "monthlyCost": 52,
      "priceText": "월세 500/45", "subPriceText": "관리비 7만 (수도·인터넷 포함)",
      "priceHistory": [{ "changedAt": "2026-11-24T03:00:00Z", "text": "월세 500/50 → 500/45" }]
    },
    "location": {
      "neighborhood": "청파동",
      "campusLandmark": "LIB_BACK",
      "locationText": "청파동 · 도서관 후문 근처",
      "map": { "centerLat": 37.5452, "centerLng": 126.9661, "radiusM": 150 }
    },
    "room": { "floorText": "3층 / 5층", "areaM2": 20.5, "areaPyeong": 6.2, "roomStructure": "SEPARATED", "options": ["AIRCON", "WASHER"], "buildingFeatures": ["WOMEN_ONLY"] },
    "moveIn": { "immediate": true, "text": "즉시 입주" },
    "contract": { "form": "SUCCESSION", "landlordConsent": "YES", "endDate": "2027-08-31" },
    "photos": [
      { "kind": "ROOM", "url": "https://…/detail.webp", "thumbUrl": "https://…/thumb.webp", "width": 1280, "height": 960, "alt": "원룸 방 사진" }
    ],
    "author": { "id": "a-77…", "nickname": "청파동눈송이", "verifiedBadge": "MEMBER", "joinedText": "2026년 3월 가입" },
    "counts": { "views": 128, "favorites": 12, "chats": 3 },
    "isFavorited": false,
    "isMine": false,
    "myChatRoomId": null,
    "publishedAt": "2026-11-26T01:20:00Z",
    "updatedAt": "2026-11-26T02:00:00Z"
  }
}
```

- `map.centerLat/Lng`는 무작위로 옮긴 표시 중심이다. 건물 좌표·도로명 주소·상세 주소는 작성자 본인에게도 상세 API로 주지 않고, 수정 화면용 `GET /posts/{id}?view=edit`(작성자만)에서만 준다 (AC-010-1).
- 작성자 실명·학번·학교 이메일은 어떤 응답에도 없다 (NFR-005).

---

### 5.9 POST /api/v1/reports - 신고

| 항목 | 내용 |
|------|------|
| **인증** | 이메일 인증 (채팅 상대 신고는 정회원·참여자) |
| **관련 요구사항** | FR-018, AC-018-1·2, AC-015-6 |
| **Rate Limit** | 사용자당 10회/일 |

```json
{
  "targetType": "POST",
  "postId": "8d2e4b10-…",
  "reason": "FAKE_LISTING",
  "detail": null
}
```

```json
{
  "targetType": "CHAT_USER",
  "roomId": "r-55…",
  "messageId": "m-903…",
  "reason": "REMITTANCE_REQUEST",
  "detail": "계약 전에 계약금 먼저 보내라고 했어요"
}
```

| 필드 | 검증 규칙 |
|------|-----------|
| `targetType` | `POST` / `CHAT_USER` |
| `reason` | DB `report_reason` 값. `OTHER`이면 `detail` 필수 (1~500자) |
| `postId` / `roomId` | 대상 종류에 맞게 필수. 자기 글·자기 자신 신고 불가 |

성공 201: `{ "success": true, "data": { "id": "…", "status": "RECEIVED" } }`. 같은 글 두 번 신고는 409 `ALREADY_REPORTED`. 서로 다른 3명이 신고하면 글은 바로 숨김 처리되지만, 신고자에게는 결과만 알린다 (신고 수·신고자 정보는 응답에 넣지 않음).

---

### 5.10 POST /api/v1/auth/refresh - 토큰 갱신

| 항목 | 내용 |
|------|------|
| **인증** | `sb_refresh` 쿠키 (본문 없음) |
| **관련 요구사항** | FR-002, NFR-004 |
| **CSRF 대응** | `SameSite=Lax` 쿠키 + `Origin` 헤더가 서비스 도메인인지 확인 |

성공 200: 새 `accessToken`, `expiresIn`과 교체된 `Set-Cookie`. 화면은 401 `TOKEN_EXPIRED`를 받으면 한 번만 갱신을 시도하고 원래 요청을 다시 보낸다. 여러 요청이 동시에 만료되면 갱신 요청은 하나로 합친다.

| 상황 | 상태 | `code` | 화면 동작 |
|------|------|--------|-----------|
| 쿠키 없음·만료 | 401 | `REFRESH_TOKEN_INVALID` | S1(카카오로 시작하기)로 |
| 교체된 토큰 재사용 | 401 | `REFRESH_TOKEN_REUSED` | 모든 기기 로그아웃, S1로 |
| 정지·탈퇴 | 403 / 401 | `ACCOUNT_SUSPENDED` / `ACCOUNT_WITHDRAWN` | 안내 화면 |

---

## 6. 에러 코드 테이블

### 6.1 인증/인가 에러

| 에러 코드 | HTTP 상태 | 메시지 (화면 표시) | 설명 |
|-----------|-----------|--------------------|------|
| `UNAUTHORIZED` | 401 | 로그인이 필요해요 | 토큰 없음 |
| `TOKEN_EXPIRED` | 401 | (표시 안 함, 자동 갱신) | Access Token 만료 |
| `INVALID_TOKEN` | 401 | 다시 로그인해 주세요 | 서명·형식 오류 |
| `REFRESH_TOKEN_INVALID` | 401 | 다시 로그인해 주세요 | Refresh 만료·폐기 |
| `REFRESH_TOKEN_REUSED` | 401 | 보안을 위해 로그아웃했어요. 다시 로그인해 주세요 | 탈취 의심 |
| `SIGNUP_TOKEN_EXPIRED` | 401 | 시간이 지나서 처음부터 다시 해 주세요 | 가입 대기 10분 경과 |
| `KAKAO_CODE_INVALID` | 400 | 카카오 로그인을 완료하지 못했어요. 다시 시도해 주세요 | |
| `SIGNUP_BLOCKED` | 403 | 지금은 이 카카오 계정으로 가입할 수 없어요 | 탈퇴 30일·영구 정지 |
| `ALREADY_REGISTERED` | 409 | 이미 가입한 계정이에요 | |
| `VERIFICATION_REQUIRED` | 403 | (단계별) 학교 메일 인증을 하면 … / 학생 인증을 마치면 … | `requiredLevel` 포함 |
| `ACCOUNT_SUSPENDED` | 403 | {날짜}까지 이용이 정지됐어요 | `details`에 종료 시각 |
| `ACCOUNT_WITHDRAWN` | 401 | 탈퇴한 계정이에요 | |
| `ADMIN_ONLY` | 403 | 접근할 수 없어요 | |
| `NOT_RESOURCE_OWNER` | 403 | 내가 쓴 글만 바꿀 수 있어요 | |
| `USER_BLOCKED` | 403 | 차단한(또는 나를 차단한) 사용자와는 채팅할 수 없어요 | 어느 쪽이 차단했는지는 알리지 않음 |

### 6.2 유효성 검증 에러

| 에러 코드 | HTTP 상태 | 메시지 | 설명 |
|-----------|-----------|--------|------|
| `VALIDATION_ERROR` | 400 | 입력 내용을 다시 확인해 주세요 | `details`에 필드별 |
| `INVALID_CURSOR` | 400 | 목록을 새로고침해 주세요 | |
| `SCHOOL_EMAIL_REQUIRED` | 400 | 숙명여대 메일(@sookmyung.ac.kr)만 쓸 수 있어요 | |
| `INVALID_CODE` | 400 | 인증번호가 맞지 않아요 (남은 횟수 N회) | |
| `CODE_EXPIRED` | 400 | 인증번호가 만료됐어요. 다시 받아 주세요 | |
| `ADDRESS_NOT_FOUND` | 400 | 주소를 다시 골라 주세요 | |
| `UPLOAD_INVALID` | 400 | 사진을 다시 올려 주세요 | 남의 업로드·만료·용도 다름 |
| `IMAGE_TOO_SMALL` | 400 | 사진이 너무 작아요 | |
| `FILE_TOO_LARGE` | 413 | 사진은 한 장에 10MB까지 올릴 수 있어요 | |
| `UNSUPPORTED_FILE_TYPE` | 415 | JPG, PNG, HEIC 사진만 올릴 수 있어요 | |

### 6.3 비즈니스 로직 에러

| 에러 코드 | HTTP 상태 | 메시지 | 설명 |
|-----------|-----------|--------|------|
| `NICKNAME_TAKEN` | 409 | 이미 쓰고 있는 닉네임이에요 | |
| `NICKNAME_CHANGE_TOO_SOON` | 409 | 닉네임은 30일에 한 번 바꿀 수 있어요 | 초안 |
| `EMAIL_ALREADY_USED` | 409 | 이미 다른 계정에서 인증한 메일이에요 | |
| `RESEND_TOO_SOON` | 429 | {N}초 후에 다시 받을 수 있어요 | 60초 |
| `CODE_LOCKED` | 429 | 30분 후에 다시 시도해 주세요 | 5회 실패 |
| `VERIFICATION_ALREADY_PENDING` | 409 | 검수 중이에요. 결과를 알려드릴게요 | 대기 중 재제출 |
| `POST_NOT_FOUND` | 404 | 삭제됐거나 볼 수 없는 글이에요 | |
| `POST_LIMIT_EXCEEDED` | 409 | 공개 중인 판매 글은 3개까지예요 … | 구함 1·단기숙박 1 |
| `INVALID_STATUS_TRANSITION` | 409 | 이 상태로는 바꿀 수 없어요 | 완료 24시간 지나 되돌리기 등 (AC-012-3) |
| `POST_NOT_AVAILABLE` | 409 | 거래가 끝났거나 숨겨진 글이에요 | 채팅 열기·전송 |
| `CANNOT_CHAT_OWN_POST` | 409 | 내 글에는 채팅할 수 없어요 | |
| `CANNOT_FAVORITE_OWN_POST` | 409 | 내 글은 찜할 수 없어요 | |
| `CHAT_ROOM_NOT_FOUND` | 404 | 채팅방을 찾을 수 없어요 | |
| `ACCOUNT_NUMBER_BLOCKED` | 422 | 계좌번호는 채팅으로 보낼 수 없어요 … | 텍스트·사진 (ADR-007) |
| `CONTACT_INFO_NOT_ALLOWED` | 422 | 글에는 연락처나 계좌번호를 쓸 수 없어요. 연락은 채팅으로 해 주세요 | |
| `ALREADY_REPORTED` | 409 | 이미 신고한 글이에요 | |
| `CANNOT_REPORT_SELF` | 409 | 내 글이나 나 자신은 신고할 수 없어요 | |
| `INTEREST_LIMIT_EXCEEDED` | 409 | 관심 조건은 5개까지 저장할 수 있어요 | AC-021-4 |
| `INTEREST_CONDITION_EMPTY` | 400 | 조건을 하나 이상 골라 주세요 | FR-021-1 |
| `IDEMPOTENCY_KEY_REUSED` | 409 | (표시 안 함) | 같은 키에 다른 본문 |

### 6.4 시스템 에러

| 에러 코드 | HTTP 상태 | 메시지 | 설명 |
|-----------|-----------|--------|------|
| `RATE_LIMITED` | 429 | 잠시 후 다시 시도해 주세요 | `retryAfter` |
| `INTERNAL_ERROR` | 500 | 일시적인 오류예요. 잠시 후 다시 시도해 주세요 | Sentry 기록 |
| `KAKAO_UNAVAILABLE` | 502 | 카카오 로그인이 잠시 안 돼요 | |
| `MAIL_UNAVAILABLE` | 502 | 메일을 보내지 못했어요 | |
| `ADDRESS_SERVICE_UNAVAILABLE` | 502 | 주소 확인이 잠시 안 돼요. 임시 저장해 두세요 | |
| `SERVICE_UNAVAILABLE` | 503 | 점검 중이에요 | `Retry-After` |

---

## 7. Rate Limiting 정책

SRS NFR-004가 SAD로 넘긴 수치다. MVP는 DB 카운터(`rate_limit_counters`, 고정 창)로 구현한다 (SAD 3.6, DB 설계서 3.9). 수치는 모두 **초안**이며 `app_settings.rate_limits` 키로 바꿀 수 있게 한다 (DB 설계서 `app_settings` 초기 값에 추가 필요, API-Q1).

### 7.1 전체 정책

| 구분 | 제한 | 기준 | 초과 시 |
|------|------|------|---------|
| 비회원 | 60회/분 | IP | 429 `RATE_LIMITED` |
| 로그인 사용자 | 120회/분 | 회원 ID | 429 |
| 관리자 | 300회/분 | 회원 ID | 429 |
| 내부 작업 | 제한 없음 | `CRON_SECRET` | - |

같은 학교 와이파이에서 여러 학생이 같은 IP로 보일 수 있어, 로그인 후에는 IP가 아니라 회원 ID로 센다.

### 7.2 엔드포인트별 제한

| 엔드포인트 | 제한 | 기준 | 근거 |
|------------|------|------|------|
| `POST /auth/kakao` | 10회/분 | IP | 로그인 남용 |
| `POST /auth/signup` | 10회/시간 | IP | 계정 대량 생성 |
| `POST /auth/refresh` | 30회/시간 | 세션 | |
| `GET /users/nickname-availability` | 30회/분 | IP | |
| `POST /verifications/email-codes` | 60초 간격, 5회/시간, 10회/일 | 회원 + 이메일 | FR-001 (60초), 메일 폭탄 |
| `POST /verifications/email-codes/verify` | 5회 실패 시 30분 잠금 | 이메일 | AC-001-4 |
| `POST /verifications` | 5회/일 | 회원 | |
| `POST /posts` | 10회/시간, 30회/일 | 회원 | 도배 |
| `PATCH /posts/{id}` | 30회/시간 | 회원 | |
| `POST /uploads/photos` | 60장/시간 | 회원 | 저장소 비용 |
| `POST /addresses/resolve` | 30회/시간 | 회원 | 카카오 로컬 API 한도 |
| `POST /chat-rooms` | 20개/일 | 회원 | 무차별 문의 |
| `POST /chat-rooms/{id}/messages` | 30개/분, 방당 600개/일 | 회원 | 도배 |
| `POST /reports` | 10회/일 | 회원 | 허위 신고 |
| `PUT /posts/{id}/favorite` | 60회/분 | 회원 | |
| `GET /posts` (검색 `q` 포함) | 60회/분 | 회원·IP | |

### 7.3 Rate Limit 응답 헤더

| 헤더 | 설명 | 예시 |
|------|------|------|
| `RateLimit-Limit` | 창 안 최대 요청 수 | `30` |
| `RateLimit-Remaining` | 남은 요청 수 | `12` |
| `RateLimit-Reset` | 창이 초기화될 때까지 남은 초 | `41` |
| `Retry-After` | 429일 때 다시 시도까지 초 | `41` |

---

## 8. API 변경 관리

### 8.1 버저닝 정책

| 항목 | 정책 |
|------|------|
| 버전 표기 | URL 경로 `/api/v1` |
| 새 버전 조건 | 8.2 Breaking Change가 있을 때만 |
| 이전 버전 유지 | 새 버전 배포 후 최소 30일 (초안) |
| 폐기 안내 | 응답 헤더 `Deprecation`, `Sunset` + 화면 새로고침 안내 |
| 웹앱 특성 | 화면과 API를 같은 배포로 올리므로 대부분의 변경은 버전 없이 함께 바뀐다. 서비스 워커는 새 배포를 감지하면 "새 버전이 있어요. 새로고침" 배너를 띄운다 |

### 8.2 Breaking Change 정의

| 변경 유형 | 예시 |
|-----------|------|
| 필드 삭제·이름 변경 | `priceText` → `price.text` |
| 필드 타입 변경 | 금액 단위를 만 원 → 원 |
| 필수 파라미터 추가 | `POST /posts`에 새 필수 항목 |
| 열거형 값 삭제·의미 변경 | `post_category` 값 제거 |
| 오류 코드 변경 | `POST_LIMIT_EXCEEDED` 이름 변경 |
| 권한 강화 | 이메일 인증 → 정회원으로 상향 |

### 8.3 Non-Breaking Change (하위 호환)

| 변경 유형 | 예시 |
|-----------|------|
| 응답 필드 추가 | `badges`에 새 값, 새 표시용 문자열 |
| 선택 파라미터 추가 | 새 필터 |
| 새 엔드포인트 | FR-026 끌어올리기 (P2) |
| 열거형 값 추가 | 새 신고 사유 (화면은 모르는 값을 "기타"로 표시) |
| 설정값 변경 | 숙대 기준 위치 목록 (`app_settings`) |

### 8.4 API 변경 로그

| 날짜 | 버전 | 변경 유형 | 내용 |
|------|------|-----------|------|
| 2026-11-26 | v1 (초안) | 신규 | 최초 설계 |

---

## 부록

### A. API 문서 자동화

| 항목 | 내용 |
|------|------|
| 스키마 원본 | `src/lib/schemas/*.ts`의 Zod 스키마 (클라이언트·서버 공유, SAD 3.2) |
| 문서 생성 | `zod-to-openapi`로 OpenAPI 3.1 생성 → `docs/openapi.json` (CI에서 갱신 여부 확인) |
| 열람 | 개발 환경에서만 `/api/docs` (운영에서는 끔) |
| 예시 값 | 문서 예시에는 실제 키·토큰·개인정보를 쓰지 않는다. 토큰 예시는 `eyJhbGciOi…`처럼 잘린 값만 (SAD 4.5) |

### B. API 테스트 컬렉션

| 항목 | 내용 |
|------|------|
| 도구 | Bruno (컬렉션을 저장소 `api-collection/`에 텍스트로 저장) |
| 환경 변수 | `baseUrl`, `accessToken`은 Bruno의 로컬 환경 파일(`.env`)에만 두고 **저장소에 올리지 않는다** (`.gitignore`의 `.env*`) |
| 자동 테스트 | 권한 단계별(비회원·인증 전·이메일 인증·정회원·권한 제한·정지·관리자) 호출 결과를 Vitest 통합 테스트로 검사 (SAD 4.3) |

### C. 미결 사항

| ID | 내용 | 상태 | 제안 |
|----|------|------|------|
| API-Q1 | 요청 제한 수치(7장) | 초안 | 출시 후 2주 로그를 보고 `app_settings`로 조정 |
| API-Q2 | 닉네임 변경 주기 30일 | 초안 | PRD에 없음. 이유나 확인 |
| API-Q3 | 송금 요청 표현 목록 (AC-015-6) | 초안 | `app_settings.remittance_words`로 관리, 운영하며 보강 |
| API-Q4 | 비회원 목록 노출 범위 (첫 페이지만 / 무한 스크롤 허용) | 초안 | 무한 스크롤 허용, 카드 탭 시 가입 안내 (화면 설계서 S4) |
| SAD-Q1 | 서비스 도메인 | 미결 (이유나) | Base URL·쿠키 도메인·카카오 redirect URI가 여기에 따름 |
| SAD-Q3 | 홈 화면 PWA에서 카카오 로그인 복귀 (iOS) | 상세 설계 | 실제 기기 시험 |
| DEC-012 | 숙대 기준 위치 목록 | 미결 | `GET /settings/public`으로 내려주므로 API 변경 없음 |

### D. 요구사항 추적 (FR → API)

| FR | API |
|----|-----|
| FR-001 | `POST /auth/kakao`, `POST /auth/signup`, `GET /users/nickname-availability`, `POST /verifications/email-codes`, `…/verify` |
| FR-002 | `POST /auth/kakao`, `POST /auth/refresh`, `POST /auth/logout`, `DELETE /users/me` |
| FR-003 | `POST /verifications`, `GET /verifications/me`, `POST /admin/verifications/{id}/approve·reject` |
| FR-004 | 2.4 인가 규칙 (모든 API) |
| FR-005 | `POST /verifications` (`kind: REVERIFY`), 내부 작업 재인증 안내·만료 |
| FR-006 | `GET /posts`, `GET /posts/count` |
| FR-007·008·009·010 | `POST·PATCH·DELETE /posts`, `PUT /drafts/me`, `POST /uploads/photos`, `POST /addresses/resolve`, `GET /settings/public` |
| FR-011 | `POST·PATCH·DELETE /posts` (`type: WANTED`) |
| FR-012 | `PATCH /posts/{id}/status`, `POST /posts/{id}/keep` |
| FR-013 | `GET /posts/{id}` |
| FR-014 | `PUT·DELETE /posts/{id}/favorite`, `GET /favorites` |
| FR-015 | `/chat-rooms*`, Realtime 구독, `POST /uploads/photos` (`CHAT`) |
| FR-016 | `/blocks*` |
| FR-017 | `GET /posts` 필터·정렬·`q` |
| FR-018 | `POST /reports` |
| FR-019 | `/admin/*` |
| FR-020 | `/notifications*`, `/notification-settings`, `/devices/push-token` |
| FR-021 | `/interest-conditions*` |
| FR-022 | `GET·PATCH /users/me`, `GET /users/me/posts`, `GET /verifications/me` |
| FR-023 | `POST /posts` `nonInterventionAgreed`, `GET /chat-rooms/{id}` 안내 표시 여부 |
| FR-024 | `GET /posts/{id}` 조회 집계, 목록 `metaText` |
| FR-025 | 3.3 오류 형식, 429 `retryAfter`, 메시지 `clientMsgId` 재전송 |

### E. 참조 문서

| 문서 | 경로 |
|------|------|
| 요구사항 명세서 (SRS) | [../01-요구사항분석/요구사항명세서-SRS.md](../01-요구사항분석/요구사항명세서-SRS.md) |
| 요구사항 추적 매트릭스 | [../01-요구사항분석/요구사항추적매트릭스-RTM.md](../01-요구사항분석/요구사항추적매트릭스-RTM.md) |
| 시스템 아키텍처 설계서 | [시스템아키텍처설계서-SAD.md](시스템아키텍처설계서-SAD.md) |
| 데이터베이스 설계서 | [데이터베이스설계서.md](데이터베이스설계서.md) |
| 화면 설계서 | [화면설계서.md](화면설계서.md) |
