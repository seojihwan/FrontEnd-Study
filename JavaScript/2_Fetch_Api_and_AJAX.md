### Fetch APi && AJAX

---
2020.08.28 서지환

---
#### 배경
1990년대 초 웹 사이트는 완전한 HTML 페이지 기반 이여서 새로운 데이터가 들어올 때 마다 새로운 페이지를 로드해야했다.

사용성과 성능 개선을 위해 AJAX가 개발됨

---
#### Fetch API

ES6에 추가된 AJAX method

```js 
let promise = fetch(url, [options])
```
url - 접근하고자 하는 URL
options - 선택 매개변수, method또는 header 지정가능

fetch는 접근하고자 하는 URL에 네트워크 요청을 보내고 Promise를 반환한다.

서버에서 응답 헤더를 받자마자 fetch 호출 시 반환받은 promise가 내장 클래스 Response의 인스턴스와 함께 이행(fulfilled)또는 거부(rejected) 상태가 된다.

이를 통해 요청이 제대로 처리되었는지 확인할 수 있다.

이후 response의 Promise기반 method를 이용하여 응답된 데이터를 처리할 수 있다.
```js
let response = await fetch(url);

if (response.ok) { // HTTP 상태 코드가 200~299일 경우
  let json = await response.json();
} else {
  alert("HTTP-Error: " + response.status);
}
```
response.text() – 응답을 읽고 텍스트를 반환
response.json() – 응답을 JSON 형태로 파싱
response.formData() – 응답을 FormData 객체 형태로 반환
response.blob() – 응답을 Blob(타입이 있는 바이너리 데이터) 형태로 반환합니다.
response.arrayBuffer() – 응답을 ArrayBuffer(바이너리 데이터를 로우 레벨 형식으로 표현한 것) 형태로 반환
response.body - ReadableStream 객체인 response.body를 사용하면 응답 본문을 청크 단위로 읽을 수 있다.

---
#### AJAX(Asynchronous JavaScript and XML)
말 그대로 비동기적으로 자바스크립트와 XML이 동작하는 기술
서버의 응답을 기다릴 필요 없이 다른 코드를 처리할 수 있어 성능이 향상된다.

---
#### 참고사이트
https://javascript.info/fetch
https://en.wikipedia.org/wiki/Ajax_(programming)