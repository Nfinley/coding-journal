# Stackline Notes

* additional notes found in [Opportunites section](stackline-opportunities.md) and [Bugs](stackline-bugs)

## Beacon Website

* Uses Fractal to organize structure which is organizing files by feature as opposed to file type

### Foundry 

* Internal Admin portal to monitor activity


### Questions
* How is the React app structured between beacon and atlas? 
    * Currently when running `yarn run compile` and make a change to the react code and go to `https://beacon-localhost.stackline.com/sign_in` it updates, however, if I go to `https://atlas-localhost.stackline.com/sign_in` it is not updated unless I run `yarn build` and then visit the link again. Both commands work for the `beacon-localhost`. 
    * How to get Beacon localhost up and running?

* How do we manage privledge users amnd super users? (IN FOUNDRY)
* Review Foundry and what each Prod, Dev, localhost mean? 
* Project/Task flow JIRA? ? We will start using it
* How are front-end sessions managed? Are we clearing data on log-out or between tabs? Should we be? Is that a concern?
* Is there a default brand that is populated into entity on load? Looks like honest kitchen but the id is -1?
* Code deployment process? Pipeline, dev, stage, testing, prod?
* How do you feel about comments in the code if it helps to understand what is happening?

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

### Web Crawlers (Data Collection)
* Job Manager (ECS Task) - sends messages to the queue
    * Query into Redshift that generates a JSON which will then be put into the queue to be consumed by the crawler
    * This is a custom proxy server written by Raj
* Crawlers listen to the queue and then the data ends up in S3 or Redshift (saving raw data to S3 and parsed to redshift)
* Crawl.crawSchedule is
* There are two clusters: Storage(Read) and Compute (Read &Write)
* Content Raw is GZIP and base-64 encoding
* Content Parsed is what we save in Redshift
* We Crawl: 
    * Reviews
    * Content
    * Buy Box: (Seller ID, Price) (the current winner of all the sellers)
    * Sales: Comes from VendorCentral
    * FPR: First Page Results (crawl 1million keywords)
    * USR: Universal Search results: crawl all pages, only get all the possible products returned. Generate the inventory for the client
    * Offers: Helps with price tracking it returns all of the sellers not just buy box
* Clean processed data that is put into Redshift is taken by Sean and published in ElasticSearch

### Things to study/ To do

* [ ] Look at using `this` to declare/bind variables in react
* [ ] Go through React Tic Tac Toe Tutorial
* [ ] Read about Object Desctructuring
* [X] Create a repo on AWS - DEV ONLY onboarding 
* [ ] Build Basic C# .NetCore project (Debug)
* [ ] ECS tutorials (SQS jobs)
* [ ] Dynamo DB tutorial (within console)
* [ ] ElasticSearch Client - Kibana

#### React
* [ ] Beacon Local


#### API Repo

* [ ] .Net CORE projects and how they work
 
#### Webcrawlers

* [ ] Webhooks with Slack
* [ ] ElasticSearch Client - Kibana
* [ ] Slack Bot integration




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
* Scrapping data on Amazon daily
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


### Amazon 101
* Vendor Central
    * All Data for SKUs
    * Feeds into Beacon
* AMS
    * amazon search 
    * We manage the search for clients
    * Also feeds into Beacon
* AMG - Amazon Marketing Group
    * Custom Ads would be AMG
* Usually when a new client is on boarded they give us access to vendor central and AMS
    * We load everything into Beacon
* Foundry - You can see everyone's Beacon account
    Data for "Share of Shelf" and "Share of Voice" is in Foundry

### BI (Barry and Peter)
* Data flow correctyl into Beacon
* Beacon - client specific (Vendor Central, AMS and Seller central) they download the content
* Barry works with Esteban/Alex to ensure all data is correct
* Premium allows year data
* They sit somewhere between engineering and product
* Do a lot of reporting (Peter), also bidding tools to help with marketing
* Audit all the sales data to make sure there is consistency
* Ingesting most of auditing time on Beacon since it
* Would use an API but data quality is bad and don't release certain data

* Day to Day?
* Software used?
    SQL, EXCEL, and a little Python (for regex)
* Peter - Came from Digital marketing (ads words), also did finance where to invest money
* Barry - used to work at Packar (build semi trucks) for 6 years. Business analytic roles (Data auditing, analytics)

The summer meltdown tour in Darrington
Big Gigantic, The dip 