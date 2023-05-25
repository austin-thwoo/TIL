### 패키지 구조


#### 1. 레이어 계층형
![picture/git_good.png](spring/../picture/1.png)
장점 : 해당 프로젝트에 대한 이해가 낮아도 전체적인 구조를 빠르게 파악
단점 : 디렉토리에 클래스들이 너무 많이 모이게 됨


#### 2. 도메인형
![picture/git_good.png](spring/../picture/2.png)
장점 : 코드 응집
단점 : 구조파악 어려움
yeahyeahyeah
###### 2-1. 전체구조
![picture/git_good.png](spring/../picture/3.png)
/////

## Spring
### @Controller
@Controller - view와 연결지을수있다 
@RestController  controller + responseBody
컨트롤러에responseBody를 추가시켜 편리한 어노테이션
클래스레벨 메소드레벨
view를 리졸빙 하는게 아니고 body로 리턴해ㅜㅈㅁ

 ### 함수형 프로그래밍?
  - 특징
    - 상태가 엇음
    - 대입문이 없음
    - 부작용이(side effect) 없는 순수함수
    - 불변셩(immutability)
    - 역사가 오래됨
 - 함수형 엔드포인트
   - spring web 의 엔드포인트를 함수형 스타일로 작성하는 방버을 제공
   - webMvc.fn
   - routing, requestHandling
   - 불변성을 고려하여 설계됨
   - 기존의 DispatcherServket위에서 동작
   - 애노테이션 스타일과 함께 사용 가능
 - 주요 키워드
   - handler fuction == @RequestMapping
     - 입력 serverReqyest
     - 츌력 serverResponse
   - RouterFuntio == @RequestMapping
     - 입력 serverRequest
     - 출력 Optional<HandlerFuntion>
    - handlerfunction vs routerFunction
      - handlerFunction 의 결과 : data
      - routerFunction 의 결과 : data + behavior
 https://ko.wikipedia.org/wiki/함수형_프로그래밍
 https://en.wikipedia.org/wiki/Functional_programming
https://blog.cleancoder.com/uncle-bob/2012/12/22/FPBE1-Whats-it-all-
about.html
https://docs.spring.io/spring-framework/docs/current/reference/html/
web.html#webmvc-fn