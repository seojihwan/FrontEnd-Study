### Convention: 협약

HTML의 Convention이란 코드를 더 쉽게 읽고 이해하기 위한 협약이다.


이에 대한 여러가지 좋은 방침을 w3schools에서 확인할 수 있었다.
[w3schools](https://www.w3schools.com/html/html5_syntax.asp)

#### HTML에는 대 소문자 모두 사용가능하지만, 소문자를 사용하기

```html
<body>
<p>This is a paragraph.</p>
<a href="https://www.w3schools.com/html/">Visit our HTML tutorial</a>
</body>

```
vs
```html
<BODY>
<P>This is a paragraph.</P>
<a HREF="https://www.w3schools.com/html/">Visit our HTML tutorial</a>
</BODY>

```
#### 닫을 필요가 없는 태그들도 닫기
```html
<section>
  <p>This is a paragraph.</p>
  <p>This is a paragraph.</p>
</section>
```
vs
```html
<section>
  <p>This is a paragraph.
  <p>This is a paragraph.
</section>
```

#### 따옴표를 이용하여 속성 값 표기

```html
<table class="striped">
```
vs

```html
<table class=striped>
```
#### 이미지의 alt, width, height 지정

alt: 이미지를 표시할 수 없는 경우 사용
width, height: 브라우저가 로딩하기 전 이미지를 위한 공간 선점을 통해 화면 깜박임을 줄임
```html
<img src="html5.gif" alt="HTML5" style="width:128px;height:128px">
```

#### 공백, 등호

각 엔티티를 공백없이 묶어 사용하기
```html
<link rel="stylesheet" href="styles.css">
```

가독성을 위해 빈 줄, 띄어쓰기 두칸의 공백 이용하기

```html
<body>
  <h1>Famous Cities</h1>

  <h2>Tokyo</h2>
  <p>
    Tokyo is the capital of Japan, the center of the Greater Tokyo Area, and the most populous
    metropolitan area in the world. It is the seat of the Japanese government and the Imperial
    Palace, and the home of the Japanese Imperial Family.
  </p>
</body>
```

#### \<title> 생략하지 않기

SEO에서 배운것 처럼 검색 결과에 나타나는 조건중 중요한 요소이다.

#### 뷰포트 설정하기

페이지의 너비를 장치의 화면 크기에 맞게 조정한다.
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">

```
#### 주석

1줄
```html
<!-- This is a comment -->
```
2줄 이상
```html
<!--
  This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example.
-->
```

#### 소문자 파일 이름 사용

일부 웹 서버는 파일 이름의 대소 문자를 구분하기도, 구분하지 않기도 한다.
만약 대소 문자를 구분하지 않는 서버에서 대소 문자를 구분하는 서버로 이동한다면 문제가 발생할 수 있다. 이를 방지하기 위해 소문자 파일 이름을 사용하자

#### 기본 파일 이름
서버는 기본적으로 URL끝에 파일이름을 지정하지 않으면 index.html으로 기본 파일 이름을 추가한다.
