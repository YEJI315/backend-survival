# 🥑 REST API

API란 Application Programming Interface의 약자인데, 컴퓨터나 컴퓨터 프로그램 사이의 연결이다. 나는 API가 서버에 요청을 보내면 사용자는 그 내부를 알 수 없더라도 원하는 결과를 가져올 수 있도록 하는 편리한 소프트웨어  도구라고 생각한다.&#x20;

REST API와 SOAP API를 많이들 비교하길래 SOAP이 뭔지 궁금해졌다.&#x20;

&#x20;SOAP API는 Simple Object Access Protocol으로 그 자체로 프로토콜이다. 그렇기 때문에 보안이나 메시지전송 등에 있어 REST보다 더 많은 표준들이 정해져 있기 때문에 더 복잡하다. 보안이나 트랜잭션 등등 많은 규칙들을 준수해야 하기 때문에 웹 서비스 보다는 기업용 애플리케이션이나 은행어플같은 보안수준이 높아야 하는 경우에 선호된다.

REST API란 Representational State Transfer Application Programming Interface 의 약자.  웹 애플리케이션이 제공하는 각각의 데이터를 리소스 즉, 자원으로 간주하고 각각의 자원에 고유한 URI를 할당함으로써 이를 표현하는 API를 정의하기 위한 소프트웨어 아키텍쳐 스타일이다. 네트워크를 통해서 컴퓨터들끼리 통신할 수 있게 해주고  식별자(URI)와 HTTP프로토콜을 기반으로 한다. 데이터 포맷은 브라우저 간 호환성이 좋은 JSON을 사용한다. 클라이언트 서버 모델로 구축되어 그사이에서 통신할 수 있게하고, 아키텍처를 만들 수 있게 한다. 단일 인터페이스를 사용하기 때문에 해당 API를 사용하는 애플리케이션들이 동일한 경로를 통해 접속해야하고, 그 방식이 단순하다.

REST API는 서버에 URI를 이용하여 접근하지만 SOAP은 프로토콜이기 때문에 서비스 인터페이스를 통해 서버에 접근한다.

어쨌든 두 방식의 큰 차이는 프로토콜이냐 아키텍쳐냐 인데, 프로토콜은 통신규약이고 아키텍쳐는 그 통신규약을 이용해서 서비스를 만드는 구조 정도로 이해했다.&#x20;

정보은닉과 캡슐화 : 학원 다닐 때 단순히 정보은닉 = 캡슐화 로 이해했는데, 정보은닉에 캡슐화가 포함되어 있었다. 정보은닉은 1.업캐스팅(자식 객체의 타입을 부모 객체의 타입으로 형변환 함으로써 구체적인 자식 객체의 타입을 은닉) 2.캡슐화(내부를 묶음.  그래서 내부와 외부는 인터페이스로 소통. 내부가  바깥으로 드러나지 않음.)   3.인터페이스&추상클래스 의 방법으로 보다 다형하게 구현이 가능하다.

아키텍처와 아키텍처 스타일 : 아키텍처란 소프트웨어를 구성하고있는 부품들 간의 연결관계이다. 소프트웨어를 어떻게 구조화 시켜야 하는지, 상위메뉴와 하위메뉴를 어떻게 배치해야 하는지 등등.. 소프트웨어를 구성하고 있는 기능 하나하나를 어떻게 관계시킬지에 대한 모든 구조적인 문제.. 아키텍처 스타일은 이러한 아키텍처 설계에서 반복해서 나타나는 문제를 해결하고 아키텍처가 만족시켜야 하는 시스템 품질 속성을 달성할 수 있는 방법을 체계화 한 것.=> 내가 뭘 설계를 했는데(아키텍처) 거기에 어떤 공통적인 스타일, 패턴을 적용했다.(아키텍처 스타일)

REST -> 내부와 외부가 소통하는 인터페이스를 쓰는 원칙.  필딩 제약조건을 따르느냐 안따르느냐가 중요. 표현의 상태 전송!

## REST 제약조건 7가지

1. Starting with the Null Style : 설계자는 어떠한 제약조건 없이 시스템의 전반에서 시작하여 점진적으로 제약조건을 추가한다. 그리고 추가한 제약조건들이 시스템 내에서 조화롭고 자연스럽게 동작할 수 있도록 설계를 진행. 시스템의 맥락에 대한 이해와 규제를 강조하는 관점.&#x20;
2. Client-Server : 사용자 인터페이스에 대한 관심을 데이터 저장에 대한 관심으로부터 분리. 클라이언트 측면에서는 여러 플랫폼에 대한 사용자 인터페이스의 이식성을 개선시키고, 서버 측면에서는 서버측 구성요소를 단순화함으로써 확장성을 개선.
3. Stateless : 클라이언트와 서버는 서로의 상태를 모른다. 그러므로 클라이언트가 서버로 보내는 요청에는 해당 요청을 이해하는 데에 필요한 모든 정보가 담겨있어야 한다!
4. Cache : 캐시가 가능해야 한다. 즉 모든 서버의 응답은 캐시 가능한지 아닌지 알 수 있어야 한다. 효율, 규모확장성, 사용자 입장에서의 성능이 개선된다.
5. Uniform Interface → 핵심! 이 제약조건을 가장 만족 못한다. 인터페이스를 이용하기 때문에 구현부가 분리되어 독립적으로 작업 할  수있음. 대신 trade-off가 존재해 효율성이 떨어질 수 있다. standard form 이기 때문! web에서 일반적으로 사용하는 대용량 하이퍼 미디어 전송에 효율적임.

{% hint style="info" %}
Uniform Interface 제약 조건에서 가장 중요한 필딩 제약 조건. Four Interface Constraints
{% endhint %}

* identification of resources : resource가 URI로 식별되면 됨.
* manipulation of resources through representations : resource CRUD 작업시 요청을 담아 전송해서 resource 조작을 달성하면 됨.
* self-descriptive messages : 메시지는 스스로를 설명해야한다. 자기서술적! -> MIME 타입으로 설명해줄 수 있다.  홀맨   왈 "자기 서술이란 건 결국 내가 나를 설명했을 때 내가 누구인지 받아들이는 쪽에서 이해가 된다는 겁니다. 받아들이는 쪽에서 이해하지 못하면 자기 서술적이지 않죠." 서버나 클라이언트가 변경되더라도 오고가는 메시지는 언제나 자기서술적이므로 언제나 해석 가능하다.
* hypermedia as the engine of application state (HATEOAS) : 애플리케이션의 상태는 Hyperlink를 이용해 전이되어야한다. html같은 경우 이를 만족한다. ex)\<a href="/test">test\</a> 누름으로써 원하는 상태로 전이가 가능하기 때문에 hateoas 만족! 어디서 어디로 전이가 가능한지 미리 결정되지 않는다. 어떤 상태로 전이가 완료되고 나서야 그 다음 전이될 수 있는 상태가 결정된다. 즉, 링크는 동적으로 변경될 수 있다. => 클라이언트가 서버로부터 어떠한 요청을  할때, 요청에 필요한 URI를 응답에 포함시켜 반환하는 것.

{% hint style="info" %}
아키텍처 요소에서 Resource와 Representation을 구분
{% endhint %}

* Resource -> 추상. 특정 시점의 스냅샷이 아니라 모든 시간에 통용되는 엔티티의 집합이다. 객체지향에서 말하는 Entity라고 생각하면 됨. "앨리스"  라는 리소스는 키가 커지던 작아지던 항상 "앨리스"다. - 객체지향의 사실과 오해
* Representation -> Data + Metadata + Meta-metadata.. => 사실 상 HTTP메시지. 리소스를 어떻게 조작할 것인가는 HTTP Method로, 리소스를 무엇으로 조작할 것인가는 Content-Type과 Body로 표현.

{% hint style="info" %}
HATEOAS 관련
{% endhint %}

* 대부분은 효율 문제로 표현에 링크를 넣지 않고 클라이언트 개발자가 API문서를 활용해 처리한다. 예를 들어, 5번째 링크를 클릭하면 5번째 장을 볼거야  -> 5번째장을 보는 방법이 정해져있고 거기에 따라서 강제로 수행을 해주면 그 상태가 되는 것. => 표현에서 상태 전환을 선택하는 것이 아니라, API 문서를 참조해서 상태 전환을 강제한다!

6. Layered System : 각 레이어는 인접하지 않은 레이어의 정보를 몰라야 한다! 어떤 시스템이 가지고 있는 지식을 단일 계층으로 제한함으로써 전체적인 시스템의 복잡도를 감소시킴.
7. Code-On-Demand (optional) : 서버에서 코드를 클라이언트로 보내서 실행할 수 있어야한다. 서버가 네트워크를 통해 클라이언트에 프로그램을 전달하면 그 프로그램이 클라이언트에서 실행될 수 있어야 한다. ex)자바스크립트

리차드슨 성숙도 모델 : HTTP Verbs를 쓰는 것 만으로도 RESTFUL하다. 마지막은 HATEOAS인데, 자원에 호출 가능한 API 정보를 자원의 상태를 반영하여 표현하는 것. ㅅㅂ 뭔소리야...

![](<.gitbook/assets/image (3).png>)

리소스에 대한 표현으로 MIME Type(Content Type, Media Type) 사용 : 서버에 요청할 때도 넣어줌.

&#x20;1\. text/plain : 이메일에서 자주 사용.&#x20;

2. text/html : 일반적인 웹 문서. html 문서.
3. text/css : css파일
4. text/javascript : javascript 파일
5. application/xml : 범용. 자기서술적이기 어렵다. 애플리케이션과 xml을 이용해서 뭔가 작동할 수 있다는 의미. 범용이라 자기서술적이기 상대적으로 어렵다.
6. application/atom+xml&#x20;
7. application/json : 범용. 자기서술적이기 굉장히 어렵다. 아 나는 데이터일 뿐이야!

## Collection Pattern

대부분의 경우, 여러 리소스를 하나의 그룹으로 묶을 수 있다. 예를 들어 게시물의 경우, 100개의 게시물을 하나의 게시물 그룹으로 묶어서 표현하는 게 훨씬 유용하다.

'/posts/{id}/edit' 이런 식으로 페이지를 수정 요청 하고 싶다면 '/posts/{id}'로 요청을 날리고 patch로 받으면 된다! 웬만하면 /items, /items/{id} 와 같은 url만 사용해도 무방하다.

어떤 리소스를 잡느냐에 따라서 훨씬 자연스러운 표현이 가능함. ex)/posts/{id}/edit ⇒ “Edit Page”라는 리소스. 마찬가지로 /edit?post\_id={post\_id} 형태로 써줄 수도 있다. 다만, /comments/{id}/edit 같은 게 도입될 경우 /edit?comment\_id={comment\_id} 같은 것과 구분해서 처리하는 게 복잡할 수 있다. 만약 편집 페이지의 유형을 Edit ID 따위로 표현하고 싶다면, /edits/post, /edits/comment 같이 컬렉션 패턴과 복수형을 사용할 수 있다. 하지만 이렇게 하고 싶다면 edit보다는 그냥 page란 리소스를 사용하는 걸 추천. Page란 리소스, 그리고 Page ID란 모양이 훨씬 명확하다. 이렇게 하면 /pages/edit-post, /pages/edit-comment 같이 훨씬 자연스럽게 표현할 수 있게 된다.

CQS : CRUD를 중요한 특징에 따라 구분하면 Command와 Query로 나뉨. Command - Create, Update, Delete로 상태가 변하는 작업. 안전하지 않음. Query - Read로 상태가 변하지 않음. 안전하고, 분산, 캐시 등이 수월함.

이 네가지를 HTTP Method를 이용해서 표현할 수 있음. (<mark style="color:blue;">with collection pattern</mark>)

1. GET -> Read

ex) GET /posts : 게시물 목록. Collection 을 리드해옴. list. 습관적인  표현일 뿐 필수는 아님.

ex) GET /posts/{id} : 게시물 상세. Element를 리드해옴. detail. 습관적인  표현일 뿐 필수는 아님.

2. POST -> Create (POST는 원래 데이터 전송일 뿐)

ex) POST /posts : 게시물 생성 -> post id는 generatevalue등 으로 자동으로 서버에서 생성.

3. PUT, PATCH -> Update (PUT은 없으면 리소스를 만들수도있는 메서드. 특정 주소를 덮어쓰기 때문에. PATCH는 일부만을 바꿀 수 있다. 나중에 둘을 구분해서 쓸 상황이 온다.)&#x20;

ex) PUT | PATCH /posts/{id} : 게시물 수정 (update, element)

4. DELETE -> Delete 특정한 게시물 삭제 (delete, element)

종종 Bulk update, Bulk delete등을 하기도 하는데 이럴 때는 collection을 활용한다. -> collection을 어떻게 넘길 것인지는 API 문서에 정확히 명시 해 놓아야 한다.

세션처럼 추상적인 개념을 리소스로 표현할 땐 그냥 뒤에 세션을 붙이면 된다.

ex) POST /session 로그인&#x20;

ex) GET /users/me 유저 아이디를 me라고 쓰면 현재 사용자의 아이디로 처리하게 정하고 API 스펙 문서에 기록한다.

EX) 댓글

그냥 바로 comments로 시작하는 경우:

1. `GET /comments` → 전체 댓글 목록
2. `GET /comments?post_id={post_id}` → 특정 게시물에 대한 댓글 목록
3. `GET /comments/{id}` → 댓글 상세
4. `POST /comments` → 댓글 생성 ⇒ 어떤 게시물에 대해? → Body에 Post ID 정보를 담아줘야 함.(스펙으로 정의 필요)
5. `POST /comments?post_id={post_id}` → 특정 게시물에 대한 댓글 생성
6. `PUT 또는 PATCH /comments/{id}` → 댓글 수정
7. `DELETE /comments/{id}` → 댓글 삭제

특정 게시물 아래로 표현하는 경우:

1. `GET /posts/{post_id}/comments` → 특정 게시물에 대한 댓글 목록
2. `GET /posts/{post_id}/comments/{id}` → 특정 게시물에 달린 특정 댓글 상세
3. `POST /posts/{post_id}/comments` → 특정 게시물에 대한 댓글 작성
4. `PUT 또는 PATCH /posts/{post_id}/comments/{id}` → 특정 게시물에 달린 특정 댓글 수정
5. `DELETE /posts/{post_id}/comments/{id}` → 특정 게시물에 달린 특정 댓글 삭제

EX) 로그인

#### 로그인/로그아웃

로그인과 로그아웃을 어떻게 리소스로 표현할 수 있을까? 이럴 때는 추상적인 개념인 “**세션**”을 도입하곤 한다.

1. `POST /session` → 세션 생성 = 로그인
2. `DELETE /session` → 세션 파괴 = 로그아웃

덤으로…

1. `GET /session` → 세션 확인 → 내 정보 확인?
2. `GET /users/me` → User ID를 me라고 쓰면, 현재 사용자의 User ID로 처리하게 정하고, API 스펙 문서에 기록.

&#x20;@RequestMapping : 특정 uri로 보낸요청을 Controller에서 어떠한 방식으로 처리할지 정의를 내리는데, 이 때 들어온 요청을 특정 매서드와 매핑하기 위해 사용하는 어노테이션.

@RequestBody : HttpRequest 본문을 전송 또는 도메인 객체에 매핑하여 인바운드 HttpRequest 본문을 Java 객체로 자동 역직렬화 할 수 있도록 하는 어노테이션.

@ExceptionHandler : @Controller나 @RestController 어노테이션이 붙어있는 클래스에서 발생하는 에러를 잡아서 메소드로 처리해주는 기능을 제공한다. @ExceptionHandler의 value 값으로 구체적인 예외 클래스를 지정해주면 해당 어노테이션이 붙은 메소드에서 그 예외를 처리해준다.

@ResponseEntity : 스프링 프레임워크에는 HTTP Request 혹은 Response를 나타내기 위해 제공하는 HttpEntity라는 클래스가 존재한다. HttpEntity는 HttpHeader와 HttpBody를 포함하는 클래스임. 이 HttpEntity를 상속하여 추가적으로 HttpStatus 속성을 가지는 클래스가 ResponseEntity 클래스. 제네릭으로 선언되어 있으며 해당 부분은 HttpBody의 타입을 나타낸다.

제네릭 : 제네릭(Generic)은 직역하자면 '일반적인'이라는 뜻이다. 음.. 한 번에 이해가 가진 않는다. 조금 더 부연설명을 하자면 '데이터 형식에 의존하지 않고, 하나의 값이 여러 다른 데이터 타입들을 가질 수 있도록 하는 방법'이다.

우리가 흔히 쓰는 ArrayList, LinkedList 등을 생성할 때 어떻게 쓰는가?

객체<타입> 객체명 = new 객체<타입>(); 이렇게 쓰지 않는가? <>괄호 안에 들어가는 타입을 지정해준다.생각해보자. 만약에 우리가 어떤 자료구조를 만들어 배포하려고 한다. 그런데 String 타입도 지원하고싶고 Integer타입도 지원하고 싶고 많은 타입을 지원하고 싶다. 그러면 String에 대한 클래스, Integer에 대한 클래스 등 하나하나 타입에 따라 만들 것인가? 그건 너무 비효율적이다. 이러한 문제를 해결하기 위해 우리는 제네릭이라는 것을 사용한다. 이렇듯 제네릭(Generic)은 클래스 내부에서 지정하는 것이 아닌 외부에서 사용자에 의해 지정되는 것을 의미한다. 한마디로 특정(Specific) 타입을 미리 지정해주는 것이 아닌 필요에 의해 지정할 수 있도록 하는 일반(Generic) 타입이라는 것이다. 정확히 말하자면 지정된다는 것 보다는 타입의 경계를 지정하고, 컴파일 때 해당 타입으로 캐스팅하여 매개변수화 된 유형을 삭제하는 것이다.

@ResponseStatus : ResponseEntity를 사용하면 HttpStatus, HttpHeader, HttpBody를 표현할 수 있음. 이 중에서 HttpStatus를 다른 방식으로 표현할 수 있는게 ResponseStatus.
