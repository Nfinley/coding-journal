# Javascript Design Patterns by Addy Osmani - Book Notes


## What is a Pattern? 
### A pattern is a reusable solution that can be applied to commonly occurring problems in software design, also viewed as templates for how we solve problems
* Patterns are proven solutions
* Patterns can be easily reused
* Patterns can be expressive

## Advantages:
* Certain patterns can decrease overall footprint of code base
* Add to devs vocabulary
* Abstractions using design patterns can offer real-world value

## Christopher Alexander - "Pattern Language"
* He states a pattern should be both a process and a "thing".
* It is the process that creates the "thing"
* Patterns generally focus on addressing a visually identifiable structure

## Proto Patterns
* Patterns that have not yet been fully vetted and accepted by the community as full fledged patterns

## A pattern is considered good if: 
* Solves a particular problem: Can't just capture principles they need to capture solutions
* The solution cannot be obvious
* Must be proven
* It must describe a relationsip

## Rule of Three - Pattern to be valid
* Fitness of purpose - how is the pattern considered successful?
* Usefulness - why is the pattern considered successful?
* Applicability - is design worthy of begina a pattern because it has wider applicibility?

## Writing and Recognizing Patterns
* Solutions which neither interactions nor defined rules appear are not patterns
* In creating a new pattern tips are: 
    * How practical is the pattern?
    * Keep best practices in mind
    * Design patterns should be transparent to the user
    * Originality is __not__ key in pattern design
    * Patterns need a strong set of examples

## Anti-Patterns
* Is a bad design that is worth documenting
* Examples in JS:  
    * Polluting global namespace
    * Passing strings rather than functions to setTimeout or setInterval as triggers use of eval()
    * Modifying the `Object` class prototype
    * Using it in an inline form as it is inflexible
    * Use of document.write where native DOM alts such as document.createElement are more appropriate (it actually overwrites the DOM)


## Three Types of design patterns: 
    1. Creational (creating objects) - handle of object creation mechanisms, basic approach may lead to added complexity this pattern aims to solve this by __controlling__ the creation process
        * EX: __Constructor, Factory, Abstract, Prototype, Singleton and Builder__. 
    2. Structural (idea of building blocks of objects) - concerned with object composition and identify ways to realize relationships between different objects. They help ensure when one part of system changes the entire strucure doesn't need to. Also assist in recasting parts of the system which don't fit a particular purpose
        * EX: __Decorator, Facade, Flyweight, Adapter and Proxy__.
    3. Behavioral (the idea of ways objects play and work together) - Focus on improving or streamlining communication between contrasting objects in a system
        * EX: __Iterator, Mediator, Observer and Visitor 

# Patterns

## Constructor Pattern
* Object constructors are used to create specific types of objects - preparing for use and accepting arguments which it can use to set values and methods when object is first created
* There are three common ways to create new objects: 
````
  //Eachofthefollowingoptionswillcreateanewemptyobject: 
    varnewObject={};

   //or
     varnewObject=Object.create(Object.prototype); 
   //or
     varnewObject=newObject();
````
* There are four ways in which keys and values can be assigned to an object: 
    * Dot syntax
    * Square bracket syntax
    * [Object.defineProperty](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)
    * Object.defineProperties
* By prefixing `new` to a constructor function it tells JS to behave like a consructor and instantiate a new object with the members defined by that function
* Inside a constructor, the keyword `this` references the new object being created 
````
function Car (model, year, miles) {
    this.model = model;
    this.year = year;    
    this.miles = miles;
    this.toString = function () {
	return this.model + "Oh yeah"
    }
}
var civic = new Car("Honda", 2009, 20000)
console.log(civic.toString())
````
* The above suffers from two things: 1. It makes inheritace difficult and 2. the function toString() are redefined for each new object created using the constructor, instead it should be shared between all instances
* Functions contain a prototype object and when a constructor creates an object all properties of the constructor's prototype are made available to the new object: 
  * The function above can be removed from the constructor directly and placed as a new method on the prototype: `Car.prototype.toString = function() {} `
  * This way a single instance of the function is shared across all car objects
* Helpful blog post about using Objects to order [code](http://rmurphey.com/blog/2009/10/15/using-objects-to-organize-your-code)

## Module Pattern
* They help keep units of code cleanly separated and organized
* There are several options for implementing modules: 
    * Module Pattern
    * Object Literal notation
    * AMD Modules
    * CommonJS modules
    * ECMAScript Harmony Modules
* Object Literals: 
    * described as a set of comma-seperated name/value pairs enclosed in curly braces
    * Provide was to encapsulate and organize code
    * They don't require instantiation using the `new` operator
* MODULE PATTERN: 
    * Originally defined as way to provide both public and private encapsulation for classes in conventional software engineering
    * In JS used to *emulate* public/private methods and variables inside single object, shielding from parts of global scope
    * Results in reduction liklihood of name conflicts
    * This pattern encapsulates "privacy", state and organization using closures
    * With this pattern only a public API is returned keeping everything else private
    * The patter is similar to a IIFE
    * "Privacy" isn't explicitly privacy becuase unlike other language JS doesn't have access modifiers (like private, public, protected)
    * Variables can't technically be declared as private or public so we use function scope to simulate the concept
    * Variables or methods declared only available to the module, but those defined with the returning object are available to everyone
    * EX: 
  ````
    var testModule=(function(){
        var counter = 0; 
        
        return {
            incrementCounter: function () { return counter++; }     
    
            resetCounter: function () {
            console.log( "counter value prior to reset: " + counter ); 
            counter = 0;
            }
        }
    })();

    //Usage:
    //Incrementourcounter
    testModule.incrementCounter(); 
    //Checkthecountervalueandreset
    //Checkthecountervalueandreset
    //Outputs:countervaluepriortoreset:1
    testModule.resetCounter();
````
