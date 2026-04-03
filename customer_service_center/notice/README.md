#### **Request Headers** 공통사항

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

---

### `GET` /api/v1/board/notice

<img src="./n1.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n2.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n3.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n4.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n7.png" style="width: 500px; height: auto;" alt="notice">

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| page | Integer | - | 현재 보고있는 페이지 |
| size | Integer | - | 한 페이지에 보여줄 게시글 개수 (10개) |
| keyword | String | - | 검색어 |

### `POST` /api/v1/coupons/download
#### **Request Body**
```json
{
  "couponId": 2001
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
    "notices": [
      {
        "id": 53,
        "boardTag": "EVENT",
        "title": "[EVENT] 쿠폰 이벤트",
        "content": "신제품 재입고 기념 쿠폰 이벤트! 하단 버튼을 눌러 다운받으세요.",
        "imageUrls": ["https://s3.eum-shop.com/notices/coupon_eve우

<img src="./n4%20(2).png" style="width: 500px; height: auto;" alt="notice">
<img src="./n5.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n6.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n9.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n-9.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n10.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n11.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n12.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n13.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n14.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n15.png" style="width: 500px; height: auto;" alt="notice">
<img src="./n16%20(2).png" style="width: 500px; height: auto;" alt="notice">
<img src="./n17%20(2).png" style="width: 500px; height: auto;" alt="notice">
<img src="./n18.png" style="width: 500px; height: auto;" alt="notice">
