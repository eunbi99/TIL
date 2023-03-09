# useRef

자바스크립트를 사용 할 때 특정 DOM을 선택해야하는 상황에서는 `getElementById` , `querySelector` 같은 DOM Selector 함수를 사용해서 DOM을 선택한다.

- 리액트에서는 `ref`라는 것을 사용하는데, 함수형 컴포넌트에서는 ref를 사용할 때 `useRef` 라는 Hook 함수를 사용한다.
- 클래스형 컴포넌트에서는 콜백 함수나 React.createRef 라는 함수를 사용한다.

```jsx
import React, { useState, useRef } from 'react';

function InputSample() {
	const [ inputs, setInputs ] = useState({
		name:'',
		nickname:''
	});

	const nameInput = useRef();
	
	const { name, nickname } = inputs;

	const onChange = e => {
		const { value, name } = e.target;
		setInputs({
			...inputs,
			[name]: value // 변경이 생긴 input태그의 name값이 키가 된다! 
		});
	};

	const onReset= () => {
	setInputs({
		name:'',
		nickname:''
	});
	nameInput.current.focus();
};

return (
	<div> 
		<input
			name="name",
			placeholder="이름"
			onChange={onChange}
			value={name}
			ref={nameInput}
		/>
		<input
			name="nickname",
			placeholder="이름"
			onChange={onChange}
			value={nickname}
		/>
		<button onClick={onReset}> 초기화 </button>
		<div>
			<b> 값 : </b>
			{name} {nickname}
		</div>
	</div>
	);
}
```

- useRef()를 사용하여 Ref 객체를 만들고 선택하고 싶은 DOM에 ref 값으로 설정해준다. 여기서는 이름 input에 설정했다.
- Ref 객체의 .current 값은 원하는 DOM을 가르키게 된다.
- 초기화 버튼을 누르면 onReset 함수에서 focus()를 호출하면 이름 input에 포커스가 잡힌다.

### 📌 useRef의 다른 용도

컴포넌트 안에서 `조회 및 수정 할 수 있는 변수를 관리`한다.

- useRef로 관리하는 변수는 값이 바뀌어도 `리렌더링 되지않는다`.
    - 리액트 컴포넌트에서는 상태를 바꾸는 함수 호출 후 렌더링 이후 업데이트 된 상태를 조회 가능
    - useRef는 설정 후 바로 사용 가능하다.
