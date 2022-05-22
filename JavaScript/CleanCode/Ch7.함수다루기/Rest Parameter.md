## 🚀 Rest Parameters

- 함수가 정해지지 않은 수의 매개변수를 배열로 받을 수 있다.

```jsx
function sumTotal() {
	return Array.from(arguments).reduce( {
		(acc,curr) => acc + curr,
	);
}

sumTotal(1,2,3,4,5,6,7,8,9,10);
```

```jsx
function sumTotal(
	initValue,
	bonusValue,
	...args
) {
	console.log(initValue); // 100
	console.log(bonusValue); // 99
	return args.reduce( {
		(acc,curr) => acc + curr,
	);
}

sumTotal(100,99,1,2,3,4,5,6,7,8,9,10);
```

- ... 을 통해 들어온 파라미터는 배열로 사용할 수 있다.
- rest parameter는 추가적인 인자를 받을 수 있다. ex) initValue, bonusValue
- 인자 중에서도 가장 마지막에 넣어줘야한다.
    - initValue, ...args , bonusValue 처럼 중간에 넣으면 안된다!
