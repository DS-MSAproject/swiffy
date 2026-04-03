#### **회원가입** API 명세

> **Base URL:** `https://api.example.com/v1`  
> **Authentication:** `JWT Access/Refresh Token (Cookie Header)`
> **CSRF** POST 요청 시 X-XSRF-TOKEN 헤더 필수

#### **소셜 로그인**

### `GET` /oauth2/authorization/{provider}

#### **Request Headers**

| Name | Value/Type | Required | Description |
| :--- | :--- | :---: | :--- |
| 없음 | - | - | 브라우저 직접 이동 |

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| provider | String | ✅ | google, naver, kakao (Path Variable) |
| code_challenge | String | ✅ | PKCE SHA-256 해시값 (Query Param)) |
| code_challenge_method | String | ✅ | 항상 S256 (Query Param)) |


#### **Request Body**
```json
```
#### **Response Headers**

| Name | Value | Description |
| :--- | :--- | :--- |
| Location | (https://accounts.google.com/o/oauth2/auth?...) | 소셜 플랫폼 로그인 페이지로 리다이렉트 |

#### 처리 흐름
 
```
1. 브라우저 → /oauth2/authorization/google?code_challenge=xxx&code_challenge_method=S256
2. Google 로그인 완료
3. 프론트 /oauth/callback?code=one-time-code 로 리다이렉트
4. GET /api/v1/auth/oauth/token?code=xxx 호출
5. { accessToken } 수신 + refreshToken 쿠키 자동 저장
```
 
> 최초 로그인 시 회원 정보가 자동 생성됩니다. 소셜 계정에서 프로필 이미지를 가져와 S3에 자동 업로드합니다.
 
---
 
### `GET /api/v1/auth/oauth/token`
 
소셜 로그인 콜백 후 one-time code를 Access Token으로 교환합니다.
 
#### Request Headers
 
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 |
 
#### Request Parameters
 
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `code` | `String` | ✅ | 소셜 로그인 콜백으로 받은 one-time code (30초 유효) (**Query Param**) |
 
#### Request Body
 
```json
```
 
#### Success Response
 
- **Code:** `200 OK`
 
#### Response Headers
 
| Name | Value | Description |
| :--- | :--- | :--- |
| `Set-Cookie` | `refreshToken=xxx; HttpOnly; Secure; SameSite=Lax; Path=/api/v1/auth/refresh; Max-Age=604800` | Refresh Token 쿠키 자동 설정 |
| `Content-Type` | `application/json` | 응답 데이터 형식 |
 
#### Response Body
 
```json
{
  "accessToken": "eyJhbGciOiJSUzI1NiJ9..."
}
```
 
#### Error Response
 
- **Code:** `401 UNAUTHORIZED`
 
```json
"유효하지 않거나 만료된 코드입니다."
```
 
---
 
## 2. 일반 회원가입
 
### Step 1 — 이메일 인증 코드 발송
 
### `POST /api/v1/auth/email/send`
 
회원가입 전 이메일 인증 코드를 발송합니다.
 
#### Request Headers
 
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `X-XSRF-TOKEN` | `String` | ✅ | CSRF 토큰 (XSRF-TOKEN 쿠키값) |
 
#### Request Parameters
 
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `email` | `String` | ✅ | 인증받을 이메일 주소 (**Query Param**) |
 
#### Request Body
 
```json
```
 
#### Success Response
 
- **Code:** `200 OK`
 
#### Response Headers
 
| Name | Value | Description |
| :--- | :--- | :--- |
| `Content-Type` | `application/json` | 응답 데이터 형식 |
 
#### Response Body
 
```json
{
  "message": "인증 코드가 발송되었습니다. 이메일을 확인해주세요. (유효 시간: 10분)"
}
```
 
#### Error Response
 
- **Code:** `400 BAD REQUEST`
 
```json
{
  "status": 400,
  "error": "이미 사용 중인 이메일입니다."
}
```
 
---
 
### Step 2 — 이메일 인증 코드 확인
 
### `POST /api/v1/auth/email/verify`
 
발송된 6자리 인증 코드를 검증합니다.
 
#### Request Headers
 
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `X-XSRF-TOKEN` | `String` | ✅ | CSRF 토큰 (XSRF-TOKEN 쿠키값) |
 
#### Request Parameters
 
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `email` | `String` | ✅ | 인증할 이메일 주소 (**Query Param**) |
| `code` | `String` | ✅ | 6자리 인증 코드 (**Query Param**) |
 
#### Request Body
 
```json
```
 
#### Success Response
 
- **Code:** `200 OK`
 
#### Response Body
 
```json
{
  "message": "이메일 인증이 완료되었습니다. 로그인해주세요."
}
```
 
#### Error Response
 
- **Code:** `400 BAD REQUEST`
 
```json
{
  "status": 400,
  "error": "인증 코드가 올바르지 않습니다."
}
```
 
- **Code:** `400 BAD REQUEST`
 
```json
{
  "status": 400,
  "error": "인증 코드가 만료되었습니다. 다시 요청해주세요."
}
```
 
---
 
### Step 3 — 회원 정보 입력 및 가입 완료
 
### `POST /api/v1/auth/signup`
 
회원 정보를 입력하고 가입을 완료합니다.
 
#### Request Headers
 
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `X-XSRF-TOKEN` | `String` | ✅ | CSRF 토큰 (XSRF-TOKEN 쿠키값) |
| `Content-Type` | `application/json` | ✅ | 요청 데이터 형식 |
 
#### Request Parameters
 
없음
 
#### Request Body
 
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `username` | `String` | ✅ | 아이디 (영문+숫자, 4~20자) |
| `email` | `String` | ✅ | 이메일 인증 완료된 이메일 |
| `password` | `String` | ✅ | 비밀번호 (8~20자, 대소문자+숫자+특수문자 각 1개 이상) |
| `name` | `String` | ✅ | 이름 |
| `phoneNumber` | `String` | ✅ | 전화번호 (예: 010-1234-5678) |
 
#### Success Response
 
- **Code:** `200 OK`
 
#### Response Headers
 
| Name | Value | Description |
| :--- | :--- | :--- |
| `Content-Type` | `application/json` | 응답 데이터 형식 |
 
#### Response Body
 
```
"회원가입 성공!"
```
 
#### Error Response
 
- **Code:** `400 BAD REQUEST` — 입력값 검증 실패
 
```json
{
  "status": 400,
  "error": "입력값 검증 실패",
  "details": {
    "username": "아이디는 영문과 숫자만 사용 가능합니다. (4~20자)",
    "password": "비밀번호는 영문 대문자, 소문자, 숫자, 특수문자를 각각 1개 이상 포함해야 합니다.",
    "phoneNumber": "올바른 전화번호 형식이 아닙니다."
  }
}
```
 
- **Code:** `400 BAD REQUEST` — 이메일 미인증
 
```json
{
  "status": 400,
  "error": "이메일 인증이 완료되지 않았습니다."
}
```
 
- **Code:** `400 BAD REQUEST` — 중복 가입
 
```json
{
  "status": 400,
  "error": "이미 사용 중인 아이디입니다."
}
```
