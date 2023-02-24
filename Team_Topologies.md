# Team Topologies Notes

## Part I: Teams as the Means of Delivery 
### Chapter 1 - The problem with org charts

* Org Chart is a static representation of how work is actually done 
* Four fundamental team types 
  * Stream-aligned
  * Platform
  * Enabling
  * Complicated sub-system
* Three interaction modes: 
  * Collaboration
  * X-As-a-Service
  * Facilitating 

* Conway's Law: 
  * "Organizations which desit systems...are constrained to produce designs with are copies of the communication structures of these organizations"
* "Inverse Conway Maneuver": 
  * whereby an organization focues on organizing team structures to match the architecture they wany the system to exhibit rather than expecting teams to follow a mandated arch design

#### Cognitive Load and bottlenecks
* Dan Pink's three elements of intrinsic motivation: 
  * Autonomy 
  * Mastery
  * Purpose
* Team topologies advocates for org design that optimizes for flow of change and feedback from running systems
  * thois means restricting cognitive load on teams and designing the intercommunications to help produce software-system architecture we need

#### Summary: Rethink Team Structures, Purpose and Interaction 
* Take advantage of Conway's law - organizational design prevails over software arch design
* Restrict cognitive loads and implement a team-first approach 

### Chapter 2: Conway's Law and Why it Matters
#### Understanding and Using Conway's law
* Teams are often set up based on past projects or lagacy systems 
* Comm paths along formal reporting lines within an org effectivel restrict the kinds of solutions that the org can device

#### The Reverse Conway Maneuver
* Organize our teams to match the required software architecture
  
####  Software Arch that Encourage Team-Scoped flow
* We need to team-scoped flow and design software arch to fit it: 
    * Loose Coupling - components do not hold strong dependencies on other components 
    * High Cohesion - components have clearly bounded responsibilities and their internal elements are strongly related
    * Clear and appropriate version compatibility
    * Clear and appropriate cross-team testing

* Arch for participation that promotes ease of understanding by limiting module size, and eas of contributino by minimizing the propogation of design changes


#### Organization Design Requires Technical Expertise
* If we have managers deciding which services to build by which teams we implicity have managers deciding on the system architecture 
* Anyone who makes decisions about shape and placement of engineering teams is strongly influencing the software systems architecture 
* We need to involve technical peopole in organization design they understand key software design concepts
* Allan Kelly's view of an architect: Architects needs both technical and social skills. They need to understand people and work within the social framework

#### Restrict Unnecessary Communication 
* One key implication of conway's law is not all communication and colaboration is good
* Important to define "team interfaces"  
* Focused communication is what is needed
* Questions to asses health of inter-team communicationL 
  * Does the structure minimize the number of communication paths between teams?
  * Does the structure encourage teams to commuication who wouldn't otherwise do so?
* Logically if two teams shouldn't need to communicat based on the software arch design, then something must be wrong if the teams are communicating

#### Everyone Does Not Need To Communicate with Everyone
* Conway's law suggests that the thinking of "everyone should see every message" or "everyone needs to be present in meetings to approve decisions", this many-to-many communication will tend to produce monolithic, tangled, highly coupled, interdependent systems that do not support fast flow
* More communication is not always a good thing

#### Beware: Naive Uses of Conway's Law
##### Tool Choices Drive Comm Patterns
* Sometimes an org has multiple tools when a single tool would suffice - proividing a common, shared view
* Other times a single tool used and problems arise because teams need separate instances of the same toool 
* Have separate tools for independent teams  and use shared tools for Collaborative teams
##### Repeated Reorgs that Create Fiefdoms or Reduce headcount 
* Structure should anticipate product architecture
* combined with team-first approach regular reorgs for management reasons should become a thing of the past
  
#### Summary: Conway's Law is critical for efficient Team Design in Tech 
* You cannot design software withough considering the design of the teams themselves
* Fast flow requires restricting communication between teams
* One key approach to achieving software arch is to apply reverse Conway maneuver: designing teams to match the desired architecture

### Chapter 3: Team-First Thinking 
* "Disbanding high-performing teams is worse than vandalism: it is corporate psychopathy" - Allan Kelly, Project Myopia
* Google found that who is on the team matters less than the team dynamics and when it comes to measuring performance, teams matter more than individuals
* Multiple things to consider for a team: size, lifespace, relationships and cognition

#### Use Small, Long-Lived Teams as te Standard
* Most orgs have a max team of 7 to 9 people
* Dunbar's number says that 15 people to be the limit of people one person can trust deeply and five people can be known and trusted closely
* Organizations need to maximize trust between people on the team which means limiting the number of the team members

##### Smaller Size Fosters Trust
* Dunbar's limits help achieve predictable behavior and interactions: 
  * Single team => around 5-8 people
  * Families ("tribes"): groupings of teams of no more than 50 people
  * Divisiongs/streams/profit&loss lines: groupings of no more than 150 or 500
* When number of people in department exceeds 50 (or 150, 500) -> this means the software architevture needs to be realigned with the new team grouping and this is "team-first" architecture
* Amazon has proved this effective with the two pizza rule
* Approaches like microservers can help if applied with a team-first approach
  
##### Wofk Flows to Long-Lived Teams
* Best approach to team lifespans is to keep the team stable and "flow the work to the team" 
* Stable not static and only change occassionally and when necessary

##### The Team Owns the Software 
* With small long-lived teams we can begin to improve the ownership of software
* Team ownership provides the vital "continuity of care" that modern systems need
* Teams can think about care on multiple horizons: 
  * 1 -> immediate future with products and services that deliver results the same year
  * 2 -> the next few periods with expanding the reach and services
  * 3 - many months ahead where experimentaion is needed to asses market fit and suitability of new services 
* **The danger of allowing multipled teams to change the same system or subsystem is that no one wons either the changes made or the resulting mess.**    
* Awareness and ownership over these diff time horizons helps a team care for the code more effectively 
* **Every part of the software system needs to be owned by exactly one team**
  * This means there should be no shared ownership of components, librarie or code
  * Teams may use shared services at runtime but every service, application is owned by only one team
  * Outside teams may submit pull requests or suggestions for change to the owning team but they cannot make the change themselves
* Ownership of code should not be a territorial thing
* Think of code as gardening, not policing 
##### Team Members Need a Team-First Mindset
* Team members should put needs of the team above their own, they should: 
  * Arrive for meetings on time
  * Keep discussions on track 
  * Encourage a focus on team goals
  * Help unblock other team members before starting own work
  * Mentor other team members
  * Avoid "winning" arugments and instead agree to explore options
##### Embrace Diversity in Teams
  * Research suggests that teams with more diverse backgrounds tend to produce more creative solutions more rapidly and tend to be better at empathizing with other teams' needs
##### Rewared the whole team, not individuals
* W. Edwards Deming suggested the "abolishment of the annual or merit rating and of management by objective"
* Rewarding individual performance tends to drive poor results and damanges staff behavior
* With team-first approach, the whole team is rewarded for their combined effort
* Even training budgets should be set on a team basis


#### Good Boundaries Minimize Cognitive Load
* It is important to limit cognitive load
  
#####  Restrict Team Responsibilities to Match Cognitive Load
* Teams can suffer from load in terms of domains of resonsibility, number of applications they need to operate and tools they need to manage
* With team-first approach teams responsiblities are matched to the cognitive load that team can handle
* Limit the size of the software system that a team is expected to work with
* Cognitive load as defined by John Sweller in 1988 as "the total amount of mental effort being used in the working memory"
* **There are three kinds of cognitive load**: 
  * Intrinsic - relates to aspects of the task fundamental to the problem space ("How do I create a new method?")
  * Extraneous - relates to the environment in which the task is being done ("How do I deploy this component again?")
  * Germane -  relates to the aspects of the task that need special attention for learning or high performance ("How should this service interact with the ABC service?")
* Organizations should mininize *intrinsic* load through training, good tech choices, hiring or pairing. They should eliminate *extraneous* load altogether - the boring or superfluous tasks or commands that add little value to retain in working memory and can often be automated. This leaves more space for the *germane* load which is where the "value add" thinking lies
* Most orgs add more teams to the problem hoping the cognitive load will be shared across the teams, instead the teams will suffer from communication and interaction strains ([Brook's law](https://en.wikipedia.org/wiki/Brooks%27s_law))

##### Measure the Cognitive Load Using Relative Domain Complewxity 
* Quick way yo asses cognitive load ask: "Do you feel like you're effective and able to respond in a timely fashion to the work you are asked to do?"
* Trying to determine the cognitive load using measures like lines of code, number of modules, etc is misguided
* We really care about domain complexity
* While no formuala, we can asses the number and realative complexity of the domains for which a given team is responsible

##### Limit the Number and Type of Domains per Team *******
* There is no final and for "Is this the right number and type of domains for this team?"
* Domains are not static and neither is the team's cognitiv capacity
* When in doubt about the complexity of a domain, always prioritize how responsible the team feels about it.
* Downplaying the complexity will only lead to failure
* To get started, identify distinct domains that each team has to deal with and classify them into: 
  * Simple - most of the work has a clear path
  * Complicated - changes need to be analyzed and might require a few iterations
  * Complex - solutsion require a lot of experimentation and sicovery
* First heuristic is to assign each domain to a single team
  * If the Domain is too large for a team instead of splitting responsibilities, first split the domain into subdomains and then assign each new subdomain to a single team
* Second heruistic is that a single team should be able to accomodate 2-3 "simple" domains
* Third heuristic is that a team responsible for a complex domain should not have any more domains assigned to them - not even a simple on
* The last heuristic is to avoid a single team responsible for two complicated domains
  * might seem feasable but in practice the team will behave as two subteams
* these are only recommendations and use these guidelines as a starting point
##### Match Software Boundary Size to Team Cognitive Load
* Provide a team-first working environment
* Minimize team distractions during the workweek by limiting meetings, reducing emails, assigning dedicated team or person to suppport queries and so forth
* Communicate goals and outcomes rather than how
* Increase quality of DX for other teams using your team's code and APIs through good documentation, good UX and other DX practices
* Use a platform that is explcitly designed to reduce cognitive load for teams building software on top of it
* Minimize cognitive load for others is one of the most useful heuristics for good software development
  
#### Design "Team Apis" and facilitate Team Interactions
##### Define "Team Apis" that include Code, Documentation and User Experience
* Building a Team API on how to interact with the team itself
* The Team API includes: 
  * Code
  * Versioning
  * Wiki and documentation: especially how-to- guides for the software owned by the team
  * Practices and Principles: the teams preferred ways of working
  * Communication
  * Work information 
* It shold explicity consider will other teams find it easy to interact with us
* How easy will it be for a new team to get on board with our code and working practices?

##### Facilitate Team Interactions for Trust, Awareness and Learning
* Must set aside time, space and money for people to learn from each other and develop professional competencies
* TWo ways to build trust: 
  * Consiously designed physical and virtual environment
  * Time away from the desk learning, at COPs, conferences etc. 
* Goves team a freer space to rehearse their interactions and communication methods

##### Explicitly Design the Physical and Virtual Environments to Help Team Interactions
* Office design should accomodate all of the following modes: Focused individual work, collaborative intra-team work and collaborative inter-team work
* Having spaces that clearly idicate the type of work going on helps to reduce interuptions
* Interesting case studies 51-57
  
#### Warning: Engineering Practices are Foundational 
* Teams must invest in CI/CD, Test first development and a focus on software operability and releasability

#### Summary: Limit Teams' Cognitive Load and Facilitate Team Interactions to Go faster
* Teams are more effective than groups of indiviudals
* Teams are small, stable and long lived
* Due to Dunbar's number there is an effecive upper limit on the cognitive load that single team can bear
* Teams need to own the system or subsystems that are responsible for -> teams working on multiple codebases lack ownership and the mental space to understand and keep the corresponding systems healthy
* People in a team-first org have the space and suppport to develop their skills and practices within the context of a team


## Part II : Team Topologies that Work for Flow 
### Chapter 1 - Static Team Topologies

* Focus on putting together team-first approach with long lived teams in a way that maximizes flow and respects the cognitive load of teams
* Consiously design team structures are "Team Topologies" - teams should be deliberately "placed" into orgs

#### Team Anti-Patterns
* **First pattern**: Ad hoc team design 
  * inclues teams that have grown too large
  * or in response to some outage or issues
*  **Second pattern**: Shuffling of team members
   *  Context switching is high
   *  Leads to extremly volatile teams assembled on project basis then dissband
*  Questions to ask include: 
   *  How can we reduce or avoid handovers between teams in main flow of change? 
   *  Where should the boundaries be in the software system in order to preseve system viability and encourage rapid flow?

#### Design for Flow of Change
* Spotify provides a good example of explicity organizational design
* Staff are organized into cross-functional "squads" each with a long term mission and with 5-9 people 
* Several squads that work on similar areas are collected into "tribes" - affinity grouping of squads
* Engineers with similar skills share practices through chapters
* Uses a "Guild" akin to COP that includes people from squads, tribes and chapters

##### Shape Team Intercommunication to Enable Flow and Sensing
* Traditional flow of change in an org not optimized for change sees groups owning different activities and handing over work to the next team. No info flows back to the original team
* We must ensure delivery teams are cross-functional, with all the skills necessary to design, develop, test, deploy and operate the system on the same team
  
#### DevOps and the DevOps Topologies
* Key contirbution of DevOps was to raise awareness of the problems lingering in how the teams interacted across the deliver chain
##### DevOps Topologies
* Created by Matthew Skelton in 2013
* Two key ideas
  * 1. There is no one-size fits all approach to structuring teams for DevOps success
  * 2. Several known topologies detrimental to DevOps success, in short no "right" way but several "bad" topologies

#### Successful Team Patterns
* A teams success lies in the surrounding environment, teams and interactions
  
##### Feature Teams Require High-Engineering Maturity and Trust
* Feature team is cross-functional, cross-component that can take a customer facing feature from idea all the way to production
* This team can only be successfull if they are self-sufficient and don't have to wait on other teams
* This team typcially touches multiple code bases which might be owned by different component teams
* If they don't have high-engineering maturity they might take shortcuts like not automating tests for the new user workflow. Overtime this leads to a breakdown of trust between teams as technical debt increases and slows down delivery speed
  
##### Product Teams Need a Support System
* Like a Feature Team but owns entire set of features for one or more products and they depend on infrastructure, platform, test envs, build systems and delivery pipelines
* Key for success with this team is external dependencies must be non-blocking meaning new features don't sit idle waiting for something to happen
* Non-blocking dependencies often take the form of self-service capabilities developed and maintained by other teams and can be consumed by product team when needed
* Creating a product team without a compatible support system creates more bottlenecks

##### Cloud Teams Don't Create Application Infrastructure
* Focus should be in providing high-quality self-services that match both the needs of product teams and the need for adequate risk and compliance management
* Split of responsibility between designing the cloud infra process (which is the cloud team) and the actual provisioning (the product teams)

##### SRE Makes Sense at Scale
* Site reliability engineering is an approach to the operation and improvement of software apps to deal with gloabl, multi-milliion-user systems
* Focuses on "error budget" - defining what is acceptable amount of downtime
* These folks need excellent coding skills and a strong drive to automate reptivie Ops tasks using code
* SRE teams are not essential they are optional

#### Considerations When Choosing a Topologies
##### Technical and Cultural Maturity
* Important to understand your teams capabilities to handle end to end delivery

##### Organization Size, Software Scale, and Engineering Maturity
* Choosing the most effective topology depends on situational context
* Low maturity teams will need time to acquire the engineering and product development catabilities required for autonomous end to end teams
* In this case more specialized teams are acceptable AS LONG AS they collaborate closely
* As size of org grows or software scales providing the underlying infra as platform as a service is 

##### Splitting Responsibilities to Break Down Silos
* One operation breakdown  is separating database dev from database admin
* All examples mentioned highlight the importance of thinking about teams' capabilities (or lack of) and how that causes dependencies between teams

##### Dependencies and Wait Times between Teams
* To optimize teams for flow you must track and detect wait times between teams
* Dominica DeGrandis of *Making Work visible* suggests using a Physical Dependency Matrix or dependncy tags
* There are three different types of dependencies: 
  * Knowledge
  * Task
  * Resource
* Alerts and thresholds in the tool used to track dependencies should be setup and when threshold is too high adjustments in the team design should be made

#### Using DevOps Topologies to Evolve
* Anti-pattern is a separate isolated DevOps team without any collaboration

#### Summary: Adpopt and Evolve Team Topologies that Match Your Current Context
* Creating new team reactively is near sighted
* You must take into consideration technical and cultural maturity, org size, scale of software, engineering disciple or inter-team dependencies
  

### Chapter 5: The Four Fundamental Team Topologies
* Stream Aligned, Enabling team, Complicated sub-system team and Platform team
* When used with care these are the only for team needed to build and run modern software
* When combined with effective boundaries and team interactions these team types are a powerl template  
* These type should act as magnets and teams should move toward one of these four poles
* A large or mid-sized org might have one ormore teams of each fundamental topology - multiple stream aligned teams are the starting point

#### Stream-Aligned Teams
* A stream is a continuous flow of work aligned to a business domain or organizational capability
* Aligned to a single valuavle stream of work; single product or service, set of features a single user journey or a single user persona. 
* They are empowered to build and deliver customer value quickly and independently as possible without requiring hand-offs to other teams
* Primary TEAM type in an org and the purpose of the other teams is to reduce the burden of the stream-aligned team
* Enabling team assist and unblock
* Platform team reduces cognitive load for stream-aligned team by off-loading lower level detailed knowledge like provisioning, monitoring etc
* Stream-aligned team is closer to the customer and able to quickly incorporate feedback
* Different streams can co-exist in an org
  * Customer streams, business streams, geography streams
* Team is funded as a long term team
* This idea is in stark contrast with traditional work allocation
* You build it you run it
* Amazon two pizza people rule is an example of stream-aligned teams - substantially independent, have ownership over service and responsibility for runtime

##### Capabilities within a Stream-Aligned Team
* Inlude: Design and arch, dev and coding, infra and operability, metrics and monitoring, product management and ownership, testing and QA and user experience

##### Why Stream-Aligned Team, Not "Product" or "feature" team? 
* Aligning  with a stream helps to reinforce a focus on flow at the org level

##### Expected Behaviors
* Produce steady flow of feature delivery
* quick to course correct based on feedback 
* experimental approach to product evolution
* minimal (ideally zero) hand-offs of work to other teams
* must have time and space to address code quality changes
* proactively reaches out to supporting teams
* members in team feel they are on the path to acheiving autonomy, mastery and purpose

#### Enabling Teams
* Contains specialists in a given tech domain and help bridge the capability gap
* These teams cross cut into stream teams and have required bandwidth to research, try out options and make informed suggestions
* Have strongly collaborative nature
* Thrive to understand the problems and shortcomings of stream-aliogned teams
* Actively avoid becoming "ivory towers" of knowledge
* Servant leadership
* End goal is to increase the autonomy of stream-aligned teams by growing their capabilities
* Oftan focus more on buid engineering, CI/CD, deployments or test automation

##### Expected Behaviors
* enabling team stays ahead of the curve in keeping abreast of new approaches, tooling and practices 
* Acts as a messanger of both good news and bad which helps with management of the tech lifecycle
* Promotes learning not only inside the enabling team but across stream-aligned teams as curators that faciliates appropriate knowledge sharing
* Should only be expected to work with stream-aligned teams for a few weeks or months sharing the knowledge and then moving on to another team
* Small long lived team of group of specialists focused on building awareness and capability for a single team

##### Enabingteam vs COP
* They exist for different purposes, COP is a diffuse group of people across several teams coming together to learn 

#### Complicated Subsystem Teams 
* Reponsible for building and maintaining a part of the system that depends heavily on specialist knowledge, to the extent most team members must be specialists in that area of knowledge
* Goal of team is to reduce cognitive load of stream-aligned team working on systems that include complicated subsystems
* Examples of complicated subsystem might be: 
  * mathematical modelm video codec, real time trade reconciliation algorithm
* This team should only be created only when a subsystem needs mostly specialized knowledge - decision is driven by cognitive load not perceived opportunity
* Should only have a few complicated subsystem teams per org compared to number of component teams

##### Expected Behaviors
* Off-load work from stream-aligned teams on complicated subsystems
* They prioritize work based on needs of stream-algined team work needs


#### Platform Teams
* Purpose is to enable stream-aligned teams to deliver work with substantial autonomy
* Provides internal services to reduce cognitive load that would be required from stream-aligned teams
* Knowledge best made available via self-service tools or programmable API that stream-aligned teams can easily consume
* "Ease of Use" is fundamental
* They should always regard themselves as pure service providers for the domain teams
* Examples could be provisioning a new server instance to providing tools for access mangement and security enforcement

##### Expected Behaviors
* Uses strong collaboration with stream-aligned teams
* Relies on fast prototyping techniques
* Strong focus on usability and realiability for their services
* Leads by example
* Understands that adoption of internal new services like new technologies is not immediate but evolves

##### Compose the Platform from Groups of Other Fundamental Teams 
* In large orgs a platform will need more than one team to build and run it

#### Avoid Team Siles in the Flow of Change
* Team with only one area of expertise should be avoided
* Work is never handed off to another team for a later stage in the flow

#### A good platform is "Just Big Enough"
* Platform must always serve the needs of consuming applications and services
* It provides standards, templates, APIs and well-proven best practices to allow dev teams to innovate rapidly

##### The Thinnest Viable Platform
* Simplest platform is a list on a wiki page
* Always make sure we have TVP 
  * It is a careful balance of keeping the platform small and ensuring the platform is helping to accelerate ans simplify software delivery

#### Cognitive Load Reduction and Accelerated Product Development
* "Simplify the developer's life" and reduce cognitive load is an essnential part of a good platform
* Most important part of the platform is that it is built for the developers

##### Compelling, Consistent, Well-Chosen Contraints 
* Must have a focus on Developer Experience 
* Should be a way for stream-aligned teams to give feedback to platform teams
* How-to-guides should be comprehensive but not verbose, up to date and focus on achieving specific tasks not documentating every last corner
* A good test for DevEx is how easy it is to onboard a new developer to the platform

##### Built on an Underlying Platform 
* Each platform is built on another platform even if the other platform is hidden or implied

#### Manage as a Live Product or Service 
* treat the platform as a live/production system and 2 use software-product-management and service-management techniques
* Need a product roadmap and user journeys of the developers 


#### Convert Common Team Types to the Fundamental Team Topoligies
* Companies would see huge benefit to mapping their teams to one of the four team types
* Change the teams agreement to adopt the purpose and behavior patterns of the topology
  
##### Move to Mostly Stream-Aligned teams for Longevity and Flexibility 
* These teams take ownership of slices of functionality or certain user outcomes
* Stream-aligned teams can expect to have cognitive load matched to their capcbilities

##### Infra teams to Platform teams
* Converting infra teams to platform teams enables rapid safe flow of change
* Not a simpole shift because the platform is managed as a product

##### Component Teams to Platform or Other Team Types 
* Dissolve or move to other team types

##### Tooling Teams to Enabling Teams or Part of the Platform
* Typically run better as enabling teams or as a platform team with clear well-informed roadmap

##### Converting Support Teams
* Support teams aligned to the flow of change and paired with one ore more stream-aligned Dev teams. Incidents are handled with dynamic "swarming"
* If dedicated support teams are needed they are aligned to the stream of change alongside a team or squad build the software

##### Converting Architecture and Architects
* Effective pattern for arch team is part-time enabling team 
* Architects should collaborate closely with users and engineers

### Chapter 6: Choose Team-First Boundaries
#### A Team First Approach to Software Responsibiliteis and Boundaries
* You must design your systems to be loosley coupled
* Use arch approaches that enable full owernship from design through to deployment

#### Hidden Monoliths and Coupling
* Need to be fully aware of how you break up a  monolith so it doesn't create a monolith somewhere else in the chain

##### Application Monolith (CFC HAS THIS)
* A Single large aplication with many dependencies and responsibilities that exposes many services and/or different user journeys

##### Joined-at-theDatabase Monolith
* Composed of several applications or services all coupled to the same database schmea making them difficult to chagen, test, and deploy separately
* Often arises when the business sees the database not the services as the core business engine
  
##### Monolithic Builds (rebuild everything)
* Uses one gigantic CI build to get a new version of a component. 

##### Monolithic (Coupled) Releases
* Set of smaller components bundled together into a "release"
* Sometimes this is a result of having a separate QA team

##### Monolithic Model (single view of the world)
* forces a single domain language and representation across many different contexts 
* Can be fine for small orgs but imposes contraints on arch and implementation when org grows

##### Monolithic Thinking (Standardization)
* One size fits all mentality
* Enforcing standardization upon teams actually reduces learning and experimentation, leading to poorer soluition choices

##### Monolithic Worksplace (Open-Place Office)
* The idea that offices should have a standard layout if prevelany, it can have a recurring negative effect on individuals

#### Software Boundaries or "Fracture Planes"
* Splitting software can reduce consistency between different parts and can lead to accidental data duplication 
* UX can be degraded 
* A *Fracture Plane* is a natural seam in the software system that allows the system to be slit easily into two or more parts
* Best to try to align software boundaries with the differnt business domain areas
* We can and should break down a monolith by combining different types of fracture planes

##### Fracture Plane: Business Domain Bounded Context 
* Most should map to business domain context 
* *Bounded Context* is a unit for partitioning a larger domain model into smaller parts each which represents an internally consistent business domain area
* Advantage of DDD include focusing on core complexity
* Business domain fracture plans aligns tech with business and reduces mismatches in terminology

##### Fracture Plane: Regulatory Compliance
* In highly regulated industries like finance and healthcare the regulatory requirements of provide hard borders

##### Fracture Plane: Change Cadence
* A fracture plane where different parts of the system need to change a different frequency

##### Fracture Plane: Team Location
* They'd argue for a team to communicate efficiently the options are full colocation or a true remote-first approach
* When neither are available you must split off the monolith into separate subsystems for teams in differnt locations

##### Fracture Plane: Risk
* Regulatory compliance is a specific type of risk
* Number of users might drive risk
* Splitting off subsystems with clearly different risk profiles allows mapping with technology changes to business appetite

##### Fracture Plane: Performance Isolation
* Splitting off such a subsystem based on particular performance demands help to ensure it can scale autonomously

##### Fracture Plane: Technology
* Tech is often (historically) the only type of boundary when splitting up teams
* Usually bad as they introduce more constraints and reduce flow rather than improve it
* That is because the separate teams are less autonomous 
* If splitting by tech first investigate whether alternative approaches could help increase pace of change

##### Fracture Plane: User Personas
* Products with tiered pricing, the subest is built in by design (high paying customers have access to more features)
* Sometimes Admins have more access

##### Natural "Fracture Planes" for your specific org or tech
* The litmus test for the applicability of a fracture plane: 
  * **Does the resulting architecture support more autonomous teams with reduced cognitive load?**
* Simple heuristic: 
  * **Could we as a team, effectively consume or provide this subsystem as a service?**

#### Summary: Choose Software Boundaries to Match Team Cognitive Load
* Stream-aligned teams should be responsible for a single domain
* We need to look for natural ways to break down the system that allow resulting parts to evolve as independently as possible
* Essential to make teams sized so that they can effectively own and evolve their software in a sustainable way