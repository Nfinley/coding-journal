# Object Oriented Design (Coursera Class)

Upon completion of the this course I will be able to: 
1. Explain Object-Oriented analysis and design
2. Engage in object-oriented modelling
3. Explain design principles for object-oriented programming

* Software design -looks at the lower-level aspects of a system
* Software architecture looks at the higher-level aspects


#### Most important design principle
* Simplicity
    * If it is simple you can explain it easy
    * Chances of misunderstanding are lower

#### Skills needed
* Technical guru
* Empathetic Comminucate with people at their level (ie talk to a biz person at their level)
* Meta skill - look at tools to see whether or not it would be beneficial and quickly asses value

# Module 1: Object-Oriented Analysis and Design
Goals of Module: 
a. Explain object-oriented thinking
b. Understand role of design and communication in software process and link between these concepts
c. Design for quality attributes
d. Model CRC Card

#### Object - Oriented Modeling
* Using objects to represent things allows your code to stay organized, blexible and reusable
* Objects are self-aware
* Objects can be living or inanimate 

#### Design in the Software Process
* Conceptual Design: Taking requirements and asking probing questions
* Technical Diagrams
* Implementation 

#### Requirements
* Crucial to ask follow up questions and what constraints there may be
  
#### Conceptual Design 
* Made up of components, connections and responsibilities
* These highlight high level concepts   
* They are expressed through conceptual mock-ups
* Each component has a specific task it needs to perform or its responsibility.
* Responsibilities are often the verbs in user stories
* Nouns correspond to the objects


#### Technical Design 
* Spliting componets into smaller and smaller components each with specific responsibilities

#### Categories of Objects in Design
1. Entity Objects: Most familiar because they correspond to some real work entity, like a chair or a building
2. Boundary Objects: If it intereacts with another system (Ie: an object showing data to the user). Sits at the boundary of two objects. Any object that deals with another system - a user, another software system - the internet are boundary objects
3. Control Objects: Responsible for coordination. Ex is a `Mediator` it simply coordinates the activities of any different objects so they can stay loosely coupled

#### Design for Quality Attributes
* Security
* Code Quality
* Time to market

#### Trade-offs
* A good design should balance security with convenience and performance.
* The balancing act of weighing quality attributs against the requirements of the produc is an ongoing constant in Software Architecture

#### Context and Consequences
* Context provides important information when deciding on the balance of qualities in design
* To establish context talk to Stakeholders

#### Satisfying Qaulities
* Funtional Requirements describe what the system is expected to do.
* Non-Functional specify how well the system or application does what it does. Might include: performance, resource usage and efficiency 
* There are functional and non-functional requirements
* Other non-functional requirements include: Flexibility, Reusability and Maintainability

#### Compromise
 Software must meet multiple perspectives say of both developers and users
 * Common Trade Offs include
    1. Performance and maintainability  - High performance code may be less clear and less modular, making it harder to maintain. Alternatively, extra code for backward compatibility may affect both performance and maintainability
    2. Performance and security - Extra overhead for high security may lessen performance
* Common qualities to consider: Performance, Maintainability, Security and backwards compatibility 
* Important to consider project realities as well: You must balance with available resources like time, cost and  manpower


### Class Responsbility Collaborator

#### CRC Cards 
* A way to represent the components, connections and responsiblilities at a high level when forming conceptual design
* Help organize and record components into classes, identify component responsibilities and determine how they collaborate with each other. 
* Designed with three sections: 
  1. Class Name at top
  2. Responsibilities of class on left 
  3. Collaborators (connections) on the right - List other components that are related

#### Prototyping and Simulation
* Key advantage of cards it they allow you to physically reorganize your design
* They are used to `record organize and refine`
* They should be organized by placing closely collaborating compontents together
* Most powerful with used for prototyping and simulation for conceptual design

# Module 2: Object-Oriented Modeling

## Objectives for Module 2
1. Describe issues in creating models for design
2. Understand how programming languages evlove toward object orientation
3. Explain the four major design principles used in OO modelling: 
    1. Abstraction
    2. Encapsulation
    3. Decomposition
    4. Generalization
4. Exporess the above using UML class diagrams and Java code
5. Explain and express implementation inheritance
6. Explain and express interface inheritance


#### Creating Models in Design
* The design step falls between understanding your requirements and building the product
* Should describe and present concepts in a way that both users and develops both understand
* OO Design deals with both Conceptual and Technical design
* The goal during software design is to construct and refine "models" of all of the objects of the software: 
    * Entity Objects: where initial focus during the design is placed in problem space
    * Control objects: that receive events and co-ordinate actions as process moves to the solution space
    * Boundary objects: connect outside services to your system as the process moves toward solution space
* Models serve as Design Documentation and are often mapped to skeletal source code
* Expressed in visual notation called Unified Modelling Language

#### Evolution of Programming Languages

##### 1960s - Cobal and Fortran
* Followed the __imperative paradigm__ that broke up large programs into smaller programs called subroutines
* Global data was used so that data was located all in one place in computer's memory and accessible anywhere for a program so subroutines only had one place to access variables
* _ISSUE_: if changes made to the data, then subroutines might run into cases where global data is not what was expected. Better data management needed

##### Early 1970s - Algol 68 and Pascal
* Solution to fix global variables was idea of scopes and local variables
* These languages also supported __abstract data types__ which is defined by programmer and not built into the language, organizating information with a type in a meaningful way
* _ISSUE_: Having one file to maintain programs was difficult to maintain

##### Mid-1970s - C and Modula-2
* Because computers were faster and able to tackle more complex problems mean that the programs of the past were too big to maintain
* These two languages provided way to organize programs into separate files and allow developer to create multiple but unique copies of abstract data types
* _ISSUE_: It is not easy for abstract data types to inherit from another in these languages, so while they could have as many data types, one type cannot be declared as an extension of another

##### 1980s to Present - OOP, Java, C++, C#, etc
* Although programs were easier to maintain there was still no way to inherit data types, as such concepts of OOD became popular as a solution to this problem 
* Object - Oriented Design seeks to: 
    * Make an abstract data type easier to write
    * Structure a system around abstract data types called classes
    * Introduct the ability for an abstract data type to extend another through _inheritance_
* Class definition files in oop replace the files in C and Modula-2
* A class acts like a factory, making individual objects of all specific types
* Data can now be compartmentalized and manipulated into its own separate classes

#### Four Design Principles

##### Abstraction
* Is one way humans deal with complexity
* Idea of simplifying a concept in the problem domain
* It breaks a concept down into a simplified description that ignores unimportant details
* Abstractions can only be created given the strict context
* Abstraction should follow __Rule of Least Astonishment__
    * The abstraction captures the essential attributes and behavior for a concept with no surprises and no definitions that fall beyond its scope
* Abstractions you create are relative to their context
* Essential characteristics of an abstraction can be understood in two ways: 
    * Basic attributes - Name, age, color, weight, height ( for a cat)
    * Basic behaviours or responsibilities
* __Benefits__: Helps simplify class desgin so they are more focused, succinct and understandable


##### Encapsulation
* Principle involves a concept that allows something to be contained in a capsule, some of which is accessible from the outside and some of which is not
* Three IDEAS: 
    * "Bundle" attribute values (data) and behaviours (or functions) that mainpulate those values into a self-contained object
    * Ability to "expose" certain data and functions
    * Ability to "restrict" access to certain data and functions
* The principle of abstraction helps determine what attributes and behaviors are relevant about a concept and Encapsulation takes this a step further and ensures these characteristics are bundled together in the same class
* Certain methods can be exposed, this provides an interface to other objects to use the class
  
* __Integrity and Security__ : 
    * One idea of encapsulation is restricting access and this naturally links encapsulation to data integrity and the security of sensitive information. 
    * Additionally, this prevents data from being changed through variable assignments 
    * And it secures sensitive information
* __Changeable Implementation__: 
    * Implementation of attributes and methods can change but the accesbile interace of a class can remain the same. For example if I need to bring a teach an apple, the teacher doesn't care how I get the apple. 
    * Meaning users don't care how a method is implemented behind the interface - they will still use the same means to access it
* __Black Box__: 
    * Its the idea that the computation steps taken never need to be known by any other class as long as they are able to access the interface
    * What happens in the box doesn't matter
    * _Abstraction Barrier_ is where the internal workings of a class are not relevant to the outside world. This results in an abstraction that reduces complexity for usersof the class
    * Encapsulation increases reusability and keeps software modular and easy to work with


##### Decomposition
* Taking a whole thing and dividing it into different parts or it can be to take different pars and create a whole
* Allows problems to be broken down into smaller pieces that are easier to understand and solve
* General rule is to look at different responsibilities of a whole and evaluate how the whole can be separted into parts
* __The Nature of Parts__: 
    * A whole thing may have fixed or dynamic number of certain type of part
    * _Fixed_: doesn't change over the lifetime
    * _Dynamic_: does change
    * Whole objects and part objects have lifetimes, sometimes closely related and sometimes not
    * _Sharing_ : Whole things may also contain parts that are shared with another whole at the same time, but sometimes its not possible or intended

##### Generalization
* Helps reduce redundancy when solving problems
* Methods - used to model algorithmic behaviours, and allow programmers to generalize behavior and reduce redundant code
* Object-oriented modelling achieves generalization by classes through __Inheritance__
* Achieved by taking repeated code or shared characteristics between two or more classes and factor them out into another class
* As such you can have two kinds of classes: _parent_ and _child_
* Child classes inherit attributes and behaviors of parent classes 
* Parent classes capture general ideas and have broader application
* _Superclass_ is a parent class
* _Subclass_ is a child class
* Parent classes save time and reduce errors
* Generalization provides more robust software solutions and allows for more resusable code because the same blocks of code can be used for different classes
* __DRY__: Both methods and inheritance explemmplify generalization through DRY - "Don't Repeat Yourself" rule


#### Design Structure in Java and UML Class Diagrams

##### Abstraction expressed in UML    
* UML Class Diagrams have three parts: 
    * Header which is the `Class Name`
    * Properties: like `name: String`
    * Operations (functions): like `isOnSale(date: Date): boolean`
* These diagrmas provide more detail than the CRC Cards
* The _properties_ section is equivalent to Java’s member
variables. This section defines the attributes of the
abstraction by using a standard template for variable name
and variable type. Variable types can be classes or primitive
types.
    <variable name>:<variable type>
* The _operations_ section is equivalent to Java’s methods. This
section defines the behaviours of the abstraction, using a
standard template for the operation name, parameter list,
and return type.
    <name>( <parameter list> ) : <return type>

##### Encapsulation expressed in UML    
* Getter methods, which are used to retrieve data. These
methods typically have the format: get<Name of the
attribute>, where the attribute is the value that will be
returned through the method. Getters often retrieve private
data.
* Setter methods, which are used to change data. These
methods typically have the format: set<Name of the
attribute>, where the attribute is what will be changed
through the method. Setters often set a private attribute in a
safe way
ie: 
````
public class Person { 
    private String name;

    public String getName() {
        return name;
    }
    public void setName(String newName){
        name = newName;
    }
}
````

##### Decomposition in UML 
* Three relationships in decomposition
    * Association: 
        * indicates a loose relationship between two objects, which may interact with each other for some time
        * Loose interactions between parts  
  
  public class Student {
    public void play( Sport sport ){
        execute.play( sport );
    }
  }
    * Aggregation
        *  is a weak “has-a” relationship where a whole has parts that belong to it. Parts may be shared among wholes in this relationship
        *  Relationship is weak they can both exist without the other
        *  IE: An Airliner and Crew Members each can exist without the other

    public class Airliner {
        private ArrayList<CrewMember> crew;
        public Airliner() {
        crew = new ArrayList<CrewMember>();
        }
        public void add( CrewMember crewMember ) {
        …
        }
    }

    * Composition: 
        * Exclusive containment of parts also known as a __strong__ "has-a" relationship
        * A whole cannot exist without its parts and if the whole is destroyed the parts are destroyed too. Ie a Human and a Brain

##### Generalization in UML 
* This design principle takes repeated, common or shared characteristics between two or more classes and factors them out into another class so code can be reused
* The # on an UML is: Protected attributes in Java and can only be accessed by:
    * the encapsulated class itself
    * all subclasses
    * all classes within the same package
* Keyword _abstract_ indicates that a class cannot be instantiated, meaning an Animal object cannot be created
* * Inheritance is declared using keyword _extends_
* A subclass can be a superclass for another subclass
* Classes can have implicity constructors or explicit constructors 
* Subclasses can override the methods of its superclass in other words provide its own implementation for an inherited superclass' method

__Implementation Inhereitance__
* In Java, only single implementation is allowed


__Interface Inheritance__
* Interfaces fulfill a specific need: to provide for a way for related
classes to work with consistency. 
* An interface only declares method signatures and specifies specific behaviors does not contain any implementation details 
* They are not classes
* Keyword _interface_ is used to indcate that one is being defined
* Interfaces are means you can acheive _polymorhpism_, which is when two classes have same description but implementations may be different
* Java doesn't support multiple ineritance so _data ambiguity_ is not an issue

# Module 3: Design Principles

* Understand the general guidelines for evaluating the
structure of your software solution so that it’s flexible,
reusable, and maintainable. These guidelines are:
    a. evaluating design complexity with coupling
and cohesion
    b. the separation of concerns
    c. information hiding
    d. conceptual integrity
    e. generalization principles
* Model behaviours of the objects in your software using
the specialized UML state and UML sequence
diagrams.
* Explain the importance of model checking. 


#### Evaluating Design Principles

##### Coupling 
* Coupling focuses on complexity between a module and other
modules. 
* Tight coupling example would be a puzzle and its pieces as they only fit certain pieces
* Loose coupling would be like LEGO because LEGOs can be attached to whatever Lego piece
* To evaluate coupling of a module the metrics to consider are: 
  1. Degree
  2. Ease 
  3. Flexibility
   
__DEGREE__ : The number of connections between the module and others, you want to keep the numbers small for loose coupling   
__EASE__ : How obvious are the connections between the module and others. Connections should be easy to make without meedint to understand the implementations of other modules
__FLEXIBILITY__: How interchangable the other modules are for this module. Other modules should be easily replaceable for something better in the future. 

##### Cohesion 
* Focuses on complexitiy _within_ a module
* Cohesion can work between two extremes: high cohesion and low cohesion
* Good design has high cohesion and will have a clear purpose
* If a module has more than one responsibility it may be a good idea to split the module

#### Seperation of Concerns
* A Design principle that is ongoing throughout the design process
* A concern is a very general notion:  A Concern is anything that matters in providing a solution to a problem 
* Separation of concerns is about keeping the different concerns in your design separate

#### Information Hiding
* Encapsulation is the practical design principle to implement the concept of information hiding
* Hide information using access modifiers. 
    * Access Modifiers change which classes are able to access attributes and behaviours. There are four levels
* Rule of thumb: Hide things that might change like implementation details and reveal things that won't change like assumptions in the interfaces
  
__PUBLIC__: attributes are accessbile by any class, meaning other classes can access and modify the attricute. Methods can be public so any class can access it but cannot modify it
__PROTECTED__: Only available to encapsulated class itself, all subclasses and classes within the same package
__DEFAULT__: only available to subclasses or classes that are part of the same package or encapsulation
__PRIVATE__: Only accessible to the encapsulating class and not by any other class. 

#### Conceptual Integrity
* Concept related to creating consistent software
* Ways to acheive conceptual integriy include: 
    * Communication, code reviews, certain deisgn priciples and programming constructs, well-defined design or architecture
  
#### Generalization Principles
* Liskov Substitution Principle: states that a subclass can replace a superclass if and only if, the sublcass does not change the functionality of the superclass


#### UML Sequence Diagrams
* Used to show a design team how objects in a program interact with each outher to complete tasks.
* _Role_ is typically named after the the class for object
* _Lifelines_ are vertical dotted lines used to indicate passing of time
* _Messages_ are represented by `solid` line arrows that are sent from one object to another, sender to receiver and a message is usually included above the arrow. `Dotted` line arrows show a return of data back to initiating objects
* Small rectangles denote a method activation being activated whenever an object sends, receives or waits for a message
* _Actors_ or people are typcailly represented by stick figures
* Good practice to draw sequence diagrams from left to right in sequence they interact with eachother

#### UML State Diagrams
* Describe how system behaves or repsonds
* They have three sections: 
    * State Name
    * State Variables
    * Activities (actions performed when in a certain state)
        * Three types of activites: Entry, Exit and Do
* Arrows indicate `transitions` from one state to another
* Transitions are triggered by events