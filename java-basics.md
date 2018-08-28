## Java Basics
* [Pluralsight course]()

##### What is Java? 
* It is a Programming Language
    * Syntax, Control Flow, Object Oriented
* It is also a Runtime Environment
       * Config, security, Threading, Input/output
       * Java SE, EE, ME and Android
* JRE = Java runtime
    * Required to run JAva apps
    *  End users normally require only the JRE
* JDK =  Java Development Kit
    * Provides tools to create apps
    * JDK installation include JRE
    * The JDK produces a JAVA APP which then runs on top of a JRE which is read by Host environment

##### Statement Structure
* All lines ends with semi-colon
* Not whitespace sensitive. White space are just separators where the semi-colon is the end of the statement
##### Comments
* Line comments `//`
* Block comments `/* ... */`
* JavaDoc comments `/** ... */` You can write documentation in your code
    
##### Packages
* Provide organization and uniquess in class names
* naming convention is all lowercase
* user reverse domain name ie `package com.pluralsight`
* add further qualifiers within a company/group `package com.pluralsight.myproject`
* even further to add departments `package com.pluralsight.accounting.myproject`


##### Variables
* It is a Named data storage
* Strongly typed and we have to specify the type: `int dataValue`
* Value can be modified
* Rules allow us to use letters and numbers and must be started with a letter
* Convention of naming is camelCase

##### Primitive Variable Types
* Foundation of all other data types
* 4 types: Integer, Floating Point, Character and Boolean

###### INT types
   * byte: size is 8 bits
   * short: size is 16 bits
   * int: size is 32
   * long: size is 64, you have to put the capital L
###### FLoating points 
   * Allows you to store values containing fractional portion
   * There are 32 bit and 64 bit floating point type
   * Float = 32- bit
   * Double = 64-bit
   
###### Character and Boolean (true/false)
   * Different than strings
   * it is `char regularU = 'U';` or `char unicode = '\u0567'`
   * `boolean iLoveJava = true;`
   
   
##### Primitive Types are stored by value
##### Arithmetic Operators
   * Basic Operators: `+ - / %`
   * Prefix/Postfix: ++ increments by 1, -- decrements by 1
        * As prefix applies operation before returning value
        * As postfix applies operation after returning the value
   * Compound
        * Combines an operation and assignment
        * Applies result of right side to left side and stores that result in variable on left side

* Order of precendence: Postfix, prefix, Multiplicative, and then Additive

##### Type Conversion
* Implicit Type Conversion: They automatically convert by compiler
    * Widening conversions are automatic: IE: 32-bit to 64-bit
    * Mixed integer sizes choose largest integer in equation
* Explicit  Type Conversion: Conversions performed explicitily in code with cast operators: 
    ````
        long lVal = 50;
        int iVal = (int) lVal;
    ````
    