<img src="1.png" style="width: 500px; height: auto;" alt="설명">
<img src="2.png" style="width: 500px; height: auto;" alt="설명">
<img src="3.png" style="width: 500px; height: auto;" alt="설명">

=======

## 엔드포인트 상세
삭제
`DELETE` api/v1/product/{productId}
관심상품
`POST` api/v1/wishlist/{productId}
옵션변경
`PUT` api/v1/option/{productId}
주문하기
`POST` api/v1/product/{productId}

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
|  | - | - | - |

#### **Request Body**
```json
{
  "option" :
  "옵션변경" :
  "삭제" :
  "wishlist" :
  "주문하기" :
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
    "productUrl" : ""
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

<img src="4.png" style="width: 500px; height: auto;" alt="설명">
<img src="all_select.png" style="width: 500px; height: auto;" alt="설명">
<img src="all_select2.png" style="width: 500px; height: auto;" alt="설명">
<img src="delete_select1.png" style="width: 500px; height: auto;" alt="설명">
<img src="delete_select2.png" style="width: 500px; height: auto;" alt="설명">
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
