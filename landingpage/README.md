<img src="1.png" style="width: 800px; height: auto;" alt="설명">


## 지금은 사용자에게 렌더링하는 페이지
### 1\. API 개요 (선택 사항)

> **Base URL:** `https://api.example.com/api/v1`  
> **Authentication:** JWT Access/Refresh token (Cookie 헤더)

-----

### 2\. 엔드포인트 상세 (Example)

### `GET` /api/v1/main

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | - | - |

#### **Request Body**
```json
{
  
}
```


#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "username": "gemini_user",
    "email": "hello@gemini.ai",
    "created_at": "2026-04-02T09:00:00Z"
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----







# 추천 상품 
## 관리자 추천 상품 페이지 필요
### 추천 상품 등록 데이터
|제품명|?|
|-----|---|
|?|?|
### 등록 URL
`/api/v1/admain(관리자)`
`/api/v1/admin/banner`


<img src="2.png" style="width: 800px; height: auto;" alt="설명">

### 1\. API 개요 (선택 사항)

### 2\. 엔드포인트 상세 (Example)

### `GET /users/{id}`

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `id` | `Integer` | ✅ | 사용자의 고유 ID (Path Variable) |
| `include_posts` | `Boolean` | ❌ | 작성한 포스트 포함 여부 (Query Param) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }

 {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
{
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----

## 💡 작성 시 꿀팁 (Best Practices)

### 1\. 상태 코드 명시

단순히 성공/실패만 적지 말고, HTTP 상태 코드($200$, $201$, $400$, $404$, $500$ 등)를 명확히 기재하세요.

### 2\. 코드 블록 언어 설정

JSON 응답 예시를 적을 때 반드시 \`\`\`json 이라고 명시하세요. 그래야 문법 하이라이팅이 적용되어 가독성이 비약적으로 상승합니다.

### 3\. 배지(Badge) 활용 (시각화)

상태나 권한을 표현할 때 유용합니다.

  * `![Static Badge](https://img.shields.io/badge/AUTH-REQUIRED-red)` -\> 
  * `![Static Badge](https://img.shields.io/badge/METHOD-GET-blue)` -\> 

### 4\. 테이블 정렬

표 작성 시 `:---`는 왼쪽 정렬, `:---:`는 중앙 정렬입니다. `Type`이나 `Required` 유무는 중앙 정렬이 보기에 좋습니다.

#### 참고사항
베스트셀러는 [전체판매1위] 이런 템플릿으로 하고 
태그는 [판매1위] 이런식으로 템플릿을 합니다.





<img src="3.png" style="width: 800px; height: auto;" alt="설명">
### 1\. API 개요 (선택 사항)

> **Base URL:** `https://api.example.com/api/v1`  
> **Authentication:** JWT Access/Refresh token (Cookie 헤더)

-----

### 2\. 엔드포인트 상세 (Example)

### `GET` /api/v1/main

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | - | - |

#### **Request Body**
```json
{
  
}
```


#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }

 {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
{
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
{
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
{
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항

* 태그 최대 개수는 5개 
* 태그 별제품은 최대 5개
* 랜더링되는 제품은 (태그별)판매량순(판매량 정보도 백엔드에서 던져주는 것으로)
* 

-----

<img src="4.png" style="width: 800px; height: auto;" alt="설명">

### 1\. API 개요 (선택 사항)
-----

### 2\. 엔드포인트 상세 (Example)

### `GET /users/{id}`

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `id` | `Integer` | ✅ | 사용자의 고유 ID (Path Variable) |
| `include_posts` | `Boolean` | ❌ | 작성한 포스트 포함 여부 (Query Param) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "username": "gemini_user",
    "email": "hello@gemini.ai",
    "created_at": "2026-04-02T09:00:00Z"
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----

## 💡 작성 시 꿀팁 (Best Practices)

### 1\. 상태 코드 명시

단순히 성공/실패만 적지 말고, HTTP 상태 코드($200$, $201$, $400$, $404$, $500$ 등)를 명확히 기재하세요.

### 2\. 코드 블록 언어 설정

JSON 응답 예시를 적을 때 반드시 \`\`\`json 이라고 명시하세요. 그래야 문법 하이라이팅이 적용되어 가독성이 비약적으로 상승합니다.

### 3\. 배지(Badge) 활용 (시각화)

상태나 권한을 표현할 때 유용합니다.

  * `![Static Badge](https://img.shields.io/badge/AUTH-REQUIRED-red)` -\> 
  * `![Static Badge](https://img.shields.io/badge/METHOD-GET-blue)` -\> 

### 4\. 테이블 정렬

표 작성 시 `:---`는 왼쪽 정렬, `:---:`는 중앙 정렬입니다. `Type`이나 `Required` 유무는 중앙 정렬이 보기에 좋습니다.
<img src="5.png" style="width: 800px; height: auto;" alt="설명">

### 1\. API 개요 (선택 사항)

> **Base URL:** `https://api.example.com/v1`  
> **Authentication:** Bearer Token (Header: `Authorization`)

-----

### 2\. 엔드포인트 상세 (Example)

### `GET /users/{id}`

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `id` | `Integer` | ✅ | 사용자의 고유 ID (Path Variable) |
| `include_posts` | `Boolean` | ❌ | 작성한 포스트 포함 여부 (Query Param) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "username": "gemini_user",
    "email": "hello@gemini.ai",
    "created_at": "2026-04-02T09:00:00Z"
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----

## 💡 작성 시 꿀팁 (Best Practices)

### 1\. 상태 코드 명시

단순히 성공/실패만 적지 말고, HTTP 상태 코드($200$, $201$, $400$, $404$, $500$ 등)를 명확히 기재하세요.

### 2\. 코드 블록 언어 설정

JSON 응답 예시를 적을 때 반드시 \`\`\`json 이라고 명시하세요. 그래야 문법 하이라이팅이 적용되어 가독성이 비약적으로 상승합니다.

### 3\. 배지(Badge) 활용 (시각화)

상태나 권한을 표현할 때 유용합니다.

  * `![Static Badge](https://img.shields.io/badge/AUTH-REQUIRED-red)` -\> 
  * `![Static Badge](https://img.shields.io/badge/METHOD-GET-blue)` -\> 

### 4\. 테이블 정렬

표 작성 시 `:---`는 왼쪽 정렬, `:---:`는 중앙 정렬입니다. `Type`이나 `Required` 유무는 중앙 정렬이 보기에 좋습니다.
<img src="6.png" style="width: 800px; height: auto;" alt="설명">

### 1\. API 개요 (선택 사항)

> **Base URL:** `https://api.example.com/v1`  
> **Authentication:** Bearer Token (Header: `Authorization`)

-----

### 2\. 엔드포인트 상세 (Example)

### `GET /users/{id}`

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `id` | `Integer` | ✅ | 사용자의 고유 ID (Path Variable) |
| `include_posts` | `Boolean` | ❌ | 작성한 포스트 포함 여부 (Query Param) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "username": "gemini_user",
    "email": "hello@gemini.ai",
    "created_at": "2026-04-02T09:00:00Z"
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----

## 💡 작성 시 꿀팁 (Best Practices)

### 1\. 상태 코드 명시

단순히 성공/실패만 적지 말고, HTTP 상태 코드($200$, $201$, $400$, $404$, $500$ 등)를 명확히 기재하세요.

### 2\. 코드 블록 언어 설정

JSON 응답 예시를 적을 때 반드시 \`\`\`json 이라고 명시하세요. 그래야 문법 하이라이팅이 적용되어 가독성이 비약적으로 상승합니다.

### 3\. 배지(Badge) 활용 (시각화)

상태나 권한을 표현할 때 유용합니다.

  * `![Static Badge](https://img.shields.io/badge/AUTH-REQUIRED-red)` -\> 
  * `![Static Badge](https://img.shields.io/badge/METHOD-GET-blue)` -\> 

### 4\. 테이블 정렬

표 작성 시 `:---`는 왼쪽 정렬, `:---:`는 중앙 정렬입니다. `Type`이나 `Required` 유무는 중앙 정렬이 보기에 좋습니다.

