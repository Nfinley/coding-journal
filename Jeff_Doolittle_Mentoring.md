# Mentoring w/ Jeff Doolittle

TECH LEARN: GOALS

1. High level design and architecture/System design
   https://www.coursera.org/specializations/software-design-architecture
1. Data structures and algorithms
   https://www.coursera.org/learn/data-structures/home/welcome
1. Diving deep into javascript
   https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd0044 (one option)

LEET Code

Find a mentor to help guide me as I learn (one on one help). Either through a program/course

How can I incorporate into my app and resonate

Jeff discussion:
12/5:

How do you
Can email anytime, with questions

He lives in Happy valley, near the city of Damascus
He works downtown Portland on the eastside Willamette
He has a 19 daughter in college, 17 son, 15 son both in high school still in California

# Session 1, December 5th, 2019

As I continue my software development journey I have found a need for advice and guidance in order to continue my technical and professional growth... enter [Jeff Doolittle](https://jeffdoolittle.com/). What drew me to reach out to Jeff, is his degree in transformational leadership, his tenure in the industry, his desire to help developers of all levels and to grow the whole person not just technical skills. What follows are my notes from my first conversation with Jeff.

## What is Software Architecture?

Software Architecture is a totally different realm of software development and really should be called Software Engineering. It is:

- A discipline, a mindset of an engineer who takes a long term view of a system
- The ability to look at a problem and design a system that can withstand the test of time
- Designing that long term, sustainable system _and_ creating and facilitating a process to implement the creation of your system design
- It is being a lion tamer, yes the lion could eat you (in this case the lion is the developer) but they respect the tamer

It just so happens that its Jeff's mission to evangelize how Software Architecture should be done, to help transform the industry, and find people who want to do it and do it well. Software Architecture is not just about programming, it's about understanding the whole picture including the user pain points and with that empathy. The software industry, in general, lacks emotional intelligence but if you possess it you can use these soft skills to your advantage and climb the corporate ladder(if that is your goal).

More to come on the definition of a Software Architecture.

## Where to start?

As we spoke my main question to him was "where do I start?". There is so much I want to learn and so much to learn that it can be paralyzing. He spoke about how when he first began his career there were new technologies coming out maybe every two months or so, and nowadays it is practically every week and soon it will be seconds. Point being you can't keep up and you have to learn how to learn not learn every new technology.

Back to "where do I start?" His answer:

> "You need to identify your North Star"

A North Star is your highest goal to attain, it is everything that guides you through your professional career and life, involving your family, and friends. It is not something that you will ever achieve because you should always continue to aim higher. When you think you found your North Star aim higher, and when you think you have found it again aim higher, rinse and repeat. However, this in itself can be daunting so you have to start somewhere, something that provides clarity.

I am not there yet but the way he phrased this and the passion he spoke with gives me hope that I can begin to find it.

On the path to finding it and during your career it is more important to what you say _no_ to than what you say _yes_ to.

## Homework, no Growthwork

> "The first law of thermodynamics, there is no value without sweat"

In other words, mentorship, just as most things worth anything in life is about putting in the hard work to get the most out of something.

Jeff considers himself to be a doctor diagnosing problems with systems, architecture, and processes. So my growthwork is as follows:

- Channel my inner pain investigator and put on my pain archeologist hat
- Then look to my current environment to see who is designing our architecture, who is responsible for it, and are we experiencing any areas of pain within the development and delivery lifecycle
- Take notes, what pain do I see? I must become a glutton for punishment
- Once a pain point is identified, rank it by effort, risk, and value

Pain is optional and the primary role of an Architect is to resolve pain.

#### Fun fact about Jeff

He wants to be his own real-life rock band, like Dave Groll. He already plays guitar, bass, piano and his next mission is drums.

---

Until next time... remember don't eat the lion tamer and do listen to the guitar genius [Tommy Emanuel](https://www.youtube.com/watch?v=S33tWZqXhnk)

# Session 2, Feb 21st, 2019

Agenda:

- CFC Pain points (As discussed in previous call observe pain points). See cfc_pain point doc

- Architecting my music application
  - Suggestions on how to start, I currently has started writing some lambda functions, I also have a basic flow but would love input
    -UML and Sequencing diagrams

What happen since we last talked?
Evaluated what is good between now and next time?
Interpersonal? Technical?

Not primary interest is consulting which this could be

- Super detailed would be consulting, then do this and this

Standards Adoption

- Do some research on the numbers that convey the reduction in defects in code reviews
- Doe some research on the cost of defects
- Defects caught on research before production - 10x difference between dev and prop
- **You want to get your team relentless committment to quality**
- If you can make case with data that says look we have to go fix this process
- Mentality shifts from Code review can do it, to we can't afford to do code review
- All other benefits like learning, all pale in comparison to defects introduced
- All on par with testing and do more testing
- Track current defect count, by quarter or sprint, be careful because you can game it with defects
- Then you are driving the defects with data
- Numbers that help answers questions for you
- Balance between code review and standards otherwise it is paralyzing

Keep up in more of the grand vision or strategy personally

- Personal Project

**I'm working on writing up my thoughts on teaching engineers to remain focused on design (why, what and who) instead of jumping so quickly to infrastructure, technology and implementation (how).** \*_Why --> what --> who --> when --> how much --> where --> THEN how_

- He tries to avoid infrastructre for as long as possible
- Software devs want to jump to the where and how way to quickly
- We need to focus first on the why, what and the who and the how much
- Distilling that down to less abstract - Where (AWS, Lambdas, etc) and How (specific details of implementation)
- Find a way to think about the margins in between them and how they interact
- Who are the users of the system (People, system components, actors services)
- Why? What are the uses cases that this fulfills
- How much - Load, scale, what quality metrics are going to matter, up time, what is resonanle
- And thought about what you are going to do when these questions change
- It is a Ying and Yang and you want to find that balance in the middle
- Once you have all of that you want to distill down to CORE USE CASES
- CORE USE Cases: Fundamental value that it provides
- Usually there are only a few that are core use cases

* Focus on design as an artchitect - making blueprints like an architect. We are not worrying about a concrete path
* The more you do this is creating standards for these kinds of things you can build up
* We need better standards as a software world - if we ask framers everytime how to build it it is a disaster
* Am I validating the design, does it make sense

- come up with model of relentless quality and defect count
- Slack he is building a communtiy to discuss architecture and problems, let's help everyone to help learn - START SHARING MY JOURNEY
- Send him deliverables of what we talked about and also research I find about the model I define for defect count in relation to velocity, code review etc

* Use Change Contaimnet - Not Encapsulation
* Don't just wrap something and say its encampsulated but think about what is going to change over time
* True encapsulation is the orchestartion of use case is outside the client application
* The client as a service does not have any dependencies on the the services

* Dont focus on Cloud or actual serice
* We ultimately want to create components that contain the areas of significant change
* The benefit here is that evetyhin we experience in the world uses component design
* House, cars, human body - each of these compontents uses the change contaimnent principle
* No rippling effect when you change something in one
* If you do it right you can create a system that can handle anything that the business cass can throw at it current, present, and future
* When you get really good at it you can do it in three-5 days
* He practices this all the time - there is no handwashing component when washing a hands - if a dev took it they would create a handwashing component
* Features are aspect of integration not implementing
* We are integrating hands, soap, faucet
* Features are emmergent properties
* Consiousness is an immergent property of complicated process

* Definetly try new things and expereiment but it is the larger context tha, don't get bogged down
* Design over Technology
* Technology needs to serve the design not the otherway around
* Love of the instrument - coinded by abhram maslo- summarized I have a hammer therefore everything is a nail
* For the most part consturction workers are not in love with their concrete but software devs are
* Customer may have requirements
* Gonna take time

According to the law of the instrument, “If all you have is a hammer, everything looks like a nail.”
