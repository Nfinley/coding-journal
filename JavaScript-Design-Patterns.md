# Javascript Design Patterns by Addy Osmani - Book Notes


## What is a Pattern? 
### A pattern is a reusable solution that can be applied to commonly occuring problems in software design, also viewed as templates for how we solve problems
* Patterns are proven solutions
* Patterns can be easily reused
* Patterns can be expressive

## Advantages:
* Certain patterns can decrease overall footprint of code base
* Add to devs vocabulary
* Abstractions using design patterns can offer real-world value

## Christopher Alexander - "Pattern Lanugage"
* He states a pattern should be both a process and a "thing".
* It is the process that creates the "thing"
* Patterns generally focus on addressing a visually identifiable structure

## Proto Patterns
* Patterns that have not yet been fully vetted and accepted by the community as full fledged patterns

## A pattern is considered good if: 
* Solves a particular problem: Can't just capture principles they need to capture solutions
* The solution cannot be obvious
* Must be prove
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

## Patterns

### Constructor Pattern
* Object constructors are used to create specific types of objects - preparing for use and accepting arguments which it can use to set values and methods when object is first created
* There are three common ways to create new objects: 
````
  //Eachofthefollowingoptionswillcreateanewemptyobject: 
    varnewObject={};

   //or
     varnewObject=Object.create(Object.prototype); 
   //or
     varnewObject=newObject();
```