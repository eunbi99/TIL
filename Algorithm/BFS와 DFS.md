
# ✍️ BFS 와 DFS 
![](https://iq.opengenus.org/content/images/2020/05/dfs-vs-bfs.gif)
참고 ) https://iq.opengenus.org
- BFS와 DFS는 그래프를 탐색하는 방법이다.
- BFS는 `큐(FIFO)`를 사용
- DFS는 `스택(LIFO)`를 사용한다.
## 📝 BFS (너비 우선 탐색)
- 리스트나 배열을 가지고 큐를 만든다.
- 큐에 무언가가 있다면 계속 루프를 돌린다.
- 큐에서 dequeue를 하고, 배열을 사용하는 경우 shift를 사용해서 배열의 앞을 제거한다.
- 노드에 왼쪽값이 있는지 확인을 해서 큐에 넣어주고 오른쪽을 확인해서 값을 넣어준다.

### 👩‍💻 큐를 사용하여 BFS 구현하기
```
         10
      6     15
     3  8      20
```
```jsx
 BFS(){
        let data = [];
        let queue =[];
        let node = this.root;
        queue.push(node);
        while(queue.length) {
            node = queue.shift(); // 큐의 맨앞 요소를 node에 담는다.
            data.push(node.value);
            if(node.left) {
                queue.push(node.left);
            }
            if(node.right) {
                queue.push(node.right);
            }
        }
         return data;
    }
```
> `shift() 메서드`는 배열에서 첫 번째 요소를 제거하고, 제거된 요소를 반환한다.
### 🧐 순서?
1. 루트를 큐에 담아준다.
    - queue: [10]
    - visited: [] 

2. 큐에 값(=10)이 있다면 visited에 값을 담은 후 큐에서 제거한다. (shift)
    - queue: [6,15]
    - visited: [10] 

3. 왼쪽에 값이 있는지 확인 후 없다면 오른쪽의 값을 확인
    - queue: [3,8,20]
    - visited: [10,6,15] 
--- 

## 📝 DFS( 깊이 우선 탐색 )
DFS는 3가지 방식(전위순회, 중위순회, 후위순회)이 있다. 
### 👩‍💻 DFS 전위순회 구현하기
전위순회는 루트 > 왼쪽 자식 > 오른쪽 자식 순으로 조회한다.
```js
DFSPreOrder() {
        let data = [];
        function traverse(node) {
            data.push(node.value);
            if(node.left) {
                traverse(node.left);
            }
            if(node.right) {
                traverse(node.left);
            }
        }
        traverse(this.root);
        
    }
```
### 👩‍💻 DFS 중위순회 구현하기
중위순회는 왼쪽 자식 > 루트 > 오른쪽 자식 순으로 순회한다.
 ```js
DFSInorder() {
        let data = [];
        function traverse(node) {
            if(node.left) {
                traverse(node.left);
            }
            data.push(node.value);
            if(node.right) {
                traverse(node.right);
            }
        }
        traverse(this.root);
        return data;
    }
```

### 👩‍💻 DFS 후위순회 구현하기
- 후위순회란 왼쪽 자식 > 오른쪽 자식 > 루트 순으로 순회한다.
```js
    DFSPostOrder(){
        let data = [];
        function traverse(node) {
            if(node.left) {
                traverse(node.left)
            } 
            if(node.right) {
                traverse(node.right);
            }
            data.push(node.value);
        }
        traverse(this.root);
        return data;
    }
```




