# JSX란

React에서 사용하는 `JavaScript를 확장한 문법`이다. 

JSX에서는 React “엘리먼트”를 생성한다. 화면에서 보고 싶은 것을 나타내는 표현이다.

React는 이 객체를 읽어 DOM을 구성하고, 최신 상태로 유지하는데 사용한다.

```jsx
return <div> 안녕하세요 </div>;
```

### 태그는 꼭 닫혀있어야 한다.

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
	return (
		<div>
			<Hello />
			<Hello />
			<Hello />
		<div>
		</ div>
	);
}

export defaullt App;
```

### 태그는 꼭 감싸져야한다.

App.js

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
	return (
		<div> ---> 아래 div 태그만 있다면 오류 발생
			<Hello />
			<div> 안녕히계세요. </div>
		<div>
		</ div>
	);
}

export defaullt App;
```

감싸기 위해 불필요한 div를 사용하는 대신 리액트의  `Fragment` 를 사용하면 된다.

Fragment는 브라우저상에서 따로 별도의 엘리먼트로 나타나지 않는다.

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
	return (
		<>
			<Hello />
			<div> 안녕히계세요. </div>
		<div>
		</>
	);
}

export defaullt App;
```

### JSX 안에 자바스크립트 변수를 보여줄 때는 {} 로 감싸야한다.

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
const name = 'react'
	return (
		<>
			<Hello />
			<div>{name}</div>
		</>
	);
}

export defaullt App;
```

### style 과 className은 camelCase 형태로 네이밍해야한다.

- 인라인 스타일은 **객체 형태**로 작성해야한다.
- **CSS class**를 설정해야할때 `className =` 으로 설정해야한다.

```
.gray-box {
  background: gray;
  width: 64px;
  height: 64px;
}
```

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
const name = 'react'
const style = {
	backgroundColor: 'black',
	color: 'aqua',
	fontSize: 24,
	padding: '1rem'
}

	return (
		<>
			<Hello />
			<div style={style}>{name}</div>
			<div className="gray-box"></div>
		</>
	);
}

export defaullt App;
```

### JSX 내부 주석은 {/* */}로 작성한다.

- 중괄호로 감싸지 않으면 화면에 보이게 된다.
