# TypeScript

## What is it?
* TypeScript is JavaScript's runtime with a compile-type type checker
* A Typed Superset of Javascript - It adds rules about how different kinds of values can be used
* Static Type Checking - which means it checks before execution and does based on the kinds of values
* It preserves the *runtime behavior* of Javascript and will never change it 
* Once the compiler is done checking code it erases the types to produce the resulting "compiled code", meaning once your code is compiled the resulting plain JS has no type information


## Defining Types 
* There are already primitive tpyes in JS: boolean, bigint, null, number, string, symbol, and undefined, which you can use in an interface
* TypeScript extends this list with: any (allow anything), unknown (ensure someone using this type declares what the type is), never (it’s not possible that this type could happen), and void (a function which returns undefined or has no return value).

## Types and Interfaces
* Used to declare the shape of an object. They are similar and for most use cases act the same
* Interfaces are typically used for defining contracts that classes or objects must adhere to. They are well-suited for describing the structure of objects
    ```typescript
    interface Person {
        firstName: string;
        lastName: string;
    }
    ```
* Use a `type` when you want to create a union or intersection of different types. Types are versatile and can be used to create complex types by combining existing ones using union (|) and intersection (&) operators.
    ```typescript
    type Point = { x: number; y: number };
    type Shape = Circle | Square | Triangle;
    type Status = "Pending" | "Approved" | "Rejected";
    ```
* It is recommened to use `interface` over `type` aliases because you will get better error messages
* For publicy exposed types it's better to make then an `interface` 
* They both support extending other interfaces and types Type alias do this via intersection types while interfaces have a keyword
    ```typescript 
    type Robin = { nocturnal: false } & BirdInterface;

    interface Peacock extends BirdType {
    colourful: true;
    flies: false;
    }
    ```
* You can use an interface declaration with classes
    ```typescript
    interface User {
        name: string;
        id: number;
    }

    class UserAccount {
    name: string;
    id: number;
    
    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
    }
    
    const user: User = new UserAccount("Murphy", 1);
    ```
* You can use interfaces to annotate parameters and return values to functions
    ```typescript
    function deleteUser(user: User) {
    // ...
    }

    function getAdminUser(): User {
    //...
    }
    ```
* One Major difference is type aliases are closed and interfaces are open meaning you can extend an interface by declaring it a second time

* Edge case [resource](https://stackoverflow.com/questions/37233735/typescript-interfaces-vs-types/52682220#52682220
) 


## Unions 
* Declare a type that could be one of many
* Popular use case is to describe the set of string or number literals that is a value is allowed to have: 
  ```typescript
    type WindowStates = "open" | "closed" | "minimized";
    type LockStates = "locked" | "unlocked";
    type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;
  ```

## Generics 
* Generics provide Variables to types
* Common example is an Array. An array without Generics could contain anything but an array with generics can describe the values that the array contains
  
 ```typescript
    type StringArray = Array<string>;
    type NumberArray = Array<number>;
    type ObjectWithNameArray = Array<{ name: string }>;
 ``` 



## Enums 