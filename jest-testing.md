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



