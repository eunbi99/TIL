## 🚀void & return

```jsx
function handleClick() {
	// return setState(false);
	setState(false);
}

function showAlert(message){
	// return alert(message);
	alert(message);
}
```

- setState와 alert는 void형이다. 만약 return을 사용할 경우 undefined를 리턴하게 된다.
- api 명세를 보고 반환하는 값이 있는지 확인하는 습관을 가져야한다!

```jsx
function isAdult(age) {
	return age >19;
}

function getUserName(name) {
	return '유저' + name;
}

const isFlag = isAdult(10)
```

함수를 작성할때 반환이 있는지 없는지를 명확히 생각해서 작성해야한다!
