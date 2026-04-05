<!-- <img src="payment_details/p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1"> -->

<img src="p1 (1).png" style="width: 500px; height: auto;" alt="결제상세1">

---

Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| **cartItemIds** | String | Y | 장바구니에서 선택해서 넘어온 아이템 ID들 (예: "101,102") |
| **orderId** | String | N | (이미 생성된 주문이 있다면) 해당 주문의 고유 번호 |

* **Request Body**:
```json
{
  "selectionType": "회원 정보와 동일",
  "receiverName": "전인렬",
  "zipCode": "46915",
  "baseAddress": "부산광역시 사상구...",
  "detailAddress": "",
  "phoneNumber": "010-5910-6393",
  "email": "dlsfuf222@gmail.com",
  "deliveryMessage": "-- 메시지 선택 (선택사항) --"
}
```

---

**GET** `/api/v1/orders/checkout`

* **Success Response**:
```json
{
  "status": "success",
  "data": {
    "title": "주문/결제",
    "cartCount": 2,
    "userInformation": {
      "name": "전인렬",
      "phoneNumber": "010-5910-6393",
      "email": "dlsfuf222@gmail.com"
    },
    "orderItems": [
      {
        "name": "어글어글 강원도 대관령 무염 황태채 40g",
        "count": 1,
        "price": 12000
      },
      {
        "name": "어글어글 우유껌 50g 7종",
        "option": "제주 당근 우유껌 50g",
        "count": 1,
        "price": 6500
      }
    ],
    "shippingFee": 5000
  }
}
```



## **참고사항**



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

## 엔드포인트 상세
**GET** `/api/v1/delivery/messages`

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
|  |  |  |  |

#### **Request Body (JSON)**

```json
{
}
```

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

<!-- <img src="payment_details/p1 (8).png" style="width: 500px; height: auto;" alt="결제상세8"> -->

<img src="p1 (8).png" style="width: 500px; height: auto;" alt="결제상세8">


## 엔드포인트 상세
**PUT** `/api/v1/orders/checkout/delivery`

---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | - | - |

#### **Request Body (JSON)**

```json
{
  "receiverName": "전인렬",
  "zipCode": "46915",
  "baseAddress": "부산 사상구 운산로 25 덕양환신아파트",
  "detailAddress": "나머지 주소 입력분", 
  "phoneNumber": "010-5910-6393",
  "email": "dlsfuf222@gmail.com",
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
  "data": {
    "receiverName": "전인렬",
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

---

<!-- <img src="payment_details/p1 (9).png" style="width: 500px; height: auto;" alt="결제상세9"> -->

<img src="p1 (9).png" style="width: 500px; height: auto;" alt="결제상세9">

---

### **주문/결제 상세 정보 조회 (GET)**
**엔드포인트:** `GET /api/v1/orders/checkout`

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| **cartItemIds** | String | Y | 주문할 장바구니 아이템 ID 목록 (예: "105,106") |

#### **Request Body**
```json
{
}
```

#### **Success Response (JSON)**

```json
{
  "status": "success",
  "data": {
    "pageTitle": "주문/결제",
    "orderItems": [
      {
        "productName": "어글어글 강원도 대관령 무염 황태채 40g",
        "quantity": 1,
        "price": 12000,
        "imageUrl": "https://swiffy.com/items/fish_snack.png"
      },
      {
        "productName": "어글어글 우유껌 50g 7종",
        "optionName": "제주 당근 우유껌 50g",
        "quantity": 1,
        "price": 6500,
        "imageUrl": "https://swiffy.com/items/milk_gum.png"
      }
    ],
    "paymentSummary": {
      "totalProductPrice": 18500,
      "shippingFee": 5000,
      "totalDiscount": 0,
      "finalPaymentAmount": 23500
    }
  }
}
```

---

### **참고사항**
* **orderItems**: 사진 왼쪽 빨간 박스의 상품 2종 정보를 담고 있습니다.
* **paymentSummary**: 사진 오른쪽 빨간 박스의 **배송비 5,000원**과 **최종 결제 금액 23,500원**을 계산해서 보여줍니다.

<!-- <img src="payment_details/p1 (10).png" style="width: 500px; height: auto;" alt="결제상세10"> -->

<img src="p1 (10).png" style="width: 500px; height: auto;" alt="결제상세10">

---

**엔드포인트:** `POST /api/v1/orders/payment`

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | Y | - |

#### **Request Body (JSON)**

```json
{
  "orderId": "ORD-20260405-001",
  "paymentMethod": "TOSS_PAY", // 사진의 'toss pay' 선택 반영
  "finalAmount": 23500, // 사진 하단 버튼의 '23,500원'
  "savePaymentMethod": true, // 사진 하단 '결제수단과 입력정보를 다음에도 사용' 체크 여부
  "paymentVendor": "TOSS"
}
```

#### **Success Response (JSON)**

```json
{
  "status": "success",
  "message": "결제가 성공적으로 완료되었습니다.",
  "data": {
    "receiptId": "REC-99823445",
    "paymentMethod": "토스페이",
    "paidAt": "2026-04-05 14:40:00",
    "finalAmount": 23500
  }
}
```

---

### **참고사항**
* **결제수단 / toss pay**: 사용자가 여러 수단 중 토스페이를 클릭했음을 나타내며, `paymentMethod` 필드로 전달됩니다.
* **결제수단과 입력정보들 다음에도 사용**: 이 체크박스는 사용자의 편의를 위해 결제 수단을 저장할지 결정하는 `savePaymentMethod` 값으로 매핑됩니다.
* **23,500원 결제하기**: 이 버튼을 누르는 순간 위의 `Request Body`와 함께 POST 요청이 날아가게 됩니다.



-----

<!-- <img src="payment_details/p1 (11).png" style="width: 500px; height: auto;" alt="결제상세11"> -->

<img src="p1 (11).png" style="width: 500px; height: auto;" alt="결제상세11">

<!-- <img src="payment_details/p1 (12).png" style="width: 500px; height: auto;" alt="결제상세12"> -->

<img src="p1 (12).png" style="width: 500px; height: auto;" alt="결제상세12">

<!-- <img src="payment_details/p1 (13).png" style="width: 500px; height: auto;" alt="결제상세13"> -->

<img src="p1 (13).png" style="width: 500px; height: auto;" alt="결제상세13">

<!-- <img src="payment_details/p1 (14).png" style="width: 500px; height: auto;" alt="결제상세14"> -->

<img src="p1 (14).png" style="width: 500px; height: auto;" alt="결제상세14">

---

### **주문 완료 상세 정보 조회 (GET)**
**엔드포인트:** `GET /api/v1/orders/success/{orderId}`

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| **orderId** | String | Y | 방금 생성이 완료된 주문 번호 (예: "20260331-0000194") |

#### **Request Body**
```json
{
}
```

#### **Success Response (JSON)**

```json
{
  "status": "success",
  "data": {
    "orderSummary": {
      "message": "고객님의 주문이 정상적으로 완료되었습니다.",
      "orderNumber": "20260331-0000194",
      "totalPaymentAmount": 23500
    },
    "paymentMethodInfo": {
      "methodTitle": "결제수단",
      "selectedMethod": "토스페이 간편결제"
    },
    "deliveryInfo": {
      "receiverName": "전인렬",
      "receiverEmail": "dlsfuf222@gmail.com",
      "fullAddress": "46915 부산 사상구 운산로 25 동양환신아파트 102동 408호",
      "phoneNumber": "010-5910-6393",
      "deliveryRequest": "부재 시 문 앞에 놓아주세요."
    }
  }
}
```

---

### **참고사항**

---

<!-- <img src="payment_details/p1 (15).png" style="width: 500px; height: auto;" alt="결제상세15"> -->

<img src="p1 (15).png" style="width: 500px; height: auto;" alt="결제상세15">

---

### **주문/결제 상세 정보 조회 (GET)**
**엔드포인트:** `GET /api/v1/orders/checkout`

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| **cartItemIds** | String | Y | 주문할 장바구니 아이템 ID 목록 (예: "105,106") |

#### **Request Body**
```json
{
}
```

#### **Success Response (JSON)**

```json
{
  "status": "success",
  "data": {
    "pageTitle": "주문/결제",
    "orderItems": [
      {
        "productName": "어글어글 강원도 대관령 무염 황태채 40g",
        "quantity": 1,
        "price": 12000,
        "imageUrl": "https://swiffy.com/items/fish_snack.png"
      },
      {
        "productName": "어글어글 우유껌 50g 7종",
        "optionName": "제주 당근 우유껌 50g",
        "quantity": 1,
        "price": 6500,
        "imageUrl": "https://swiffy.com/items/milk_gum.png"
      }
    ],
    "paymentSummary": {
      "totalProductPrice": 18500,
      "shippingFee": 5000,
      "totalDiscount": 0,
      "finalPaymentAmount": 23500
    }
  }
}
```

---

### **참고사항**
* **orderItems**: 사진 왼쪽 빨간 박스의 상품 2종 정보를 담고 있습니다.
* **paymentSummary**: 사진 오른쪽 빨간 박스의 **배송비 5,000원**과 **최종 결제 금액 23,500원**을 계산해서 보여줍니다.

-----

<!-- <img src="payment_details/p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16"> -->

<img src="p1 (16).png" style="width: 500px; height: auto;" alt="결제상세16">

<!-- <img src="payment_details/p1 (17).png" style="width: 500px; height: auto;" alt="결제상세17"> -->
