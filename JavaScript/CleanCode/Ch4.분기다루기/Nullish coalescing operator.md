## 🚀 Nullish coalescing operator
### 💎 ?? (Nullish coalescing operator): null 이거나 undefined 일 때 만 작동한다.
```
function createElement(type,height,width) { 
    const element = document.createElement(type ?? 'div');

    element.style.height = height ?? 100;
    element.style.width = width ?? 100; 

    retrun element;
}
```
```
null || undefined ?? 'foo'; // 💣 raises a SyntaxError!
(null || undefined) ?? 'foo'; //👍 return 'foo'!
```
