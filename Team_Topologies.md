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