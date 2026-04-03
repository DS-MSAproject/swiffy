#### **Request Headers** 공통사항(리뷰쓰기 제외)
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

> **Base URL:** `https://api.example.com/api/v1
---
<img src="1.png" style="width: 500px; height: auto;" alt="설명">

2
<img src="2.png" style="width: 500px; height: auto;" alt="설명">


## 3

<img src="3.png" style="width: 500px; height: auto;" alt="설명">

## 4

### `POST` /carts     
장바구니 버튼
<img src="4.png" style="width: 500px; height: auto;" alt="설명">

#### **Request Body**
```json
{
  "productId" : "",  // 어떤 상품? (추천상품도 포함한 템플릿)
    "selectedOptions" [{
      "optionId" : "우유맛",
      "Quantity" : "2",
    },
    "selectedOptions" {
      "optionId" : "바나나맛",
      "Quantity" : "2",
    },
  ],
  "totalPrice" : "" (프론트에서 계산한 총액, 백엔드 검증용)
}
```
#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
  "data": {
    "cartItemId": "",       // 💡 방금 생성된 장바구니 아이템 고유 ID
    "productId": 30,          // 상품 ID
    "productName": "테린 내 맘대로 세트",
    "quantity": 2,            // 최종 담긴 수량
    "totalCartCount": 5,      // 💡 현재 장바구니에 담긴 총 아이템 개수 (상단 배지 업데이트용)
    "message": "장바구니에 상품을 담았습니다.",
    "redirectUrl": "/cart"    // [장바구니 가기] 버튼 클릭 시 이동할 경로
  }
}
```
  
#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`
### 참고사항
---

## 5
<img src="5.png" style="width: 500px; height: auto;" alt="설명">

### `GET` /reviews      
상품 후기 탭 클릭시 

---


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | - | - |
| page | Integer | - | - |
| size | Integer | - | - |
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
    "reviewHeader": {
      "starAverage" : "",
      "totalReviewNumber" : "",
      "ratioStar5" : "", // 5점 비율
      중략
      "ratioStar1" : "", // 1점 비율
      "preferenceRatio" : "", // 선호도 비율
      "repurchaseRatio" : ""  // 재구매 비율
    },
    "reviewBody" : {
      "reviewId" : "",
      "reviewMediaUrl" : "",
      "likeCount" : "",
      "content" : "",
      "star" : "",
      "reviewDetailUrl : ""
    }
    "pageInfo" {
      "pageable": {
        "sort": {
          "sorted": true,    // 정렬 여부
          "unsorted": false,
          "empty": false
        },
        "offset": 0,         // 시작 지점 (인덱스)
        "pageNumber": 0,     // 💡 현재 페이지 번호 (0부터 시작)
        "pageSize": 10,       // 💡 한 페이지당 데이터 개수
        "paged": true,
        "unpaged": false
      },
      "totalPages": 33,      // 💡 전체 페이지 수 (전체 161개 / 5개씩 = 33페이지)
      "totalElements": 161,  // 💡 전체 데이터 총 개수
      "last": false,         // 💡 마지막 페이지 여부
      "size": 5,
      "number": 0,
      "sort": { ... },
      "numberOfElements": 5, // 현재 페이지에 담긴 데이터 개수
      "first": true,         // 💡 첫 번째 페이지 여부
      "empty": false         // 결과가 비어있는지 여부
    }
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항
---
### `GET` /reviews           
리뷰 더보기 눌렀을때

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| reviewId | Long | - | - |
<!-- end list -->

#### **Request Body**
```json
{
   "isInterested" : ""  // 유용해요
}
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**


```json
{
  "status": "success",
  "data": {
    "reviewId" : "",
    "reviewMediaUrl" : "",
    "likeCount" : "",
    "writerName" : "",
    "star" : "",
    "createAt" : "",
    "reportUrl" : ""
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항

---

### 리뷰쓰기 `POST` /reviews

#### **Request Headers**

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Content-Type` | `multipart/form-data` | ✅ | 이미지/동영상 파일과 데이터를 함께 보내기 위함 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Body**
```json
{ // data(application/json)
  "productId" : "",
  "star" : "",
  "preference" : "",
  "repurchaseScore" : "",
  "content" : "",
}
// 'files' multipart/form-data
  - reviewsImage.jpg .....
```
####
#### **Success Response**

  * **Code:** 200 OK
  * **Content:**


```json
{
  "status": "success",
  "data": {
    "reviewId": 1025,
    "message": "리뷰가 성공적으로 등록되었습니다.",
    "redirectUrl": "/profile/reviews" // 등록 후 이동할 페이지 경로 예시..
  }
}
```  
#### **Error Response**

 400 Bad Request: { "message": "content is null" } (내용 누락/오류)
 413 Payload Too Large: { "message": "File size exceeds limit (Max 50MB)" } (동영상 용량 초과)
 409 Conflict: { "message": "You have already reviewed this product" } (중복 리뷰 방지)

## 6

<img src="6.png" style="width: 500px; height: auto;" alt="설명">


## 7

<img src="7.png" style="width: 500px; height: auto;" alt="설명">


## 8

<img src="8.png" style="width: 500px; height: auto;" alt="설명">

## 9

<img src="9.png" style="width: 500px; height: auto;" alt="설명">

## 10

<img src="10.png" style="width: 500px; height: auto;" alt="설명">
---

### `GET` /products   # 1, 2, 3, 6, 7, 8, 9, 10
---

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | - | - | - |
<!-- end list -->


#### **Request Body**
```json
{
 	"isInterested" : "" // 관심등록
}
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status": "success",
    "productInfo": {
      "imageUrl" : "",
      "productId" : "",
      "productName" : "",
      "productTag" : "",
      "price" : "",
      "deleveryFee" : "",
      "deleveryMethord" : "",
      "totalPrice" : "",   // 총 제품금액
      "totalNumber" : "", // 총 제품 갯수
      "productDetailUrl" : "",  // 상세정보
    }
    "Button" : {
      "cartButtonText" : "장바구니",
      "purchaseButtonText" : "구매하기"
   }
    "recommandInfo" : {
      "productId" : "",
      "pruductImageUrl : "",
      "productName" : "",
      "productTag" : "",
      "price" : "",
      "optionName" : "",
      "optionDetail" : ""
    }
    "productTemplete" {  // 상품 맨 아랫단
      "paymentInfo" : "", // 결제안내
      "deleveryInfo" : "", // 배송안내
      "exchangeAndReturnInfo" : "", // 교환/반품 안내
      "serviceDetailInfo" : "" // 서비스 문의 안내
    }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항
1. 관련상품은 3개까지.

