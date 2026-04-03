<!-- <img src="payment_details/p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1"> -->

<img src="p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1">

<!-- <img src="payment_details/p1 (2).png" style="width: 500px; height: auto;" alt="결제상세2"> -->

<img src="p1 (2).png" style="width: 500px; height: auto;" alt="결제상세2">

<!-- <img src="payment_details/p1 (3).png" style="width: 500px; height: auto;" alt="결제상세3"> -->

<img src="p1 (3).png" style="width: 500px; height: auto;" alt="결제상세3">

<!-- <img src="payment_details/p1 (4).png" style="width: 500px; height: auto;" alt="결제상세4"> -->

<img src="p1 (4).png" style="width: 500px; height: auto;" alt="결제상세4">

<!-- <img src="payment_details/p1 (5).png" style="width: 500px; height: auto;" alt="결제상세5"> -->

<img src="p1 (5).png" style="width: 500px; height: auto;" alt="결제상세5">

<!-- <img src="payment_details/p1 (6).png" style="width: 500px; height: auto;" alt="결제상세6"> -->

<img src="p1 (6).png" style="width: 500px; height: auto;" alt="결제상세6">

<!-- <img src="payment_details/p1 (7).png" style="width: 500px; height: auto;" alt="결제상세7"> -->

<img src="p1 (7).png" style="width: 500px; height: auto;" alt="결제상세7">

<!-- <img src="payment_details/p1 (8).png" style="width: 500px; height: auto;" alt="결제상세8"> -->

<img src="p1 (8).png" style="width: 500px; height: auto;" alt="결제상세8">


<!-- <img src="payment_details/p1 (9).png" style="width: 500px; height: auto;" alt="결제상세9"> -->

<img src="p1 (9).png" style="width: 500px; height: auto;" alt="결제상세9">

<!-- <img src="payment_details/p1 (10).png" style="width: 500px; height: auto;" alt="결제상세10"> -->

<img src="p1 (10).png" style="width: 500px; height: auto;" alt="결제상세10">

=======
## 엔드포인트 상세

`POST` /api/v1/payment


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | - | - |
| imageUrl | String | - | - |
| productName | String | - | - |
| productList | String | - | - |
| price | Integer | - | - |
| discountPrice | Integer | - | - |
| count | Integer | - | 상품 갯수 |
| option | String | - | - |
| options | String | - | 전체옵션 |
| totalPrice | Integer | - | - |
| 총 배송비 | Integer | - | - |
| totalDiscountPrice | Integer | - | - |
| coupon | String | - |  |
| couponCount | Integer | - | 유저가 가지고 있는 갯수 |
| 쿠폰 결제 조건 | String | - | - |
| 적립금 | Integer | - | - |
| 적용금액 | Integer | - | 총 할인+쿠폰+적립가격 |
| 결제정보 | Integer | - | 주문상품 가격 / 배송비 / 할인 부가결제 / 최종 결제금액 |
| 적립혜택 | Integer | - | 1% |
| message | String | - | 선택사항 |
| 받는사람 | String | - | - |
| 주소 | Long | - | - |
| phone | String | - | - |
| email | String | - | - |
| 배송지 | String | - | - |
| 배송지 저장유무 | Boolean | - | - |
| 할인코드 | String | - | 쿠폰과 할인코드는 동시적용 불가 |
| 쿠폰적용 여부 |  | - | - |
| 적립금사용 여부 | Integer | - | - |
| 결제수단 | String | - | - |



#### **Request Body**
```json
{
  "message" : "",
  "받는사람" : "" ,
  "주소" : "",
  "phone" : "",
  "email" : "",
  "배송지 저장여부" : "",
  "배송지" : "",
  "할인코드" : "",
  "쿠폰적용 여부" : "",
  "적립금사용 여부" : "",
  "결제 수단" : ""
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
    "productId" : ,
    "productList" : "",
    "imageUrl" : "",
    "option" : "",
    "count" : ,
    "price" : ,
    "totalDiscountPrice" : "",
    "coupon" : "",
    "쿠폰 결제 조건" : ,
    "적립금 잔액" : ,
    "적용금액" : ,
    "결제정보" : ,
    "적립혜택" : 
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항
쿠폰에 표시되야하는 것 :
* 쿠폰이름
* 유효기간
* 사용가능여부
* 가격 할인 총가격 ( 상품 할인, 적립 가능유무, 배송비 할인, 주문서 할인??)

-----

<!-- <img src="payment_details/p1 (11).png" style="width: 500px; height: auto;" alt="결제상세11"> -->

<img src="p1 (11).png" style="width: 500px; height: auto;" alt="결제상세11">

<!-- <img src="payment_details/p1 (12).png" style="width: 500px; height: auto;" alt="결제상세12"> -->

<img src="p1 (12).png" style="width: 500px; height: auto;" alt="결제상세12">

<!-- <img src="payment_details/p1 (13).png" style="width: 500px; height: auto;" alt="결제상세13"> -->

<img src="p1 (13).png" style="width: 500px; height: auto;" alt="결제상세13">

<!-- <img src="payment_details/p1 (14).png" style="width: 500px; height: auto;" alt="결제상세14"> -->

<img src="p1 (14).png" style="width: 500px; height: auto;" alt="결제상세14">

<!-- <img src="payment_details/p1 (15).png" style="width: 500px; height: auto;" alt="결제상세15"> -->

<img src="p1 (15).png" style="width: 500px; height: auto;" alt="결제상세15">

<!-- <img src="payment_details/p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16"> -->

<img src="p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16">

<!-- <img src="payment_details/p1 (17).png" style="width: 500px; height: auto;" alt="결제상세17"> -->

