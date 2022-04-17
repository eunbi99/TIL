## 🚀 else-if 피하기
- else if를 사용하여 코드를 늘리기 보다는, else로 한번 끊어주고 다시 if를 사용하는 것이 낫다.
- 만약, else if처럼 코드를 늘려야한다면 switch case문을 사용하는 것이 좋다.

```
const x = 1;

if(x >= 0) {
    console.log('x는 0과 같거나 크다.');
} else if(x > 0 ){
    console.log('x는 0보다 크다.');
}
```

```
if (x >= 0){
    console.log('x는 0과 같거나 크다');
} else {
    if (x > 0) {
        console.log('x는 0보다 크다');
    }
}
```

## 🚀 else 피하기
```
function getActiveUserName(user) {
    if(user.name) {
        retrun user.name;
    } else {
        return '이름없음';
    }

    return user.name || '이름없음';
}
```

```
funtion fetAcitveUserName(user) {
    if(user.name) {
        return user.name;
    }

    return '이름없음';
}
```

💣 하나의 함수가 두가지 역할을 할 경우 else에서 문제가 생길 수 있다.
```
/* age가 20 미만시 특수 함수 실행 */
👉 변경 전 : 20세 미만일 경우에는 report라는 함수를 실행하지만 else 때문에 '안녕하세요' 문구는 반환하지 못한다.

function getHelloCustomer(user) {
    if(user.age <20) {
        report(user);
    } else {
        return '안녕하세요.';
    }
}
```
👉 변경 후 : 20세 미만일 경우에만 report라는 함수 실행 후 안녕하세요 라는 문구도 반환한다.
```
function getHelloCustomer(user) {
    if(user.age <20) {
        report(user);
    } 
      return '안녕하세요.';
}
```
