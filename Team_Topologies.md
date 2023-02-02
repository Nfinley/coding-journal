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

