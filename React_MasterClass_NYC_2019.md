# React Master Class NYC 2019 
  - By Dustin Myers
* Al the new and shiny code 

* Context 
* Hooks
* Suspense

## Context
* A solution for prop drilling


## Hooks
* Motivation: 
    * Reusing stateful logic between components is hard
    * Complex components can be hard to understand
    * Classes confuse machines and people
* They can only called in a functional component, you can't call them conditionally inside an if for example
* Use Effect reference: https://reactjs.org/docs/hooks-effect.html
* React Florence: The question is not "when does this effect run" the question is "with which state does this effect synchronize with"     
    * useEffect() // all state sync
    * useEffect(fn, []) //no state sync (ie mount and unmount)
    * useEffect(fn, [these, states])
    
* Basic Hooks: 
    * useState
    * useEffect
    * useContext
    

For DEMO
1. What are hooks?
2. Show useState
3. Show useEffect
4. Then show how to refactor to create custom hooks (you have to name then as "use...")


* to Show Use Effect: In componentDidMount use the document.title piece to show, use Dan Abramov's react video 
* Can use useEffect for subscriptions like to listen to changes in the brower window size
* To clean up return the function at the end of the useEffect hook

* Group state and effects by function


