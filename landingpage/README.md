<img src="1.png" style="width: 800px; height: auto;" alt="설명">



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
<img src="3.png" style="width: 800px; height: auto;" alt="설명">
<img src="4.png" style="width: 800px; height: auto;" alt="설명">
<img src="5.png" style="width: 800px; height: auto;" alt="설명">
<img src="6.png" style="width: 800px; height: auto;" alt="설명">

