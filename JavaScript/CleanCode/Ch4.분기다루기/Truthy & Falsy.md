## 🚀 Truthy 와 Falsy 사용하기
### 💎 Truthy
- if (true)
- if ({})
- if ([])
- if (42)
- if ("0")
- if ("false")
- if (new Date())
- if (-42)
- if (12n)
- if (3.14)
- if (-3.14)
- if (Infinity)
- if (-Infinity)

### 💎 Falsy
- if (false)
- if (null)
- if (undefined)
- if (0)
- if (-0)
- if (0n)
- if (NaN)
- if ("")

<hr>

```
function printName(name) {
    if(name === undefined || name === null) {
        return '사람이 없네요';
    }
    return '안녕하세요' + name + '님';
}

console.log(printName()); // 사람이 없네요
```

> 💣  만약 name === undefined 이나 name === null 이 빠지거나 var를 사용할 경우 문제가 될 수 있다.
이럴 경우 truthy & falsy를 사용하여 변경하면 간단하게 사용할 수 있다.

````
function printName(name) {
    if(!name) {
        return '사람이 없네요';
    }
    return '안녕하세요' + name + '님';
}
````


## 🚀 단축평가(short-circuit evaluation)
### AND 
```
true && true && '도달 o' // 도달 o
 
true && false && '도달 x' // false
```

### OR
```
false || false || '도달 o' // '도달 o'
true || true || '도달 x' // true
```

```
function fetchData() {
   // if (state.data) {
   //     return state.data;
   // } else {
   //     return 'Fetching...';
   // }

   👉 return state.data || 'Fetching...'; 
}
```

> OR연산자를 사용하여 state.data가 있을 경우(true) state.data 반환, 없을 경우(false) 'Fetching...' 반환!


```
function favorite(someDog) {
    let favoriteDog;

    if(someDog) {
        favoriteDog = dog;
    } else {
        favoriteDog = '냐옹';
    }

    return favoriteDog + '입니다';
}

favoriteDog() // 냐옹
favoriteDog('포메') // 강아지 입니다. 
```
👉 truthy & falsy를 통해 간단하게 변경해보자.
```
function favorite(someDog) {
    return (someDog || '냐옹') + '입니다';
}
```
> someDog가 false인 경우 뒤의 '냐옹'까지 가서 '냐옹'을 반환!
undefined는 falsy로 무조건 false를 반환하고, 문자열은 truthy로 true를 반환하므로 someDog가 없을경우 냐옹을 반환한다!
```
const getAtiveUserName(user,isLogin) {
    if(isLogin) {
        if(user){
            if(user.name) {
                return user.name
            } else {
                return '이름없음'
            }
        }    
    }
}
```
👉 truthy & falsy를 통해 간단하게 변경해보자.
```
const getAtiveUserName(user,isLogin) {
    if(isLogin && user) {
       return user.name || '이름없음';
    }
}
``` 
