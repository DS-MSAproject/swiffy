### 1. API 개요
> **Base URL:** https://api.example.com/api/v1/main

> **Authentication:** Bearer Token (Header: Authorization: Bearer {YOUR_TOKEN})

<img src="1.png" style="width: 500px; height: auto;" alt="설명">
<img src="2.png" style="width: 500px; height: auto;" alt="설명">

### 회의 내용
```
적립금
등급
쿠폰 개수
주문내역
최근주문내역(입금전 / 배송준비중 / 배송중 / 배송완료 / 취소 / 교환 / 반품)
```
### 엔드포인트 상세
```GET /users/{id}/profile```
#### **Request Headers**
| Name | Value / Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `Authorization` | `Bearer {token}` | ✅ | API 접근을 위한 인증 토큰 |
| `Accept` | `application/json` | ✅ | 응답받을 데이터 형식 지정 |

#### **Request Parameters**
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
Res
```
상태 
기간 (오늘 / 1개월 / 3개월 / 6개월 )

```
<img src="3.png" style="width: 500px; height: auto;" alt="설명">

```
기간별 상품주문내역
상품 주문 날짜
주문번호
이미지
타이틀
가격
수량
옵션
배송상태 ex) 배송중 / 총 결제금액(상품구매금액 + 배송비 - 총할인금액)
배송조회 누르면 배송정보를 뿌림(보류)
구매후기 (없으면 구매후기 작성 페이지로)
주문조회 10개씩
```
상세보기
```
주문번호
주문일자
주문자
주문처리상태
주문한 상품 총 개수
주문리스트 ( 이미지 / 타이틀 / 수량 / 옵션 / 상태 )
결제 정보 ( 결제금액 / 할인금액 / 배송비 / 결제예정금액 )
배송지 정보 ( 수령지 / 받으시는분 / 우편번호 / 주소 / 휴대전화 / 배송메시지 )
환불 정보 ( 상품이름 / 수량 / 환불일자 / 환불처리상태 / 상품금액 + 배송비 합계 / 환불수단 )
```

<img src="3_1.png" style="width: 500px; height: auto;" alt="설명">

```
취소/교환반품 내역
위와 동일
```

Res
```
기간 (오늘 / 1개월 / 3개월 / 6개월 )
상세날짜 정보
```


<img src="4.png" style="width: 500px; height: auto;" alt="설명">

## 회원정보 수정

```
아이디
이름
전화번호
이메일
주소 ( 주소를 입력했을 시 )
수신여부 (sns/이메일)
```
Res
```
비밀번호
비밀번호확인
주소 ( 첫가입시 )
휴대전화
수신여부 ( 수신함 수신안함 )
이메일
회원탈퇴

```


<img src="5.png" style="width: 500px; height: auto;" alt="설명">

```
관심상품리스트 ( 이미지 / 타이틀 / 가격 / 옵션 )
```
Res 
```
옵션
장바구니 담기
삭제여부
주문여
```

<img src="5_1.png" style="width: 500px; height: auto;" alt="설명">

```
백엔드에서 5개이상 있으면 문구가 뜨게 
```

<img src="6.png" style="width: 500px; height: auto;" alt="설명">

```
총적립금
사용가능 적립금
사용된 적립
환불예정 적립금
```

<img src="6_1.png" style="width: 500px; height: auto;" alt="설명">

```
날짜
적립금
내용
적립내역 10개씩
```

<img src="6_2.png" style="width: 500px; height: auto;" alt="설명">
이거 안하는 내용
<img src="6_3.png" style="width: 500px; height: auto;" alt="설명">
이거 안하는 내
<img src="7.png" style="width: 500px; height: auto;" alt="설명">
예치금 보류

<img src="7_1.png" style="width: 500px; height: auto;" alt="설명">
예치금 보류
<img src="8.png" style="width: 500px; height: auto;" alt="설명">

```
쿠폰 내역
쿠폰명
할인율
적립가능 여부
비고

쿠폰내역 10개씩
```

Res
```
쿠폰인증내역
```

<img src="8_1.png" style="width: 500px; height: auto;" alt="설명">


<img src="8_2.png" style="width: 500px; height: auto;" alt="설명">
<img src="9.png" style="width: 500px; height: auto;" alt="설명">
<img src="10.png" style="width: 500px; height: auto;" alt="설명">
<img src="11.png" style="width: 500px; height: auto;" alt="설명">
<img src="12.png" style="width: 500px; height: auto;" alt="설명">

```
배송지 이름 ( 지정 안하면 미지정)
저장된 주소 ( 우편번호 / 주소 / 국가번호 / 전화번호 )
```

Res
```
신규 배송지 등록 ( 배송지명 / 성명 / 주소 / 휴대전화 / 기본 배송지 저장여부 )
배송지 수정 ( 배송지명 / 성명 / 주소 / 휴대전화 / 기본 배송지 저장여부 )
삭제요
```

<img src="13.png" style="width: 500px; height: auto;" alt="설명">
<img src="14.png" style="width: 500px; height: auto;" alt="설명">

```
신청 내역
혜지 내역
보류
```

<img src="14_1.png" style="width: 500px; height: auto;" alt="설명">

## 게시글 관리 뷰의 댓글 선택시 렌더링 화면

<img src="comments.png" style="width: 500px; height: auto;" alt="설명">


#### 참고사항1
**`예치금(Deposit) vs 적립금(Points): 스크린샷에 두 항목이 모두 존재하므로, benefits 객체 내에서 명확히 분리하여 관리합니다.`**

**`확장성: 향후 관심상품이나 게시물 개수가 업데이트될 때, activity_counts 객체만 갱신하여 응답하면 프론트엔드 UI에 즉시 반영됩니다.`**

**`보안: id를 통한 조회 시 토큰의 소유주와 일치하는지 서버 측 검증이 반드시 필요합니다. (403 Forbidden 처리)`**
