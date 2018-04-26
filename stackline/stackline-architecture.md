# Stackline Proposed Project Architecture for UI Codebase

### File Structure
* All Images should be housed in the `SvgIcon` folder
* All components should be inside `components folder`
* All components that are only containers and contain no logic only render a view should be housed in `containers` folder
* Any `utils`
* Repeated function logic throughout app must be consolidated
*  __TODO__:  Decide on index.js convention
*  __TODO__:  ROUTES file should only house the routing logic


* See proposed folder structure below:

````
App.js
    |--
    
project.config.js    
````

### Naming Convention
* All components should be uppercase and named with the `.jsx` syntax ie: `Uppercase.jsx`
* Helper functions and non-jsx content should named lowercase and with `.js`
* All actions and reducers should be named appropriately ie: `userAction.js` or `userReducer.js`
 * __NO DUPLICATE FILE NAMES__. Uppercase reserved for components only!! 

### Handling API Calls/Data Requests
* No Api calls should be in the components and instead should be handled in thunks
* Signin component has axios call in the form submit (needs to be extracted)

### Leveraging Redux
* Currently managing state in components and could leverage Redux better. 
* Look into using Connected-Router vs. Context router
* The following we could manage using redux: 
    * __TODO__: Look at how to leverage
        * One way for Charts display, have basic config of a chart then use Redux to call the api and return the data and pass the updated config into the component
        * Use it to dispatch action to call `/AdvancedSearch` call
### Error Handling 
* All network/api calls should handle for errors
* Utilize library like Flow for Type enforcement

### CSS Conventions
* Need to figure out if css should live in component folders or on the main level (currently have both, `base.scss` not being utilized)
* If the class will only be applied to the specific component and NO WHERE ELSE then the file can be located within the component file, otherwise it should be a generic class and within the `styles` folder
* __TODO__: LOOK HOW CURRENTLY STRUCTURED



### Files to Rename: 
* Brand
* Brands
* Products
* App and app (multiple `app.js` one in types folder and one in utils folder)
* BaseRoute (Should be Summary)
* Line (there are at least three)
* advanced-search (there are three, two lowercase and one uppercase)

### Duplicate Code: 
* Segments.scss and Brand.scss have quite a few classes that are exactly the same
* Function: `buildRequestSearchType` exists in both utils/data/index.js and utils/advanced-search.js (both of these files share quite a few duplicate code)
* Need TO remove all AUTOSUGGEST references in both beacon and atlas