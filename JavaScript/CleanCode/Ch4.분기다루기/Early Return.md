## 🚀 Early Return

```
function loginService(isLogin,user) {
    if(!isLogin) {
        if(checkToken()) {
            if(!user.nickName) {
                return registerUser(user);
            } else {
                refreshToken();

                retrun '로그인 성공';
            }
        } else {
            throw new Error('No Token');
        }
    }
}
```
-  로그인 여부
-  토큰 존재 여부
- 기가입 유저 확인 
    -  가입
    -  로그인
```
function loginServeice(isLogin,user){
    // 로그인이 되어있는 경우는 Early Return을 사용하여 함수를 미리 종료시켜 사고하기 편하게 만든다!

    if(isLogin) {
        return 
    }
    
    // 토크이 없는 경우 에러 발생 시킴.
    if(!checkToken()){
        throw new Error('No Token');
    }

    // 닉네임이 없을 경우에는 registerUser 함수 실헹시킴.
    if(!user.nickName) {
        return registerUser(user);
    }

    refreshToken();

    return '로그인 성공';
}
```

#### 👉 변경 전 : 하나의 조건 condtion === 'GOOD'에 너무 많은 의존성들이 있는 문제를 가지고있다.
```
function 오늘하루(condition,weather, isJob) {
    if(condition === 'GOOD') {
        공부();
        게임();
        유튜브보기();

        if(weather === 'GOOD') {
            운동();
            빨래();
        }

        if(isJob === 'GOOD') {
            야간업무();
            조기취침();
        }
    }
}
```
#### 👉  변경 후 : Early Return을 통해 코드를 분리해주면 코드의 흐름이 더 간단해진다.
```
function 오늘하루(condition,weather, isJob) {
    if(condition !== 'GOOD') {
        return
    }

    공부();
    게임();
    유튜브보기();

    if(weather !== 'GOOD') {
        return
    }

    빨래();

    if(isJob !== 'GOOD') {
        return 
    }

    야간업무();
    조기취침();
    운동();
    
}
```
