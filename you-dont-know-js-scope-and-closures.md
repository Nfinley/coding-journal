# You Don't Know JS: Scope & Closures

### Chapter 1: Scope

* Scope is a well-defined set of rules for storing variables in some location and for retrieving those variables at a later time
* JS is actually a compiled language but not compiled way in advance like other traditionally compiled languages, it is compiled mere microseconds before the code is executed. 

#### Three steps of Compilation

1. Tokenizing/Lexing: breaking up a sting of characters into meaningful chunks or tokens
2. Parsing: Taking an array of tokens and turning it into a tree of nested elements, called **Abstract Syntax Tree**
3. Code-Generation: This is the process of taking the **AST **and turning it into executable code, ie creating the variable `a` including reserving memory and store a value into `a`. 

Note: The JS compiler is vastly more complex than just these three steps but gives a good overview. 

#### The Cast needed to executed a program

1. **The Engine:** Responsible for start-to-finish compilation and execution of JS program
2. **Compiler**: Engine's friends, handles all the dirty work of parsing and code-generation
3. **Scope: **Collects and maintains a look-up list of all declared identifiers and enforces strict set of rules as to how these are accessible

**Two distinct actions are taken for variable assignment: **

1. Compiler declares a variable in current scope\(if not already exists\)
2. When executing Engine looks up the variable in Scope and assigns it if found





