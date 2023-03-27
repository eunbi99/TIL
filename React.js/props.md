# props

- 어떤 값을 컴포넌트에게 전달해줘야 할 때, props를 사용한다.
- props는 객체 형태로 전달되어 .를 사용하여 조회하면 된다.

App.js

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
  return (
    <Hello name="react" />
  );
}

export default App;
```

Hello.js

```jsx
import React from 'react';

function Hello(props) {
	return <div>안녕하세요 {props.name}</div>

export default Hello;
```

### 여러개의 props를 사용할 때, 구조분해 할당을 사용한다.

- props.color , [props.name](http://props.name) 대신 구조분해 할당을 사용하여 { color, name }으로 간결하게 사용한다.

App.js

```jsx
import React from 'react';
import Hello from './Hello';

function App() {
  return (
    <Hello name="react" color="red"/>
  );
}

export default App;
```

Hello.js

```jsx
import React from 'react';

function Hello({color, name}) {
	return <div style={{ color }}> 안녕하세요. {name} </div>
}

export default Hello;

```

### props 값을 지정하지 않았을 때 defaultProps로 기본값을 설정한다.

`<Hello color="pink"/>` 와 같이 name이 없는 컴포넌트에 defaultProps가 설정된다.

```jsx
Hello.defaultProps = {
	name: '이름없음'
}
```

### props.children를 사용하여 컴포넌트 태그 사이 넣은 값을 조회한다.

Wrapper.js

```jsx
import React from 'react';

function Wrapper() {
	const style = {
		border: '2px solid black',
		padding: '16px',
};
return (
		<div style={style}>
		
		</div>
	)
}
```

App.js

```jsx
import React from 'react';
import Hello from './Hello';
import Wrapper from './Wrapper';

function App() {
  return (
    <Wrapper>
      <Hello name="react" color="red"/>
      <Hello color="pink"/>
    </Wrapper>
  );
}

export default App;
```

- Wrapper 안에 Hello 컴포넌트를 넣었지만, 브라우저를 확인하면 컴포넌트는 보여지지 않는다. 이때 `props.children` 을 랜더링 하여 내부의 내용을 보여지게 한다.
    - A 컴포넌트 사이에 B컴포넌트가 있을 때, A 컴포넌트에서 B 컴포넌트 내용을 보여주려고 사용하는 props이다.
