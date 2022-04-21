## Defalut Case 고려하기
- 사용자에게 원하는 값을 받지 못했을 경우를 대비하여 Default 값을 설정하자!
```
function sum(x,y){
    x = x || 1
    y = y || 1;

    return x+y;
}

sum();
```

```
function createElement(type,height,width) { 
    const element = document.createElement(type || 'div');

    element.style.height = height || 100; // 📌 height 값이 없다면 100
    element.style.width = width || 100; // 📌 width 값이 없다면 100

    retrun element;
}

createElement();
```
📌 사용자가 입력값에 오타를 내는 경우를 대비하여 에러를 명시!

```
function registerDay(userInputDay) {
    switch (userInputDay) {
        case '월요일':
        case '화요일':
        case '수요일':
        case '목요일':
        case '금요일':
        case '토요일':
        case '일요일':
        default:
            throw Error('입력값이 유효하지 않습니다.');
    }
}

e.target.value = '월ㄹ요일'
registerDay(e.target.value);
```
