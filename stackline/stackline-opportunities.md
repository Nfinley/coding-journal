# Notes on potential opportunities for Stackline


### Bugs while refactoring
* Sort by Week does not seem to be working correctly as it shows essentially the same view as YTD (period of 'year' is in the api call)

### Short-Term Fixes (as you edit files)

* Use Descructured {Component} in React files 
* extract all constants and insert into contansts file
* Examine Scss colors and remove from individual files
* Currently calling api calls inside of the components (maybe move out to thunk)
* Naming convention to remove duplicate component or file names
* Currently the `Advanced Search` call is being called more than 7 calls (is it necessary?)
* Rename redundant files and move files to respective folders
* Extract duplicate functions into own folders
* Use the SgvIcons component to render svg's and remove all hard coding of images. And move all images to SvgIcons folder 

#### Standardizing

* Examine current redux structure and figure out how to leverage the tools much more and add api calls within the thunks
* Check Testing setup - and fix all tests
* Commitizen to standardize commit messages
* Alphabetize imports and consts
* Documentation of React components (look at Storybook or https://react-styleguidist.js.org/docs/documenting.html)
* Have uniquely named components across app (ie right now there are multiple `Brand.js` files and `advanced-search.js` files)
* Currently not handling any errors in thunks/api calls
* Read about Css strategies for easiest use
* How to import Material-UI to take only small portions (import as a const and dynamic loading)
* Don't nest props (currently have calls like `this.props.props`)
* Package Auto-Suggest not being used on ATLAS only Auto-Complete from Material-UI is. Consider removing


### RAJ Requests
* Have some sort of state management so we don't make unecessary API calls and it loads quicker
* Integrate JARVIS as a chatbot

### Tasks Completed/Accomplishments

* Added Webpack analyzer to dev in `test-branch` and pushed to master(https://www.npmjs.com/package/webpack-bundle-analyzer)
* Updated Honest Kitchen image on S3 bucket (chrome extension may have a glitch)
* Added Lodash webpack--plugin and saved `474.84KB` in the bundle - see images in stackline folder
* Added `npm-run-all` to run scripts in parrallel
* Created new script `dev` to run lint and compile at the same time
* Added `lint:watch` script to run watch on linting
* Finished PI-1: Fixed comparison brands graphs issue
* Removed straight lodash import to only use those modules we need savings is
* Lodash use only use what we need
* SEE JIRA
* Created a new Docker Image with node, yarn and aws cli

### REFACTOR OF APP STARTED May 7th
* Header refactored
* Nav bar refactored (may 24)


#### Accomplishments
* Employee #34
* Built a Docker image based off of crawler image in dockerhub and added python and aws cli to it. Using it as the image for the website codebuild projects
* Created a Terraform file representing the codepipeline for the front ent
* Created multiple code pipelines for beacon and atlas deployment
* Set up CI/CD for the website using CloudFront, S3, CodePipeline and Terraform
* Point person for web dev roles, and updated Web dev assessment, created a grading rubric, FAQs and codified what are test acheives and what we are looking for in a candidate
* Refactoring on entire application implementing React and Redux standard patterns to make it more scalable (with Raj help) started May 7th officially
* 


### Requests from Morgan

* She would ultimately like to have a living-styleguide
* Would like to focus more on accessibility
* Would like to create a better flow and collaboration between devs and design 

### Webpage Opportunities  - From CHROME AUDIT (based on Chrome audit of BEACON site)

#### Accessiblity 

* Beacon ranked 65% for accessibility - improvements to be made: 
        * Buttons do not have accessible names
        * Links do not have a discernable name
        * Background and foreground colors do not have enough contrast ratio

#### SEO

* Document doesn't use legible font sizes
    * 95% of text is too small

#### Performance
* As of 4/4/2018 Performance audit ranked 49%
* Thing to do to improve: 
    * Enable Text Compression (GZIP)
    * Properly sized images
    * Serve images in next-gen formats including JPEG 2000, WebP and JPEG XR
    * Remove unsed CSS Rules 
    * Improve caching on frequently used content (CloudFront)
* Diagnostics: main bundle is 1850KB and transfer time is 10,070ms

* Ran Coverage report in Chrome (4/4/2018)
    * Currently there is 58% unused code in the main.js file. There is 1 864 998 Bytes and 1 081 475 bytes are unused
    * Solution (code-splitting) - IE `index.js` route file can benefit from Dynamic routing

---

### Goals
* Have more tests - Focus on testing (Abhijeet)

### AWS Improvements
* S3 - Save thumnails in RRS instead of Standard to save on price