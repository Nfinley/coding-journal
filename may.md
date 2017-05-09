### What I learned {#LnPWebApp-I.OnboardingGuide(devenvironmentsetup)}

#### Regex expressions

* Playground: [https://regex101.com/](https://regex101.com/) 
* Tuts turotial \([https://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149\](https://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149\)\) 
* Regex Expression to exclude all letters,  " - " and " ' " and certain character set from UTF-8
* Other regex references: http://work.lauralemay.com/samples/perl.html

```
nameValidation = /[^\\w'a-z-A-Z\s\u{0080}-\u{017F}\u{1E00}-\u{1EFF}]+/u

phoneValidation = /((\(\d{3}\) ?)|(\d{3}-))?\d{3}-\d{4}/.test(fieldValue)
address = /^[A-Za-z0-9#/.\-,'\s]+$/gm . (this makes it so it accepts all letters and numbers and 
only certain characters
```

* [Jest](http://facebook.github.io/jest/) Testing
* Redux[ training](https://www.gitbook.com/book/nfinley/react-notes/edit#/edit/master/chapter1.md?_k=so23lf)
* Considerations on how to structure your data

  * Always think about how your data will flow before building it. In this context it is with Redux. 

* Git commands for pulling, merging and branching

* Posted on Stack Overflow: http://stackoverflow.com/questions/43872975/regular-expression-to-match-u-s-cities-allowing-certain-special-characters

* 
### What I Liked

* Went to a Kyle Simpson Talk \(insert notes on talk\)
  * 

### 

### What I disliked

### 

### Accomplishments

* Built reusable components in React

* Wrote Regex expressions and validation to validate phone, name, and email.

  * Using the Validity.valid method
  * Using Regex

* Minor Jest Tests \(contact info component\)



