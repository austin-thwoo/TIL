https://codepen.io/pen/?editors=0011

https://www.youtube.com/watch?v=KF6t61yuPCY

함수
- alert(): 경고창
- console.log() 

변수
- let 변수선언 - 바뀔 수 있음
- const 상수선언 : 절대 바뀌지않는 상수 ex)pi=3.14 / birthday =0125
- tip
  - 1. 변수는 문자와 숫자, $와 _만 사용  ex) let _ =1 ; / let $ =3;
  - 2. 첫글자는 숫자가 될 수 없다 ex) let 1model XXXX
  - 3. 예약어는 사용 할 수 없습니다. ex) let let ="3" XXXX
  - 4. 가급적 상수는 대문자로 ex) MAX_NUM=3;
  - 5. 변수명은 읽기 쉽고 이해할 수 있게 선언
  
자료형
const name1 = "austin";
const name1 = 'austin";
const name1 = `austin`;

const message1 = "I'm a boy.";
const message2 = 'I\'m a boy.'; 역슬래쉬를 함께쓰면 특수문자로 인식함

cosnt age = 20;
const message3 = `my name is ${age+8}.`;



typeof : 변수타입 알아내기

대화상자
alert() : 경고창 띄우기(알림)
prompt : 입력받을 수 있는 확인창 띄우기
prompt(messeage,<optional>default)
confirm: 확인받기 return : bool 
