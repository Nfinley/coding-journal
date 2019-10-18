# Notes on A Philosophy of Software Design by John Ousterhout

## Nature of Complexity (ch. 2)

- Symptoms:
  - Change Amplification: A seemingly simple change requires code modifications in many different places.
  - Cognitive Load: How much a developer needs to know in order to complete a task
  - Unknown unknowns: When it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully. This category is the worst
- Causes:

  - Dependencies:
    - A dependency exists when a given piece of code relates in some way to other code and the other code must considered/modified if the give code is changed
    - There will always be dependencies but the goal is to reduce the number and those that remain make as simple and obvious as possible
  - Obscurity:
    - occurs when important information in not obvious
    - Inconsistency is also a major contributor to obscruity (using the same variable in different contexts)
    - It comes about because of inadequate documentation. The need for extensive documentation is often a red flag that design is not right

- Isolating complexity in a place where it will never be seen is almost as good as eliminating the complexity itself.
- Complexitiy is incremental so adopt a zero tolerance philosophy
- Most important goal in design of a system is for it to be _obvious_

## Working Code Isn't Enough - Strategic vs. Tactical Programming (ch. 3)

- Tactical Programming
  - Main focus is getting something working
  - Makes it nearly impossible to produce a good system design
  - Short-sighted and getting things done quickly with a plan introduces complexity
- Strategic Programming
  - First step is to realize working code isn't enough
  - Most important thing is the long-term structure of the system
  - Primary goal must be to produce a great design, which also happens to work
  - Requires an investment mindset
- Strategic wins over time. At the beginning tactial approach will make more progress but as the complexity accumulates more rapidly with the tactical approach it reudces productitivty. Over time the strategic appraoch results in greater progress
- The most effective approach is one where every engineer makes continous small investments in good design

## Modules Should be Deep (ch. 4, p. 19)

- Modular Design
  - This approach is a system decomposed into a collection of modules that are relatively independent
  - Goal of this approach is to minimize the dependencies between modules
  - TWO PARTS:
    - Interface:
      - Everything a developer working in a different module must know in order to use a the given module
      - Describes _what_ the module does but not _how_ it does it
      - Contains two kinds of information: _formal_ (everything a dev needs to know to implement, like signature, parameters, return type, etc) and _informal_ (includes high-level behavior or constraints on usage and can only be described using comments and can be complex)
    - Implementation:
      - Consists of the code that cirries out the promises made by the interface
      - A developer working in a module must understand the interface and implementation, plus the interface of any other modules invoked by given module
    - Best Modules are those whose interfaces are much simpler than their implementations (ie jQuery)
- Abstractions
  - A simplified view of an entity, which omits unimportant details
  - An abstraction can go wrong if it includes details that are not really important or when important details are omitted. The result is obscurity
- Deep Modules
  - Best modules are those that provide powerfull functionality yet have simple interfaces
  - Module depth is a way of thinking of cost vs. benefit
    - Benefit: is its functionality
    - Cost: the complexity of its interface
- Shallow Modules
  - Opposite of a deep module, a shallow module is one whose interface is relatively complex in comparison to the functionality it provides
- Classitis
  - Value of deep classes is not widely appreciated today, conventional wisdom is that classes should be small not deep
  - Any method longer than N lines should be divided into multiple methods, this approach results in a large number of shallow classes and methods which add to the overall complexity
- Providing choice is good but _interfaces should be designed to make the common case as simple as possible_
- By separating the interface of a module from its implementation we can hide complexity from the rest of the system
- Most important thing in desiging a class is making it deep so that they have a simple interface for common use cases, yet still provide significatn functionality.

# Information Hiding( ch. 5 p.29)

- Information Hiding

  - Most important technique for making modules deep is information hiding
  - Basic idea is each module should encapsulate a few piueces of knowledge which represent design decisions, this knowledge only appears in the interface so it is not visible to other modules
  - The details hidden usually consist of details about _how to implement a mechanism_

    - This could include data structures and algorithms related to the mechanism
    - Information hiding can often be improved by making a class slightly larger
    - It is important to avoid exposing internal data structure as musch as possible

- Information Leakage
  - Opposite of information hidding, when a design decision appears in multiple modules, creates a dependency between modules
  - One of the _biggest red flags_ in software design
  - Requires changes to multiple modules
  - Best skills you can learn is a high level of sensitivity to information leakage
  - If encoutered ask "How can I reorganize the classes so particular piece of knowledge only affects a single class
- Temporal Decomposition
  - In this, the structure of a system corresponds to the time order in which operations will occur
  - Example is an application that reads a file, modifies it and writes the file out, if these operations are broken out into three classes, both the file reading and writing steps have knowledge of the file format thus leakage across classes
  - **When designing modules, focus on the knowledge that's needed to perform each task not the order in which tasks occur**
  -
- Defaults
  - Use defaults as they illustrate thee principle that interfaces should be designed to make the common case as simple as possible
  - They are also an example of partial information hiding
  - Whenever possible classes should "Do the right thing" without being asked explicity asked
  - The best features are the ones you get without knowing they even exist
- Information hiding within a CLASS
  - Try to design private methods within a class so that each method encapulsates some information or capability and hies it from the rest of the class
- Going too far
  - Information hiding only makese sense when the information being hidden is not needed outside a module
- GOAL: Minimize the amount of information needed outside of a module

## General Purpose Modules are deeper (ch 6, pg 39)

- Make classes somewhat general-purpose
  - Sweet spot is to implement new methods in a somewhat general purpose fashion
    - This means the functionality should reflect your needs but its interface but its interface should not. The interface should be general enough to support multiple uses
    - Most important benefit of general-purpose approach is that it results in simpler and deeper interfaces
  - Generality leads to better information hiding
    - General purpose interfaces reduce cognitive load
    - One of the most important elements of software design is determining who needs to know what and when
- Questions to ask yourself
  - What is the simplest interaface that will cover all of my cvurrent needs?
    - Reducing number of methods will make it more general purpose but only as long as each API for each individual method stays simple
    - If you have to add lots of additional arguments in order to reduce the methods then its not simplifying things
  - In how many situations will this method be used?
    - If a method is for one use only it is a red flag, see if you can combine several special-purpose methods with a single general-purpose method
  - Is this API easy to use for my current needs?
    - If you have to write a lof additional code to use a class your current purpose that is a red flag that the interface doesn't provide the right functionality
  - Conclusion
    - General-purpose interfaces have many advantages over special-purpose function including:
      - Simpler
      - Cleaner separation between classes, whereas special-purpose interfaces tend to leak information
      - One of the best ways to reduce over system complexity
