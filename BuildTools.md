# Build Tools and Pipelines

### Notes on what a build pipeline is, how it fits into development and examples of build tools


## What is a build pipeline AKA Continuous Delivery Pipeline (also CI/CD ipeline)?
* At a basic level a build pipeline is an automated manifestation of the process for getting your code into the hands of your users, or from 'check-in' to 'release'.
* * A CD pipeline delivers, as per business needs, **quality** products **frequently** and **predictably** from test to staging to production in an automated fashion.
* CDP is a software strategy that enables orgs to deliver new features to users as fast and efficient as possible. 
* Core idea is to create a repeatable, reliable and incrementally improving process to bring changes to the users
* The build pipeline breaks the software delivery process into stages, each aimed at verifying the quality of new features and prevent bugs from affecting your users. 
* It should provide feed back to the team and visibility into the flow of changes
* It is about enabling the ogranization to bring new features to production, one by one quickly and reliably
* Allows teams to ship features in a secure, preditable and auditable way


### Typical Pipeline Steps

1. __Build Automation and Continuous Integration/Component Phase__
    *  This is the stage that build the source code that is passed to subsequent stages (generally programmed to trigger with a push to main branch)
    *  New features are integrated into the central code based on a continuous basis, built and unit tested
    *  Verified by code reviews, static analysis and unit tests
2. __Test Automation__
    * New version of app is rigoursly tested to ensure it meets all desired system qualities. 
    * May include different types of automared or manual activites 
    * Can run performance, integration and DAST (dynamic analysis security testing) 
3. __Deployment Automation__ 
    *  The automated deployment of the code to users. Can be staged initally released to a lower environment and monitored before being rolled out to another environment
    *  ZDD or zero downtime deployment is a must for deployment to prevent downtime for customers
    * Blue-Green deployment is popular ZDD where small *green* parts are deployed to cross-section of users. If things look good move everyone slowly to green from blue
   
## Provisioning and Configuration Management
* The pipeline is supported by platform provisioning and config management. 
* This allows teams to create, maintain, and tear down complete environments automatically at push of a button
* Automtated platform provisioning ensures all new features are deployed and tested against correctly configured and reliable environments    

## Shift Left
* The principle that refers to validations being pulled earlier in the pipeline. 

## Continuous Delivery vs. Continuous Deployment
* Continuous Delivery allows manual gates while CDeployment doesn't. Delivery requires more discipline and rigor since no human interaction

Sources: 
* [CD Pipeline](https://devops.com/continuous-delivery-pipeline/)
* [Atlassian Pipeline](https://www.atlassian.com/continuous-delivery/pipeline)


## Jenkins
### What is it? 
* Most popular self-Contained open source automation server which can be used to automate all sorts of tasks relating to building, testing and delivering/deploying software. 
* Built with Java
* Similiar to TravisCI

 * **[Jenkins DOCS](https://jenkins.io/doc)** 

## Bamboo (Atlassian)
### What is it? 
* CI/CD server from Atlassian that allows you to automatically build, integrate and test source code then prepare for deployment
* Integrates seamlessly with JIRA and Hipchat
* Tie automated builds, tests, and releases together in a single workflow
* **[Bamboo DOCS]((https://www.atlassian.com/software/bamboo)


## Webpack


## Docker


## Vagrant

## Kupernetes 