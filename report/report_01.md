# HTML & CSS 기초 정리

> 공부한 날짜: 2026년 10월
> 목표: 포트폴리오 사이트를 직접 만들면서 배운 개념 기록

---

## 1. HTML이란

HTML은 **"이 내용이 무슨 역할인지"**를 정해주는 언어. 디자인(색깔, 크기, 위치)이 아니라 **구조**를 만드는 역할.

비유하면, HTML은 책의 **목차와 본문 배치**를 정하는 것이고, 디자인(CSS)은 그 책의 **표지 디자인과 폰트**를 고르는 것.

### 기본 뼈대

```html
<html>
  <head>
    <title>페이지 제목</title>
  </head>
  <body>
    여기에 화면에 보이는 모든 내용이 들어감
  </body>
</html>
```

- `<html>`: 문서 전체를 감싸는 가장 바깥 껍데기
- `<head>`: 화면엔 안 보이지만 브라우저가 알아야 할 정보 (탭에 뜨는 제목, CSS 연결 등)
- `<body>`: 실제로 화면에 보이는 모든 내용

---

## 2. 자주 쓰는 태그

| 태그 | 역할 | 예시 |
|---|---|---|
| `<h1>` ~ `<h6>` | 제목. 숫자가 작을수록 더 큰(중요한) 제목 | `<h1>이장원</h1>` |
| `<p>` | 문단 하나 | `<p>안녕하세요</p>` |
| `<a>` | 링크 | `<a href="주소">클릭</a>` |
| `<img>` | 이미지 | `<img src="사진.png">` |
| `<ul>` + `<li>` | 리스트(목록). `<ul>`은 리스트 전체, `<li>`는 항목 하나 | 아래 참고 |
| `<div>` | 의미는 없고 영역만 묶는 상자 | `<div>...</div>` |

### 리스트 예시

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>Javascript</li>
</ul>
```

➡️ 결과: 점(•)이 찍힌 목록 3개 생성됨

> ⚠️ **실수 포인트**: `<li>` 하나에 여러 내용을 몰아넣으면 안 됨. 항목이 3개면 `<li>`도 3번 써야 함.

---

## 3. 속성(attribute)이란

태그 혼자서는 못 하는 일이 있음. 예를 들어 `<a>` 태그는 "여기 링크임"을 알려주지만, **어디로 연결할지는 따로 알려줘야 함**. 이때 쓰는 게 속성.

```html
<a href="mailto:jw19@dankook.ac.kr">jw19@dankook.ac.kr</a>
```

- `href`가 속성 이름, `"mailto:jw19@dankook.ac.kr"`이 속성값
- `mailto:`를 앞에 붙이면 브라우저가 "이건 이메일 주소구나"라고 인식해서 메일 작성 화면을 띄움

> ⚠️ **처음에 했던 실수**: `href` 없이 화면에 보이는 글자에만 `mailto:`를 써놓으면, 그냥 텍스트일 뿐 실제로 작동하는 링크가 아님. 속성에 넣어야 진짜 작동함.

---

## 4. CSS란

CSS는 HTML로 짠 구조에 **디자인을 입히는 언어**. 글자 색, 배경색, 크기, 간격 등을 지정함.

### CSS를 HTML에 연결하는 법

`index.html`의 `<head>` 안에 아래 한 줄 추가:

```html
<link rel="stylesheet" href="style.css">
```

"style.css라는 파일을 가져와서 이 페이지에 디자인으로 입혀라"는 의미.

### 기본 문법

```css
h1 {
  color: blue;
}
```

- `h1` → **선택자**: "h1 태그를 가진 모든 요소를 골라라"
- `{ }` 안 → 그 요소에 적용할 디자인 규칙들
- `color: blue;` → **속성: 값;** 형태. 반드시 세미콜론(`;`)으로 종료.

### 여러 태그를 한 번에 선택

```css
h1, h2 {
  color: white;
}
```

콤마(`,`)로 여러 선택자를 나열하면 하나씩 따로 안 써도 한 번에 적용됨.

---

## 5. 클래스(class) — 같은 태그를 다르게 꾸미기

같은 `<p>` 태그라도 "이건 굵게, 저건 그냥"처럼 다르게 하고 싶을 때 클래스 사용.

**1단계: HTML에서 이름표 달기**
```html
<p class="intro">안녕하세요</p>
```

**2단계: CSS에서 그 이름표에 규칙 걸기**
```css
.intro {
  font-weight: bold;
}
```

> 💡 **중요 포인트**: CSS에서 클래스를 선택할 땐 이름 앞에 **마침표(`.`)**를 붙임. (`p`나 `h1`처럼 태그 이름을 선택할 땐 마침표 없음)

> ⚠️ **실수 포인트**: CSS에 `.intro { }`를 써놓기만 하고 HTML 쪽 태그에 `class="intro"`를 안 붙이면 아무 효과 없음. 둘 다 해야 적용됨.
> 비유: CSS의 `.intro { }`는 "intro 이름표 단 사람한테 모자 씌워줘"라는 규칙서, HTML의 `class="intro"`는 실제로 그 사람한테 이름표를 달아주는 행동. 이름표 없으면 규칙서가 있어도 소용없음.

---

## 6. 박스 모델 — 요소는 전부 네모 상자

모든 HTML 요소는 눈에 안 보이는 네모 상자로 둘러싸여 있음. 이 상자는 4겹.

| 용어 | 의미 | 비유 |
|---|---|---|
| `content` | 실제 글자/이미지가 들어가는 부분 | 액자 속 그림 |
| `padding` | 내용물과 테두리 사이 안쪽 여백 | 그림과 액자 틀 사이 여백 |
| `border` | 테두리 선 | 액자 틀 |
| `margin` | 테두리 바깥, 다른 요소와의 간격 | 액자와 액자 사이 벽 공간 |

### 예시

```css
div {
  border: 1px solid white;
  padding: 20px;
}
```

- `border: 1px solid white;` → 두께 1px, 실선(`solid`), 흰색 테두리
  - 점선으로 바꾸려면 `dashed`
- `padding: 20px;` → 안쪽 여백 20px

```css
body {
  padding: 40px;
}
```

→ 화면 전체(`body`) 가장자리에 40px 여백 추가. 글자들이 화면 끝에 딱 붙지 않고 여유 공간 생김.

---

## 7. Flexbox — 요소를 가로로 나란히 배치

HTML 요소는 기본적으로 **위에서 아래로 세로**로 쌓임. 이걸 가로로 나란히 배치하고 싶을 때 쓰는 게 Flexbox.

### 핵심 원리: 부모와 자식

Flexbox는 "부모"가 "자식"들을 정렬하는 방식.

```html
<div class="row">
  <div>상자 1</div>
  <div>상자 2</div>
</div>
```

```css
.row {
  display: flex;
  gap: 20px;
}
```

- `display: flex;` → "나는 flex 컨테이너(부모)임"을 선언
- 바로 안에 있는 **직속 자식들**(상자 1, 상자 2)이 자동으로 가로 나란히 배치됨
- `gap: 20px;` → 자식들 사이 간격을 20px로 지정

> ⚠️ **처음에 했던 실수**: `class="row"`를 두 번 따로 써서 각각 자식이 1개씩만 있었음. Flexbox는 **같은 부모 안에 형제로 같이 있는 요소들끼리** 나란히 배치하는 거라, 자식이 1개뿐이면 나란히 놓을 상대가 없어서 효과가 안 보임. 나란히 놓고 싶은 요소들을 **하나의 부모** 안에 함께 넣어야 함.

### 정렬 세부 조정

```css
.row {
  display: flex;
  gap: 20px;
  justify-content: space-between; /* 가로 방향 정렬 */
  align-items: center;            /* 세로 방향 정렬 */
}
```

**`justify-content`** (가로 방향으로 어떻게 퍼질지)

| 값 | 결과 |
|---|---|
| `flex-start` (기본값) | 왼쪽부터 쭉 붙음 |
| `center` | 가운데로 모임 |
| `space-between` | 양 끝에 붙고, 사이 간격은 균등하게 벌어짐 |
| `space-around` | 각 요소 둘레에 균등한 여백 |

**`align-items`** (세로 방향으로 어디에 맞출지)

| 값 | 결과 |
|---|---|
| `flex-start` | 위쪽 맞춤 |
| `center` | 세로 가운데 맞춤 |
| `flex-end` | 아래쪽 맞춤 |
| `stretch` (기본값) | 가장 큰 요소 높이에 맞춰 늘어남 |

> 💡 `gap`과 `justify-content`는 역할이 다름. `gap`은 "요소 사이 최소 간격을 몇 px로 할지" 지정, `justify-content`는 "요소들을 가로줄 전체에서 어떻게 배치할지" 지정. `space-between` 사용 시 `gap`보다 간격이 더 벌어져 보일 수 있음.

---

## 8. 오늘까지 배운 내용 코드로 정리

**index.html (구조)**
```html
<html>
  <head>
    <title>jw-portfolio</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>이장원</h1>

    <div class="row">
      <div>
        <p class="intro">자기소개...</p>
        <a href="mailto:jw19@dankook.ac.kr">jw19@dankook.ac.kr</a>
      </div>
      <div>
        <h2>010-4449-5126</h2>
        <p>ljw.jang05@gmail.com</p>
      </div>
    </div>

    <h2>기술 스택</h2>
    <ul>
      <li>HTML</li>
      <li>CSS</li>
      <li>Javascript</li>
    </ul>
  </body>
</html>
```

**style.css (디자인)**
```css
h1, h2 {
  color: white;
}

body {
  background-color: black;
  padding: 40px;
}

p {
  font-size: 30px;
  color: white;
}

li {
  color: white;
}

.intro {
  font-weight: bold;
}

div {
  border: 1px solid white;
  padding: 20px;
}

.row {
  display: flex;
  gap: 20px;
  justify-content: space-between;
  align-items: center;
}
```

---

## 9. 앞으로 배울 것 (예정)

- [ ] `@media` — 화면 크기에 따라 다른 디자인 적용 (반응형, 모바일 대응)
- [ ] `flex-direction` — Flexbox 방향을 세로로 전환
- [ ] CSS 변수(`:root`, `var()`) — 색상 한 번에 관리
- [ ] 폰트 적용

---

## 10. 오늘 느낀 점 / 헷갈렸던 것

> class 이름이 같으면 여러 부분을 따로 묶어도 같은 객체로 여겨져 묶일 줄 알았음. 하지만 그냥 중복되는 자식으로 인식되는 것이었음.
> href 하고 mailto를 수식어로 생각해 텍스트 입력 공간에 적었는데 그게 아니라 하나의 형식 명령어였음.