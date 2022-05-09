## 🚀 Shorthand Properties & Concise Method
### 📍 shorthand properties (단축 속성)이란?
객체를 정의 할 때 객체의 key 값과 value 값이 같으면, 각각을 표기하지 않고 한번만 표기하는 것을 의미한다.

### 📍 Concise Method (간결한 메소드)
할당 자체를 콜론과 함수 키워드를 생략함으로서 간결한 문법을 제공한다. 


```
const counterApp = combineReducers({
    counter: counter,
    extra: extra,
});
```
📍 Shorthand Propertie를 사용해보자!

```
const counterApp = combineReducers({
    counter,
    extra,
    counter
});
```

```
const firstName = 'poco';
const lastName = 'jang';

const person = {
    firstName: 'poco',
    lastName: 'jang',
    getFullName: function () {
        return this.firstName + ' ' + this.lastName;
    },
};
```

```
const firstName = 'poco';
const lastName = 'jang';

const person = {
    firstName,
    lastName
    getFullName() {
        return this.firstName + ' ' + this.lastName;
    },
};
```
