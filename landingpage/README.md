#### **Request Headers** 공통사항

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(AccessToken/RefreshToken), Cookie` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

### 2\. 엔드포인트 상세 (Example)

### `GET` /api/v1/main

<img src="1.png" style="width: 800px; height: auto;" alt="설명">


=======


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | - | - | - |

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
    "imageUrl" : ""
    "productUrl" : ""
    "displayOrder" : ""
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



<img src="2.png" style="width: 800px; height: auto;" alt="설명">


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | - | - |

#### **Response Body**

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  {
    "status": "success",
      "id":"",
      "title": "",
      "productUrl" : "",
      "imageUrl": "",
      "tagName": "",
      "price": ""
  }
  {
    "status": "success",
      "id":"",
      "title": "",
      "productUrl" : "",
      "imageUrl": "",
      "tagName": "",
      "price": ""
  }
  {
    "status": "success",
      "id":"",
      "title": "",
      "productUrl" : "",
      "imageUrl": "",
      "tagName": "",
      "price": ""
  }

 
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----
#### 참고사항
베스트셀러는 [전체판매1위] 이런 템플릿으로 하고 
태그는 [판매1위] 이런식으로 템플릿을 합니다.


<img src="3.png" style="width: 800px; height: auto;" alt="설명">

-----


#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | - | - |

<!-- end list -->

#### **Request Body**
```json
```


#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  {
  "status" : "success",
    "productId" : ,
    "title" : "",
    "imageUrl" : "",
    "productUrl : "",
    "price" : ,
    "tagName" : "",
    "hashtagName
  "
  {
  "status" : "success",
    "productId" : ,
    "title" : "",
    "imageUrl" : "",
    "productUrl : "",
    "price" : ,
    "tagName" : "",
    "hashtagName
  "
  }
{
  "status" : "success",
    "productId" : ,
    "title" : "",
    "imageUrl" : "",
    "productUrl : "",
    "price" : ,
    "tagName" : "",
    "hashtagName
  "
  }
{
  "status" : "success",
    "productId" : ,
    "title" : "",
    "imageUrl" : "",
    "productUrl : "",
    "price" : ,
    "tagName" : "",
    "hashtagName
  "
  }
{
  "status" : "success",
    "productId" : ,
    "title" : "",
    "imageUrl" : "",
    "productUrl : "",
    "price" : ,
    "tagName" : "",
    "hashtagName
  "
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

#### 참고사항

* 태그 최대 개수는 5개 
* 태그 별제품은 최대 5개
* 랜더링되는 제품은 (태그별)판매량순(판매량 정보도 백엔드에서 던져주는 것으로)
* 

-----

<img src="4.png" style="width: 800px; height: auto;" alt="설명">

-----

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |

<!-- end list -->

RequestBody
```json
```

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status" : "success",
    "Id" : ,
    "title": "",
    "subtitle": "",
    "mainIamgeUrl": "",
    "contentImageUrl": "",
    "buttonText": ""
}
```



#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`


#### 참고사항

*
* 
-----

<img src="5.png" style="width: 800px; height: auto;" alt="설명">

-----

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| productId | Long | ✅ |  |
| reviewId | Long | ✅ |  |

<!-- end list -->

RequestBody
```json
```
#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

```json
{
  "status" : "success",
      "Id" : ,
      "title": "",
      "tagName" : "",
      "reviewIamgeUrl": "",
      "star": "",
      "content": "",
      "starAverage" : "",
      "totalReviewAmount" : ,
      "reviewUrl" : "",
      "userName" : "",
      "productOption" : "",
      "reviewCreatAt" : "",
      "likeCount" : "",
      "reportUrl" : ""
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`


#### 참고사항

<img src="6.png" style="width: 800px; height: auto;" alt="설명">

### 참고사항
프론트에서 이미지로 대체

