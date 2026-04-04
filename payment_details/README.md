<!-- <img src="payment_details/p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1"> -->

<img src="p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1">

---

## 1. 주문서 초기 정보 조회 (GET)

## 엔드포인트 상세
**GET** `/api/v1/orders/checkout`

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| userId | Long | Y | 사용자 고유 번호 |
| cartItemIds | String | Y | 주문할 항목 ID들 (예: "1,2,5") |

---

## 엔드포인트 상세
**POST** `/api/v1/orders`

#### **Request Body (JSON)**
```json
{
  "userId": 1,
  "deliveryInfo": {
    "receiverName": "김민규",
    "receiverPhone": "010-2059-5477",
    "email": "gjtjfud@naver.com",
    "zipCode": "12345",
    "baseAddress": "서울특별시 강남구 테헤란로",
    "detailAddress": "101호",
    "deliveryMessage": "부재 시 문 앞에 놓아주세요"
  },
  "orderItems": [
    { "cartItemId": 105, "count": 1 },
    { "cartItemId": 106, "count": 1 }
  ],
  "paymentMethod": "CARD"
}
```

#### **Success Response**
```json
{
}
```

---

### **참고사항**



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

## 엔드포인트 상세
**GET** `/api/v1/delivery/messages`

---

#### **Success Response**

* **Code:** 200 OK
* **Content:**

```json
{
  "status": "success",
  "data": [
    { "id": 1, "message": "배송 전에 미리 연락바랍니다." },
    { "id": 2, "message": "부재 시 경비실에 맡겨주세요." },
    { "id": 3, "message": "부재 시 문 앞에 놓아주세요." },
    { "id": 4, "message": "빠른 배송 부탁드립니다." },
    { "id": 5, "message": "택배함에 보관해 주세요." },
    { "id": 6, "message": "직접 입력" }
  ]
}
```

---

## 엔드포인트 상세
**PUT** `/api/v1/orders/checkout/delivery`

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| userId | Long | Y | 주문을 진행 중인 사용자 ID |

#### **Request Body (JSON)**

```json
{
  "receiverName": "최서령",
  "zipCode": "46915",
  "baseAddress": "부산 사상구 운산로 25 덕양환신아파트",
  "detailAddress": "나머지 주소 입력분", 
  "phoneNumber": "010-2059-5477",
  "email": "gjtjfud@naver.com",
  "deliveryMessage": "부재 시 문 앞에 놓아주세요.",
  "isDefaultAddress": true
}
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
  "message": "배송지 정보가 성공적으로 반영되었습니다.",
  "data": {
    "receiverName": "최서령",
    "fullAddress": "(46915) 부산 사상구 운산로 25 덕양환신아파트 나머지 주소 입력분",
    "deliveryMessage": "부재 시 문 앞에 놓아주세요."
  }
}
```

#### **Error Response**

  * **Code:** 400 BAD REQUEST
  * **Content:** `{ "message": "필수 입력 항목(이름, 주소, 연락처)이 누락되었습니다." }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "인증되지 않은 사용자입니다." }`

---

#### **참고사항**
* **배송지 선택**: '회원 정보와 동일' 또는 '새로운 배송지' 선택에 따라 `Request Body`의 값이 달라집니다. 사진에서는 '최서령'이라는 이름이 입력되어 있으므로 해당 값이 전달됩니다.
* **나머지 주소**: 사진 중앙의 빨간 박스인 **'나머지 주소(선택 입력 기능)'** 필드는 `detailAddress`에 매핑됩니다.
* **배송 메시지**: 하단 드롭다운에서 선택한 **"부재 시 문 앞에 놓아주세요."**라는 문구가 `deliveryMessage`로 전달됩니다. 만약 '직접 입력'을 선택하면 사용자가 타이핑한 내용이 전송됩니다.

---

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
| totalPrice | Integer | - | - |
| 총 배송비 | Integer | - | - |
| totalDiscountPrice | Integer | - | - |
| coupon | String | - |  |
| couponCount | Integer | - | 유저가 가지고 있는 갯수 |
| 쿠폰 결제 조건 | String | - | - |
| 적립금 | Integer | - | - |
| 적립금사용 여부 | Integer | - | - |
| 적용금액 | Integer | - | 총 할인+쿠폰+적립가격 |
| 주문상품총가격 | Integer | - | |
| 적립혜택 | Integer | - | 1% 소수점 버림 |
| message | String | - | 선택사항 |
| 받는사람 | String | - | - |
| phone | String | - | - |
| email | String | - | - |
| 배송지 | String | - | - |
| 배송지 저장유무 | Boolean | - | - |
| 할인코드 | String | - | 쿠폰과 할인코드는 동시적용 불가 |
| 쿠폰적용 여부 |  | - | - |
| 결제수단 | String | - | - |



#### **Request Body**
```json
{
  "message" : "",
  "받는사람" : "" ,
  "phone" : "",
  "email" : "",
  "주소" : "",
  "배송지 저장여부" : "",
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
    "주문상품" : ,
    "배송비" : ,
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

=======
## 엔드포인트 상세

`POST` /api/v1/payment  
// 주문완료라 잘모르겠습니다.


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| 주문번호 | String | - | - |
| 결제금액 | String | - | "%,d원" |
| 결제수단 | String | - | - |
| 배송지 | String | - | - |
| 받는사람 | Integer | - | - |
| 주소 | Integer | - | - |
| phone | Integer | - | |
| email | String | - | - |
| message | Integer | - | - |
| productImageUrl | String | - | - |
| productName | String | - | - |
| option | Integer | - | 상품갯수 |
| price | Integer | - | - |
| productImageUrl | String | - |  |
| productName | String | - |  |
| option | String | - |  |
| price | Integer | - |  |
| 배송비 | Integer | - |  |
| 결제금액 | String | - | - |
| 회원 적립금 | Integer | - | - |
| 적립 예정금액 | Integer | - |  |

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
    "주문번호" : ,
    "결제금액" : "",
    "결제수단" : "",
    "받는사람" : ,
    "주소" : ,
    "phone" : "",
    "email" : "",
    "message" : ,
    "productImageUrl" : ,
    "productName" : ,
    "option" : ,
    "price" : ,
    "주문상품" : ,
    "배송비" : ,
    "결제금액" : ,
    "적립금" : ,
    "적립 예정금액" : 
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

<!-- <img src="payment_details/p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16"> -->

<img src="p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16">

<!-- <img src="payment_details/p1 (17).png" style="width: 500px; height: auto;" alt="결제상세17"> -->
