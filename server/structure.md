# data_structure_algorithm

## 1.기본 자료구조

- 자료구조 : 데이터 단위와 데이터 자체 사이의 물리적 또는 논리적 관계
- 배열 : 같은자료형의 변수로 이루어진 구성요소
  - `int[] a;`  `int a[];`  
   </br>
- 값을 대입하지 않은 지역 변수 (전역변수라면 기본값)
  `int a; //값이 들어있지 않은 지역변수 에서 값을 꺼내려 할때`  
  `System.out.println("a 의값으 + a + 입니다.")` -> 컴파일 오류  
</br>

- 접근 제한자
  - 객체의 멤버의 대한 접근을 제한할때 이를 접근 제한자라 합니다.
  - 접근 제한자 종류
    - public : 모든 접근 허용
    - protected : 같은 패키지의 객체, 상속 관계의 객체 허용
    - default : 같은 패키지의 객체 허용
    - private : 현재의 객체 안에서만 허용
  - 접근 제한자 사용
    - 클래스 : public, default
    - 생성자 : public, protected, default, private
    - 멤버변수 : public, protected, default, private
    - 지역변수 : 접근 제한자를 사용할 수 없음