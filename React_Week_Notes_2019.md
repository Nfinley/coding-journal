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

