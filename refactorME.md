# Refactor ME - Notes on refactoring

## Refactoring a React Application (5/7/2018)
* Issue: We have a react application that is big and has way too many functions, not utilizing redux, routing is not standard and it is really hard to make updates

### Things to refactor: 
1. Routing
2. Redux Design (using modular re-Duck pattern)
3. Folder Architecture
4. Adding type checking
5. Adding Tests - Make sure tests are next to the files they are testing
6. Updating the JSON Config
7. Codify CSS structure / image conventions
8. Layout Design => Component Design => USE Semantic HTML Tags when composing UI Components
9. Codify Constants and standardize use
10. Add static text to an i18m file to ensure all changes can happen in one place
11. Create a 404 Page
12. Code-Split (react-loadable)
13. Ensure the linter is working properly 

### Process I took 
* Installed a few tools to help debug and increase performance of the app in the long run. Why-did-you-update, state updates notifications and Redux-logger to keep track of the redux actions getting called to make sure only calling when necessary
* Started by looking at the App.js and Signin.js which is entry point and login flow
* Strategy first was to remove any api calls, abstract it to redux. Get it to work here and refactor further. Used the module redux pattern here. 
    * second refactor would be to use the container component and presentational component pattern to abstract it and make it even cleaner
* Then Break stuff
* Started with the App.jsx file to pair it down and make it more re-usable
* Dont' get paralyzed by how many tools are out there (For me it was flow, typescript, Rxjs, etc). Start refactoring. You can always improve on it. The goal should always be to make it better than it was (even when you are writing new code)
* I also think it is okay if when refactoring you can't refactor exactly to what the acceptable standards are right away. Just as long as you improve and strive to hit those standards. Refactoring is a multi-tiered process.



## When Starting a New job - How to go about becoming familiar with the Application
* In this case I inherited a React application that was large and confusing (and not written using current standards)
* Start small and work your way in. 
* Identify what libraries are being leveraged, in my case we were using React, Router and Redux
* Find the entry point into the application from the index.html, find where the Redux Store is getting rendered
