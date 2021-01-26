# Questions Asked While Interviewing

## Sinclair Broadcast Group (10/8/2018)

1. What is the `this` context of an annonymous function?

2. What is a Closure?
    * Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope 
    * Example:
   
````
    function foo(){
        var a = 2;
        function bar(){
            console.log(a);
        }
        return bar;
    }
    var baz = foo();

    baz(); // 2

````

3. Difference betwen `let` vs. `const`

4. How do you change the the context of `this`?
   A: You can change the this context through .call(), .apply() and .bind()
   * [Helpful link](https://toddmotto.com/understanding-the-this-keyword-in-javascript/)



## LivePerson (Joey Jiron) 10/12


## Disney 10/15
