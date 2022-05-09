## 🚀Computed Property Name 
### computed property name( [] )은 표현식(expression)을 이용해 객체의 key 값을 정의하는 문법이다.

```
const [state, setState] = useState({
    id: '',
    password: '',
});

const handleChange = (e) => {
    setState({
        [e.target.name]: e.target.value,
    });
};

return (
    <React.Fragment>
        <input value={state.id} onChange={handleChange} name="name" />
        <input value={state.password} onChange={handleChange} name="password" />
    </React.Fragment>
);
```
#### 📍 []를 사용함으로서, e.target.name에는 input의 name이, e.target.value에는 input의 value가 동적으로 들어오게 된다!

```
const noop = createAction('INCREMENT');

const reducer = handleActions(
    {
        [noop]: (state, action) => ({
            counter: state.counter + action.payload,
        }),
    },
    { counter: 0 },
);
```

```
const key = 'name';
const value = 'Eunbi';

const user = {
    [`${key}12`] : value
}

console.log(user.name12); // Eunbi
```
