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

> **Base URL:** `https://api.example.com/v1`  
> 





<img src="3.png" style="width: 800px; height: auto;" alt="설명">
<img src="4.png" style="width: 800px; height: auto;" alt="설명">
<img src="5.png" style="width: 800px; height: auto;" alt="설명">
<img src="6.png" style="width: 800px; height: auto;" alt="설명">

