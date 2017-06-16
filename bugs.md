#### DeBugging and fixes
_Documenting bugs and the solutions found_

#####Instructions 
* Anytime an unexpected error is received, document the date, the scenario, the problem and once trouble shooting is completed, add a solution.



##### 6/11/17

###### Bug 1: 
Writing Jest tests for a validation form js file. Trying to test a boolean value is changed when a certain classname exists on a form element
* Error received: `TypeError: Cannot assign to read only property 'addressEmpty' of object '#<Object>'`
* Fix: Currently didn't pursue a fix because the loop contained in the validation form wasn't accesbile to the test and it would take a while to mock it and would have to make the variables and loop publically accesible 



##### 6/13/17
###### Bug 2 - Jest Testing Issue:
Using validation logic to validate certain form elements. While trying to abstract the logic from the component field was trying to create a thenable promise chain but since the validate form is an asynchornous action it didn't return a promise so couldn't continue in the promise chain
* Error received: Something to the extent of `TypeError: Cannot read property 'then' of undefined`
 
 * Fix: Needed to return a promise. So, used the `new Promise` constructor from Javascript to ensure what I was calling was returning a promise. See code below: 
 ````
 export function validate(state, stringOfState, formTargeted){
     return (dispatch, getState) => {
         return new Promise((resolve, reject) => {
             if (validateForm(state, stringOfState, formTargeted)){
                 resolve(state, dispatch);
             } else {
                 reject(state);
             }
         });
     }
 
 }
````
 
 ######Bug 3 - SetState Issue: 
 React Error when trying to update state to a component which is no longer mounted. 
 * Error: `Warning: setState(...): Can only update a mounted or mounting component. This usually means you called setState() on an unmounted component. This is a no-op. Please check the code for the blahblah component.`
 
 * Fix: 
 
 
 ###### Bug 4 - Component Update issue with setState: 
 Trying to figure out how to update React component state before rest of actions of the onSubmit are called. 
 [Article about setState and lifecycle events](http://reactkungfu.com/2016/03/dive-into-react-codebase-handling-state-changes/)
 * Error: state changes are not reflected in state when onSubmit is called because the component hasn't finished its lifecycle to update state. 
 * Fix: 
 
 forceUpdate()