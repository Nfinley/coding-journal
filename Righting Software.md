# Righting Software Book Notes

* (Link to site)[https://rightingsoftware.org/]
  

## Chapter 1 



## Chapter 2 


## Chapter 3 - 



## Chapter 4 - Composition (p. 83)
* Never design against the requirements

#### Core Use Cases
* There are only ever two use cases: *CORE* uses cases and everything else
* *CORE* use cases represent the essence of the business of the system
* A *CORE* use case will almost always be some kind of an abstraction of other use cases, and it may even require new term or name to differentiate it from the rest
  
#### Architects Mission
* Identify the smallest set of ocmponents that you can put together to satisy all core use cases
* The regular use cases simply represent a different interaction between compontns not a different decomposition
* **COMPOSABLE DESIGN**  - it does not aim to satifsy any use case in particular 
  
#### Architecture Validation  
* Composable design enabled design validation
* After producing interaction between services for core use cases you have produced a valid design 
* Act of validating design can be as straightforward as producing simple diagrams demonstrating the interactions - called *CHAIN* diagram (figure 4.1 page.88)
* You can superimpose the call chain onto the layered architecture diagram
* Components are connected by arrows indicating the direction and type of call between components
  * Solid Black arrow for sync calls (requests/responses) 
  * Dashed Grey arrow for a queued call
* Validate also with *SEQUENCE* diagrams (figure 4.2 page. 89)

#### Smallest Set
* Less is more in Architecture
* You should produce architecture that minimizes not maximizes the amount of work involved
* Smallest set of services required in a typical software system contains 10 services in order of magnitude
* Using *The Method* even in large systems you are commonly looking at 2-5 *Managers*, 2-3 *Engines*, 3-8 *ResourceAccess* and *Resources* and half-dozen utilities

#### Duration of Design Effort
* Author expects most readers of this book to pick a day or a week and with practice it could be a few hours
  
## There is no Feature
* **DESIGN RULE**: Features are always and everywhere aspects of integration, not implementation
* Car example, there is no transport feature, it emerges during the integration of the engine, chassis, gear box, road, etc

## Handling Change
* We must repond quickly to change and accept it is innevitable

### Containing the Change
* A change to a requirement is actually a change to the required behavior of the system - specifically a use case
* If your design follows *The Method* then these types of changes mainly occur in the *Managers* which should be almost expendable. This isolates the volitility and the underlying components that the manager integrate with are not affected by the change to the required behavior

