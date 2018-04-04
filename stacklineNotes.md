# Stackline Notes

## Beacon Website

* Uses Fractal to organize structure which is organizing files by feature as opposed to file type

### Foundry 

* Internal Admin portal to monitor activity


### Questions
* How is the React app structured between beacon and atlas? 
    * Currently when running `yarn run compile` and make a change to the react code and go to `https://beacon-localhost.stackline.com/sign_in` it updates, however, if I go to `https://atlas-localhost.stackline.com/sign_in` it is not updated unless I run `yarn build` and then visit the link again. Both commands work for the `beacon-localhost`. 


* [ ] How is the backend structured?
    * [ ] Data beacon: Redshift => simple SQL query and can export to S3. Save to Redshift, process it and everything is send to Elastic Search, UI pull from elastic search
* [ ] Review VPN process
    * [ ] For Foundry - get Raj access
    * [ ] VPN chrome extension (RAJ)
* [ ] What is the Git workflow?
    * [ ] Web hooks for slack - only thing right now
    * [ ] Breakdown tasks to measurable
    * [ ] Opportunity to update process - PR requests
        *  Automate as much as possible
        * Linting/testing fail/pass
* [ ] JIRA/Trello?
    * Weekly meetings where Michael dictates flow
    * For now mainly fixing bugs
    * There is a JIRA system (ask Michael for access) - Micth to create JIRA tickets
* [ ] What is our tech stack?
    * React
    * Need for UI to run queries to see what is failing
        * See trends in when the jobs run (whether or not the job ran, data) - if run how many messages processed
    * .Net API
    * 
* [ ] Testing?
    * React - Jest/Karma
    * Backend - working on setting it up
* [ ] AWS account, services?
    * Using SQS, Redshift, Kinesis
* [ ] Docker containers?
* [ ] Get an idea of manual processes to see what we can automate

### Goals
* Have more tests - Focus on testing

## For Morgan

* What are you using for prototyping?
* InVision? 
* How does the workflow work betwen you and devs for new features? Hand off of assets
* Prototyping flow
* Accessbility?
* StyleGuide?

### Requests from Morgan

* She would ultimately like to have a living-styleguide
* Would like to focus more on accessibility
* Would like to create a better flow and collaboration between devs and design 



### Things to study/ To do

* [ ] Create a repo on AWS - DEV ONLY onboarding 

#### React
* [ ] Beacon Local


#### API Repo

* [ ] .Net CORE projects and how they work
 
#### Webcrawlers

* [ ] Webhooks with Slack
* [ ] ElasticSearch Client - Kibana
* [ ] Slack Bot integration

### Effeciency improvements

* [ ] Create Dev Onboarding including the API repo (to get up and running)



### AMS (Amazons marketing services)
* Headline search campaigns
    * Keyword driven (on blanket bids)
    * A little more expensive
    * Lower conversion rates
    * high competitive
* Product Detail Ads (Sponsored Products)
* Product Display Ads (don't use too much)
    * Keep daily budget low because they don't do that well
    * Can add coupons to these in order to boost value prop
* Takes a while for amazon campaigns to get imputted in the algorithms so you never want to end the campaign (set to infinity)
* Impressions: Amount of views ads get
* Aco$: Lower percentage better off you are, 50% and below is good but 30% or below is best
* ROAS (Return on Ad Spend): total sales and divided ad spen ($2 or above)
* aCPC: Cost per click (make sure they don't go through the roof)
* Amazon customers are generally value driven
* Typically people don't shop below the fold
* All CPC bids will add a 1, ie $17.21, idea is to keep a little more competitive

* BrandName-CampaignName-version

* Questions about AMS:
    * How long are campaigns? Infinity until cancelled
    * Setting budgets
    * How to set your CPC Bid?
    * What kind of visibility does the client has for the campaigns?
    * 


### NOTES

* Front-end uses [Mixpanel](https://mixpanel.com/help/reference/javascript) (product analytics)


### Software

#### Atlas
* Most recently refreshed - Atlas 2.0
* The Problem = only get access to a limited set of data through Amazon - no access to catagory level sales. Atlas attempts to solve this
* Access to competitive market data on Amazon platform
* REtail sales, pricing, and promotion
* Market Analytics
* Assesment of competitors
* Trends that could affect sales
* Using Amazon data using competitors data
* Product Map of all competitors (an Atlas)
* Standard View: 
    * Catagories (using bazean classifier)
    * Yin/Yang to come up with a way to re-catagorize to get more granular (neuro-network)
* Data aggregation
* Four Big PIECES: Catagory, Segments (custom group by - have to build this), Brands and Products
* Date Range Toggle
* Set own custom date range (Only available in Atlas)

#### Beacon
* Secondary product
* Track metrics that matter to the brands and what are driving the business
* Vendor and Seller Portals are what Amazon provides and ie General mills have to log into all of these portals to see their data
* Problem this solves: One place to login
* Beacon collects data from VendorCentral, Seller Central and AMS platform
* Very specified view of the clients
    * Have data like retail sales, ad sales, score and in-stock rate
* Retail Link - has Walmart information
* Reviews - Scraping from page
* Stackline creates Content Score
    * Title - how much space being used? %%
    * Bullet - how much space being used? %%
    * A Plus (type of template) - yes/no
    * Image - how many using and are they high res
    * Video - yes/no
* Feature ADD: Performance - user will be able to see what keywords they are using 
* Buy Box: The 3rd party sellers that are taking business away



Brands we work with?
* 320 ish brands - 60 are service clients
Two types of clients: 
    * Data-only: Just want data and use the interface
    * Service Clients: Run ad campaigns, an extension of the team