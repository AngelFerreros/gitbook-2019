## ES6 destructuring

### destructuring arrays:

Since react forces us to replace `state` with a __new__ `state` value every time, we can use __destructuring__ ES6 syntax:
```
let banana = 'yellow';
const fruits = ['kiwi', 'apple'];
const newFruits = [banana, ...fruits];
console.log( fruits, newFruits );
```

### destructuring objects
How do we add to the state object `this.state.monkey`?
```
constructor(){
  this.state = {
    monkey: {
      hair: "brown"
    }

  }
}
```
Key same name as variable:
```
let food = 'banana';
this.setState({monkey: {food, ...this.state.monkey}});
```
Named key:
```
let banana = 'ripe banana';
this.setState({monkey: {food: banana, ...this.state.monkey}});
```

Key name variable:
```
const keyName = 'food';
let stuff = 'banana';
this.setState({monkey: {[keyName]: stuff, ...this.state.monkey}});
```

See some more ES6 destructuring techniques [here.](https://medium.freecodecamp.org/handling-state-in-react-four-immutable-approaches-to-consider-d1f5c00249d5)

## pure react functions
You may get this [error.](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/prefer-stateless-function.md
)
If yout component doesn't deal with props or state, use this syntax:
```js
const App = () => (
  <div>
    <Main />
  </div>
);

export default App;
```
This is more efficient because it prevents react from having to check this component for changes to render.

### More Resources:
Do you want asset pipeline-like controls over asset urls? Check out the webpack [`file-loader`](https://github.com/webpack-contrib/file-loader)

Webpack sass: [https://github.com/webpack-contrib/sass-loader](https://github.com/webpack-contrib/sass-loader)

### Simplified starting app template:
A less opinionated express / webpack / react starting app:
[https://github.com/wdi-sg/react-express](https://github.com/wdi-sg/react-express)

### Exercise: ES6 destructuring
Run these code snippets:

Variables from returned array
```
function f() {
  return [1, 2];
}

var a, b;
[a, b] = f();
console.log(a); // 1
console.log(b); // 2
```

Spread operators
```
var [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```

Object spread operators
```
let {a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40}
a; // 10
b; // 20
rest; // { c: 30, d: 40 }
```

Variable assignment from keys
```
var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true
```

Variable key access to objects
```
let key = 'z';
let {[key]: foo} = {z: 'bar'};

console.log(foo); // "bar"
```

See also: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

Also: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)