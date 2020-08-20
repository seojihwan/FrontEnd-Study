## HTTP란 무엇인가?

- **HTTP** 는 Hyper Text Transfer Protocol의 두문자어로, 인터넷에서 데이터를 주고받을 수 있는 **프로토콜** 입니다.
- **프로토콜 :** 컴퓨터들 간의 정보 교환에 있어, 네트워크에서 프로토콜이 맞지않으면 통신이 불가능하다. 정보의 정확한 교환을 위해서는 프로토콜의 사용이 필수적이라고 할 수 있다. 그리하여 일정한 약속을 정해 여러 계층으로 나눠진 네트워크에서 동위 계층에서 사용하는 표준통신규약을 만들어 두었는데, 이 네트워크 통신규약이 프로토콜이다.

## HTTP 동작

클라이언트(사용자)가 브라우저를 통해서 어떠한 서비스를 요청(request)을 하면 서버에서는 해당 요청사항에 맞는 결과를 찾아서 사용자에게 응답(response)하는 형태로 동작한다.

![image alt](https://media.vlpt.us/post-images/surim014/e0aa5520-2d59-11ea-86da-fb3b00230640/image.png)

#### 1. 사용자가 웹 브라우저에 URL 주소 입력

#### 2. DNS 서버에 웹 서버의 호스트 이름을 IP 주소로 변경 요청한다.

#### 3. 웹 서버와 TCP 연결 시도

- HTTP는 TCP/ IP를 이용하는 응용 프로토콜이다.

#### 4. 클라이언트가 서버에게 Request 한다

- Request 메시지 구조

  - Request Line => Request Method + URL + HTTP ver.
  - Request Headers
  - Request Body

![image alt](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile3.uf.tistory.com%2Fimage%2F9943544C5BB4BF5231E17E)

#### 5. 서버가 요청에 대한 답변을 클라이언트에게 Response 한다

- Response 메시지 구조

  - Status Line => HTTP ver. + Status Code + Status Name
  - Response Header
  - Response Body

![image alt](https://media.vlpt.us/post-images/rosewwross/6fc65770-4b39-11ea-abce-67c155f8f58a/image.png)

#### 6. 서버 - 클라이언트간 연결 해제

#### 7. 웹 브라우저가 웹 문서를 출력한다.

## HTTP Method

클라이언트가 서버로 요청을 할 때, 어떠한 목적을 갖는 행위인지 HTTP 메서드에 명시합니다.

- **GET**
  - 서버에게 리소스를 달라는 요청 ( 조회 )
- **HEAD**
  - 정확히 GET과 같지만, 서버는 응답으로 엔터티 본문 반환없이 헤더만을 반환.
  - 클라이언트는 리소스를 가져올 필요 없이 헤더만을 통해 정보를 얻을 수 있습니다.
- **PUT**
  - 서버가 요청의 본문을 갖고 요청 URI의 이름대로 새 문서를 만들거나, 이미 URI가 존재한다면 요청 본문을 변경할 때 사용합니다. ( 수정 )
- **POST**
  - 서버에 입력데이터를 전송하며 요청 엔티티 본문에 데이터를 넣어 서버에 전송합니다. ( 삽입 )
- **DELETE** - 서버에서 요청 URI 리소스를 삭제하도록 요청합니다. ( 삭제 )
  클라이언트는 항상 삭제된다고 생각하지만, 서버에서는 이 요청을 무시할 수도 있습니다.
- **TRACE**
  - 클라이언트와 목적지 서버 사이에 있는 모든 HTTP 애플리케이션의 요청/응답 연쇄를 따라가면서 자신이 보낸 메시지의 이상 유무를 파악합니다.
  - 서버는 응답 메시지의 본문에 자신이 받은 요청메시지를 넣어 응답하며, 주로 진단을 위해 사용합니다.
- **OPTIONS**
  - 서버에게 특정 리소스가 어떤 메소드를 지원하는지 물어볼 수 있습니다.

## HTTP 헤더

패킷에 대한 정보들을 담고 있습니다.
[제로초 님의 헤더관련 강의](https://www.zerocho.com/category/HTTP/post/5b3ba2d0b3dabd001b53b9db)

## Response 상태 코드

- **100 - 109**
  - 메시지 정보
- **200 - 206**
  - 요청 성공
- **300 - 305**
  - 리다이렉션
- **400 - 415**
  - 클라이언트 에러
- **500 - 505**
  - 서버에러

## HTTP/1.1 & HTTP/2.0

[자세한 설명 보기](https://www.popit.kr/%EB%82%98%EB%A7%8C-%EB%AA%A8%EB%A5%B4%EA%B3%A0-%EC%9E%88%EB%8D%98-http2/)

### 참고 사이트

- https://jess-m.tistory.com/17
- https://victorydntmd.tistory.com/286
- https://www.zerocho.com/category/HTTP
- https://www.popit.kr/%EB%82%98%EB%A7%8C-%EB%AA%A8%EB%A5%B4%EA%B3%A0-%EC%9E%88%EB%8D%98-http2/
- https://velog.io/@surim014/HTTP%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
