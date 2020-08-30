## moduler js && ES 6

### 모듈러 js

- Module이란
    - Module은 단지 파일 하나에 불과합니다. 스크립트 하나는 모듈 하나입니다.
     - Module에 특수한 지시자 `export`와 `import`를 적용하면 다른 모듈을 불러와 불러온 모듈에 있는 함수를 호출하는 것과 같은 기능 공유가 가능합니다.
     
    
- Module의 핵심기능
    - 항상 엄격 모드 `use strict` 실행됩니다.
        - 선언되지 않은 변수에 값을 할당하는 등의 코드는 에러를 발생시킵니다.
    - 모듈 레벨 스코프
        - 모듈은 자신만의 스코프가 있습니다. 따라서 모듈 내부에서 정의한 변수나 함수는 다른 스크립트에서 접근할 수 없습니다.
    - 단 한번만 평가됨
        - 동일한 모듈이 여러 곳에서 사용되더라도 모듈은 최초 호출 시 단 한 번만 실행됩니다. 실행 후 결과는 이 모듈을 가져가려는 모든 모듈에 내보내 집니다.
    - import.meta
        - `import.meta` 객체는 현재 모듈에 대한 정보를 제공해줍니다.
    - this
        - 모듈 최상위 레벨의 this는 undefined입니다.
        - 모듈이 아닌 일반 스크립트의 this는 전역 객체인 것과 대조됩니다.
    - 비동기
        ```javascript=
        <script type="module">
          alert(typeof button); 
          // 모듈 스크립트는 지연 실행되기 때문에 페이지가 모두 로드되고 난 다음에 얼럿 함수가 실행되므로
          // 얼럿창에 object가 정상적으로 출력됩니다. 모듈 스크립트는 아래쪽의 button 요소를 볼 수 있죠.
        </script>

        // 하단의 일반 스크립트와 비교해 봅시다.

        <script>
          alert(typeof button); // 일반 스크립트는 페이지가 완전히 구성되기 전이라도 바로 실행됩니다.
          // 버튼 요소가 페이지에 만들어지기 전에 접근하였기 때문에 undefined가 출력되는 것을 확인할 수 있습니다.
        </script>

        <button id="button">Button</button>
        ```
    - 경로가 없는 모듈은 금지
        ```javascript=
        import {sayHi} from 'sayHi'; // Error!
        // './sayHi.js'와 같이 경로 정보를 지정해 주어야 합니다.
        ```
    - 외부 스크립트
        - src 속성값이 동일한 외부 스크립트는 한 번만 실행됩니다.
        - 외부 사이트같이 다른 오리진에서 모듈 스크립트를 불러오려면 fetch와 Cross-Origin 요청 챕터에서 설명한 바와 같이 CORS 헤더가 필요합니다. 모듈이 저장되어있는 원격 서버가 Access-Control-Allow-Origin: * 헤더를 제공해야만 외부 모듈을 불러올 수 있습니다. 참고로 * 대신 페치(fetch)를 허용할 도메인을 명시할 수도 있습니다.

### ES 6

#### ES6 Features

- Classes
    - Class 문법을 제공합니다. constructor 메소드도 사용할 수 있고 extends를 통해서 클래스 상속도 가능합니다.

    ```javascript
     class Person {
        constructor (id, name) {
            this.id = id
            this.name = name
        }
        toString() {
            return `(${this.id}, ${this.name})`
        }
    }

    class Student extends Person {
        constructor (id, name, age) {
            super(id, name)
            this.age = age
        }
        toString() {
            return super.toString() + ' and ' + this.age
        }
    }
    ```
- let & const
    - const 는 블록 범위이며 값이 지정되면 나중에 바꿀 수 없습니다. 또한, 재선언 될 수도 없습니다.
    ```javascript
    const schoolName = "ABC"
    schoolName = "CBA"  // Error    
    ```
    - let 은 블록 범위이며 값이 지정되어도 값을 바꿀 수 있습니다.
    ```javascript
    function test() {
      let x = "a"
      if (true) {
        let x = "b"
        console.log(x);  // b
      }
      console.log(x);  // a
    }
    ```
- Arrow Functions
    - Arrow Function 은 자신만의 this를 생성하지 않습니다
    - Arrow Function는 자신의 this가 바인드 되지 않기 때문에 함수의 스코프에서의 this 가 적용됩니다.

- Modules
    - Export, Import 를 이용해 function이나 variables 들을 다른 곳에서 사용할 수 있습니다. 

- Promises
    - 비동기 프로세싱을 위해 사용됩니다. (Asynchronously)
    - 가독성이 좋으며 중첩된 콜백의 단점을 완화합니다. (Callback Hell이라는 Callback 함수가 다시 Callback을 호출하고 또다시 Callback을 호출하는 코드를 읽기도 관리하기도 힘들어지는 것은 완화할 수 있습니다.)
    - Promise의 세가지 상태
        - 대기중(pending)
        - 이행됨(fulfilled)
        - 거부됨(rejected)
        ```javascript
        var promiseTest = (num) => {
            return new Promise((resolve, reject) => {
                if (num > 3) {
                    resolve(num)
                } else {
                    reject("err")
                }
            }
        }

        promiseTest(5)
            .then(val => console.log(val)) // 5
            .catch(err => console.log(err))
        ```

    