### What I learned {#LnPWebApp-I.OnboardingGuide(devenvironmentsetup)}

#### Regex expressions

* Playground: [https://regex101.com/](https://regex101.com/) 
* Regex Expression to exclude all letters,  " - " and " ' " and certain character set from UTF-8

```
nameValidation = /[^\\w'a-z-A-Z\s\u{0080}-\u{017F}\u{1E00}-\u{1EFF}]+/u

phoneValidation = /((\(\d{3}\) ?)|(\d{3}-))?\d{3}-\d{4}/.test(fieldValue)
```

* [Jest](http://facebook.github.io/jest/) Testing
* Redux[ training](https://www.gitbook.com/book/nfinley/react-notes/edit#/edit/master/chapter1.md?_k=so23lf)



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



