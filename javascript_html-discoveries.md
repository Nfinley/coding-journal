# Glossary of Javascript and HTML Discoveries

#### Javascript

- `.concat()` can be called on an array (Array.prototype.concat()) or on a string (String.prototype.concat())
  - Array: can be called to merge two or more arrays
    - Syntax: `var new_array+ old_array.concat(value1[, value2[,...[, valueN]]])`
    - [Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat?v=example)
  - String: method combines the text of one or more stings and returns a new string.
    - Syntax: `str.concat(string2[, string3, ..., stringN])`
    - [Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)
- `Promise`: The javascript promise creates a promise and there are certain parameters you can use with this. For example `reject()` and `resolve()`

- `Debounce`: It improves performance by limiting the number of expensive calculations, API calls, and DOM updates. Can use in React.

  - By debouncing, we prevent the setState() which serves to significantly reduce the number of times we force React to reconcile and append the list to the DOM.
  - Common scenarios for a debounce are `resize`, `scroll`, and `keyup/keydown` events. In addition, you should consider wrapping any interaction that triggers excessive calculations or API calls with a debounce.
  - [Link 1](https://levelup.gitconnected.com/debounce-react-and-redux-code-for-improved-performance-4b8d3c19e305)
  - [Link 2](https://levelup.gitconnected.com/debounce-in-javascript-improve-your-applications-performance-5b01855e086)

- New React fucntion called `static getDerivedStateFromProps(nextProps, prevState)`

  - [Link](https://reactjs.org/docs/react-component.html#static-getderivedstatefromprops)
  - It is used in place of componentWillReceiveProps()
  - It is a static function so it doesn't have access to `this`
  - Also calling `this.setState() generally does not trigger this function

- `!!MyVarbariableExists`: The use of the double exclamation mark converts a value to a boolean and ensures a boolean type
  ```
  "foo"      =    "foo"
  !"foo"     =    false
  !!"foo"    =    true
  ```
- Using an arrow function like: `handleChange = () => {}` Arrow functions adopt the `this` binding of the enclosing scope (in other words, they don’t change the meaning of this), so things just work automatically.

- Sorting by two fields: `.sort((a, b) => b.productCount - a.productCount || a.name.localeCompare(b.name));` This will first sort by the first one and then if they are equal it sorts by the second. In this case it first sort the greater of two product count and then if they are equal sorts alphabetically.

###### Argument vs. Parameters

###### Let vs. Const

#### HTML

- `HTMLSelectElement.namedItem` will return the HTMLOptions Element corresponding to the name or id that matches or null if no options match: [Docs](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement/namedItem)
- `Document.forms` returns a collection of the `<form>` elements within the current document: [Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/forms)
