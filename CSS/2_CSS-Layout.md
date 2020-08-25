# CSS Layout
레이아웃이란, 화면 상의 문자 또는 그림 등의 구성 및 배열을 뜻한다.
### 1.Float
float 속성은 다른 텍스트나 inline 요소가 자신의 컨테이너를 감싸게 해주는 속성이다. 왼쪽 또는 오른쪽(때에 따라 전역 값 혹은 블록의 시작 위치에 따라)에 배치될 수 있다. float 속성이 없는 그림과 글이 있다면 그림이 존재하는 행에서는 그림만 존재할 것이다. 
![](https://i.imgur.com/EBNLXTd.jpg)
위 사진은 float 속성의 값을 left로 준 결과이다. float 속성은 그림뿐만 아니라 텍스트에도 지정해줄 수 있다.

### 2.Positioning
CSS의 position 속성은 요소의 배치 위치를 결정해주는 속성이다. 속성 값으로 relative, static, absolute, fixed, sticky가 있다.
#### relative
top, bottom, left, right을 통해 자신의 위치 기준으로 배치 위치를 변화시킬 수 있다.
![](https://i.imgur.com/8TXy0zJ.jpg)
#### static
태그들의 position을 지정해주지 않은 초기 상태이다. 요소들이 왼쪽에서 오른쪽으로, 위쪽에서 아래쪽으로 배치된다.
![](https://i.imgur.com/Aoa7VWq.jpg)
#### absolute
부모들 중에서 position: static 속성을 가지고 있지 않은 부모를 기준으로 배치한다. 만약 없다면 body가 기준이 된다.
![](https://i.imgur.com/CaFQP1o.jpg)
#### fixed
뷰포트에서 고정된 위치를 갖는다. 스크롤이 움직여도 고정되어 있다.
#### sticky
fixed와 다르게 scroll 박스를 기준으로 고정된다. 스크롤이 임계점에 다다르면 일반적인 흐름을 따른다.
![](https://i.imgur.com/vmMx1C2.jpg)

### 3.Display
display 속성은 요소를 어떻게 나타낼지 결정할 수 있다. b, span, a 같은 태그들은 inline 속성을 갖는다. 줄바꿈이 되지 않는게 특징이다. div, p와 같은 태그들은 block 속성이고 줄바꿈을 갖는다. display 속성을 통해 inline 태그들을 block 속성처럼 나타낼 수 있다. 예를 들어, span 태그의 display 속성 값을 block으로 준다면 하나의 행이 아닌 여러개의 행으로 줄바꿈되어 나타날 것이다. display: none은 보여지지 않고, display: inline-block은 내부는 block 형태이지만 요소들은 inline으로 나타난다.
![](https://i.imgur.com/CDXQ2As.png)

### 4.Box Model
![](https://i.imgur.com/JYDWhPK.png)
#### CSS 기초배우기 문서 참조

### 5.Flex Box
Flex Box는 레이아웃 배치 전용 기능으로 고안됐다. 기존 float, inline-block 등을 이용한 방법보다 강력하고 편리한 기능이 많다. Flex Box는 가로를 나타내는 메인 축과 세로를 나타내는 교차 축이 존재한다. 그리고 부모 요소를 Container, 자식 요소를 Item이라고 한다. display: flex으로 Flex Box 선언 가능하고 지원하는 기능들은 다음과 같다.
* flex-direction : 배치 방향 설정
* flow-wrap : 줄넘김 처리
* flex-flow : flex-direction과 flow-wrap을 한 번에 지정
* justify-content : 메인 축 방향 정렬
* align-items, content : 교차 축 방향 정렬
* flex-basis : 아이템의 기본 크기 설정
* flex-grow : 유연하게 늘리기
* flex-shrink : 유연하게 줄이기
* order : 아이템의 시각적 나열 순서

### 6.CSS Grid
Flex Box는 한 방향 레이아웃이지만 CSS Grid는 두 방향 레이아웃이다. Flex Box와 마찬가지로 부모 요소를 Grid Container, 자식 요소를 Grid Item이라고 한다. display: grid로 선언 가능하다.
![](https://i.imgur.com/40hpjbU.jpg)
(출처 : https://studiomeal.com/archives/533)
