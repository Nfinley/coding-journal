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
 
 * Fix: When you are are a .thenable block a promise returns two parameters, 1. A response and 2. an error. See below for the code fix: 
 ````
 this.props.applicationAction.updateApplication(this.getPayload())
                 .then(() => {
                         this.props.history.push('/create-application/app-dates');
                     }, (err) => this.setState({submissionError: err.message}) )
                 .catch((err) => { console.error(err) });
````
 * See the second paramater `err` which fixed the problem which was inpart due to the fact that the error was not bubbling up into the last catch block but instead only in the first then
 
 ###### Bug 4 - Component Update issue with setState: 
 Trying to figure out how to update React component state before rest of actions of the onSubmit are called. 
 [Article about setState and lifecycle events](http://reactkungfu.com/2016/03/dive-into-react-codebase-handling-state-changes/)
 * Error: state changes are not reflected in state when onSubmit is called because the component hasn't finished its lifecycle to update state. 
 * Fix: In order to pass to state to another function there are a few options. 
 
    * 
 
 
 
 ##### 6/20/17
 
 ###### Bug 5 - Reducer not setting state in Redux
 * Issue: Was trying to add a new property to redux, it was dispatching the action,  but it was not saving to redux state
    *  Fix: Forgot to add the reducer I created to the index.js reducer files to bind it to state. Once I added it, the parameter showed up in Redux state
 
 
 ###### Bug 6 - Jest testing not calling the mock onClick function 
 * Issue: While jest testing I was trying to mock an onClick function but for some reason it would not call the mock function.  
 * Error: `expect(jest.fn()).toHaveBeenCalled()
          Expected mock function to have been called.`
          
    * Fix: I needed to spyOn the function as opposed to mock. Additionally, in order to trigger the call, the way I got it to work is to call the `forceUpdate()` method. [Docs](https://facebook.github.io/react/docs/react-component.html#forceupdate).
     The forceUpdate() calls the component to re-render allowing it to call the spy. Usually one should try to avoid using this. See the code below for the fix:          
 
````
	describe('Choose Profile Actions Test', () => {
		it('Should call onClick event on Guest Card', () =>{
			const handleClickMock = jest.spyOn(wrapper.instance(), 'handleClick');
			wrapper.instance().forceUpdate();
			wrapper.find('#guest').simulate('click', {currentTarget: {getAttribute:()=> "value"}});
			expect(handleClickMock).toHaveBeenCalled();
		});
		it('Should call router push method', () => {
			wrapper.setProps({identityTypeAction: {createIdentityTypeSuccess: () => Promise.resolve( { type: 'ENTITY' }) }});
			const spyPropHistoryPush = jest.spyOn(wrapper.instance().props.history, 'push');
			wrapper.find('#guest').simulate('click', {currentTarget: {getAttribute:()=> "value"}});
			setTimeout(() => {
				expect(spyPropHistoryPush).toHaveBeenCalledWith('/create-application/create');
			}, 100);
		});
	});
````