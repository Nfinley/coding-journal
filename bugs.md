#### DeBugging and fixes

_Documenting bugs and the solutions found_

_Also contains solutions for issues found_

#####Instructions

- Bug: Anytime an unexpected error is received, document the date, the scenario, the problem and once trouble shooting is completed, add a solution.
- Pattern: Anytime working through a pattern and find a better solution document it

##### 6/11/17

######If need to use Inspector in node use this: `node --inspect --debug-brk node_modules/.bin/jest --runInBand`

###### Bug 1 - Validation issue:

Writing Jest tests for a validation form js file. Trying to test a boolean value is changed when a certain classname exists on a form element

- Error received: `TypeError: Cannot assign to read only property 'addressEmpty' of object '#<Object>'`
- Fix: Currently didn't pursue a fix because the loop contained in the validation form wasn't accesbile to the test and it would take a while to mock it and would have to make the variables and loop publically accesible

##### 6/13/17

###### Bug 2 - Jest Testing Issue:

Using validation logic to validate certain form elements. While trying to abstract the logic from the component field was trying to create a thenable promise chain but since the validate form is an asynchornous action it didn't return a promise so couldn't continue in the promise chain

- Error received: Something to the extent of `TypeError: Cannot read property 'then' of undefined`

- Fix: Needed to return a promise. So, used the `new Promise` constructor from Javascript to ensure what I was calling was returning a promise. See code below:

```
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
```

######Bug 3 - SetState Issue:
React Error when trying to update state to a component which is no longer mounted.

- Error: `Warning: setState(...): Can only update a mounted or mounting component. This usually means you called setState() on an unmounted component. This is a no-op. Please check the code for the blahblah component.`

- Fix: When you are are a .thenable block a promise returns two parameters, 1. A response and 2. an error. See below for the code fix:

```
this.props.applicationAction.updateApplication(this.getPayload())
                .then(() => {
                        this.props.history.push('/create-application/app-dates');
                    }, (err) => this.setState({submissionError: err.message}) )
                .catch((err) => { console.error(err) });
```

- See the second paramater `err` which fixed the problem which was inpart due to the fact that the error was not bubbling up into the last catch block but instead only in the first then

###### Bug 4 - Component Update issue with setState:

Trying to figure out how to update React component state before rest of actions of the onSubmit are called.
[Article about setState and lifecycle events](http://reactkungfu.com/2016/03/dive-into-react-codebase-handling-state-changes/)

- Error: state changes are not reflected in state when onSubmit is called because the component hasn't finished its lifecycle to update state.
- Fix: In order to pass to state to another function there are a few options.

  -

##### 6/20/17

###### Bug 5 - Reducer not setting state in Redux

- Issue: Was trying to add a new property to redux, it was dispatching the action, but it was not saving to redux state
  - Fix: Forgot to add the reducer I created to the index.js reducer files to bind it to state. Once I added it, the parameter showed up in Redux state

###### Bug 6 - Jest testing not calling the mock onClick function

- Issue: While jest testing I was trying to mock an onClick function but for some reason it would not call the mock function.
- Error: `expect(jest.fn()).toHaveBeenCalled() Expected mock function to have been called.`
  - Fix: I needed to spyOn the function as opposed to mock it. Additionally, in order to trigger the call, the way I got it to work is to call the `forceUpdate()` method. [Docs](https://facebook.github.io/react/docs/react-component.html#forceupdate).
    The forceUpdate() calls the component to re-render allowing it to call the spy. Usually one should try to avoid using this. See the code below for the fix:

```
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
```

- Can also use the JEST debugging they suggest in the [docs](https://facebook.github.io/jest/docs/troubleshooting.html)

###### Bug 7 - Jest Testing not mocking a function that is passed from props

- Issue: While jest testing trying to test a function being passed in from a parent wrapper as prop but it is not being called
- Error: `expect(jest.fn()).toHaveBeenCalled() Expected mock function to have been called.`

  - Fix: You need tou use Enzyme's mount instaed of shallow rendering so that it can be aware of functions coming from the parent wrapper

```
	const mountWrapper = mount(<AfqPhoneEmail {...props}/>);
	describe('AfqName Actions Test', () => {
		it('Should call the handleState function from wrapper component when child component mounts', () => {
			const handleState = jest.spyOn(mountWrapper.instance().props, 'handleState');
			expect(handleState).toBeDefined();
			expect(handleState).toHaveBeenCalled();

		});
	});
```

##### 7/17/17

######Bug 8 - TypeError and exception error

- Issue: Trying to pass down an array of objects from parent component to a child and when in the child I get the data fine but
  then when trying to map or do a forEach over it, three Jest tests fail
- Error: `AFQ Name Component Test › encountered a declaration exception; TypeError: Cannot read property 'map' of undefined`
  - Fix: It has something to do with the fact we are using mount (from Enzyme) in the tests. When I comment out that code the errors go away. I took it out of the parent component and the tests worked.

##### 7/18/17

######Bug 9 - Troublshooting an API

- Issue: Trying to send a payload to an API
  - Fix: Check the network tab and retreive the payload and the url and put both in Postman and troubleshoot until you find the error

##### 7/24/17

######Bug 10 - Testing a stateless component and getting a TypeError

- Issue: When testing a stateless component that contains a .map method the test is failing because it cannot find a method. Might be because it doesn't have a component to reference
- Error:

```
SelectedOptions Test › encountered a declaration exception
TypeError: options.map is not a function
```

- Fix: To get this error to disappear you need to mock the wrapper container and surround the stateless component when instantiating it

```
const data = [
		{formId: 'Test', options: [{name: 'NAME', show: true}]},
		{formId: 'New Test', options: [{name: 'NAME 2', show: true}]}]

	const wrapper = mount(<ConfigTable data={data}><SelectedOptions {...props}/></ConfigTable>);
```

###### 7/25/17

###### Bug 11 - Checkboxes not working - <label> issue

- Issue: The checkboxes on the page stopped working when in production. They worked locally but not live
- Error: It turns out to be an HTML input error. The label tag was not bound to the input tag.

```
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
```

In the example above you notice that we are passing `{label}` to the `htmlFor` property instead of being bound
So to solve the issue you need to make sure you bind the input with the label tag like so:

```
<label htmlFor={id}>
    {showLabel ? label : ''}
</label>
```

##### 1/8/2018

###### Bug 12 - Using Fetch API, Can't get cookie in header

- Issue: While sending an api request to our backend I wasn't able to get or retrieve the appropriate cookie header. Everytime the back would just keep reseting the cookie
- Fix: To solve the issue I added the following header to each call where there was a cookie involved:
  `credentials: 'same-origin'`

##### 1/26/2018

###### Bug 13 - Using Jest - When testing a function that is not dispatching anything

- Instead of using `store.dispatch` all you need to do is export the function in the other file and then test it directly like: functionName();

##### 2/8/2018

###### Bug 14 - Using Jest - When testing an onChange function

- Issue: when callind the function in jest like handleInputChageSpy(); getting the following error:
  `TypeError: Cannot read property 'target' of undefined`
- Fix: Just passed a mocked event object to the function

```
    const event = {
        target: {
            value: 1,
            name: 'Test Name'
        }
    }
    handleChangeSpy(event);
```

#### 2/2/2018

##### Bug 13 - Getting a weird loading error on Showcase app after clicking Login button:

`Refused to load the font 'data:font/woff;base64,d09GRgABAAAAAKD5ABIAAAABjrQAAAAAAACfoAAAAVkAAAKCAAAAAAAAAABHUE9TAACLrAAAE6UAAGmo3w+nD0dTVUIAAJ9UAAAASgAAAFjau94BTFRTSAAAi3wAAAAvAAABSW5js1FPUy8yAAAB7AAAAFoAAABgq5xp3FZETVgAAIXAAAADdwAABeBvDHaKY21hcAAAAkgAAAE7AAADVCy12qZjdnQgAACJSAAAADgAAAA4BiEDumZwZ20AAImAAAABAgAAAXMGWZw3Z2FzcAAAiTgAAAAQAAAAEAAaAAlnbHlmAAANvAAAeAEAAQTc9heJHWhlYWQAAAG0AAAANgAAADb6hXFDaGhlYQAAA4QAAAAhAAAAJAdUBBdobXR4AAADqAAAArsAAAUUhLg2g2xvY2EAAAswAAACjAAAAowhImIQbWF4cAAAAZQAAAAgAAAAIANdBGZuYW1lAAAGZAAAAXwAAAM9wTILRnBvc...A5FjDNAcRSYJqJgY2Bh9ERSPswOgFJf6AoI4MnAIqpB3EAAHjafZLda8IwFMXf+1dc8rTBTKqDMaStjIEvwzHQsefY3GowH12Stvrfr/FrimyQh0DOPef8LskmW62gReelNTkZ0pQAmtIKaVY5+VxMB89kUiSZxsAFD/xaWmSNkd8NSgFS5KS0mupdZU3wVHO38VJb462htbNbqfnA2JYPvK0CdbhqFHe0qzYyjGj11owIK7IWjbAODNeYk9luGq0INE7lZB1CPWas67pzRp/H4pRAXzpZh75XkQXcBlA81kdDisVaeugPhy9cxjGonNVw9KYwbZQCaSrrNI8GwJe2CRDiWJSPkz+C9zd2icluMFmSsdinyNhVRyVLNB7/BWsldkfdRPXbHT49phG2tPXOydU63KC+nl7grryHWd8M5sdqDzBKhymFlx52L/Hg0KNrUdBzxUtnxwVGtpuQjwMjvPeMMO8ZD8s9D4CtrqN//S9M2ek/FckP9vfjlA==' because it violates the following Content Security Policy directive: "default-src 'self'". Note that 'font-src' was not explicitly set, so 'default-src' is used as a fallback.`

- It seems like it is putting the state in the url ```

##### 2/24/2018

###### Bug 15 - Using Jest - testing an .catch block with error

- Issue: Cross-contaimination within the tests
- Fix: Return your function call and use a catch block. See code below:

```
it('Should throw error when searchCertificates results in error', () => {
                 const onSearchSpy3 = jest.spyOn(wrapper.instance(), 'onSearchSubmit');
                 const event = {
                     target: {
                         value: 1,
                         name: 'Test Name'
                     },
                     preventDefault: jest.fn()
                 };
                 wrapper.setProps({
                     searchAction: {
                         searchCertificates: jest.fn(() => Promise.reject('fail')),
                         displayCertificate: jest.fn(() => Promise.resolve()),

                     },
                 });
                 onSearchSpy3(event);
                 return wrapper.instance().props.searchAction.searchCertificates().catch(e => expect(e).toMatch('fail'));
             });
```

##### 5/9/2018

###### Bug 16 - this.context.router.history.push is rerouting to correct page but page not rendering

- Issue: When trying to reroute to a new route the route will be called but it will not re-render the page. Meaning once I hit that route and then do a hard refresh the page loads.
  - Currently the Component is just connected to redux
- Fix: There was an issue with the asyncronisity of the call. The route change was being called before redux updated with new props

##### 5/15/2018

###### Bug 17 - default export from action => operations => index in redux (import export issue)

- Issue: Having an issue exporting and importing correctly in redux when there is only one action and trying to get it into a component. It is saying it is not a function

- Fix: This is a temporary solution because it pull it from the operations file which is not correct. But can't figure it out.
  When exporting from action => operations => index you need to do it as follows:

```javascript
// action.js file

func(){}

export default {
    func
    }
```

```javascript
// operations.js file

// import the entire object from actions file
import Creators from "./actions";

// destructure it
const { func } = Creators;

// then export this as a function
export default func;
```

```javascript
// index.js file

// DO Nothing here. Can't figure out how to import it from operations when single function (not yet)
```

```javascript
// Then in your component file

// import it directly from operations file without destructing or anything and from the operations folder (this is not the best way)
import updateWeekRange from "../../store/modules/week-range/operations";
```

##### 6/8/2018

###### BUG 18 - React Render Error

- Error: ErrorBoundary.jsx:25 Error: Objects are not valid as a React child (found: object with keys {}). If you meant to render a collection of children, use an array instead.
- Issue: One of the pieces inside of component was an empty object and you can't render an empty object. Changed it to `null` on initial load and the component rendered

###### 7/7/2018

###### BUG/Issue 19 - Issue Comparing Two Array

- Issue: I had two arrays one that was flat lik `[2018, 2017]` and one that was nested like `[{weekId: 2018}, {weekId:2019}]` and the goal was to create a new object inside the second array if it didn't exist. The issue was I was trying to figure out how to map over the first and then the second and if it didn't exist in the second, add it to the array. However, this method would have added the date to the second array multiple times.

- The fix, I looped through the second array and pull out the weekIds. Then I looped over the first array and if it doesn't exist in the second array I push it to the second array. Lesson is don't compare different array types. Put them in the format needed then compare.

```
function fillMissingWeeks(metrics_by_group, currentWeekIds, groupByField) {
  Object.keys(metrics_by_group).forEach((metricsGroupName) => {
    const existingWeekIds = metrics_by_group[metricsGroupName].data.map((newItem) => newItem.weekId);
    currentWeekIds.map((week) => {
      if (existingWeekIds.indexOf(week) === -1) {
        const processedMetaData = groupByField.processAdditionalMetaData
          ? groupByField.processAdditionalMetaData({ name: `${week}` })
          : {
              name: week
            };
        metrics_by_group[metricsGroupName].data.push({ ...processedMetaData, value: 0 });
      }
    });
    metrics_by_group[metricsGroupName].data.sort((a, b) => a.weekId - b.weekId);
  });
}
```
