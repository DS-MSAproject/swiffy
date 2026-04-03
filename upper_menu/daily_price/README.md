| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

---

<img src="daily_price_select.png" style="width: 500px; height: auto;" alt="설명">
<img src="daily_price_page1.png" style="width: 500px; height: auto;" alt="설명">
<img src="daily_price_page2.png" style="width: 500px; height: auto;" alt="설명">

<img src="daily_price_reg_delivery_sale1.png" style="width: 500px; height: auto;" alt="설명">
<img src="daily_price_reg_delivery_sale2.png" style="width: 500px; height: auto;" alt="설명">

res
메인
```json
{
  "status": "success",
  "data": {
    "id": 1,
    "제품 총 개수": "",
    "ImageUrl": "",
    "title": "",
    "price" : ,
    ""
  }
}
```

### `GET` /api/v1/store/regular_delivery


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
    "productId" : "",
    "totalProductNumber" : "",
    "imageUrl" :"",
    "productUrl" : "",
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








