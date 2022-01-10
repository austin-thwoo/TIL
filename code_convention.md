## 

[https://lh5.googleusercontent.com/a8rOQtBF7olc6OoSG-_pVAZgYhFwjVXBCl0Qpj-Q-iq8hPM8lR_1J0II5wubUE-1VRaiExDThlRjsGkN8QlneOU5aABq3Aw2rLSq2EuQpJ2bTWyYd_YJZApVpqVg_lmRsqEDHUf8](https://lh5.googleusercontent.com/a8rOQtBF7olc6OoSG-_pVAZgYhFwjVXBCl0Qpj-Q-iq8hPM8lR_1J0II5wubUE-1VRaiExDThlRjsGkN8QlneOU5aABq3Aw2rLSq2EuQpJ2bTWyYd_YJZApVpqVg_lmRsqEDHUf8]


[How the internet Works vedio](https://www.youtube.com/watch?v=7_LPdttKXPc) in 5 
_다누한**_code convention_**

#객체지향

#java

#springBoot

#JPA

#CODE

#RESTFULL API

작성일 : 2021년 12월 29일

작성자 : 하현수

**─**

# **개요**

# **프로그래머 사이에서 약속한 코드 작성 양식이다. 틀리면 프로그래밍 언어에서 컴파일 에러가 나는 문법 오류와 달리, 컨벤션은 지키지 않아도 오류가 나진 않는다.**

그러나 컨벤션을 지켜서 코드를 작성하면 코드의 **가독성**을 증진시키고, 여러명이 협업할 때 일관된 코드 스타일을 유지할 수 있어 중요하다.

IDE를 사용하여 코드를 작성한다면 이클립스에선 [ctrl + shift + f**]** 를 통해, 인텔리제이에선 [ctrl + alt + L**]** 을 통해 포맷 기능을 한번쯤은 사용해보았을 것이다.

하지만 IDE가 잡아줄 수 있는 건 개행이나 공백 추가 등이고, 단락(paragraph) 의 순서나 변수명 등 까지 수정해주진 않는다.

개발의 80%가 유지보수에 소모되고 코드 작성자가 유지보수를 하지 않을 확률이 다분하며

작성시점에 개발자간에 원활하게 커뮤니케이션이 이루어져야 하고 코드의 질을 높이고

‘좋은 개발자’가 되기 위해 clean code가 필요하기 때문에

**프로그래머가 코드 작성단계에서 컨벤션을 고려하여 작성해야한다.**

# **목표**

1. 코드의 빠른 이해
2. 유지보수의 용이함
3. 코드 커뮤니케이션 활성화
4. ==Teamwork

# **코드 작성 규칙**

### **용어 정리**

- 클래스는 일반적인 class 및 Enum, Interface, Annotation type을 총칭한다.
- 멤버는 inner class, field, method, constructor을 의미한다.
- 주석은 구현주석을 의미한다. 문서화 주석은 Java Doc에서 따로 다룬다.

### **ENCODING**

encoding은 UTF-8이 기본이다

### **import**

1. 와일드 카드로 가져오지 않는다.
    - 이유 1. 성능 이슈가 생길 수도 있다. Wildcard Import 는 컴파일 할 때 실제 클래스를 찾기위해 해당 패키지의 클래스를 전부 탐색하는데, 그 시간이 더 걸리니까. 하지만 파일 몇개를 탐색한다고 차이가 더 날지 사실 의문이다. 또한 많은 어플리케이션이 사전에 컴파일된 jar나 war를 사용하는 경우가 많으므로 이 이유는 크게 중요하지 않다.
    - 이유 2. 별도의 두 패키지를 wildcard import 했는데, 두 패키지 모두에 있는 동일한 이름의 클래스를 활용하는 경우이다. 이 때 참조할 클래스를 결정할 수 없으므로 컴파일 할 수 없는 상황이 발생한다. 단순히 클래스를 import 했는데 소스코드를 수정해야 하므로 바람직하지 못하다.
2. import 문도 패키지 문과 마찬가지로 길다고 개행하지 않는다.
3. static import 와 non-static import은 따로 모아서 블록을 만든다. 블록의 순서는 static, non static이다. 블록 사이에는 1줄의 개행을 넣는다

### **class 정의**

소스 내에서 최상위 클래스는 단 하나여야 한다.

클래스 멤버들간의 순서는 정답이 없지만, 논리적 순서를 갖추는게 중요하다.

비슷한 역할을 하는 메소드 끼리 뭉쳐놓고, 추상화 단계에 따라 배치하자

### **포맷**

### 중괄호 { } (brace)

괄호는 if, else, for, do 및 while문에 코드가 없거나 단 하나라도 생략하지 않습니다.

개인적으로는 코드가 한 줄일때는 중괄호를 생략하는게 더 깔끔하다고 생각해 왔는데, 가이드를 보고 가독성에 대해 다시 한 번 생각해보게 됐다

**{** 의 경우...

- 여는 중괄호 전에는 개행하지 않는다.
- 여는 중괄호 뒤에서는 개행한다.

**}** 의 경우...

- 닫는 괄호 앞에서 개행한다.
- 닫는 괄호 뒤의 개행은, 중괄호가 끝나거나 생성자, 메소드, 클래스가 끝날 때 개행한다. 그러므로, else나 , 앞에서는 개행하지 않는다.

[https://lh3.googleusercontent.com/thwiXsz1IP7Oxm6-UDS_UNL7IGJXocl33P93Ulas2PcEGshyR9niYp0k4eUO9A3oO_eKi9TOWPTCzEC7b62kUca8Uiz43dDPxhD6zrJuMDpYaLouSdM7Yo1oGkOoW1OgGzq1fI1u](https://lh3.googleusercontent.com/thwiXsz1IP7Oxm6-UDS_UNL7IGJXocl33P93Ulas2PcEGshyR9niYp0k4eUO9A3oO_eKi9TOWPTCzEC7b62kUca8Uiz43dDPxhD6zrJuMDpYaLouSdM7Yo1oGkOoW1OgGzq1fI1u)

### **들여쓰기**

# 블록여쓰기는 2공백이다.

# 즉 새로운 블록이 시작하면 2공백을 추가해서 작성하다가, 블록이 끝나면 들여쓰기를 끝내면 된다.

# *** 보통 1탭은 4공백인데, 우린 컨벤션을 따르지 않고 탭을 통해 들여쓰기를 표현한다 ****

### **줄바꿈**

# 한 줄을 차지할 수 있는 코드를 여러줄 로 나누는 것을 줄바꿈 이라고 한다. 줄바꿈도 여러 방식이 있다.

# 보통 줄 바꿈은 하는 이유는 열 제한(100자)을 초과하지 않기 위해서이지만, 열 제한을 넘지 않아도 가독성을 위하여 줄바꿈을 할 수 있다.

- 줄바꿈 규칙

줄바꿈의 더 높은 구문 수준(higher syntactic level)에서 끊어주는 것을 원칙으로 한다.

1. 연산자 같은 상징들 (operator-like symbol)들 앞에서 끊어준다. operator-like symbol은 다음이 있다
    - .
    - 람다의 ::
    - <T extends Foo & Bar>와 같은 타입에서의 &
    - catch(FooException | BarException e) 같은 캐치블록에서의 |
2. ,는 앞에 오는 토큰의 뒤에 적는다.
- 줄바꿈 시 들여쓰기
1. 줄바꿈을 하고 나면 최초 행보다 최소 4자(1tap)를 들여쓰기 한다.

# **자바 코딩 규칙**

### **선언**

1. 한 줄당 선언문의 수
    1. 한 줄에 하나의 선언문을 쓰는 것이 주석문 쓰는 것을 쉽게 해주기 때문에 한 줄에 하나의 선언문을 쓰는 것이 좋다.
    2. int a, b; 는 사용하지 않는다.(for문 헤더에선 예외)
2. 초기화
    1. 지역 변수의 경우, 지역 변수를 선언할 때 초기화 하는 것이 좋다. 변수의 초기화 값이 다흔 계산에 의해서 결정되는 경우라면, 변수를 선언할 때 초기화 하지 않아도 좋다.
3. 배치
    1. 선언은 블록의 시작에 위치해야 한다. ( 보통 블록은 중괄호 ) 변수를 처음 사용할 때까지 변수의 선언을 미루지 말아라, 이러한 경우 부주의한 프로그래머들을 혼돈에 빠뜨릴 수 있고, 영역내에서 코드를 이동해야 하는 경우에 문제를 야기시킬 수 있다.
4. 클래스와 인터페이스의 선언
    1. 자바 클래스와 인터페이스를 선언할 때, 다음과 같은 원칙을 따르도록 하자.
    2. 메서드 이름과 그 메서드의 파라미터 리스트의 시작인 괄호 사이에는 빈 공간이 없어야 한다.
    3. 여는 중괄호는 클래스/인터페이스/메서드 선언과 동일한 줄의 끝에 사용하자.
    4. 닫는 중괄호는 null 문인 경우를 제외하고는, 여는 문장과 동일한 들여쓰기를 하는 새로운 줄에서 사용하자
5. 필요할 때 선언지역 변수는 습관적으로 블록의 시작 부분에 선언되는 경향이 있다.하지만 지역 변수의 범위를 최소화 하기 위해 처음 사용되는 지점에 가깝게 선언한다.

### 

### **명명규칙(Naming Convention)**

- 명명 규칙, 즉 이름을 정하는 규칙은 프로그램을 더 읽기 쉽게 만들어 줌으로써 더 이해하기 쉽게 만들어 준다. 또한 식별자를 통해서 기능에 대한 정보도 얻을 수 있다.
- 카멜 케이스 사용한다.
1. 패키지
    - 패키지의 이름은 최상위 레벨은 항상 ASCII 문자에 포함되어 있는 소문자로 쓰고, 가장 높은 레벨의 도메인 이름 중 하나이어야 한다.
    - 패키지 이름의 나머지 부분은 조직 내부의 명명 규칙을 따르면 된다. 이러한 규칙을 따라 만들어진 이름은 디렉토리 구조에서 디렉토리 이름으로도 사용된다
- 의견 : Entity별 패키지 구성ex) => user[domain{user(),team()},repo{repository,support,dao}] board[domain{content(),comment()},dto{request,response}]//
1. 클래스

클래스 이름은 명사이어야 하며, 단어의 첫 글자는 대문자, 클래스 이름은 간단하고 명시적이 되도록 작성한다. 완전한 단어를 사용하고 두 문자어와 약어는 최대한 피하는걸로

1. 인터페이스
    - 인터페이스 이름도 클래스 이름과 같은 대문자 사용 규칙을 적용해야 한다.
2. 메서드
    - 메서드의 이름은 동사이어야 하며, 복합 단어일 경우 첫 단어는 소문자로 시작하고 그 이후에 나오는 단어의 첫 문자는 대문자로 사용해야 한다.
3. 변수
    - 변수 이름의 첫 번째 문자는 소문자로 시작하고, 각각의 내부 단어의 첫 번째 문자는 대문자로 시작해야 한다. 이름은 짧지만 의미 있어야 한다. 변수 이름의 선택은 그 변수의 사용 의도를 알아낼 수 있도록 의미적으로, 한 문자로만 이루어진 변수 이름은 임시적으로만 사용하고 버릴 변수일 경우를 제외하고는 피해야 하지만 적게 사용될 객체라면 상관없을듯?
4. 상수
    - 클래스 상수로 선언된 변수들의 이름은 모두 대문자로 쓰고 각각의 단어는 언더바로 분리해야 한다.

# **J P A**

검색 메서드

**1.findAll()**

DB에서 전쳉값을 list로 불러올때 사용한다.

**2. findOne()**

primary key로 값을 1건을 조회할때 사용한다

**3. findByXX == Like where syntex in SQL**

findBy뒤에 우리가 정의한 entity의 이름을 붙이면 된다

Entity의 이름의 첫글자는 대문자로 하며, id를 조건으로 검색한다면 findById()로 검색하면 된다.

- And조건

–findByIdAndName(Long Id, String name)And를 사용하여 검색한다.

- OR조건

–findByIdOrName(int Id, String name)으로 Or을 사용하여 검색한다.

**4. Like / NotLike**

like를 붙이면 인수에 지정된 텍스트를 포함하는 Entity를 검색한다

NotLike는 반대로 지정된 텍스트를 포함하지 않는 엔티티를 검색한다.

findByNameLike 라고 사용하게 된다면, name에서 인수의 텍스트를 검색한다.

**5.StartingWith / EndingWith**

값에서 지정된 텍스트로 시작하거나 끝나는 값을 검색한다

ex) findByNameStartingWith(“BOB”)이름이 bob으로 시작하는 이름을 검색한다.

**6. IsNull / IsNotNull**

값이 Null이거나 null이 아닌것들을 검색한다.

**7. findByTrue/false**

true거나 false인 것들을 검색한다.

**8. LessThan / GreaterThan**

숫자(값)를 기준으로 더 작은, 큰값을 검색한다

예를들어 cnt가 20보다 작은것들을 검색하고 싶다면 findaByCntLessThan(20)으로 검색할 수 있다.

**9. between**

사잇값을 검색한다

**10. OrderBy**

정렬 한다

저장

**1. save()**

레코드 저장 like INSERT or UPDATE

삭제

**1. delete()**

레코드 삭제 like DELETE

# **SpringBoot**

***what is***

Spring Boot는 Java를 기반으로 한 웹 어플리케이션 프레임워크이다. Spring Boot가 등장하기 전 Spring 프레임워크가 먼저 등장했는데 Spring의 초기 환경 설정시 시간이 많이 할애되는 문제를 해결하고자 등장한 프레임워크가 Spring Boot이다.

**특징 1**

스프링부트는 메이븐이나 그레이들의 dependency에 starter 라이브러리만 작성한다면 초기 셋팅에 필요한 라이브러리들을 모두 세팅해주게 된다.

초기 개발 환경을 설정할 때 메이븐의 pom.xml이나 그레이들의 build.gradle 파일을 통해 스프링과 스프링부트의 프로젝트를 관리할 수 있다.

**특징 2**

프링 부트의 두 번째 특징은 톰캣과 같은 내장 서버가 존재한다는 것

**특징 3**

마지막으로 스프링의 경우 servlet-context, root-context와 같은 xml 파일을 직접 작성해서 웹과 관련된 설정이나 스프링 프로젝트 내 객체 의존성을 관리해줘야 했지만 스프링부트에서는 이럴 필요 없이 자동으로 의존성 관리가 가능해졌다.

# **RestFull Api**

POST, GET, PUT, DELETE 4가지 methods는 반드시 제공한다.

OPTIONS, HEAD, PATCH를 사용하여 완성도 높은 API를 만든다.

rest의 요소

자원, 행위 표현

REST API 설계 시 가장 중요한 항목은 다음의 2가지로 요약할 수 있습니다.

**첫 번째,** URI는 정보의 자원을 표현해야 한다.

**두 번째,** 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현

### **REST API 중심 규칙**

### 1) URI는 정보의 자원을 표현해야 한다. (리소스명은 **동사보다는 명사**를 사용)

GET /members/delete/1

위와 같은 방식은 REST를 제대로 적용하지 않은 URI입니다. URI는 자원을 표현하는데 중점을 두어야 합니다. delete와 같은 행위에 대한 표현이 들어가서는 안됩니다.

### 2) 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)로 표현

위의 잘못 된 URI를 HTTP Method를 통해 수정해 보면

DELETE /members/1

으로 수정할 수 있겠습니다.

회원정보를 가져올 때는 GET, 회원 추가 시의 행위를 표현하고자 할 때는 POST METHOD를 사용하여 표현합니다.

**회원정보를 가져오는 URI**

GET /members/show/1     (x)

GET /members/1          (o)

**회원을 추가할 때**

GET /members/insert/2 (x)  - GET 메서드는 리소스 생성에 맞지 않습니다.

POST /members/2       (o)

**HTTP METHOD의 알맞은 역할**

POST, GET, PUT, DELETE 이 4가지의 Method를 가지고 CRUD를 할 수 있습니다.

[제목 없음](https://www.notion.so/4b5542558f334f20b17d34144091d50c)

다음과 같은 식으로 URI는 자원을 표현하는 데에 집중하고 행위에 대한 정의는 HTTP METHOD를 통해 하는 것이 REST한 API를 설계하는 중심 규칙입니다.

### URI 설계 시 주의할 점

### 1) 슬래시 구분자(/)는 계층 관계를 나타내는 데 사용

http://restapi.example.com/houses/apartments

http://restapi.example.com/animals/mammals/whales

### 2) URI 마지막 문자로 슬래시(/)를 포함하지 않는다.

URI에 포함되는 모든 글자는 리소스의 유일한 식별자로 사용되어야 하며 URI가 다르다는 것은 리소스가 다르다는 것이고, 역으로 리소스가 다르면 URI도 달라져야 합니다. REST API는 분명한 URI를 만들어 통신을 해야 하기 때문에 혼동을 주지 않도록 URI 경로의 마지막에는 슬래시(/)를 사용하지 않습니다.

http://restapi.example.com/houses/apartments/ (X)

http://restapi.example.com/houses/apartments  (0)

### 3) 하이픈(-)은 URI 가독성을 높이는데 사용

URI를 쉽게 읽고 해석하기 위해, 불가피하게 긴 URI경로를 사용하게 된다면 하이픈을 사용해 가독성을 높일 수 있습니다.

### 4) 밑줄(_)은 URI에 사용하지 않는다.

글꼴에 따라 다르긴 하지만 밑줄은 보기 어렵거나 밑줄 때문에 문자가 가려지기도 합니다. 이런 문제를 피하기 위해 밑줄 대신 하이픈(-)을 사용하는 것이 좋습니다.(가독성)

### 5) URI 경로에는 소문자가 적합하다.

URI 경로에 대문자 사용은 피하도록 해야 합니다. 대소문자에 따라 다른 리소스로 인식하게 되기 때문입니다. RFC 3986(URI 문법 형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정하기 때문이지요.

RFC 3986 is the URI (Unified Resource Identifier) Syntax document

### 6) 파일 확장자는 URI에 포함시키지 않는다.

http://restapi.example.com/members/soccer/345/photo.jpg (X)

REST API에서는 메시지 바디 내용의 포맷을 나타내기 위한 파일 확장자를 URI 안에 포함시키지 않습니다. Accept header를 사용하도록 합시다.

GET / members/soccer/345/photo HTTP/1.1 Host: restapi.example.com Accept: image/jpg

### 4-3. 리소스 간의 관계를 표현하는 방법

REST 리소스 간에는 연관 관계가 있을 수 있고, 이런 경우 다음과 같은 표현방법으로 사용합니다.

/리소스명/리소스 ID/관계가 있는 다른 리소스명

ex)    GET : /users/{userid}/devices (일반적으로 소유 ‘has’의 관계를 표현할 때)

만약에 관계명이 복잡하다면 이를 서브 리소스에 명시적으로 표현하는 방법이 있습니다. 예를 들어 사용자가 ‘좋아하는’ 디바이스 목록을 표현해야 할 경우 다음과 같은 형태로 사용될 수 있습니다.

GET : /users/{userid}/likes/devices (관계명이 애매하거나 구체적 표현이 필요할 때)

[https://sanghaklee.tistory.com/57](https://sanghaklee.tistory.com/57)

# **객체지향**

## (SOLID)객체지향 설계

[제목 없음](https://www.notion.so/22ccf04467ee4ec9bf3ee74f7741ce4a)

## [애자일 소프트웨어 개발](https://ko.wikipedia.org/wiki/%EC%95%A0%EC%9E%90%EC%9D%BC_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C)[적응적 소프트웨어 개발](https://ko.wikipedia.org/w/index.php?title=%EC%A0%81%EC%9D%91%EC%A0%81_%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EA%B0%9C%EB%B0%9C&action=edit&redlink=1)

## TDD / BDD / DDD

1. TDD(Test-Driven-Development)

테스트 주도 개발

- 매우 짧은 개발 서클의 반복을 갖는 소프트웨어 개발 프로세스
- 새로운 기능에 대한 자동화된 테스트케이스를 작성하고 해당 케이스를 통과하는 가장 짧고 가독성이 좋고 유지보수성이 뛰어난 코드를 작성

(실패하는 테스트 케이스를 먼저 작성한 후에 개발을 진행한다!)

- 일단 테스트를 통과하는 코드를 작성하고 상황에 맞게 리팩토링

=> 말 그대로 테스트가 주도하는 개발!

- **장단점**
- 개발하다 꼬여도 테스팅을 돌려봄으로써 안심하고 진행할 수 있음
- 보다 객체지향적이고 확장 가능이 용이한 코드, 재설계의 시간을 단축시킬 수 있는 코드, 디버깅 시간이 단축되는 코드
- 코드량이 늘기 때문에 빠른 생산성이 요구되는 시점에서 TDD는 큰 걸림돌일 수 있음

[https://lh4.googleusercontent.com/nHhGQjVb3HB5V_XXOwuSi8pGKpFpx7IACk20WpB4HRgs4WQEAvGJyg9h3gHzMvFSG0UdfQjimD8yXGhI5x25nrjVnWMjOzOnR7SKSRt_zu28dThuMbpDYPv6qvtoH0tUZ5wye33O](https://lh4.googleusercontent.com/nHhGQjVb3HB5V_XXOwuSi8pGKpFpx7IACk20WpB4HRgs4WQEAvGJyg9h3gHzMvFSG0UdfQjimD8yXGhI5x25nrjVnWMjOzOnR7SKSRt_zu28dThuMbpDYPv6qvtoH0tUZ5wye33O)

**1. 테스트 코드 작성하기**

앞서 말했던 것처럼 TDD는 테스트 주도 개발이기 때문에 구현해야할 부분을 코드를 먼저 작성해야 한다.

**2. 테스트 코드를 실행하기**

먼저 작성한 테스트 코드가 실패하는 지 확인해야 한다. 만약 이 테스트가 성공한다면 구현하지도 않은 부분의 코드의 테스트가 성공했다는 뜻이므로 버그를 찾아야 한다.

**3. 실패한 테스트 코드를 성공시키기 위한 최소한의 코드 구현하기**

이제 자신이 먼저 작성한 테스트 코드에 따라서 코드를 작성하면 된다.

**4. 코드 리팩토링하기**

필요에 따라서 구조적으로 잘못된 부분을 수정하면 된다.

2. BDD(Behavior-Driven-Development)

행동 주도 개발

- TDD를 근간으로 파생된 개발 프로세스
- TDD와 거의 유사하긴 하지만. 차이가 있다면 TDD는 테스트 자체에 집중해 개발하는 방면, BDD는 비즈니스 요구사항에 집중하여 테스트 케이스를 개발한다
- 테스트 케이스 자체가 요구사양이 되도록 하는 개발 방식
- TDD 를 결합해 시나리오 테스트까지 하는것
- 시나리오는 어디서부터 테스트를 시작할지, 어떤 것을 테스트하고 어떤 것을 하지 않을지, 한 번에 얼마만큼을 테스트할지, 테스트에 어떤 이름을 붙일지, 테스트가 왜 실패했는지 등에 대한 고민을 해결해줌
- 메소드 이름을 "이 클래스가 어떤 행위를 해야한다(should do something)" 라는 식의 문장으로 작성해 "**행위**"를 위한 테스트에 집중

**3. DDD(Domain_Driven-Development)**

도메인 주도 개발

- 일반적으로 많이 사용하는 데이터 중심의 접근법 X -> 순수한 도메인의 모델과 로직에 집중하는것
- 보편적인 언어의 사용을 추구 (유비쿼터스 언어)
- 상호가 이해할 수 있고 모든 문서와 코드가 동일한 표현과 단어로 구성되게!
- 분석 작업과 설계 그리고 구현까지 통일된 방식으로 커뮤니케이션 가능
- 도메인 모델부터 코드까지 항상 함께 움직이는 구조의 모델을 지향

[출처] [TDD, BDD, DDD, 테스트 주도 개발 개념 및 차이](https://blog.naver.com/rkdudwl/221973507455)|작성자 [영수달지](https://blog.naver.com/rkdudwl)