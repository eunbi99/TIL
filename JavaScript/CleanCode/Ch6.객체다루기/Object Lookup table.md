## 🚀 Object Lookup table (집합)

```
function getUserType(type) {
    if(type === 'ADMIN') {
        retrun '관리자';
    } else if (type === 'INSTRUCTOR') {
        retrun '강사';
    } else if (type === 'STUDENT') {
        return '수강생';
    }
    ...
}
```
#### 🤯 if-else문을 사용하게 된다면 점점 코드가 늘어질때 힘들어진다. 
#### 이러한 경우 switch case문을 사용하는 것도 좋지만 Object Lookup table (집합)을 사용하여 불필요한 분기문을 줄일 수 있다.
#### Object에 키값이 없으면 바로 기본 값을 반환한다
```
function getUserType(type) {
    const USETR_TYPE = {
        ADMIN: '관리자',
        INSTRUCTOR: '강사',
        STUDENT: '수강생',
        UNDEFINED: '해당없음',
    }
    return USER_TYPE[type] ?? USER_TYPE[UNDEFINED];
}

👍 상수 파일이 있다면 수많은 함수를 한번에 관리 할 수 있도록 해준다!

import USER_TYPE from './constants/...some.js'

function getUserType(type) {
    return USER_TYPE[type] || USER_TYPE[UNDEFINED];
}
```

```
function getUserType(type) {
    return (
        {
            ADMIN: '관리자',
            INSTRUCTOR: '강사',
            STUDENT: '수강생',
        }[type] ?? '해당 없음'
    );
}

(getUserType('ADMIN')); // 관리자
```
