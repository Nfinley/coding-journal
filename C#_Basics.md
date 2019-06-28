# C# Basics

### C# vs .NET
   * C# is a coding language - static typed language
   * .Net is a Framework for building applications on Windows 

### CLR - Common language Runtime
   * CLR is an application that sits in memory and whose job it is to translate the IL Code (intermediate code) into Native code
   * This process is called Just In Time compilation (JIT)
   
### Architecture of .NET Applications
* Start with Classes
    * A class is a container that has data and methods
* A namespace is container to contain related classes
* Assembly is a container for related name spaces - physically it is a file that can be a dll or exe
* So when you compile your code it builds assembly files that are then executable


### First C# Application
* C# is case sensitive
* You must also have brackets around your scopes

### Variables and Constants
 * Variable: a name given to a storage location in memory
 * Constant: an immutable value (it cannot change which creates stability)
 * Have to assign variables a value - has to be initialized 
 * Identifiers cannot start with a number and they cannot have whitespace and cannot be reserved keyword and use meaningful names
 * Hungarian Notation (not used in C#): <type>NAME
 * Local variables use Camel case
 * Constants use Pascal Case

### Primitive types
* Integral Numbers
    * byte
    * short
    * int
    * long
* Real Numbers
    * float
    * double
    * decimal
* Character   
    * char (unicode at 2 bytes)
* Boolean
    * bool 
 * Double numbers are the default number that is compiled

### Non-Primitive Types
* String
* Array
* Enum
* Class

### Overflowing
* Means that we have gone beyond the bound of the type
* Use the `checked` keyword to check the overflow, with this an exception is thrown and oveflow will not happen - IT IS NOT USED

### Operators
* Arithmetic Operators
    * simple math but also Increment or decrement
* Comparison Operators
* Assigment Operators
* Logical Operators: && and, || or, ! not
* Bitwise Operators (used in sockets): & And, | is or


