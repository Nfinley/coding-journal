# Regex

#### Regex expressions

Regex is basically a sequence of characters that define a search pattern. See [Wikipedia](https://en.wikipedia.org/wiki/Regular_expression)

###### Tools:

* [Playground](https://regex101.com/)
* Tuts [tutorial](https://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149\ )
* [Rexegg](http://www.rexegg.com/regex-quickstart.html)

* [W3 Schools](https://www.w3schools.com/jsref/jsref_obj_regexp.asp)

* Other regex [references](http://work.lauralemay.com/samples/perl.html)

###### Examples of written Regex:

* For Names: This regex excludes all letters " - " and " ' " and certain character set from UTF-8 including tilde

```js
let nameValidation = /[^\\w'a-z-A-Z\s\u{0080}-\u{017F}\u{1E00}-\u{1EFF}]+/u;
```

* Phone Validation: 

```js
let phoneValidation = /((\(\d{3}\) ?)|(\d{3}-))?\d{3}-\d{4}/;
```

* Address Validation: This will allow any letters, digits and certain characters

```js
let addressValidation = /^[A-Za-z0-9#/.\-,'\s]+$/gm;
```

* City Validation: This will allow and letters, certain characters and spaces and is limited to 25 characters

```js
let cityValidation = /^[a-zA-Z',.\s-]{1,25}$/g;
```

###### To Test each use the following method:

```js
nameValidation.test('yourstringhere')
```

###### Stack Overflow post \(May 9th\)

[Posted a question about cities to stack overflow](http://stackoverflow.com/questions/43872975/regular-expression-to-match-u-s-cities-allowing-certain-special-characters): [http://stackoverflow.com/questions/43872975/regular-expression-to-match-u-s-cities-allowing-certain-special-characters](http://stackoverflow.com/questions/43872975/regular-expression-to-match-u-s-cities-allowing-certain-special-characters)

