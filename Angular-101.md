# Angular 101
[Angular101](https://medium.com/formcept/angular-101-a-technical-guide-to-basic-ui-design-with-angular-605fb0090ae3_)

## What is Angular?

* Angular is a frameowrk created by Google and is used in development of SPA's
* It is popular for its modular approach and reusable code, reusability can be enabled by creating Components
  
## AngularJS (one) vs. Angular  
* AngularJS is written in JS and Angular 2+ is written in Typescript

## Fundamentals:

### Components
* Most basic building blocks of a UI
* To create a component run `ng generate component <compName>`
  
### Interpolation
* Used to bing properites of our cloass to HTML Code

### Property Binding

### 2-Way Binding 
* Helpful if you wish to set an also retreive value of any HTML field
* Syntax is `[()]`

### Built-In Directives
* ngIf, ngFor, ngSwitch
* Typically associated to existing elements using attribute selectors
  ````
    <h1>Welcome to {{title}}</h1>
    <div *ngFor = 'let color of colors'>
    <h2 style.color = "{{color}}">{{color}}</h2>
    </div>
````

### Routing
* Used for navigating
*  Just create an application with routing option, you can do that by adding ‘ — routing’ while creating a new application.

## Service
* A class with a specific purpose
* They are used to share data between components and to implement application logic