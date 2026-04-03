#### **Request Headers** 공통사항

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

---

### `GET` /api/v1/store/bestseller

---


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | - | - |

<!-- end list -->

#### **Request Body**
```json
{
 
}
```


#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
  "data": {
    "totalProductNumber" : "6",
    "imageUrl" : "",
    "productUrl" : "",
    "productTitle" : "",
    "price" : "",
    "pageInfo" : ""
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항
1. 리스폰스 데이터에 제품 총갯수(베스트셀러에 전시할 제품 수)는 6개로 고정.
