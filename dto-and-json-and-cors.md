# 🥑 DTO & JSON & CORS

DTO (DATA TRANSFER OBJECT) : 데이터 전송 객체. between processes! 계층 간 데이터 교환을 위해 사용하는 객체이다. DTO를 사용하면 도메인을 캡슐화하고 UI화면에서 사용하는 데이터만 선택적으로 보낼 수 있다. DTO는 클라이언트 요청에 포함된 데이터를 담아 서버에 전달하고, 서버의 응답 데이터를 담아 클라이언트에 전달하는 계층간 전달자 역할을 한다.

무기력한 도메인 모델 : 객체에  GETTER SETTER 이외에 별다른 행위가 없는 것.. 대표적인 안티패턴으로 알려져 있다. (\*안티패턴 : 비효율적이거나 생산성이 저해되는, 다시 말해서 권장사항의 반대편에 있는 소프트웨어 설계 관행을 의미한다. ) 비즈니스적으로 유의미한 행동 즉, 비즈니스 로직은 정말 하나도 없는 게터 세터만 있는 단순 DTO 느낌.. 왜 안티패턴이냐, 객체지향과 정 반대이기 때문이다. 일반적으로 객체는 속성과 기능을 가져야한다. 이러한 구현이 객체지향스러운 개발이지만 무기력한 도메인 모델은 행위가 없이 단순 속성만 갖고 있기 때문에 정 반대라고 할 수 있다. 단순 속성만 갖고 있기에 해당 객체와 관련된 비즈니스 로직을 파악하기 위해서는 전체 서비스 레이어를 살펴보아야 하고, 그렇게 되면 상당히 비효율적이기 때문에 안티패턴으로 여겨지는 것 같다. -> 이 부분에 대해서는 더 알아봐야겠다.

자바빈즈 : 자바로 작성된 소프트웨어 컴포넌트로 데이터 표현을 목적으로 하는 자바 클래스를 의미한다. 자바 빈즈 클래스는 자바 빈즈 컨벤션을 지켜야 한다. (\*자바빈즈컨벤션 : 클래스는 인자가 없는 기본 생성자를 갖는다, 클래스의 멤버 변수(속성)는 프로퍼티 라고 하며 PRIVATE 접근 제한자를 가져야 한다, SERIALIZABLE 인터페이스를 구현하며 패키징 되어야 한다. 등.. JSP에서 데이터를 담기 위한 표준 규약으로 만드는 클래스라고 생각하면 될듯) 자바빈즈는 클래스를 생성하고 PRIVATE 속성과 생성자의 초기화, GETTER SETTER를 추가함으로써 만들 수 있는데, 그렇게 되면 무기력한 도메인 모델인가? 라는 의문점이 들었다.. 이 부분도 시간이 없어 일단 여기까지만 정리했는데 더 알아봐야겠다.

EJB : 엔터프라이즈 자바 빈, 기업환경의 시스템을 구현하기 위한 서버 측 컴포넌트 모델이다. 일반적으로 업무 로직을 가지고 있는 서버 어플리케이션이다. 비즈니스 로직을 탑재한 부품을 Enterprise Bean, 데이터베이스 처리, 트랜잭션 처리 등의 시스템 서비스를 이용한 로직을 감추고 있는 부품을 컨테이너 라고 부른다.&#x20;