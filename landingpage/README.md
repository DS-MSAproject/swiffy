#### **Request Headers** 공통사항

| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `JWT(Cookie)` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

### 2\. 엔드포인트 상세 (Example)

### `GET` /api/v1/main

<img src="1.png" style="width: 800px; height: auto;" alt="설명">

# 필요시 협의 내용들
# 


=======

## 지금은 사용자에게 렌더링하는 페이지

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| ImageUrl | - | - | - |
| productUrl | | | |

#### **Request Body**
```json
{
  IamgeUrl : "",
  배너로 들어간 Url : 
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
    "produtpageinfo : ~~
    (etc..)
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`

-----



<img src="2.png" style="width: 800px; height: auto;" alt="설명">


사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| id | Long | - | - |
| title | String | - | - |
| content | String | - | - |
| productUrl | String | - | - |
| ImageUrl | String  | - | - |
| price | integer | - | - |
| tagName | String | - | (판매2위) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }

 {
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
  }
{
    "id": "success",
    "title":
    "image url":
    "content":
    "price":
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
productInfo : 


<img src="3.png" style="width: 800px; height: auto;" alt="설명">

-----

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| id | Long | - | - |
| title | String | - | - |
| content | String | - | - |
| productUrl | String | - | - |
| ImageUrl | String  | - | - |
| price | integer | - | - |
| tagName | String | - | (판매2위) |
| hashtagName | String | - | - |


#### **Request Body**
```json
{
  "id" : ,
  "title" : "",
  "contnet" : "",
  제품으로 들어가는 Url : "",
  "price" : ,
  "태그" : ""
}
```


#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  {
    "produtpageinfo : ~~
    (etc..)
  }
  }

 {
    "produtpageinfo : ~~
    (etc..)
  }
  }
{
    "produtpageinfo : ~~
    (etc..)
  }
  }
{
    "produtpageinfo : ~~
    (etc..)
  }
  }
{
    "produtpageinfo : ~~
    (etc..)
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

* 태그 최대 개수는 5개 
* 태그 별제품은 최대 5개
* 랜더링되는 제품은 (태그별)판매량순(판매량 정보도 백엔드에서 던져주는 것으로)
* 

-----

<img src="4.png" style="width: 800px; height: auto;" alt="설명">

-----

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| id | Long | ✅ | 사용자의 고유 ID (Path Variable) |
| title | String | ❌ |  |
| mainImageUrl | String | ❌ |  |
| content | String | ❌ |  |
| contentImageUrl | String | ❌ | ) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

RequestBody
```json
{
    "Id" : ,
    "title": "",
    "mainIamgeUrl": "",
    "content": "",
    "contentImageUrl": "
  }
}
```

```json
{
  "status": "success",
  "data": {
    "imageUrl" : ,
  }
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

사용자의 상세 정보를 조회합니다.

#### **Request Parameters**

| Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `id` | `Integer` | ✅ | 사용자의 고유 ID (Path Variable) |
| `include_posts` | `Boolean` | ❌ | 작성한 포스트 포함 여부 (Query Param) |

#### **Success Response**

  * **Code:** 200 OK
  * **Content:**

<!-- end list -->

```json
{
  "status": "success",
  "data": {
    "Id" : ,
    "title": "",
    "firstreviewIamgeUrl": "",
    "star": "",
    "content": "",
    "평균" : "",
    "리뷰개수" : ,
    "리뷰보여주는 Url" : ""
  }
{
  "status": "success",
  "data": {
    "Id" : ,
    "title": "",
    "firstreviewIamgeUrl": "",
    "star": "",
    "content": "",
    "평균" : "",
    "리뷰개수" : ,
    "구매자이름" : "",
    "좋아요 개수" : "",
    "댓글" : "",
    "작성일자" : "",
    "기호도" : "",
    "재구매의사" : [있어요, 없어요],
  }
}
```

#### **Error Response**

  * **Code:** 404 NOT FOUND
  * **Content:** `{ "message": "User not found" }`
  * **Code:** 401 UNAUTHORIZED
  * **Content:** `{ "message": "Invalid token" }`


#### 참고사항

<img src="6.png" style="width: 800px; height: auto;" alt="설명">

