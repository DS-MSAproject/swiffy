### 1. API 개요
* **Base URL:** `https://api.example.com/api/v1`
* **Authentication:** Bearer Token (Header: `Authorization: Bearer {YOUR_TOKEN}`)

<img src="1.png" style="width: 500px; height: auto;" alt="설명">
<img src="2.png" style="width: 500px; height: auto;" alt="설명">

## 프로필

### 엔드포인트 상세
`GET /users/profile`

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| - | - | - | - |

#### **Request Body**

#### **Success Response**
* **Code:** `200 OK`
* **Response Headers:**
    * `Content-Type: application/json; charset=utf-8`
* **Content:**
  
```json
{
  "status": "success",
  "data": {
    "user_summary": {
      "id": 1,
      "name": "김선국",
      "greeting_message": "김선국님 안녕하세요!",
      "membership_level": "일반회원"
    },
    "benefits": {
      "points": 2000,
      "coupon_count": 0,
      "order_total_count": 0,
      "deposit_balance": 0
    },
    "order_status_summary": {
      "recent_period": "최근 3개월",
      "main_statuses": {
        "pending_payment": 0,
        "preparing": 0,
        "shipping": 0,
        "delivered": 0
      },
      "sub_statuses": {
        "cancelled": 0,
        "exchanged": 0,
        "returned": 0
      }
    },
    "activity_counts": {
      "wishlist_count": 0,
      "post_count": 0,
      "regular_delivery_count": 0
    }
  }
}
```
-----------------------------------------------------------------
<img src="4.png" style="width: 500px; height: auto;" alt="설명">

## 회원정보 수정(삭제 고려)

### 엔드포인트 상세
```PUT /users/profile```

#### **Request Parameters**

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | 본인 확인을 위한 인증 토큰 |
| `Content-Type` | `application/json` | ✅ | 요청 본문의 데이터 형식 |

#### **Request Body (JSON)**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `name` | `String` | ✅ | 변경할 실명 |
| `phone_number` | `String` | ✅ | 휴대전화 번호 (010-0000-0000) |
| `status` | `String` | ✅ | 이메일 주소 (형식 검증 필요) |
| `page` | `Object` | ❌ | 주소 정보 (입력 시에만 업데이트) |
| `marketing_consent` | `Object` | ✅ | 수신 동의 여부 (SMS, Email) |

#### **Request Body Example**
```json
{
  "name": "김선국",
  "phone_number": "010-1234-5678",
  "email": "seonguk@example.com",
  "address": {
    "zip_code": "48058",
    "base_address": "부산광역시 해운대구 우동",
    "detail_address": "센텀중앙로 123"
  },
  "marketing_consent": {
    "sms_allowed": true,
    "email_allowed": false
  }
}
```
#### Success Response
* **Code:** `200 OK`
* **Content:**
```json
{
  "status": "success",
  "message": "회원 정보가 성공적으로 수정되었습니다.",
  "data": {
    "updated_at": "2026-04-03T17:15:00Z"
  }
}

```
## 회원정보 수정(Response 확장된 내용)

### 엔드포인트 상세
```PUT /users/profile``` : 사용자의 비밀번호 변경, 연락처, 주소 및 마케팅 수신 여부를 업데이트합니다.

#### **Request Parameters**

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | 본인 확인을 위한 인증 토큰 |
| `Content-Type` | `application/json` | ✅ | 요청 본문의 데이터 형식 |

#### **Request Body (JSON)**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `current_password` | `String` | ✅ | 정보 수정을 위한 현재 비밀번호 확인 |
| `new_password` | `String` | ❌ | 변경할 새 비밀번호 (변경 시에만 입력) |
| `confirm_password` | `String` | ❌ | 새 비밀번호 확인 (프론트/백엔드 교차 검증) |
| `phone_number` | `String` | ✅ | 휴대전화 번호 |
| `email` | `String` | ✅ | 이메일 주소 |
| `address` | `Object` | ❌ | 주소 정보 (최초 등록 또는 변경 시) |
| `marketing_consent` | `Boolean` | ✅ | 수신여부 (true: 수신함 / false: 수신안함) |

#### **Success Response**
* **Code:** `200 OK`
* **Content:** 수정 후 최신화된 정보를 반환합니다.
```json
{
  "status": "success",
  "data": {
    "user_id": "seonguk95",
    "name": "김선국",
    "email": "seonguk@example.com",
    "phone_number": "010-1234-5678",
    "address": {
      "zip_code": "48058",
      "base_address": "부산광역시 해운대구 우동",
      "detail_address": "센텀중앙로 123",
      "is_first_registration": false
    },
    "marketing_consent": true,
    "updated_at": "2026-04-04T15:30:00Z"
  }
}
```
------------------------------------------
### 회원 탈퇴 처리
```DELETE /users``` : 서비스 이용을 종료하고 회원 탈퇴를 처리합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | 본인 확인을 위한 인증 토큰 |

#### **Request Body (JSON)**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `password` | `String` | ✅ | 탈퇴 확정을 위한 비밀번호 재확인 |
| `reason` | `String` | ❌ | 탈퇴 사유 (서비스 개선 목적) |

#### **Success Response**
* **Code:** `200 OK`
* **Content:**
```json
{
  "status": "success",
  "message": "회원 탈퇴가 완료되었습니다. 그동안 이용해 주셔서 감사합니다.",
  "data": {
    "withdrawal_date": "2026-04-04T15:40:00Z"
  }
}
```
-----------------------------------------------------------------
<img src="3.png" style="width: 500px; height: auto;" alt="설명">

## 주문 조회

### 엔드포인트 상세
```GET /orders```

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `start_date` | `String` | ❌ | 조회 시작일 (YYYY-MM-DD, 기본값: 3개월 전) |
| `end_date` | `String` | ❌ | 조회 종료일 (YYYY-MM-DD, 기본값: 오늘) |
| `status` | `String` | ❌ | 배송 상태 필터 (SHIPPING, DELIVERED 등) |
| `page` | `Integer` | ❌ | 페이지 번호 (기본값: 1) |

#### **Request Body**

#### **Success Response**
* **Code:** `200 OK`
* **Content:**
```json
{
  "status": "success",
  "data": {
    "total_orders": 12,
    "current_page": 1,
    "orders": [
      {
        "order_number": "20260403-0000123",
        "order_date": "2026-04-03T14:20:00Z",
        "order_status": "SHIPPING",
        "order_status_text": "배송중",
        "items": [
          {
            "product_id": 101,
            "title": "[리틀버디] 고단백 연어 사료 2kg",
            "image_url": "https://cdn.petfood.com/products/salmon_01.jpg",
            "option": "입자크기: 소립",
            "price": 25000,
            "quantity": 2
          }
        ],
        "payment_info": {
          "total_product_amount": 50000,
          "shipping_fee": 3000,
          "total_discount_amount": 5000,
          "final_payment_amount": 48000
        }
      }
    ]
  }
}
```
### 추후 고려 사항
```
배송상태 ex) 배송중 / 총 결제금액(상품구매금액 + 배송비 - 총할인금액)
배송조회 누르면 배송정보를 뿌림(보류)
구매후기 (없으면 구매후기 작성 페이지로)
주문조회 10개씩
```
----------------------------------------------------------------------
## 상세보기

### 엔드포인트 상세
```GET /orders{order_number}```
 
#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `order_nember` | `String` | ✅ | 조회를 원하는 주문 번호 (Path Variable) |

#### **Request Body**

#### **Success Response**
* **Code:** `200 OK`
* **Content:**
```json
{
  "status": "success",
  "data": {
    "order_info": {
      "order_number": "20260403-0000123",
      "order_date": "2026-04-03T14:20:00Z",
      "orderer_name": "김선국",
      "order_status": "DELIVERED",
      "order_status_text": "배송완료",
      "total_item_count": 3
    },
    "order_items": [
      {
        "product_id": 501,
        "image_url": "https://cdn.petfood.com/products/salmon_01.jpg",
        "title": "[유기농] 프리미엄 연어&고구마 건식 사료",
        "quantity": 1,
        "option": "중량: 5kg / 알갱이: 소립",
        "status": "배송완료"
      }
    ],
    "payment_info": {
      "paid_amount": 45000,
      "discount_amount": 5000,
      "shipping_fee": 3000,
      "estimated_total_amount": 43000
    },
    "shipping_info": {
      "recipient_name": "김선국",
      "zip_code": "48058",
      "base_address": "부산광역시 해운대구 우동",
      "detail_address": "센텀중앙로 123",
      "phone_number": "010-1234-5678",
      "shipping_message": "문 앞에 놓아주세요."
    },
    "refund_info": {
      "product_name": "가수분해 닭가슴살 져키",
      "quantity": 1,
      "refund_date": "2026-04-05T10:00:00Z",
      "refund_status": "COMPLETED",
      "refund_status_text": "환불완료",
      "total_refund_amount": 12000,
      "refund_method": "신용카드 부분취소"
    }
  }
}
```
------------------------------------------------------------------
<img src="3_1.png" style="width: 500px; height: auto;" alt="설명">

## 취소/교환반품 내역

### 엔드포인트 상세
```GET /orders/{order_number}/cs-history``` : 해당 주문에서 발생한 취소, 교환, 반품에 대한 상세 이력과 진행 상태를 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**

#### **Request Body**

#### **Success Response**
* **Code:** `200 OK`
* **Content:**
```json
{
  "status": "success",
  "data": {
    "order_number": "20260403-0000123",
    "cs_summary": {
      "has_history": true,
      "cancel_count": 1,
      "exchange_count": 1,
      "return_count": 0
    },
    "cancellation_details": [
      {
        "cancel_id": "CAN-9982",
        "product_name": "[리틀버디] 고단백 연어 사료 2kg",
        "quantity": 1,
        "reason": "단순 변심 (주문 실수)",
        "request_date": "2026-04-03T15:00:00Z",
        "status": "COMPLETED",
        "status_text": "취소 완료"
      }
    ],
    "exchange_details": [
      {
        "exchange_id": "EXC-1102",
        "original_product": "가수분해 닭가슴살 져키",
        "exchange_product": "가수분해 오리고기 져키",
        "reason": "상품 오배송 (맛 변경 요청)",
        "status": "RESIPPING",
        "status_text": "교환 상품 배송 중",
        "reshipping_tracking_number": "CJ대한통운 123456789",
        "request_date": "2026-04-04T10:00:00Z"
      }
    ],
    "return_details": [
      {
        "return_id": "RET-5541",
        "product_name": "프리미엄 덴탈껌 (30개입)",
        "quantity": 1,
        "reason": "상품 파손 (포장지 훼손)",
        "pickup_status": "PICKUP_COMPLETED",
        "pickup_status_text": "수거 완료",
        "refund_status": "PROCESSING",
        "refund_status_text": "환불 처리 중",
        "request_date": "2026-04-05T09:30:00Z"
      }
    ]
  }
}
```

Res(해야됨)
```
기간 (오늘 / 1개월 / 3개월 / 6개월 )
상세날짜 정보
```
----------------------------------------------------------------------------
<img src="5.png" style="width: 500px; height: auto;" alt="설명">

## 관심상품리스트

### 엔드포인트 상세
```GET /users/wishlist``` : 사용자가 '좋아요' 또는 '찜'한 관심 상품 리스트를 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `page` | `Integer` | ❌ | 조회할 페이지 번호 (기본값: 1) |
| `limit` | `Integer` | ❌ | 한 페이지에 보여줄 상품 개수 (기본값: 20) |

#### **Success Response**
* **Code:** `200 OK`
* **Response Headers:**
  * `Content-Type: application/json; charset=utf-8`
* **content:**
```json
{
  "status": "success",
  "data": {
    "total_count": 5,
    "wishlist": [
      {
        "product_id": 1024,
        "image_url": "https://cdn.petfood.com/products/beef_stew_01.jpg",
        "title": "[수제간식] 소고기 야채 스튜 150g",
        "original_price": 12000,
        "discount_price": 9900,
        "option_summary": "용량: 150g / 패키지: 파우치",
        "is_out_of_stock": false,
        "added_at": "2026-04-01T10:30:00Z"
      },
      {
        "product_id": 882,
        "image_url": "https://cdn.petfood.com/products/dental_chew.jpg",
        "title": "눈물 자국 개선 덴탈껌 30개입",
        "original_price": 18000,
        "discount_price": 18000,
        "option_summary": "사이즈: S (소형견용)",
        "is_out_of_stock": true,
        "added_at": "2026-03-28T15:45:12Z"
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="5_1.png" style="width: 500px; height: auto;" alt="설명">

### 엔드포인트 상세
```GET /users/{id}/wishlist``` : 사용자의 관심 상품 리스트를 조회하며, 장바구니 연동 및 주문 여부 상태를 포함합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "total_count": 3,
    "wishlist": [
      {
        "wishlist_id": 5001,
        "product_id": 1024,
        "image_url": "https://cdn.petfood.com/products/beef_stew.jpg",
        "title": "[수제간식] 소고기 야채 스튜 150g",
        "price": 9900,
        "selected_option": {
          "option_id": 201,
          "option_name": "용량: 150g",
          "extra_price": 0
        },
        "cart_action": {
          "can_add_to_cart": true,
          "stock_quantity": 50,
          "message": "장바구니 담기 가능"
        },
        "order_status": {
          "is_ordered": true,
          "last_order_date": "2026-03-15T09:00:00Z"
        },
        "is_deleted": false,
        "added_at": "2026-04-01T10:30:00Z"
      },
      {
        "wishlist_id": 5002,
        "product_id": 882,
        "image_url": "https://cdn.petfood.com/products/dental_chew.jpg",
        "title": "눈물 자국 개선 덴탈껌 30개입",
        "price": 18000,
        "selected_option": {
          "option_id": null,
          "option_name": "기본 선택",
          "extra_price": 0
        },
        "cart_action": {
          "can_add_to_cart": false,
          "stock_quantity": 0,
          "message": "품절된 상품입니다."
        },
        "order_status": {
          "is_ordered": false,
          "last_order_date": null
        },
        "is_deleted": false,
        "added_at": "2026-03-28T15:45:12Z"
      }
    ]
  }
}
```
```
백엔드에서 5개이상 있으면 문구가 뜨게 (뭔지 모르겠음. 일단 놔둡니다.선국)
```
--------------------------------------------------------------------
<img src="6.png" style="width: 500px; height: auto;" alt="설명">

## 적립금

### 엔드포인트 상세
```GET /users/points``` : 사용자의 적립금 요약 정보와 상세 이용 내역을 조회합니다

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `page` | `Integer` | ❌ | 내역 조회를 위한 페이지 번호 (기본값: 1) |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "summary": {
      "total_accumulated_points": 25000,
      "available_points": 2000,
      "used_points": 23000,
      "pending_refund_points": 5000
    },
    "history": [
      {
        "point_id": 105,
        "event_date": "2026-04-04T10:00:00Z",
        "description": "상품 구매 시 적립 ([유기농] 연어 사료)",
        "amount": 450,
        "type": "EARNED",
        "type_text": "적립"
      },
      {
        "point_id": 102,
        "event_date": "2026-04-01T15:30:00Z",
        "description": "주문 결제 시 사용 (주문번호: 20260401-001)",
        "amount": -5000,
        "type": "USED",
        "type_text": "사용"
      },
      {
        "point_id": 98,
        "event_date": "2026-03-25T09:12:00Z",
        "description": "반품 처리로 인한 적립금 환불 예정",
        "amount": 5000,
        "type": "REFUND_PENDING",
        "type_text": "환불예정"
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="6_1.png" style="width: 500px; height: auto;" alt="설명">

## 적립내역

### 엔드포인트 상세
```GET /users/points/history``` : 사용자의 적립금 적립 및 사용 내역을 10개씩 페이징하여 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `page` | `Integer` | ❌ | 조회할 페이지 번호 (기본값: 1) |
| `limit` | `Integer` | ❌ | 페이지 당 항목 수 (기본값: 10) |
| `filter` | `String` | ❌ | 필터링 (ALL, EARNED, USED) |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "pagination": {
      "total_count": 45,
      "current_page": 1,
      "total_pages": 5,
      "limit": 10
    },
    "history": [
      {
        "event_date": "2026-04-04T17:30:00Z",
        "description": "상품 구매 적립 (주문번호: 20260404-0012)",
        "amount": 1250,
        "type": "EARNED",
        "type_text": "적립",
        "balance_after": 5250
      },
      {
        "event_date": "2026-04-01T12:00:00Z",
        "description": "주문 시 적립금 사용 (주문번호: 20260401-0005)",
        "amount": -3000,
        "type": "USED",
        "type_text": "사용",
        "balance_after": 4000
      },
      {
        "event_date": "2026-03-28T09:00:00Z",
        "description": "리뷰 작성 보상 적립",
        "amount": 500,
        "type": "EARNED",
        "type_text": "적립",
        "balance_after": 7000
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="8.png" style="width: 500px; height: auto;" alt="설명">

## 쿠폰

### 엔드포인트 상세
```GET /users/coupons```: 사용자가 보유한 쿠폰 리스트를 10개씩 페이징하여 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `page` | `Integer` | ❌ | 조회할 페이지 번호 (기본값: 1) |
| `status` | `String` | ❌ | 쿠폰 상태 필터 (AVAILABLE, USED, EXPIRED) |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "pagination": {
      "total_count": 12,
      "current_page": 1,
      "total_pages": 2,
      "limit": 10
    },
    "coupons": [
      {
        "coupon_id": "CPN-2026-001",
        "coupon_name": "신규 가입 축하 10% 할인 쿠폰",
        "discount_rate": 10,
        "discount_type": "PERCENTAGE",
        "is_point_earnable": false,
        "expiry_date": "2026-05-01T23:59:59Z",
        "remarks": "3만원 이상 구매 시 사용 가능 / 타 쿠폰과 중복 불가",
        "status": "AVAILABLE",
        "status_text": "사용가능"
      },
      {
        "coupon_id": "CPN-2026-005",
        "coupon_name": "리틀버디 첫 구매 감사 쿠폰",
        "discount_value": 5000,
        "discount_type": "FIXED_AMOUNT",
        "is_point_earnable": true,
        "expiry_date": "2026-04-30T23:59:59Z",
        "remarks": "전 상품 사용 가능 / 적립금 중복 적립 가능",
        "status": "AVAILABLE",
        "status_text": "사용가능"
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="8_1.png" style="width: 500px; height: auto;" alt="설명">
<img src="8_2.png" style="width: 500px; height: auto;" alt="설명">

## 쿠폰인증내역 

### 엔드포인트 상세
```GET /users/coupons/registrations```: 사용자가 코드를 입력하여 인증/등록한 쿠폰의 상세 내역을 10개씩 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `page` | `Integer` | ❌ | 조회할 페이지 번호 (기본값: 1) |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "pagination": {
      "total_count": 25,
      "current_page": 1,
      "total_pages": 3,
      "limit": 10
    },
    "registration_history": [
      {
        "auth_id": 501,
        "auth_date": "2026-04-04T18:00:00Z",
        "auth_code": "PET-FOOD-2026-SALE",
        "coupon_name": "[인증] 봄맞이 전품목 15% 할인 쿠폰",
        "discount_rate": 15,
        "is_point_earnable": false,
        "status": "REGISTERED",
        "status_text": "인증완료",
        "remarks": "인증 후 30일 이내 사용 가능 / 정기배송 상품 제외"
      },
      {
        "auth_id": 482,
        "auth_date": "2026-03-20T10:15:00Z",
        "auth_code": "WELCOME-LITTLE-BUDDY",
        "coupon_name": "신규 가입 기념 5,000원 할인 쿠폰",
        "discount_value": 5000,
        "is_point_earnable": true,
        "status": "USED",
        "status_text": "사용완료",
        "remarks": "전 상품 사용 가능 / 적립금 중복 혜택 적용"
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="9.png" style="width: 500px; height: auto;" alt="설명">
<img src="10.png" style="width: 500px; height: auto;" alt="설명">
<img src="11.png" style="width: 500px; height: auto;" alt="설명">

## 게시물관리

--------------------------------------------------------------------
<img src="12.png" style="width: 500px; height: auto;" alt="설명">

## 주소록관리1

### 엔드포인트 상세

* ```GET /users/addresses```: 사용자가 저장한 모든 배송지 리스트를 조회합니다.
* ```POST /users/addresses```: 새로운 배송지 추가. 이때 address_name이 비어있으면 서버에서 "미지정"으로 저장.
* ```PUT /users/addresses```: 특정 배송지 정보 수정.
* ```DELETE /users/addresses```: 배송지 삭제. (단, 기본 배송지는 삭제 전 경고 또는 다른 주소로 기본값 이전 로직 필요)

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "total_count": 2,
    "addresses": [
      {
        "address_id": 101,
        "address_name": "우리집",
        "is_default": true,
        "recipient_name": "김선국",
        "zip_code": "48058",
        "base_address": "부산광역시 해운대구 우동",
        "detail_address": "센텀중앙로 123",
        "country_code": "KR (+82)",
        "phone_number": "010-1234-5678"
      },
      {
        "address_id": 105,
        "address_name": "미지정",
        "is_default": false,
        "recipient_name": "이멍멍",
        "zip_code": "06035",
        "base_address": "서울특별시 강남구 가로수길",
        "detail_address": "45-6 3층",
        "country_code": "KR (+82)",
        "phone_number": "010-9876-5432"
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="13.png" style="width: 500px; height: auto;" alt="설명">

## 주소록관리2

### 엔드포인트 상세
```POST /users/addresses```: (신규 등록) 새로운 배송지를 추가합니다.

#### **Request Body (JSON)**
```json
{
  "address_name": "우리집", 
  "recipient_name": "홍길동",
  "zip_code": "48058",
  "base_address": "부산광역시 해운대구 우동",
  "detail_address": "센텀중앙로 123",
  "phone_number": "010-1234-5678",
  "is_default": true 
}
```
* Note: ```address_name```이 비어있을 경우 서버에서 자동으로 **"미지정"**으로 저장합니다.

```PUT /users/addresses```: (정보 수정) 기존에 저장된 특정 배송지의 정보를 수정합니다.
* **Path Variable:** ```address_id``` (수정할 배송지의 고유 번호)
* **Request Body (JSON):** 등록과 동일한 필드를 사용하며, 변경된 값만 보내거나 전체를 다시 보냅니다

```DELETE /users/addresses```: (삭제 요청) 더 이상 사용하지 않는 배송지 정보를 삭제합니다.

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "message": "배송지 정보가 삭제되었습니다.",
  "data": {
    "deleted_address_id": 101
  }
}
```
**성공 응답 예시 (등록/수정 공통)**
```json
{
  "status": "success",
  "message": "배송지 정보가 성공적으로 반영되었습니다.",
  "data": {
    "address_id": 101,
    "address_name": "우리집",
    "recipient_name": "홍길동",
    "full_address": "(48058) 부산광역시 해운대구 우동 센텀중앙로 123",
    "phone_number": "010-1234-5678",
    "is_default": true,
    "updated_at": "2026-04-04T18:30:00Z"
  }
}
```

## 최근 배송지 (추가 API)

### 엔드포인트 상세
```GET /users/addresses/checkout```: 결제 화면 진입 시, 즉시 렌더링해야 할 '기본 배송지' 1건과 최근에 주문했던 '최근 배송지 이력' 리스트를 함께 조회합니다.

#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `limit` | `Integer` | ❌ | 가져올 최근 배송지 개수 (기본값: 3) |

#### **Success Response**
* **Code:** `200 OK`
* **content:**
```json
{
  "status": "success",
  "data": {
    "default_address": {
      "address_id": 101,
      "address_name": "우리집",
      "recipient_name": "김선국",
      "zip_code": "48058",
      "base_address": "부산광역시 해운대구 우동",
      "detail_address": "센텀중앙로 123",
      "phone_number": "010-1234-5678"
    },
    "recent_addresses": [
      {
        "order_number": "20260401-0005",
        "used_at": "2026-04-01T12:00:00Z",
        "recipient_name": "김선국",
        "zip_code": "48058",
        "base_address": "부산광역시 해운대구 우동",
        "detail_address": "센텀중앙로 123",
        "phone_number": "010-1234-5678",
        "shipping_message": "문 앞에 두고 벨 눌러주세요."
      },
      {
        "order_number": "20260315-0088",
        "used_at": "2026-03-15T09:30:00Z",
        "recipient_name": "이멍멍",
        "zip_code": "06035",
        "base_address": "서울특별시 강남구 가로수길",
        "detail_address": "45-6 3층",
        "phone_number": "010-9876-5432",
        "shipping_message": "도착 전 연락 바랍니다."
      }
    ]
  }
}
```
--------------------------------------------------------------------
<img src="14.png" style="width: 500px; height: auto;" alt="설명">

## 정기배송 내역 (보류?)
```
신청 내역
해지 내역
보류
```

<img src="14_1.png" style="width: 500px; height: auto;" alt="설명">

## 게시글 관리 뷰의 댓글 선택시 렌더링 화면

<img src="comments.png" style="width: 500px; height: auto;" alt="설명">


<img src="6_2.png" style="width: 500px; height: auto;" alt="설명">

**`X`**

<img src="6_3.png" style="width: 500px; height: auto;" alt="설명">

**`X`**

<img src="7.png" style="width: 500px; height: auto;" alt="설명">

**`보류`**

<img src="7_1.png" style="width: 500px; height: auto;" alt="설명">

**`보류`**

