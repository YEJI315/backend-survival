# 🥑 Layered Architecture

Layered Architecture 는 관심사의 분리(Seperation of concerns)에 따라 시스템을 유사한 책임(관심)을 지닌 레이어로 분해하고, 각각의 레이어가 하위 레이어에만 의존하도록 구성하는 아키텍처 패턴이다.&#x20;

각 레이어들이 특정 관심사와 관련된 개체만을 포함하도록 만듦으로써 전체적인 시스템의 결합도를 낮추고, 개발자의 인지 과부하를 방지하며 재사용성을 높이고 유지보수성을 향상시키는 목적이 있다.

## 기본 구조

백엔드 서버 구조에는 여러 변형들이 존재할 수 있지만, 서버가 가지는 주요 관심사들을 분리하면 크게 3\~4가지 레이어로 구성된다.

1. Presentation Layer : 사용자와 소프트웨어 간 상호작용의 최선단에 위치. View와 Controller이다. 클라이언트의 요청을 변환해야하고 기본적인 요청내용을 검증, 수행 결과를 클라이언트에 반환하는 역할을 한다. 클라이언트에서 요청하는 방식이 json이던 form-data이던 관계 없이 Application Layer가 영향을 받지 않고 동일하게 동작할 수 있도록 DTO로 변환하는 과정을 거쳐야 한다.

* JSON : 스프링에서는 JSON의 요청내용을 DTO로 쉽게 변환하기 위해 @ReauestBody 어노테이션을 사용한다. JSON이 가진 property와 이름이 같은 DTO의 attribute에 자동으로 매핑된다.
* form-data : @RequestParam 혹은 @modelAttribute 어노테이션을 사용한다. 기본적으로 form-data가 controller에 들어올 때 query parameter하고 비슷한 취급을 받기 때문에 그와 동일한 어노테이션을 사용한다.

2. Application Layer : 모든 것을 하나로 묶는다. 즉, 어플리케이션의 오브젝트와 서비스를 조정한다. 비즈니스로직과 프레젠테이션 간의 인터페이스 역할. 앞단에서 들어오는 요청이 API 요청인지, SOCKET 통신 호출인지에 상관 없이 동일하게 동작해야함. 도메인 레이어가 외부에 대해 가지는 의존을 최소화 한다. 여러 클라이언트로부터 호출될 수 있는 API를 제공한다.(렌더링 후 웹페이지를 반환하는 controller REST API나 controller 호출) => 도메인 개념들이 상호작용 하는 방식을 기반으로 DOMAIN Layer를 단순하게 만들고 이를 어떻게 사용하는지가 Application Layer의 역할. 인터페이스 이기에 도메인 레이어에 비해 단순한 모습. Application Layer는 적절한 객체에게 도메인 로직 수행을 요구하는 FACADE의 기능을 수행한다.
3. Domain Layer : Business Logic Layer. 시스템의 코어이다. 모든 비즈니스 모델과 서비스는 여기에 정의되어있다.&#x20;
4. Infrastructure Layer : 가장 낮은 수준(가장 높은 추상화 정도)의 코드를 포함. 데이터베이스나 메시징 큐와 같은 외부서비스와의 상호작용을 한다. 이 레이어에 위치한 모든 것들은 쉽게 교체될 수 있어야 한다. 또한 비즈니스 로직이나 어플리케이션의 작동방식에 영향을 주지 않아야 한다.
