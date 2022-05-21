## 💻 Default Value / Default Parameter

```jsx
function createCarousel(options) {
	options = options || {}; {} // 방어코드
	var margin = options.margin || 0;
	var center = options.center || false;
	var navElement = options.navElement || 'div';

	return {
		margin,
		center,
		navElement,
	};
}

createCarousel() ; // { margin: 0, center: false, navElement: 'div' }
```
### 인자가 없는 경우 default value가 필요하다!
- createCarousel(); 에 인자가 없는 경우 options는 undefiend가 된다
- undefined.margin .. 등 접근할 경우 에러가 발생한다.
- options = options || {}; 를 통해 options가 undefined일 경우 객체를 생성후 default value 를 담아준다.

### 👍 위의 코드를 리팩토링 해보자!

```jsx
function createCarousel({
	margin = 0, // undefiend 일 경우 기본값 세팅!
	center = false,
	navElement = 'div',
} = {}) } // 객체 구조분해를 통해 객체에 담아준다! 
	return {
		margin,
		center,
		navElement,
	};
}

createCarousel(); // { margin: 0, center: false, navElement: 'div' }
```

### 👍인자를 넘기지않는 경우 Defalt Parameter를 통해 에러를 발생시켜보자!

```jsx
const required = (argName) => {
	throw new Error('required is' + argName); 
};

function createCarousel({
	items = required('items'),
	margin = 0, // undefiend 일 경우 기본값 세팅!
	center = false,
	navElement = 'div',
} = {}) } // 객체 구조분해를 통해 객체에 담아준다! 

	// ..some code
 
	return {
		margin,
		center,
		navElement,
	};
}

```
