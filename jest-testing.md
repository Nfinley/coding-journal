# Jest Testing

Jest is a testing framework developed by facebook to use in conjunction with React

Enzyme is a JS Testing utility for React that makes it easier to assert, manipulate and travers React components. It was created by AirBnB

###### Tools/Docs:

* [Jest Docs](https://facebook.github.io/jest/docs/) 
* [Enzyme Docs](http://airbnb.io/enzyme/index.html)





Difference between `mount` and `shallow`: 

`mount(<Component />)`for Full DOM rendering is ideal for use cases where you have components that may interact with DOM apis, or may require the full lifecycle in order to fully test the component \(ie, componentDidMount etc.\)

vs.

`shallow(<Component />)`for Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure that your tests aren't indirectly asserting on behavior of child components.



## Examples of Tests
For more examples please see the Redux Testing [documentation](http://redux.js.org/docs/recipes/WritingTests.html) 

### Component Test example
````
describe('Component Test', () => {
 
    describe('Component State Test', () => {
        it('Should have the correct state', () => {
            // Test state here
        });
    });
 
    describe('Component Props Test', () => {
        it('Should have the correct set of Props', () => {
            // Test Props Here
        });
    });
    describe('Component Actions Test', () => {
        it('Should have the correct set of actions', () => {
            // Test Actions Here
        });
    });
 
    describe('Component Elements Test', () => {
        it('Should contain two elements', () => {
            expect(wrapper.find('element').length).toEqual(2);
        });
        describe('Component Card Tests', () => {
            it('Should contain this element', () => {
                expect(wrapper.find('#someId').exists()).toBe(true);
            });
            it('Should contain this element', () => {
                expect(wrapper.find('#anotherId').exists()).toBe(true);
            });
        });
    });
});

````

### Action Test example

````
import configureMockStore from 'redux-mock-store';
import thunk from 'redux-thunk';
import * as actionName from  './actionName';
 
const middlewares = [ thunk ];
const mockStore = configureMockStore(middlewares);
 
 
describe('Action Name', () => {
    const payload = {
        showPage: true,
        showName: false
        default_organization: '',
    };
    beforeEach(() => {
        fetch.resetMocks();
    });
 
 
 
    describe('Action function name', () => {
        it('Should dispatch ACTION_NAME_1', () => {
            const store = mockStore({});
            const actions = store.getActions();
            store.dispatch(actionName.actionNameFunction('test'));
            const expectedPayload = {applications: 'test', type:'ACTION_NAME_1'};
            expect(actions).toEqual([expectedPayload]);
        });
            //Test each action
 
 
    });
    describe('Thunk functions', () => {
        it('should post updated user preferences to the api', () => {
            fetch.mockResponse(JSON.stringify({test: 'test'}), {status: 200});
 
            const store = mockStore({});
            const actions = store.getActions();
            const mockactionNameAction = {
                'actionName': {
                    showPage: true,
                    showName: false,
                    'default_organization': '',
                     
                },
                'type': 'ACTION_NAME_1'
            };
 
            return store.dispatch(actionName.actionNameFunction(payload))
                .then(() => {
                expect(actions).toEqual([mockactionNameAction]);
                });
        });
 
        it('should post an error if the response status is > 300', () => {
            fetch.mockResponse(JSON.stringify({testError: 'test error'}), {status: 301});
 
                const store = mockStore({});
 
                return store.dispatch(actionName.actionNameFunction(payload))
                    .catch((err) => {
                    expect(err).toEqual({testError: 'test error'});
                    });
        });
            //Test each Thunk
    });
});
````

### Reducer Test example

````
import reducerName from './reducerName';
import * as actions from '../actions/actionName';
 
describe('Reducer Name', () => {
    it('Should have a default state', () => {
        const action = {type: 'UNSPECIFIED_ACTION', blah: 'blah'};
        const newState = reducerName({}, action);
        expect(newState).toEqual({});
    });
 
    it('should handle REDUCER_CASE_1', () => {
        const initialState = {
            showPage: true,
            showName: false,
            default_organization: '',
             
        };
 
        const newPreference = {
            showPage: false,
            showName: true,
            default_organization: 'LnP',
  
        };
 
        //Begin Redux "Mock" Process
        const action = actions.updateUserPreferencesSuccess(newPreference);
        const newState = userPreferencesReducer(initialState, action);
        expect(newState).toEqual(newPreference);
    });
 
    it('should handle REDUCER_CASE_2', () => {
        const updatedPreference = {
            showPage: false,
            showName: true,
            default_organization: 'LnP',
  
        };
 
        const action = actions.actionNameFunction(updatedPreference);
        const newState = reducerName([], action);
        expect(newState).toEqual(updatedPreference);
 
    });
        //Test all reducer cases
 
});

````

Another Example with comments: 

````
import identityTypeReducer from './identityTypeReducer';
import * as actions from '../actions/identityTypeAction';



describe('Identity Type Reducer', () =>{
	it('Should have default state', () => {
		const action = {type: 'UNSPECIFIED_ACTION', blah: 'blah'};
		const newState = identityTypeReducer({}, action);
		expect(newState).toEqual({});
	});

	it('Should handle CREATE_IDENTITY_TYPE_SUCCESS', () => {
	        //need to set initial state
		const initialType = {type: ''};
		
	        //then set the new structure of state
		const newType = {type: 'ANONYMOUS'};

	        //then set the action to call this action and pass new state
		const action = actions.createIdentityTypeSuccess(newType);

	        //then set new state to the reducer needed to handle this action and pass the action defined above
		const newState  = identityTypeReducer(initialType, action);

	        //then expect new state to equal new structure of state
		expect(newState).toEqual(newType);
	});

	it('Should handle LOAD_IDENTITY_TYPE_SUCCESS', () => {
		//mocking initial state of identityType
		const initialType = {type: 'ENTITY'};

		//setting action to the dispatch of load identity type and dispatch the state
		const action = actions.loadIdentityTypeSuccess(initialType);

		//setting newState through calling the reducer and passing the state and the action
		const newState = identityTypeReducer(initialType, action);

		//comparing the newstate of the app to the initial state and they should be equal
		expect(newState).toEqual(initialType);

	});

});
````