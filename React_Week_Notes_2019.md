# Code Splitting in React Native
@geekykaran @karan
* Lower First Paint time
* Lower Time to interactive 

### Bundling In React Native
#### Metro Bundles 
* Regular JS bundle  - into a single file
* Size increases linearly with complexity

#### Ram Bundles
* Output is still a single file
* Give a table of contents in binary
* It only loads the modules currently you need for the screen by leveraging the binary table of contents and then only takes what it needs and injects it into the VM
* Faster startup but slower subsequent screen loads
* Also you have not control over "When"js is loaded

### How to make this better
* He has a beta implementation
1. Tweak metro to generate multiple bundles using dynamic imports
2. Add custom implementation for dynamic imports
3. Use our custom dynamic import implemenation to tell the native side to the new bundle
4. Write native code to inject new bundle into the JS VM

### React loadable 
* Used to help dynamically render components
* Loadable takes loader (function) and loading (function)

### Future 
Apennine Architecture which supports multiple bundle on a single 

# Conditional Modules and Dynamic Bundling 
Rajat Kumar
rajatk@netflix.com
@rajatkumar

I. The Problem - delivering multiple experiences even if user is only using one
* Apps are huge
    * WebUI = 10mb
    * TVUI = 30mb
* Started seeing slower load fti times
* they do multivarient A/B testing 
* Problem: they need to serve billions of smaller packages that are very specific to the User's AB tests
* Broke down the problem into two pieces: Build (Webpack - static analysis) and Request (Node JS)

### Build
* They build a webpack plugin to work with Abstract Syntac Trees it looks for certain piece of code and then it builds the artifact
* Their plugin looks for syntax like `@condition <BOOLEAN>` and if statements `$$conditions$$.names`

### Bundling as a service
* Their bundler is called Codex
* Their response time is less than 70ms
* They also have multi-level caching

### Issues
* Developer experience 
* can't use webpack features like source maps


# React Suspense for Data Fetching
 - by Dustin Meyers
 - @dustint314
 - created React Conflux (State management library using React Context and Hooks) - alternative to Redux

* Its all about user experience
* It makes building loading states easy
* It handles the tough edge cases
    * Delayed loading indicator for fast networks
    * Multiple unresolved promises
* Caches your API calls!

### What does Suspense look like
* React Cache is the engine behind data_fetching
* See https://codesandbox.io/s/react-week-2018-demo-react-suspense-ej78d

# Data Visualization Animations
Aucher Serr - @aucher_serr
@2nfo
* 2n Design consultancy and they customize in data visualization
* Data viz provides an added layer of meaning for what you are triyng to convey 
* Amimations to data viz is to puntuation is to english
* Built a tooltip that follows user and their mouse and they used `requestAnimationFrame` from the window to redraw the path everytime the user moves

### Things to think about - building blocks
1. Interpolation - what is changing and how we get from a to b
2. Duration and Delay - how long does it take and when should it start
3. Timing and Orchestration - how should animation unfold, staggering
4. Object Lifecycle - elements should behave differently depending on state relative to the app

### Stack
* Css Transitions
* React (CSS) transition group
* D3.js
* Request Animation Frame
* Special mention: Tween.js and React-Spring

# React Native Under the Bridge
Chen Feldman - Freelance dev
@chenosfeldman
ranlevi.com/welcome

### Intro Native vs RN vs Webview apps
* Native-like : Flutter, Xamarin and React-Native
* Native: Swift, Kotlin (best performance)
* Hybrid & PWA: Cordova, Ionic, PWA (slightly lower performance)

* In React Native the JS components are mapped to a Native model in the other platforms (ios/android)

### Communication RN
``
JS Thread < JSON > Bridge < JSON > Native Threads
``
To spy on the communication 
`import MessageQueue from 'react-native/Libraries/Bridge...'`


### Bridge Structure
* JS Engines
    * Hermes - New Android engine 0.60.2
    * JS Core
    * V8

### Flow Terms
* UI MANAGER
* JS THREAD
* Shadow Node and Yoga (facebook layout system)

### Advantages
* Native Like
* Async actions between JS and native
* Batched Actions
* No need to write native code

### Disadvantages
* Only async no syn option between JS and native
* Unncessary data copying
* Loading all NativeModels
* RN library is heavy and harder to contribute


### Future Architecture "Project Fabric"
* New Terms: 
    * JSI - JS interface, exposes some objects and share memory. They want to mimic what the browser does
    * Fabris is the the new UI mamanger (no brige)
    * TurboModules - No need to communicate using batched JSON messages
    * CodeGen: JS single source of truth, smaller code and faster execution
    * Lean Core: They would split the large RN repo and split it into much smaller pieces
    
 * shared memory
 * No bridge - JSI is the new glue between native and JS
 * Developer routine shouldn't change
 * Static Type - Common Language   
 
 
 # Hooked on Context 
 * @DJWyatt
 * https://github.com/drewwyatt/hooked-on-context
 * https://github.com/testing-library/react-hooks-testing-library
 * Jw player handles videos and everything on top is react components
 * Context provides a way to pass data through a component without passing down to every level
 * Went really fast and didn't really talk about context
 
 
 # Building React Apps with Internationalization (i18n) in mind
 Naomi Meyer
 Software Dev at Adobe on the UI team
 
 
 * Globalization = T9N + L10N + I18N
 * Libraries for internationalization: 
    * Intl object build into es5 and 6 
    * Moment JS
    * Format JS - React Intl
    * Gloablize JS
    * I18next
    
    
# GraphQL
* Daniel Zen
* Zen.digital
* https://github.com/danielzen

### What is GrapQL
* Response to modern Web App
* A query language

### What can you do
* Describe your data
* Ask for what you want
* Get predictable results

### Why did facebook create it?
* Invented during move from HTML5 to native
* Problems encountered using REST
* Multiple round trips may overload the network
* Rest Client depends on server - breaking changes
* Strongly typed
* Introspection: you can get full documentation from the server just by asking for it

### Backend Servers
* Node Middleware   
    * Express
    * Hapi
    * Koa
* PostGraphile
* GraphQL Baas
    * graphcool/ Prisma
    * Scaohold
    * Hasura
* json-grapghql-server

### Why Use GrapQL
* Declarative
* Decoupled from Storage
* Super Fast

### Don't Versino just Evolve your API
* Not recommended to version to your API

### Apollo 
* Look at his repo: https://github.com/danielzen/react-graphql-apollo


