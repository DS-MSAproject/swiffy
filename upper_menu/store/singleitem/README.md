## 1

<img src="1.png" style="width: 500px; height: auto;" alt="설명">

## 엔드포인트 api/v1/products/{productname}

```json
{
  ImageUrl :
}
```

## 2

<img src="2.png" style="width: 500px; height: auto;" alt="설명">

```json
{
  ImageUrl :
  배송방법 :
  배송비 :
  타이틀 :
  가격 :
}

Req
{
  관심눌렀을 때 :
}
```

## 3

<img src="3.png" style="width: 500px; height: auto;" alt="설명">

```json
{
  추천상품 (정보 3개)
- 이름
- 가격
- 옵션(상품 개수 1개, 2개, 4개, 6개, 10개 가격) / (맛 옵션)
  ImageUrl :
  추천상품 productUrl :
}

#### **Error Response**

  * **Code:** 400 Bad Request
  * **Content:** `{ "message": "Option(amountOption)is null" }` -> alt

Res
{
  옵션 :
  가격 옵션 :
  productId
}
```

## 4

<img src="4.png" style="width: 500px; height: auto;" alt="설명">

Res
```json
{ 
  제목 :
  가격 :
- 상품개수
- 옵션
- 상품Id
}
```


## 5

<img src="5.png" style="width: 500px; height: auto;" alt="설명">

```json
리뷰과 포토리뷰를 없애는 대신에 사용후기에 동영상을 추가
사용후기 필터링 (사진,동영상,텍스트)
사진(최대5개),동영상/닉네임/만족(기호도,재구매의사)/내용/별점평균/총리뷰개수/구매자닉네임
사용후기는 페이지네이션 더보기 (5개씩)
필터링에 별점에 따라 필터 ex)5점이면 5점 후기만 보여주기 / 디폴트값으로는 최신순 
더보기를 누르면서 리뷰Url

리뷰 헤더
    "별점평균" : ,
    "총리뷰개수" : ,
    "별의 비율" : ,
    "만족도 비율" : ,  // 만족도 비율은 별의 비율 아래에다가 배치

리뷰 전체뷰
{
  "status": "success",
  "data": {
    "id": 1,
    "mediaUrl": "",
    "유용해요": "",
    "내용" : ,
    "사용자이름" : "",
    "별점" : ,
    "리뷰로 들어가는 Url" : "",
    "페이지 정보" : 
  }
}

리뷰 상세뷰
{
  "status": "success",
  "data": {
    "id": 1,
    "mediaUrl": "",
    "유용해요": "",
    "내용" : "",
    "사용자이름" : ""
    "별점" : ,
    "타이틀" : "",
    "작성날짜" : 
  }
}
Res
도움이 되요 눌렀을 때
```

## 6

<img src="6.png" style="width: 500px; height: auto;" alt="설명">


## 7

<img src="7.png" style="width: 500px; height: auto;" alt="설명">

```
상세정보
- 이미지카드Url
```

## 8

<img src="8.png" style="width: 500px; height: auto;" alt="설명">

## 9

<img src="9.png" style="width: 500px; height: auto;" alt="설명">

## 10

<img src="10.png" style="width: 500px; height: auto;" alt="설명">

## 결제 안내, 배송 안내, 교환/반품 안내, 서비스문의 안내는 텍스트로 backend가 뿌리는 것으로 결정

* 이런 제품은 어때요
1. 이미지
2. 제목
3. 가격
4. 제품3개 뿌리는 것으로 결정



## 리뷰 쓰기 엔드포인트 : api/v1/review/{userId}/{productName}/create 
```json
{
  "리뷰쓰기 눌렀을 때 Url" : "",
  "제목" : "",
  "상품이미지" : "",
  "선호도(리뷰)" : ,
  "등록하기 누르면 프로필 리뷰내역 Url" : ""
}

Res
{
  "별점 (디폴트로 5점)" :
  "선호도 선택정보" :
  "content" :
  "media(없을 시 텍스트로 분류)" :
}

컨텐츠 미작성시 
#### **Error Response**
  * **Code:** 400 Bad Request
  * **Content:** `{ "message": "content is null" }` -> alt
```
