# js 개념들

## 호이스팅, 이벤트 관리, 스코프 프로토타입, shadow DOM, strict

### 호이스팅

- hoisting : 함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효 범위의 최상단에 선언하는 것을 말한다.
    - 자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언한다.
       - 자바스크립트 Parser가 함수 실행 전 해당 함수를 한 번 훑는다.
       - 함수 안에 존재하는 변수/함수선언에 대한 정보를 기억하고 있다가 실행시킨다.
       - 유효 범위: 함수 블록 {} 안에서 유효
       - 실제 메모리에서는 변화가 없다.

- hoisting 대상 : var 변수 선언과 함수선언문에서만 호이스팅이 일어난다.
    - let과 const에서는 일어나지 않는다
    - 함수 선언문 vs 함수 표현식
    ```javascript=
    foo();
    foo2(); // 에러 발생

    function foo() { // 함수선언문
          console.log("hello");
    }
    var foo2 = function() { // 함수표현식
          console.log("hello2");
    }
    ```
- hoisting 우선순위
    - 같은 이름의 var변수 선언과 함수 선언에서 => 변수 먼저
  ```javascript=
  // 1. [Hoisting] 변수값 선언 
  var myName; 
  var yourName; 

  // 2. [Hoisting] 함수선언문
  function myName() {
      console.log("yuddomack");
  }
  function yourName() {
      console.log("everyone");
  }

  // 3. 변수값 할당
  myName = "hi";
  yourName = "bye";

  console.log(typeof myName); // > "string"
  console.log(typeof yourName); // > "string"
  ```
    - 값이 할당되어 있지 않은 변수와 값이 할당되어 있는 변수에서의 호이스팅
        - 값이 할당되어 있지 않은 변수의 경우, 함수선언문이 변수를 덮어쓴다.
        - 값이 할당되어 있는 변수의 경우, 변수가 함수선언문을 덮어쓴다.

- 정리
    - 코드의 가독성과 유지보수를 위해 호이스팅이 일어나지 않도록 한다.
    - 호이스팅을 제대로 모르더라도 함수와 변수를 가급적 코드 상단부에서 선언하면, 호이스팅으로 인한 스코프 꼬임 현상은 방지할 수 있다.
    - let/const를 사용한다.

### 이벤트 버블링 & 캡쳐링

- Event bubbling이란 
    - 이벤트 버블링은 특정 화면 요소에서 이벤트가 발생했을 때 해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성을 의미합니다.
    ```html=
    <body>
        <div class="one">
            <div class="two">
                <div class="three">
                </div>
            </div>
        </div>
    </body>
    ```
    ```javascript=
    var divs = document.querySelectorAll('div');
    divs.forEach(function(div) {
        div.addEventListener('click', logEvent);
    });

    function logEvent(event) {
        console.log(event.currentTarget.className);
    }
    ```
    - 위 코드에서 div에 클릭 이벤트를 모두 주었을 때, three를 클릭하게 되면 콘솔에 three, two, one이 출력됩니다. 
    - 브라우저는 특정 화면 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 화면 요소까지 이벤트를 전파시킵니다. 따라서, 클래스 명 three -> two -> one 순서로 div 태그에 등록된 이벤트들이 실행됩니다. 
    
- Event capture이란
    - 이벤트 캡쳐는 이벤트 버블링과 반대 방향으로 진행되는 이벤트 전파 방식입니다.
    - 위 와같은 html파일에 아래와 같이 캡쳐옵션을 달아주고
    ```javascript=
    var divs = document.querySelectorAll('div');
    divs.forEach(function(div) {
        div.addEventListener('click', logEvent, {
            capture: true // default 값은 false입니다.
        });
    });

    function logEvent(event) {
        console.log(event.currentTarget.className);
    }
    ```
    - 똑같이 three를 누르게 되면 console에 one, two, three순으로 나타나게 됩니다.

- event.stopPropagation()
    - 위와 같이 이벤트가 전달되는 방식을 막고 싶을때 사용합니다.
    - 위 코드에서 event.stopPropagation()를 사용하면 버블링에서는 three만 출력되고 캡쳐에서는 one만 출력됩니다.

- 이벤트 위임 (Event Delegation)
    - 하위 요소에 각각 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트들을 제어하는 방식입니다.
    - 이벤트 위임을 사용하면 여러 자식들이 있을때, 동적으로 추가된 자식에게 일일이 이벤트를 달아주지 않아도 됩니다. => 이벤트 버블링을 활용한 것

### 스코프 & 프로토타입

#### scope
- 정의 : 변수에 접근할 수 있는 범위, 전역(global), 지역(local)
- 블록 레벨 스코프
    - 블록 내에서만 유효한(참조 가능한) 변수
    - let, const에서만 블록 레벨 스코프가 적용된다.
    - var는 블록내에서 선언되었다 하더라도 전역으로 유효하다.
    ```javascript=
    var x = 0;
    {
      var x = 1;
      console.log(x); // 1
    }
    console.log(x);   // 1

    let y = 0;
    {
      let y = 1;
      console.log(y); // 1
    }
    console.log(y);   // 0
    ```
- 함수 레벨 스코프
    - 함수 내에서 선언된 매개변수와 변수는 함수 외부에서는 유효하지 않다.
    - 블록이랑 또 다름..
    ```javascript=
    var x = 'global';
    function foo() {
      var x = 'local';
      // x = 'local2' // 이면 전역의 x가 local2로 변한다.
      console.log(x);
    }

    foo();          // local
    console.log(x); // global
    ```
    - 중첩 스코프는 가장 인접한 지역을 우선하여 참조한다.
    ```javascript=
    var x = 10;

    function foo(){
      var x = 100;
      console.log(x); // 100

      function bar(){   // 내부함수
        x = 1000;
        console.log(x); // 1000
      }

      bar();
      console.log(x) // 1000
    }
    foo();
    console.log(x); // 10
    ```
    
- 렉시컬 스코프 
    - 함수를 어디서 선언하였는지에 따라 상위 스코프를 결정하는 것이다. 즉 함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 결정된다. 자바스크립트는 렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정된다. 함수를 어디에서 호출하였는지는 스코프 결정에 아무런 의미를 주지 않는다. 위 예제의 함수 bar는 전역에 선언되었다. 따라서 함수 bar의 상위 스코프는 전역 스코프이고 위 예제는 전역 변수 x의 값 1을 두번 출력한다.
    ```javascript=
    var x = 1;

    function foo() {
      var x = 10;
      bar();
    }

    function bar() {
      console.log(x);
    }

    foo(); // 1
    bar(); // 1
    ```
    
- 암묵적 전역
    - foo 함수가 호출되면 자바스크립트 엔진은 변수 y에 값을 할당하기 위해 먼저 스코프 체인을 통해 선언된 변수인지 확인한다. 이때 foo 함수의 스코프와 전역 스코프 어디에서도 변수 y의 선언을 찾을 수 없으므로 참조 에러가 발생해야 하지만 자바스크립트 엔진은 y = 20을 window.y = 20으로 해석하여 프로퍼티를 동적 생성한다. 결국 y는 전역 객체의 프로퍼티가 되어 마치 전역 변수처럼 동작한다. 이러한 현상을 암묵적 전역(implicit global)이라 한다.
    - 하지만 y는 변수 선언없이 단지 전역 객체의 프로퍼티로 추가되었을 뿐이다. 따라서 y는 변수가 아니다. 따라서 변수가 아닌 y는 변수 호이스팅이 발생하지 않는다.
    ```javascript=
    // 전역 변수 x는 호이스팅이 발생한다.
    console.log(x); // undefined
    // 전역 변수가 아니라 단지 전역 프로퍼티인 y는 호이스팅이 발생하지 않는다.
    console.log(y); // ReferenceError: y is not defined

    var x = 10; // 전역 변수

    function foo () {
      // 선언하지 않은 변수
      y = 20;
      console.log(x + y);
    }

    foo(); // 30
    ```
[참조 (스코프)](https://poiemaweb.com/js-scope)

#### prototype

