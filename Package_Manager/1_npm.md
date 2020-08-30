### npm(Node Package Manager)

많은 개발자들이 패키지를 공유하고 관리하는 세계에서 가장 큰 소프트웨어 레지스트리

#### 터미널 명령어

- npm init: package.json 생성
- npm search [package이름]: 패키지 검색
- npm install [package이름 || url || path || tag]
  옵션
  - -P or --save-prod (default): npm install dependencies
  - -D or --save-dev: devDependencies
  - -O or --save-optional: optionalDependencies
  - --no-save: dependencies에 저장 X
  - -E or --save-exact: ^, ~ 연산자가 포함되지 않은 정확한 버전이 설치됨
  - -B: bundleDependencies
  - -g: 전역설치
- npm ls: 설치된 파일을 전부 보여줌
  install의 태그 모두 사용가능함
- npm help [명령어]: 명령어에 대한 설명 알려줌
<br>
- npm update: 설치한 패키지 업데이트
- npm dedupe: 중복 패키지 정리
- npm cache clean: npm의 cache를 보여줌
- npm cache clean: npm cache 삭제
- npm rebuild npm 재설치
<br>
- npm config list: 현재 설정 확인
- npm set [이름] [value]: 속성 설정
- npm get [이름]: 속성 조회
##### version 연산자
![](./img/v_operator.png)

https://heropy.blog/2018/02/18/node-js-npm/
#### package.json

npm 에 패키지를 등록하기 위한 이름, 버전, 설명, 운영 환경(운영 체제, 엔진, 종속성), 종속 되지 않는 패키지 및 파일 정보를 기록하는 파일
https://docs.npmjs.com/files/package.json

