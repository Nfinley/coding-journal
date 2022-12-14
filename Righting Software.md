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
  
### There is no Feature
* **DESIGN RULE**: Features are always and everywhere aspects of integration, not implementation
* Car example, there is no transport feature, it emerges during the integration of the engine, chassis, gear box, road, etc

### Handling Change
* We must repond quickly to change and accept it is innevitable

#### Containing the Change
* A change to a requirement is actually a change to the required behavior of the system - specifically a use case
* If your design follows *The Method* then these types of changes mainly occur in the *Managers* which should be almost expendable. This isolates the volitility and the underlying components that the manager integrate with are not affected by the change to the required behavior

## Chapter 5 - System Design Example (p.95)
### System Overivew
* TradeMe is a system for matching tradesmen to contractors and projects
* Lots of varying factors like project type, skill level, certifications, years of experience and weather
* Tradesman (enter pay they expect) and Contractors can sign up to use the system
* Contractors can request specific tradesmen whom they would like to work with
* System lets market forces set the rate and find equilibirum
* Projects are construction projects for buildings but could be useful in other ways
* System processes the requests and dispatches the required tradesmen to work the sites, and it keeps track of hours and wages and reporting to the authorities
* System isolates tradesmen from contractors and contractors cannot bypass the system and hire directly because tradesmen have exclusivitiy in the system
* The System makes money on the small spread between the ask rate and the bid rate and it find the best rate for the tradesman and the most availability fo the contractors. There is also a membership fee both parties pay as such both parties are called members
* Call centers handle the majority of assignments

#### Legacy System
* Call center in europe has full time users who rely on a two-tier desktp app connected to a database. Both the tradesmen and contractors call in, with the reps entering the details and even permforming matching in real time
* Various subsystems are ineffiecnt requiring a lot of human intervention
* Users required to employ five applications to accomplish their tasks
* Clients apps are chalk full of buisiness logic and lack separation between UI and business logic prevents updating application to modern experience
* Business and users are frustrated with legacy system inability to keep up wth the times
* System is highly specific for its current business context
* Has difficulties complying with legislation 
* System has 220 res across all locations

#### New System
* Desire to automate as much as possible
* Downsize to one small call center
* Use a single system across all locales
* Adding other fields of work is out of scope, adding these markets would redefine the nature of the business

#### The Company
* Company views itself as a tradesmen broker, not a software org
* They have tried to rewrite the software and failed and they do have money to spend on new software

#### Use Cases
* The company provides 8 "use cases" via use case diagrams (p.110)

#### Core Use Case
* The use caes provided were more list of simple functionalities
* Core use case is the ESSENCE OF THE BUSINESS which is: "A system for matching tradesmen to contractors and projects"
* You should not ignore other uses cases - A great way of demonstrating the versatility of your design is to show how easy it will be to support all other use cases and anything else the business might require of the system

