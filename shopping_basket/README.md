#### **Request Headers** 공통사항

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

<img src="1.png" style="width: 500px; height: auto;" alt="설명">
<img src="2.png" style="width: 500px; height: auto;" alt="설명">

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | Y | 상품 고유 번호 |

#### **Request Body**
```json
{
  "productId": 202,
  "optionName": "제주 당근 우유 껌 50g",
  "count": 1
}
```

#### **Success Response**

* **Code:** 200 OK
* **Content:**

```json
{
  "status": "success",
  "data": {
    "imageUrl": "https://swiffy.com/items/milk_gum_carrot.png",
    "productName": "어글어글 우유껌 50g 7종",
    "option": "제주 당근 우유 껌 50g",
    "buyUrl": "/order/checkout",
    "cartUrl": "/order/cart",
    "continueShoppingUrl": "/products/list"
  }
}
```

#### **Error Response**

* **Code:** 404 NOT FOUND
* **Content:** `{ "message": "Product not found" }`
* **Code:** 401 UNAUTHORIZED
* **Content:** `{ "message": "Invalid token" }`

#### **참고사항**

<img src="3.png" style="width: 500px; height: auto;" alt="설명">

---

## 엔드포인트 상세
**GET** `/api/v1/cart`

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| userId | Long | Y | 장바구니를 조회할 사용자 ID |

#### **Request Body**
```json
{
  "cartId": ""
}
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
  "data": [
    {
      "cartItemId": 1,
      "productName": "어글어글 우유껌 50g 7종",
      "option": "제주 브로콜리 우유껌 50g",
      "price": 13000,
      "discountPrice": 0,
      "count": 2,
      "imageUrl": "https://swiffy.com/items/broccoli_gum.png",
      "deleteUrl": "/api/cart/1",
      "wishlistUrl": "/api/wishlist/1",
      "orderUrl": "/api/order/1"
    },
    {
      "cartItemId": 2,
      "productName": "어글어글 우유껌 50g 7종",
      "option": null,
      "price": 6500,
      "discountPrice": 0,
      "count": 1,
      "imageUrl": "https://swiffy.com/items/original_gum.png",
      "deleteUrl": "/api/cart/2",
      "wishlistUrl": "/api/wishlist/2",
      "orderUrl": "/api/order/2"
    }
  ],
  "totalOrderPrice": 19500,
  "totalShippingFee": 0
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### **참고사항**

---

<img src="4.png" style="width: 500px; height: auto;" alt="설명">

---

## 엔드포인트 상세
**GET** `/api/v1/cart/summary`

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| userId | Long | Y | 장바구니 요약 정보를 조회할 사용자 ID |

#### **Request Body**
```json
{
  "cartId": ""
}
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
  "data": {
    "totalProductPrice": 13000,
    "totalShippingFee": 5000,
    "estimatedPaymentAmount": 18000,
    "estimatedRewardPoints": 130,
    "memberRewardPoints": 130,
    "buttons": {
      "selectAll": "/api/v1/cart/select-all",
      "deleteSelected": "/api/v1/cart/items/delete",
      "moveToOverseasCart": "/api/v1/cart/overseas",
      "orderSelected": "/api/v1/orders/selected",
      "orderAll": "/api/v1/orders/all"
    }
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### **참고사항**

---

<img src="all_select.png" style="width: 500px; height: auto;" alt="설명">
<img src="all_select2.png" style="width: 500px; height: auto;" alt="설명">
<img src="delete_select1.png" style="width: 500px; height: auto;" alt="설명">
<img src="delete_select2.png" style="width: 500px; height: auto;" alt="설명">

=======

## 엔드포인트 상세
삭제  
`DELETE` api/v1/product/{productId}  

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
|  |  | - | - |

#### **Request Body**
```json
{
  "삭제" :
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
    "imageUrl" : ""
    "productName" : ""
    "price" :
    "discountPrice" :
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항

-----

<img src="option_change1.png" style="width: 500px; height: auto;" alt="설명">
<img src="option_change2.png" style="width: 500px; height: auto;" alt="설명">
<img src="option_change3.png" style="width: 500px; height: auto;" alt="설명">
<img src="product_like1.png" style="width: 500px; height: auto;" alt="설명">

=======
## 엔드포인트 상세

`GET` /api/v1/shoppingbasket


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | - | - |
| imageUrl | String | - | - |
| productName | String | - | - |
| 배송방법 | String | - | - |
| price | integer | - | - |
| discountPrice | integer | - | - |
| count | integer | - | 상품 갯수 |
| option | String | - | - |
| options | String | - | 전체옵션 |
| totalPrice | integer | - | - |
| 총 배송비 | integer | - | - |
| totalDiscountPrice | integer | - | - |
| 적립예정금액 | integer | - | - |
| 회원적립금 | integer | - | - |
| wishlist |  | - | - |
| 전체상품 주문하기 |  | - | - |



#### **Request Body**
```json
{
  "delete" : ,
  "wishlist" : ,
  "전체상품 주문하기" : "",
  "count" : ,
  "option" :
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
    "imageUrl" : ""
    "productId" : ""
    "productName" : "",
    "배송방법" : "",
    "price" : ,
    "discountPrice" : ,
    "count" : ,
    "option" : "",
    "options" : "",
    "totalPrice" : ,
    "총 배송비" : ,
    "totalDiscountPrice" : ,
    "적립예정금액" : ,
    "회원적립금" : 
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항

전체선택 선택헤제를 아래에서 맨위로 올립니다.

-----

<img src="product_like2.png" style="width: 500px; height: auto;" alt="설명">
<img src="Required_Option.png" style="width: 500px; height: auto;" alt="설명">
<img src="same_product.png" style="width: 500px; height: auto;" alt="설명">
