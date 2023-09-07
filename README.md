# backend-survival
# init

### 쇼핑몰 REST API 설계
    1. 로그인/회원가입 자원 members
     - 로그인 : members/login -> getmapping
     - 로그아웃 : members/logout -> patchmapping
     - 회원가입 : members/join -> postmapping

    2. 내정보 자원 members
     - 내 정보 조회 : members/{id} -> getmapping
     - 내 정보 수정 : members/{id} -> patchmapping

    3. 상품 자원 products
     - 상품 목록 : products/ -> getmapping
     - 상품 상세 : products/{id} -> getmapping

    4. 상품리뷰 자원 review
     - 상품에 리뷰 작성 : review/{id} -> postmapping
     - 상품에 리뷰 수정 : review/{id} -> patchmapping
     - 상품에 리뷰 삭제 : review/{id} -> deletemapping

    5. 장바구니 자원 cart
     - 장바구니에 상품 추가 : cart/{id} -> postmapping, patchmapping
     - 장바구니에 상품 삭제 : cart/{id} -> deletemapping
     - 장바구니 (담긴 상품 목록) : cart/{id} -> getmapping

    6. 구매 자원 orders
     - 주문하기 : orders/{id} -> postmapping, patchmapping
     - 주문 목록 : orders/{id} -> getmapping




### 화면 URL과 API의 URL이 일치해야 할까? 달라야 한다면 그 이유는 무엇일까?
#### -> 달라야 한다고 생각한다. 화면 URL은 외부로 표출 되는 부분이다. URL을 통해 여러 정보들이 오가는데 이를 외부로 표출시키면 보안의 문제가 있을거라고 생각 한다.

### 서버는 API 요청을 받을 때 사용자가 누구인지 어떻게 알 수 있을까?
#### -> 세션에 사용자의 정보를 담아 가지고 다닌다거나, URL에 쿼리스트링으로 사용자 고유의 키를 붙여 요청을 보낸다.

### API 요청으로 다른 사람의 정보를 함부로 볼 수 없게 하려면 어떻게 해야 할까?
#### -> 암호화를 시킨다.
