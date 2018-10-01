# Stackline Proposed Project Architecture for UI Codebase

### Helpful Dev Tools Being Leveraged

- [Redux Logger](https://github.com/evgenyrodionov/redux-logger)
- [Why did you update](https://github.com/maicki/why-did-you-update)
- Redux Dev Tools
- React Dev Tools

### File Structure

- React/Views are based on the function-first and Redux modular structure is based on feature-first
- Basing Redux structure off of this [Article](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be)
- Re-Duck Architecture for modular Redux pattern: [Pattern](https://github.com/erikras/ducks-modular-redux) - https://medium.freecodecamp.org/ scaling-your-redux-app-with-ducks-6115955638be
  - Additional reference on file structure: [link](https://jaysoo.ca/2016/02/28/organizing-redux-application/)
- Implement the Container and Presentational Component approach (as often as possible, it may come through refactoring as well because you don't know its needed at time of first creation)
  - Dan Abramov [article](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0) on basic rules to follow
  - Another example: [Container Pattern](http://www.thegreatcodeadventure.com/the-react-plus-redux-container-pattern/) \*In theory only the code is not the greatest. Use `Data Down Actions Up` principle
  - Use the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle), and that keeps our code DRY.
- Use [composition](https://reactjs.org/docs/composition-vs-inheritance.html) instead of inheritance
- The [React Docs](https://reactjs.org/docs/thinking-in-react.html) should be used as a strong source of implementation
- Use `StrictMode` React Component to help detect unsafelifecycle methods whenever possible.
  app.
- All components should be inside `components folder`
- All Images should be housed in the `SvgIcon` folder
- Any `utils` should be in a `utils` folder and be generic
- Repeated function logic throughout app must be consolidated
- **TODO**: Decide on index.js convention
- **TODO**: ROUTES file should only house the routing logic
- Containers: Containers only connect presentational components to actions/state
  Rule of thumb: no JSX in containers!
  One or many container components can be composed in a stateless functional components
- Always start with writing a stateless/functional component and only turn it into a stateful/class component if you need to maintain state, lifecycle hooks, or wire to Redux etc.
- See proposed folder structure below:

```
├── build                   # Contains build scripts, babel config, jest configs and webpack config
├── coverage                # Contains jest coverage reports
├── dist                    # All build-related code
├── node_modules            # All related node module packages
├── public                  # Static public assets (not imported anywhere in source code)
├── server                  # Express application that provides webpack middleware (development only)
│   └── server.js           # Server application entry point used for development only
├── src                     # Application source code directory
│   ├── index.html          # Main HTML page container for app
│   ├── main.js             # Entry point for the app
│   ├── normalize.js        # Browser normalization and polyfills
│   ├── i18n_en.js          # Internationalization english document
│   ├── components          # Global Reusable Components
│   │   ├── App             # Main folder that houses the main App jsx file for the application (Uppercase folder names for Components)
│   │   │   ├── App.jsx     # Main jsx file
│   │   │   ├── App.scss    # Scss file that only applies to the App file
│   │   │   └── index.js    # Export of App
│   │   ├── common          # Folder that houses components shared across the application (like custom buttons, charts, etc)
│   │   ├── Entity Page     # Directory that houses all specific entity containers and has a direct route listed in routeTable
│   │   ├── layouts         # Folder that houses general layouts (ie: HomeLayout), currently two, one for auth and one for non-auth
│   │   │   ├── HomeAuthLayout.jsx    # Layout that wraps the Route Table and renders appropriate route when user is Authenticated
│   │   │   └── NonAuthLayout.jsx     # Layout that wraps the Route Table and renders appropriate route when user is NOT Authenticated
│   ├── routes               # Main route definitions and houses component files mentioned directly in the routeTable.js
│   │   ├── Home Page        # Directory that houses all of the Home page/summary components for the webiste and has a direct route listed in routeTable
│   │   ├── User Account     # Directory that houses all user account specific components
│   │   ├── index.js         # index for exporting routes
│   │   ├── routeTable.js     # Route config file
│   ├── store                # Redux-specific pieces
│   │   ├── modules          # Houses feature-first redux modules ('ducks'), follows the reducks pattern
│   │   │   ├── app          # Contains top level global state configs (replaces the config file)
│   │   │   │     ├── actions.js      # pure actions for top level initial state config
│   │   │   │     ├── index.js        # export all key pieces so the main reducer file can import them
│   │   │   │     ├── operations.js   #  handles any logic the actions need, also this is a wrapper around the actions as we are only exporting operations not actions
│   │   │   │     ├── selectors.js    #  handles Selector functions take a slice of the application state and return some data based on that. They never introduce any changes to the application state.
│   │   │   │     ├── reducers.js     # all reducers for the signin feature
│   │   │   │     ├── tests.js        # tests for all actions, reducers, etc.
│   │   │   │     └── types.js        # contain all constant types
│   │   │   ├── sign-in      # Example of a feature-first re-duck folder that is self-contained with actions, reducers, operations, types and tests
│   │   │   │     ├── actions.js      # pure actions
│   │   │   │     ├── index.js        # export all key pieces so the main reducer file can import them
│   │   │   │     ├── operations.js   #  handles any logic the actions need, also this is a wrapper around the actions so we are only exporting operations not actions
│   │   │   │     ├── selectors.js   #  handles Selector functions take a slice of the application state and return some data based on that. They never introduce any changes to the application state.
│   │   │   │     ├── reducers.js   # all reducers for the signin feature
│   │   │   │     ├── tests.js     # tests for all actions, reducers contained within this module.
│   │   │   │     └── types.js     # contain all constant types
│   │   ├── createStore.js   # Create and set up redux store
│   │   └── reducers.js      # Reducer registry and injection
│   └── styles               # Application-wide styles (generally settings)
```

### Routing

- Use [React Router 4](https://reacttraining.com/react-router/web/guides/philosophy) and create Dynamic Routing
- IN V4 routes are just components and should be used within the rendering of UI
- Utilize Responsive Routes (look into implementing this)
- Think of Routing as UI not as static config

### Naming Convention

- Should Strive to following this [pattern](https://hackernoon.com/react-components-naming-convention-%EF%B8%8F-b50303551505)
- All components comtaining JSX should be uppercase and named with the `.jsx` syntax ie: `Uppercase.jsx` [Airbnb Naming Standards](https://github.com/airbnb/javascript/tree/master/react#naming)
- Helper functions and non-jsx content should named lowercase and with `.js`
- All actions and reducers should be named appropriately ie: `userAction.js` or `userReducer.js`
- **NO DUPLICATE FILE NAMES**. Uppercase reserved for components only!!

### Handling API Calls/Data Requests

- No Api calls should be in the components and instead should be handled in operations files that pertain to the appropriate module

### Leveraging Redux

- Currently managing state in components and could leverage Redux better.
- Look into using Connected-Router vs. Context router
- The following we could manage using redux:
  - **TODO**: Look at how to leverage
    - One way for Charts display, have basic config of a chart then use Redux to call the api and return the data and pass the updated config into the component
    - Use it to dispatch action to call `/AdvancedSearch` call
- Reference for redux-define to help define constants [link](https://www.npmjs.com/package/redux-define)
- Need to consider clearing Redux on logout in order to clear out previous items (currently clearing User session)
- Add `AppName` to `app` object in Redux and then replace the`getAppName` with this prop
- Add `retailer.js` as a node in Redux
- Your store should not reflect the hierarchy of your folder structure, Keep it as flat and normalized as possible.

### Error Handling

- All network/api calls should handle for errors
- Utilize [Error Boundary](https://reactjs.org/blog/2017/07/26/error-handling-in-react-16.html) from React 16
- Ultimately utilize either library like Flow or Typescript for Type enforcement

### CSS Conventions

- Need to figure out if css should live in component folders or on the main level (currently have both, `base.scss` not being utilized)
- If the class will only be applied to the specific component and NO WHERE ELSE then the file can be located within the component file, otherwise it should be a generic class and within the `styles` folder
- **TODO**: LOOK HOW CURRENTLY STRUCTURED

### Files to Rename:

- App and app (multiple `app.js` one in types folder and one in utils folder)
- index.js files should only be a pure export of other files in the folders. Currently for example `utils/data/index.js` has a lot of logic. It is making an api call!! This should be in Redux

- `Container` that is used to wrap the Sign_in needs to be moved to layouts folder and renamed (try to re-use it for Beacon)

### Duplicate Code:

- Segments.scss and Brand.scss have quite a few classes that are exactly the same
- Function: `buildRequestSearchType` exists in both utils/data/index.js and utils/advanced-search.js (both of these files share quite a few duplicate code)
- Need TO remove all AUTOSUGGEST references in both beacon and atlas
- `getAppMenuConfig` function is called a lot, figure out why and refactor
- `chart-utils` and `charts` which is inside of utils folder need to be refactored/combined or renamed
- Segments - There are four uppercase `Segments` and at least two lowercase `segments`

### Code To Refactor after Merge

- `Suggestions.js` file is very large and does way too much
- `Search.js` found in the routes folder
- Remove all references to `REFs`
- `data/advanced-search.js` - All of the functions within this file exist in other files (these functions are called onload)
- Remove/Delete `App` folder in the Sidebars folder
- Put `AdvancedSearch` folder that is inside Sidebars somewhere more appropriate

### Elastic Search Queries

#### Entities:

- Client (top-level)
- Brand (sub-category of Client, but top-level in Atlas)
- Category (a collection of products)
- Segment (a custom collection of products)
- Product (a single product searching by single ID)

#### Retail Sales

- Graph:
  - Data needed: weekIds, sum of retail sales for each weekId
- Bullets:
  - Data needed: Total sales for current and past year

#### Retail Price

- Graph:
  - Data needed: weekIds, avg of retail price per week (no calculations needed)
- Bullets:
  - Data needed: Total sales for current and past year

#### Market Share Trend

- Graph:
- Bullets:

#### Weeks

### Atlas

1.  First call is for all Categories:  
    Request:

    ```
    [{
      "name": "atlas-category-following",
      "pageNumber": 1,
      "pageSize": 20,
      "doAggregation": false,
      "returnDocuments": true,
      "searchBy": "parent",
      "searchType": "atlas-category-following",
      "aggregations": null
    }]
    ```

    Example Response:

    ```
    [
      {
        "id": null,
        "name": "atlas-category-following",
        "searchType": "atlas-category-following",
        "documents": [
          {
            "id": "193",
            "categoryId": 193,
            "retailerIds": [
              1,
              18,
              35
            ],
            "categoryName": "Laptops",
            "categoryType": "Category",
            "parentCategoryId": 7,
            "parentCategoryName": "Electronics",
            "name": "Laptops",
            "categoryNameSuggestion": {
              "input": [
                "laptops"
              ],
              "contexts": {
                "categoryIdContext": [
                  "193",
                  "0"
                ],
                "categoryTypeContext": [
                  "Category"
                ]
              }
            }
          }
        ],
        "pageNumber": 1,
        "pageSize": 20,
        "hasMoreDocuments": false,
        "retailerId": -1
      }
    ]
    ```

### Aggregation Query Requests

##### Request strcuture and examples of what data you can request

`/AdvancedSearch`

1.  Summary Pages - Categories
1.  It displays by default the sum of retail sales for that entity for all categories within a speficied time period (YTD)
    - You are requesting by the entity type of 'client'
    - You can speficy the

The request body would look like

`/GetEntityMetadata`
There are also those requests that don't require aggregations as apart of the request body. These include requesting all of the brands followed/owned by the entity, and categories subscribed to by user

`/GetConfig`

`/Login`
