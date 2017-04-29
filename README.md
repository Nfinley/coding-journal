#### Onboarding Guide  \(dev environment set up\) {#LnPWebApp-I.OnboardingGuide(devenvironmentsetup)}

_The following instructions will guide you through the dev environment set up to get the LnP website up and running on your local computer_

##### Install the following technologies: {#LnPWebApp-Installfollowingtechnologies:}

* GIT: For Mac users download [Xcode](https://developer.apple.com/xcode/), Windows users can download GIT[here](https://git-scm.com/download/win)
* [NodeJs](https://nodejs.org/en/download/)
* [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html) \(install most recent version\)

  * Set JAVA HOME PATH:

  ```
  export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_121.jdk/Contents/Home
  ```

* [Maven](https://maven.apache.org/install.html)

  * Set Maven PATH:

  ```
  export PATH=/Applications/apache-maven-3.5.0/bin:$PATH
  ```

##### AWS {#LnPWebApp-AWS}

_All code, server instances and pipelines are housed on AWS_

* Login to the [AWS console](https://aws.amazon.com/console/) using your computer login info 
* The current code repository for LnP is under CodeCommit



##### SSH key and config file setup {#LnPWebApp-SSHkeyandconfigfilesetup}

_Follow this _[_AWS article_](/h ttp://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-unixes.html)_ to setup an ssh key and register it  _

_Note_: you can add `UseKeychain yes` to the second line of the code above to avoid having to enter your password every time you commit changes to the repo.

##### Virtual Machine Setup {#LnPWebApp-VirtualMachineSetup}

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

[https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/)

Technologies used on the front-end:

1. The front end view library used is [React](https://facebook.github.io/react/)
2. The style framework used is [Material-UI](http://www.material-ui.com/#/)
3. The server is Java and Springboot

##### Run the LnP site locally {#LnPWebApp-VirtualMachineSetup}

1. Pull the lnp-mgmt repo from AWS
2. To start the server open the terminal and type `mvn spring-boot:run`
   1. This will also download all of the node packages
   2. To view the server rendering go to `localhost:8181` 
3. To start Webpack which bundles the react components and serves them to the browser run: `npm start` in a new terminal window
   1. To view go to `localhost:9191` 
4. ##### To view the current state of the Lnp-MGMT page visit: [http://mgmt-dev.lnpweb.com/](http://mgmt-dev.lnpweb.com/) {#LnPWebApp-VirtualMachineSetup}

#####  {#LnPWebApp-VirtualMachineSetup}

##### Other docs to get access to: {#LnPWebApp-Otherdocstogetaccessto:}

* [NIC Slack](https://nic-inc.slack.com/): Houses all internal team chats and communication
* Project Jupiter Onboarding documentation \(include link\)
* Confleunce: Houses all documentation for the project 
* [JIRA](https://jira.texas.local/): Houses all sprints and tasks are documented here
* Tempo: Houses all timesheet entries for the project and where PTO requests are entered



