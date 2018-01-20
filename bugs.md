#### DeBugging and fixes
_Documenting bugs and the solutions found_

_Also contains solutions for issues found_

#####Instructions 
* Bug: Anytime an unexpected error is received, document the date, the scenario, the problem and once trouble shooting is completed, add a solution.
* Pattern: Anytime working through a pattern and find a better solution document it


##### 6/11/17
######If need to use Inspector in node use this: `node --inspect --debug-brk node_modules/.bin/jest --runInBand`


###### Bug 1 - Validation issue: 
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
          
    * Fix: I needed to spyOn the function as opposed to mock it. Additionally, in order to trigger the call, the way I got it to work is to call the `forceUpdate()` method. [Docs](https://facebook.github.io/react/docs/react-component.html#forceupdate).
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
* Can also use the JEST debugging they suggest in the [docs](https://facebook.github.io/jest/docs/troubleshooting.html)

###### Bug 7 - Jest Testing not mocking a function that is passed from props
* Issue: While jest testing trying to test a function being passed in from a parent wrapper as prop but it is not being called
* Error: `expect(jest.fn()).toHaveBeenCalled()
    Expected mock function to have been called.`

    * Fix: You need tou use Enzyme's mount instaed of shallow rendering so that it can be aware of functions coming from the parent wrapper
    
````
	const mountWrapper = mount(<AfqPhoneEmail {...props}/>);
	describe('AfqName Actions Test', () => {
		it('Should call the handleState function from wrapper component when child component mounts', () => {
			const handleState = jest.spyOn(mountWrapper.instance().props, 'handleState');
			expect(handleState).toBeDefined();
			expect(handleState).toHaveBeenCalled();

		});
	});
````




##### 7/17/17
######Bug 8 - TypeError and exception error
* Issue: Trying to pass down an array of objects from parent component to a child and when in the child  I get the data fine but 
then when trying to map or do a forEach over it, three Jest tests fail 
* Error:  `AFQ Name Component Test › encountered a declaration exception; TypeError: Cannot read property 'map' of undefined`
                 
    * Fix: It has something to do with the fact we are using mount (from Enzyme) in the tests. When I comment out that code the errors go away. I took it out of the parent component and the tests worked. 
    

##### 7/18/17
######Bug 9 - Troublshooting an API
* Issue: Trying to send a payload to an API
    * Fix: Check the network tab and retreive the payload and the url and put both in Postman and troubleshoot until you find the error
    
    
    
##### 7/24/17
######Bug 10 - Testing a stateless component and getting a TypeError
* Issue: When testing a stateless component that contains a .map method the test is failing because it cannot find a method. Might be because it doesn't have a component to reference
* Error: 
```
SelectedOptions Test › encountered a declaration exception
TypeError: options.map is not a function
````
   * Fix: To get this error to disappear you need to mock the wrapper container  and surround the stateless component when instantiating it
   ````
   const data = [
   		{formId: 'Test', options: [{name: 'NAME', show: true}]},
   		{formId: 'New Test', options: [{name: 'NAME 2', show: true}]}]
   
   	const wrapper = mount(<ConfigTable data={data}><SelectedOptions {...props}/></ConfigTable>);
   
````  


###### 7/25/17
###### Bug 11 - Checkboxes not working - <label> issue
* Issue: The checkboxes on the page stopped working when in production. They worked locally but not live
* Error: It turns out to be an HTML input error.  The label tag was not bound to the input tag. 
````
<div>
				<input
					id={id}
					type="checkbox"
					name={name}
					value={value}
					checked={isChecked}
					disabled={disabled}
					onChange={this.toggleCheckboxChange}/>
				<label htmlFor={label} label={label}>
					{showLabel ? label : null}
				</label>
			</div>
````
In the example above you notice that we are passing `{label}` to the `htmlFor` property instead of being bound
So to solve the issue you need to make sure you bind the input with the label tag like so:
````
<label htmlFor={id}>
    {showLabel ? label : ''}
</label>
````




##### 1/8/2018
 ###### Bug 12 - Using Fetch API, Can't get cookie in header
 * Issue: While sending an api request to our backend I wasn't able to get or retrieve the appropriate cookie header. Everytime the back would just keep reseting the cookie
 * Fix: To solve the issue I added the following header to each call where there was a cookie involved: 
 ` credentials: 'same-origin'`
 