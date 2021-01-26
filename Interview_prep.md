# Interview Prep - JS


Helpful Prep Articles: 
- [Master JS Interview Closure](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36)
- [10 Interview questions you should know](https://medium.com/javascript-scene/10-interview-questions-every-javascript-developer-should-know-6fa6bdf5ad95)


## Things to Know in JS

- Closure [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)

```
function makeAdder2(x) {
  console.log('x', x)
  return function(y) {
    console.log('y', y)
    return x + y;
  };
}

var add5 = makeAdder2(5);
var add10 = makeAdder2(10);

add10(10) // 20
add5(2) // 7

```
- `this` keyword 


- [Linked Lists](https://www.freecodecamp.org/news/implementing-a-linked-list-in-javascript/)

- What is the difference between controlled and uncontrolled inputs in react? 
- [Event loop in js](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)