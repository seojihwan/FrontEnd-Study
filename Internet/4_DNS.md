## DNS(Domain Name System)

#### 목적

도메인 사용자에게 특정 이름을 부여함으로써 관리하기 위해 만들어짐

example.com => 126.153.141.1 

---
#### Process

![image](https://i.imgur.com/6gFzwoZ.png)

1. 사용자가 웹 브라우저에 `naver.com` 주소를 입력하면 쿼리가 `Resolver`에게 전달됨
2. `Resolver`가 `Root Server`에 쿼리 요청
3. `Root Server`가 최상위 도메인(`TLD`)서버 주소 반환
4. `TLD`에 Domain Name System Server에 대한 IP요청
5. `DNS Server`의 IP주소 Resolver에 반환
6. `DNS Server`에 쿼리 전달
7. `naver.com`에 해당하는 ip주소를 Resolver에 반환
8. Resolver가 Client에 IP주소 전달
9. 브라우저가 IP주소에 HTTP 요청
10. `naver.com`과 통신

---

#### 개념 정리
- 모든 컴퓨터들은 Root Server의 주소를 알고 있다.
- Root Server들은 Top-level DNS Server의 주소를 알고 있다.
- Top-Level DNS(TLD) Server는 Name Server의 주소를 알고 있다.

####  이를 통해 클라이언트는 수 많은 도메인에 대한 ip주소를 알 수 있다.
