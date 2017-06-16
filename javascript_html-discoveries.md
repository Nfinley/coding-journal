# Glossary of Javascript and HTML Discoveries 


#### Javascript
* `.concat()` can be called on an array (Array.prototype.concat()) or on a string (String.prototype.concat())
    * Array: can be called to merge two or more arrays 
        * Syntax: `var new_array+ old_array.concat(value1[, value2[,...[, valueN]]])`
        * [Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat?v=example)
    * String: method combines the text of one or more stings and returns a new string.
        * Syntax: `str.concat(string2[, string3, ..., stringN])`
        * [Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat)
        
* `Promise`: The javascript promise creates a promise and there are certain parameters you can use with this. For example `reject()` and `resolve()`


#### HTML 

* `HTMLSelectElement.namedItem` will return the HTMLOptions Element corresponding to the name or id that matches or null if no options match: [Docs](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement/namedItem)
* `Document.forms` returns a collection of the `<form>` elements within the current document: [Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/forms)