# AWS Training on Linux Academy


* Cloud Terminology
    * High Availability: Always available across all devices
    * Fault Tolerant: Automated workarounds if something fails. If something were to go wrong files are still available because they are backed up. Never be deleted
    * Scalabilitly: Ability for cloud system to quickly increase in size based on demand
    * Elasticity: Ability for a cloud system to both increase or decrease based on demand
    * Instance: A single iteration of an EC2 server
    
## I. AWS Concepts Course
### What is the cloud?
* It is a computer that is somewhere else
* More like a data center
* AWS, iCloud, DropBox all have data centers that tore content
* Iaas - infrastructure as a Service
* AWS is a Cloud services provider

### How is cloud beneficial?
* To use for backups and sharing (across multiple devices)
* Cost effective because you can scale up or down quickly and cost effectively
* With cloud servers you only leasing hardware on On-demand basis
    
### Understanding VPCs
##### What is a VPC?
* Virtual Private Cloud is a VPC [ImageLink](http://res.cloudinary.com/thefinleycode/image/upload/v1516068016/VPC_Example_aszkd2.png)
* Facebook example, My Homepage is a VPC, and inside your VPC you can put an AWS EC2 or db and you can put a level of security over your VPC

### Understanding EC2
##### What is an EC2?
* Elastic Cloud Compute
* Equivalant to a computer sitting in front of you but is more like a server: It has a CPU, OS, Hard Drive
* Think of it as a virtual computer that you can use for whatever you like
* Good for any type of "processing" activity. Ie: Encoding, transcoding
* Netflix uses AWS (biggest user of AWS)
* When A user clicks play it must go to the S3 bucket to retrieve code and serve to Ec2, the ec2 must then encode or transcode the content and make it available downstream

##### Uses
* Common Use: 
    * Web Hosting server, contains all files and code necessary 
    * Encode, transcode

    
### Understanding RDS
* RDS is an AWS provisionedd database service. Used for things like storing customer account information and cataloging information
##### Uses:
* Comomon Use: 
    1. Customer Account info
    2. Inventory catalog (ie netflix content)
    
### Understanding S3 (simple storage service)
* Amazon s3 is a large Unlimited Storage Bucket where you can put music, pictures, documents, etc. 
* Will alwasy have high availability of your files. 
* Dropbox is basically a nice UI of a S3 bucket

##### Uses: 
  * Common use: Mass storage and long-term storage
  
### Understanding AWS Global Infrastructure
* Each region has availability zones, These zones indicate how many physical data centers are available
* Each data center in the zone is spread across from each other maybe 20-100 miles to protect from disasters and maintain high availability
* Inside these data centers are the servers where you add your S3 or EC2

## II. AWS Essentials

### IAM (Identity and Access Management)
* What is IAM? Is it where you manage your AWS users and their access to AWS accounts and services
* By default any new users you create in the AWS account are created with no access to any AWS services (except the ability to log in)
* Permission must be given to grant access
* When you sign up for AWS that is the root user
* Common Use: Users, Groups, IAM Access Policies, and Roles

##### IAM Users & Policies
* You can assign each user to specific policies, ie: S3 Bucket
* IAM Policies are how you grant user access to servicesm and resources

#### IAM Roles
* You can grant roles to other AWS services and that services acts as a user and is given rights to use other services through that role

### Virtual Private Cloud (VPC)
* Private sub-section of AWS that you control
* Amazon definition: Let's you provision a logically isolated section of AWS where you can launch AWS resources in a virtual network that you define.
* Full control over the resources you place inside of your VPC including IP address range, creation of subntes and config of route tables and network gateways

#### Internet Gateways
* Combination of hardware and software that privides your private network with a route to the outside world
* Entryway into your network
* It is a redundant and highly available VPC component that allows communication between instances in your VPC and the internet. Imposes no availability risks or bandwidth contraints on your network traffic
* **ONLY ONE** IGW can be attached to a VPC ata time
* An IGW cannot be detatched from a VPC while there are active AWS resources in the VPC (Like ec2 or s3)

#### Route Tables (RTS)
* Table contains a set of rules, called routes, that are used to determine where network traffic is directed
* Provides the connection between various resources inside of your VPC
* Unlike an IGW, you can have multiple "active" route tables in a VPC

#### Network Access Control List (NACLs)
* Optional layer of security for your VPC that acts as a firewall controlling traffic in and out of one or more subnets
* Default NACLs allows all traffic
* For additional security you need to edit or add Inboud/Outbound rules 
    1. Rules are evaluated based on rule # lowest to highest
    2. The first rule evaluated that applies to the traffic type gets immediately applied and executed regardless of the rules that come after
* A subnet can only be associated with **ONE** NACL at a time
* Allows or denies traffic from entering a subnet. However, once inside a subnet, other AWS resources may have additional layers of security

#### Subnets
* Definition:  Sub-section of a network
* You can add one or more subnets in each availability zones
* A subnet must be associated with a route table
* Public subnet **HAS** a route to internet
* Private subnet **DOES NOT** have a route to the internet

#### Availability Zones
* Distinct locations that are engineered to be isolated from failures in other Availability zones. By launching instances in separate AZ, you cn protect your applications from the failure of a single location
* High Availability: Creating your architecture in such a way that your 'system' is always available
    * "I can always access my data in the cloud"
    * "My website never crashes and is always available to my customers"
* Fault Tolerant: Ability of your 'system' to withstand failures
    * "If something in my system fails, it can repair itself"
    
### S3 (Simple Storage Service)    
* [IMAGE OF S3](http://res.cloudinary.com/thefinleycode/image/upload/v1516467085/AWS-S3_cxogbc.png)
* Definition: Is an online bulk storage service that you can access from almost any device
* Can store any type of file

#### Buckets: 
* Bucket names must be unique across ALL of aws, they must be 3 to 63 characters in length, and contain lowercase 
* Root level "Folders" are buckets
* Any 'sub-foler' you create is refferred to as a folder
* You can use S3 buckets to host static sites

#### Storage Classes
* A storage represents the classification assigned to each object
* Available storage classes are: 
    * Standard: 
        i. Designed for all purpose
        ii. Most expensive
        iii 99.9999999999% durability
        iv. 99.99% object availability
    * Reduced Redundancy Storage (RRS):
        i. Less expensive
        ii. Designed for non-critical, reproducible objects
        iii 99.99% durability
        iv. 99.99% object availability
    * Infrequent Access (S3-IA):
        * Designed for objects you don't access frequently, but must be immediately available when accessed
        * iii 99.99999999999% durability
        * iv. 99.90% object availability
        * Less expensive than RRS
    * Glacier: 
        * Cheapest
        * Large bulk files, like medical records that they may keep for years per regulations
        * Could take up to a few hours or a day to retrieve
        * iii 99.99999999999% durability
* Each Storage class ha varying attributes things like: 
    * Storage cost
    * Object availability
    * Object durability
    * Frequency of access
* All objects assigned a storage class (Standard is default)     
* If you want to change the class you must set the proper class on upload  or change in permissions
* If you want to change to Glacier class you have to use object Lifecycles and may take up to 1-2 days to take effect


#### Objects:
* Files stored in a bucket are objects
* Minimum size of an S3 object 0 bytes
* Object Durability (Fault Tolerant): 
    * Percent over a one year period that a file stored in S3 will NOT be lost
    * For object durability of 99.99999999999% means there is a 0.0000000001% change of a file in S3 being lost in a year
* Object Availability: 
    * Percent over a one year time period that a file stored in S3 WILL be accessible
    For object availability of 99.99% that means there is a 0.01% change you won't be able to access a file store in S3 in a year
    
#### Object Lifecycle:
* Set of rules that automate the migration of an objects storage class to a different storage class
* Using a lifecycle policy you can automate the process of changing the files storage class to mee usage needs and keep costs low
* Lifecycle policies can be applied to entire bucket, specific object or folder
* You can always delete a lifecycle policy or manually change the storage class
    
#### S3 Permissions
* Allow you to have control over who can view, access, and use specific buckets and objects
* On bucket level you can control `List = who can see the bucket name`, `Upload/Delete`, `View Permissions`, `Edit Permissions`
* On file level for each file you can control `Open/Download`, `View Permissions`, and `Edit Permissions` 
* Bucket level permission are generally used for 'internal' access control
* You ca share specific objects (via a link) with anyone in the world.

#### S3 Versioning
* Versioning is feature that keeps track of and stores all old/new versions of an object
* It is either ON/OFF
* Once ON you can only suspend
* Versioning can only be set on the bucket level and applies to all objects in the bucket 


#### Regions: 
* You must select a region when you create a bucket, meaning any data you upload to the S3 bucket located in data center in that region
* Select region closes to you

#### Pricing: 
* Charged per GB used
* [Price](https://aws.amazon.com/s3/pricing/) per GB varies on region and storage class

### Elastic Compute Cloud (EC2)
* Think of it as your basic desktop computer
* Provides scalable computing capacity in the AWS cloud. Eliminating need to invest in hardware up front, so you can develop and deploy apps faster. 
* You can use EC2 to laungh as many or few virtual servers, configure security, networking and manage storage.
* It is scalable and can easily grow 
* Reduces need to forecast traffic

#### Purchasing options of Ec2
1. On Demand: 
    i. most expensive 
    ii. most flexible
    iii. only charged when instance is running and billed by hour
    iv. you can provision/terminate an on-demand instance at anytime
2. Reserved: 
    i. Allows you to purchase and instance for a set time period or 1 or 3 years
    ii. allow for a significant price reduction 
    iii. once you buy instance you own it for selected time period and responsible for entire price regardless if you use it
3. Spot: 
    i. Allows Amazon to sell unused instances for short amount of time for substantial discount
    ii. spot prices fluctuate based on supply and demand
    iii. You place a bid for an instance and it is provisioned for you when the prioce is equal to or less than your bid price. Then it terminates when spot price inscreases above bid
    
#### AMI (Amazon Machine Images)
* Preconfigured package required to launch a virtual server, which includes operating system, software package and other required settings
* Three basic components: 
    1. Root Volume Template
        * Operating System
        * Application software
    2. Launch Permissions
    3. Block Device Mapping
        * EBS (hard drive mapping)
    
* Three different types of AMI's: Community (free), AWS Marketplace (paid) and My AMIs(those you create)
* The term 'create image' from the AWS CLI,  Creates an Amazon EBS-backed AMI from an Amazon EBS-backed instance that is either running or stopped.

#### Instance Types
* Is the CPU (Computer power) of your instance
 
Types: 
1. Family: categorizing based on what they are optimized to do
2. Type: A sub-category for each family
3. vCpu: The number of virtual CPUs the instance type uses
4. Memory: Amount of RAM instance type uses
5. Instance Storage: Local instance storage volume
6. EBS-Optimized Available: Whether EBS is an option for instance type 
7. Network performance: rating based on its data transfer rate (bandwidth capability)

#### EBS (Elastic Block Store)
* EBS is a storage volume for an EC2 instance (think of it as a hard drive)
* Data stored on EBS volumes are automatically and redundantly stored in multiple physical volumes in the same Availability Zone as part of the normal operations of the EBS service and at no additional charge.
* IOPS = Input/Output per second
    * The amount of data that can be written to or retrieved from EBS per second
* You can take EBS volumes and swap them between EC2's

* Snapshot: Is an image of an EBS volume that can be stored as a backup or used to create a duplicate
    * To restpre a snapshot you need to create a new EBS volume  using the snapshot as its template

#### Security Groups
* Security on the instance level that allow/deny traffic very similar to NACL's and is a firewall
* When launch an instance you associate one or more security groups with the instance
* When you create a new Security group all traffic is denied inboud unless a explicit rule
* **BEST PRACTICE:** only allow traffic that is required

#### IP Addressing
* Providing an EC2 with a public IP address
* IP address is an instances address on the network (your home address)
##### Public vs. Private Addresses:
Private IP Address: 
* By default all EC2 have a private IP address
* Private IP allow for instance to communicate with each other as long as they are locating in the same VPC

Public IP Address: 
* EC2 Instances can be launched with your without a public IP address
* Public IP addresses are required for the instance to communicate with the Internet
* Default Ec2 has a public IP address

#### Provisioning an Instance
1. Select an AMI
2. Select an instance type
3. Configure Instance Details
    * Code below will install Apache Web server. It will also allow to test internet connectivity of EC2 instance
    ```
        #!/bin/bash
        yum update -y
        yum install -y httpd
        service httpd start
    ```
    * Make sure to select a public subnet if you want it to connect to internet


### RDS And DynamoDB 
* RDS is a relational DB: "SQL"
* Dynamo is a non-relational DB: "No-Sql"
#### RDS (Relational Database service)
* Web service that makes it easier to set up, operate, scale a relational database in the cloud. Provides cost-effienct and resizable capacity
* Includes: MariaDB, PostgresSQL, Oracle, Amazon Auroa
* Stores related data in tables using column and rows
* used for structured data - like contact list

#### Dynamo DB
* Fast and flexible NoSql database service for all applications that need consistent, single-digit millisecond latency. Great fir for mobile, web, gaming, ad-tech, and IOT.
* Stores related dat in JSAON-like name-value documents
* Typically used for non-structured data such as cataloging documents

 #### Pricing
 * [Link](https://aws.amazon.com/dynamodb/pricing/)
* Used SSH  Tunneling from Internet -> internet gateway -> route table -> NACL -> EC2 -> route table -> RDS


### SNS (Simple Notification Service)
* Aws service that allows you to automate the sending of email or text message, notifications based on events that happen in your AWS account
* Two types of clients - publishers and subscribers - also referred to as producers and consumers
* Publishers communicate asychronously with subscribers by producing and sending messages

BASICS:
* Topics: How you label and group different endpoint that you send message to
* Subscriptions: The endpoints that a topic sends messages to (ie. the email address or phone number of sys admin)
* Publishers: The human/alarm/event that give SNS the message that needs to be sent

### CloudWatch
* CloudWatch is a service that allows you to monitor various elements of your AWS Account
* Use CloudWatch to collect and track metrics. 
* Can monitor: 
    * Ec2: Cpu utilization, Status checks, disk read/writes
    * S3: Number of Objects, bucket size
    * Billing: monthly bill
* [Pricing](https://aws.amazon.com/cloudwatch/pricing/)

### Elastic Load Balancing
* An ELB evenly distributes traffic between EC2 instances that are associated with it
* Increases the fault tolerance of your apps
* It detects unhealthy instance and routes traffic only to healthy instances
* ELB are **NOT** available on free tier
* Charged per hour or partial hour the load balancer is running and charged per GB of dta transfered through the load balancer
* Security: You need to make sure you have the correct security groups set up to allow the proper traffic based on what the load balancer is set to receive
* Proper ports must have allow rules ie: HTTP/PORT 80
* Health Checks are required to ensure ELB's do not serve traffic to unhealthy EC2's

### Auto-Scaling
* Auto-Scaling automates the process of adding or removing EC2 instances based on traffic demand
* Will auto terminate or create EC2 based on your traffic
* It is a service and can span multiple availability zones and subnets but will always remain in your VPC

#### Components
1. Launch Config = Needs to know what type of AMI, the Ec2 Template used
    i. Make sure public IP address will be assigned
    ii. Bash Script to test http (See above)
    iii. When selecting a security group make sure it has the port open that you need
2. Auto Scaling Group = all the rules and settings that govern when an Ec2 server is auto added or removed
    i. Make sure to attach your load balancer within the ADVANCED DETAILS section

### Route 53
* Configure and manage web domains for websites or application you host on aWS
* Performs three functions: 
    1. Domain registration
    2. Domain Name System (DNS) service - translates friendly domain names like example.com into IP Addresses like 192.0.2.1. 
    3. Health checking - sends automated requests over the Internet to your application

* A DNS server is a database of website domains and their corresponding IP addresses. 
    * Web browsers send DNS Servers domain names and they send correct IP addresses so they can find the server on the internet
    * DNS server are used to translate common language web domains into IP addresses
* Summary: Route 53 Manages domain names and DNS records

* When configuring Route 53 and creating DNS RECORD SET you must: 
    1. Create two type A records one for www.name.com and one for name.com
    2. Then Route records to ELB by selecting "Alias" and attach the Elastic Load Balancer 


### Lambda 
* Lambda is serverless computing, it is serverless compute platform. It is next generation of cloud computing that will replace Ec2 instances (for the most part)
* Is a compute service that allows you to run code without provisioning or managing servers
* It executes code when needed and scales automatically 
* You only pay for the compute time you consume, no charge when you code is not running
* No administration: AWS Lamdba runs your code on a high-availability compute infrastrcuture and performs all of the admin of compute resources including server and OS system maintenance, provisioning, scaling, monitoring and logging
* Currently supports, Node.js, C#, JAVA and Python
* You are charged based on execution requests and execution duration
* [Pricing](https://aws.amazon.com/lambda/pricing/)




## III. AWS Solution Architect Certification Course

**Topics to REVISIT**
1. EBS Storage (IOPS and types)
2. EC2 Placement Groups
3. Shared Responsibility Model
4. Elastic Load Balancers
5. Auto Scaling Groups
6. Creating a load balancer, a launch confg and an auto scaling group to work properly
7. Bastion Host with Nat Gateway
8. S3 storage classes (Standard, RRS, Infrequent ACCESS, and Glacier)
9.  Gateway-Cached and Gateway-Stored volumes (Storage transit serivces)
10. SQS and decoupled architecture

### IAM
####STS

* STS - Security Token Service - Used to generate temporary credentials to grant access to your AWS Resources
* When requested through an STS API credentials are returned with three components: 
    * Session Token
    * An Access Key ID
    * A Secret Access Key
* Don't have to manage 
* Used for Identify Federation, Cross-Account Access, and Roles for EC2 

**NOTE: STS API CALLS are important 
AssumeRole
AssumeRleWithWebIdentity
AssumeRoleWithSAML
GetFederationToken
GetSessionToken

#### IAM API KEYS
* Required to make programmatic calls to AWS from the: 
    * CLI
    * PowerShell (windows)
    * AWS SDKs
    * Direct HTTP calls using the APIs
* Only available ONE time when a new user is create OR when you reissue a new set of keyss

### VPC
* Virtual private networks can span multiple availability zones in a only ONE region
* Whatever you set the instance tenancy as all instances created with default to that tenancy

### Internet Gateway
* 1st access point to VPC
* Has to exist in order for AWS resoursces to connect to open internet

### Route table
* Direct flow of traffic and can direct to public or privet subnets

### NACL (Network Access Control lists)
* Allow or deny traffic traveling in and out bound to subnets
* Optional layer of security
* Stateless - have to explicitly set in bound and out bound
* Import to know that Outboound traffic for SSH is not allways port 22 so you need to set outbound rules to either allow 1024-65535 or **ALL TCP** 
* RDS uses RDP as the traffic TYPE


### Security Groups
* Best practice is to only ALLOW ONLY traffic that is required
* Stateful  - Meaning return/outboud traffic requests are allowed regardless of rules
* All rule evaluated before deciding to allow traffic
* No Deny rules for security groups
* On an instance level

### EC2
#### AMI's
* HVM (Hardware Virtual Machine): Provides ability to run OS directly on top of virtual machine without modification
* PV AMIs (Paravirtual): Does not have explicit support for virtualization

**TWO IMPORTANT CLI COMMANDS**
1. `curl http://169.254.169.254/latest/user-data` displays bootstrapping commands
2. `curl http://169.254.169.254/latest/meta-data` display AMI, instance type, etc

* G2 instance type: Graphics/General Purpose GPU
    * Used for: Video encoding, machine learning, 3D application streaming
 * D2 instance type: Dense Storage
    * used for: File servers, Data warehousing, Hadoop
 * C4/C3 instance type: Compute Optimized
    * used for CPU intense applications/DBs
* All instances you provision inside of a VPC have a tenancy attribute: They can be either default (shared hardware), dedicated (single-tenant hardware) or host (instance runs on a dedicated host with configs you can control)
#### EBS Volumes

* EBS is network attached 
* Max volume size is 16TiB
* Three Types: 
     * General Purpose SSD: Used for dev/test environments and smaller DB instances, has burstable IOPS up to 10,000 IOPS (short duration of time)
     * Provisioned IOPS SSD: Used for mission critical low-latency applications that require sustained IOPS performance and large DB workloads and has sustained IOPS. Can provide up to 32,000 IOPS
     * Magnetic: Used for workloads where performance in not important or data is infrequently accessed (not used much)
     
* Can terminate on delete or keep them     

#### Instance Store Volumes
* They are ephemeral data and attached to the hard drive and only exist for the duration of instance (data is gone)

#### Snapshots of Volumes

* Incremental in nature and only charged for difference in snapshot data
* Important note: Increases Durability 
* Snaphsots should be created during off peak hours as it slows performance

#### EC2 Placement Group
* Cluster of instances within same availability zone
* Used for applications that need extremely low-latency between them
* All EC2 must be provisioned within in the placement group when creating it
* You cannot move an EC2 instance already running into a placement group
* Instances must have a 10GB network speed in order to take advantage of placement group

#### Elastic File System (EFS) - Elastic and sharable
* Storage capacity is elastic 
* Fully-managed by AWS
* Sharable amonst many EC2 instances
* Supports the Network File System version 4.0 and 4.1 (NFSv4)
* Best performance when useing an EC2 AMI with Linux kernel 4.0 or newer 
* Can scale to petabyses while maintaining low-latency and high levels of thoroughput
* Security: Can encrpyt 

###Cloud Watch
* Centralized loggind and performance for AWS resources

### Cloud Trail
* Api logging services that logs all API calls made to AWS


### Advanced Networking
* Using Elastic Load Balancer and Auto Scaling Group
* For architecture to be considered highly available and fault tolerante - it **MUST** have and ELB traffic to and ASG with a min of two instances located in separate availability zones

####Classic Load Balancer
* Best used when all instances have the exact same data 
* They are designed for simple balancing of traffic
* No granular routing "rules"
 
 #### Application Load Balancer
 * Designed for complex balancing of traffic to multiple EC'2 using "rules"
 * Host based rule: based on the header of HTTP
 * Path-based rules: based on the URL of the HTTP header
 
 
 ### VPC Network for Increased Security
 #### Bastion Host
 * Is an Ec2 instance that lives in a public subnet and is used as a "gateway" for traffic in private subnets
 * Criticial strongpoint of a netowrk 
 
 #### NAT Gateway
 * Designed to provide EC2 instances that live in a private subnet with a route to the internet
 * A bastion host is used is used as a "gateway" for traffic that is destined for instances located in a private subnet, whereas a NAT gateway provides instances in a private subnet with a route to the internet.

### S3
* Always create S3 buckets in a region where you are serving your customers
* Objects stay with an AWS region and are synced across all availability zones for extremely high availability and durability. 

#### Storage Transit Services
* Single Operation Upload - Can handle up to 5BG but only used below 100MB
* Multi-Part Upload (Suggested for 100MB or larger)
* AWS Import/Export - You literally send aWS a hard drive snail mail and they import the data within one business day (benefits: migrate large data quickly)
* Snowball: Petabyte-scale data transport solution
* Storage Gateway: 
    * Gateway-Cached Volumes: Bulk data lives in cloud and frequent data is cached on-premise
    * Gateway-Stored Volumes: Store all data locally, and periodically take snapshots of data as backups and store on S3

###  Route 53
#### DNS Failover
* If you want to use S3 as a failover you must name the bucket the same as your domain name

### CloudFront (caching mechanism)
* CloudFront is a global CDN which delivers content from an "origin" location to an "edge" location (AWS CDN data center)
* Lower latency and content load time for customers
* Can handle up to 100,000 requests per second 
* Origin location can be: 
    * An S3 Bucket
    * ELB that distributes to EC2
   
* Allows you to reduce cost as traffic is hitting edge locations and reducing load on your eC2
* To improve performance have longer cache periods (less frequent request to the source)

### VPN (Virtual Private Network)
* Enables the ability to extend a subnet from one geographic location to another geographic location on two seperate networks
* Essentially extending the on-premise network to the cloud or the cloud to the on-premise network
* Only one Virtual Private Gateway can be attached to a VPC
* A VPC can have both a VPG and IGW attached at the same time
* BOth a Customer Gateway and VPG are required to establish a VPN connection

#### Customer Gateway 
* Physical device or software application at the on-premise location that acts as the "connector" to the VPN connection
* IN AWS it is where you configure the public IP address

#### VPN Connection 
* The actual link between the virutal private gateway and the customer gateway
* This connection is setup and managed in AWS
* Each connection uses two IPsec tunnels for redundancy

#### Router 
####Virtual Private Gateway

### AWS Direct Connect
* AWS service that provided a dedicated network connection between your netowrk and one of AWS direct connect locations
* Only requires Direct Connect location and participating backbone provider
* Only provides access to the regions it is connected with
* Benefits: 
    * Reduce network costs: Data transfered is billed at lower rate
    * Increase network consistency and reduces latency
    * Dedicated private network connection to on-premise
* Private Virtual Interface
* Public Virtual Interface
    
### VPC Peering
* Used to extend your private network from on VPC or one subnet or one instance to another VPC
* Sharing internal resources via private IP addresses (not the open internet)
* Can occur in same region or two VPCs in different regions (VPC peering)
* To peer VPCs must have separate (non-overlapping) CIDR block ranges
* Can configure to peer the entire VPC or just subnets
* Transitive connections not allowed (associative peering), has to have direct connection
 
### RDS 
* Benefits: Fully-managed RDS( no access to underlying operating system)and automatic backups, auto-recovery
* Aurora: Homegrown MySql and is five times better performance and lower price point 
* Always enable Multi AZ failover in production (fault-tolerance and high availability)

#### RDS Read Replica
* Allow for all ready traffic to be redirected from primary database to the read replica
* Greatly improve the performance on the primary database
* You can create and have multiple read replicas for a primary database
* They allow for elasticity in RDS - you can scale up and scale down on demand
* Use for high volume, non-cached (read-heavy)

### Dynamo DB
* Key-value, schemaless, noSQL database that is fully managed
* All you need to provide is throughput capacity ans AWS takes care of the rest
* Fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale
* It's flexible data model and reliable performance make it a great fit for mobile web, gaming, ad-tech, IoT, and many other applications

### ElastiCache
* In memory cache engine
* Available engines to power include: 
    * Redis
    * Memcached
* Great for large, high-performance or high-taxing queries and can store them inside of a cache (Elastic Cache cluster) to be accessed later
* Reduces load on the database, which increases performance
* Can use for managing web sessions, and also caching dynamic generated data    

### Red Shift
* Pedabyte-scale data warehousing service
* Fully-managed and scalable
* Generally used for big-data analytics and can integrate with popular business intelligence tools


### SNS (Simple Notification Service)
* Coordinates and manages sending and delivery of messsage to specfici endpoints
* Three main pieces to sns:
*  Topic: Group of subscriptions
* Subscriptions: (HTTP, EMAIL, SNS), Endpoint that a message is sent 
* Publisher: The entity that triggers the sending of a message

### SQS (Simple Queue Service)
* Reliable, scalable, fully-managed message queing service
* Used to create decoupled application environments
* Used to send messages between servers and are retrieved through polling
* Two types of Polling: 
    * Long (1-20 seconds) which reduces number of API calls, returns all possible messages
    * Short which samples a subset of servers and return message from just those servers.
* Is highly available and redundant
* Two Types of Queue: Standard (delivery of message at least once but not guarantee order) and FIFO: where order is critical
* Decoupled architecture: Components are not connected - if one fails the rest of the system can continue processing (fault tolerant/highly available)

### SWF (simple work flow)
* Coordinates and manages the execution of activities that can be run async across multiple computing devices
* Components: 
    * Wokflow: steps required, referred to a **decider**
    * Activities: A single step in the workflow: 
    * Task: 
        * Activity: Tells worker to perform a function
        * Decision Task: Tells decider the state of work flow execution
   * Worker: Responsible for receiving a task and taking action on it. Can be a person or an EC2 instance
* Use cases: Media Procesing, web applications backends, business process workflows, analytics pipelines

### API Gateway
* Front-door for application allowing access to data/logic/functionality from your back-end services
* Fully-managed service that allows you to create and manage your own APIs for your application
* Build RESTful APIs
* Deploy APIS to a "Stage"
* Version control all API versions
* Create and manage API keys for acces and meter usage through CloudWatch Logs
* Set throttling rules based on number of request per second (over the limit HTTP 429 response)
* Security using signature v.4 to sign and authorize aPI calls
* API Gateway can call other public api endpoints

* Benefits: 
    * DDos protection via CloudFront (gives benefit of lower latency and less traffic on servers)
    * SDK generation for iOS, Android and JS
    * Supports Swagger (API dev tool)
    * API Gateway Cache for redundant calls
    
### Cloud Watch
* Primary monitoring service

* EC2 Monitoring
    1. System Status Checks: 
        * Loss of network, software issues on physical host, hardware issues on host
        * SOLVE: Generally starting and restarting instance
    2. Instance Status Checks: 
        * Failed system status checks, misconfigured networking or startup config, incompatible kernel
        * SOLVE: Generally a reboot or solving file system config
        
* Default will monitor metrics that can be viewed at the host level (not software level)         
    * CPU utilization
    * CPU credit balance

* OS level metrics require third party script
       * memory utilization/used/ and memory available
       * disk swap utilization
       

### CloudTrail
* API Logging service that logs **ALL** calls made to AWS
* AWS is just one big API - CloudTrail can log every action in your account

### VPC Flow Log
* Allows you to collect information about the IP traffic going to and from network interfaces
* Not a real-time stream about 10-15minutes
* They can be created on VPC, Subnet or Network Interface
* can set log capture to All, rejected or accepted
* Consist of network traffic for a specific **5-Tuple** 
* 5-Tuple set of five different values that comprise a TCP/IP connection
    * 1 source IP address, 2 source port number, 3 destination IP addresss, 4 destination port number and 5 protool
* Benefits: 
    * Troubleshoot why traffic not reaching an Ec2
    * Added security layer by allowing you to monitor the traffic that reaches EC2

## Deployment Services 
### Cloud Formation
* Only charges for the resources you create and not the templates
* Pure definition of infrastructure as code
* Can convert application architeture into a JSON formatted template
* Architecture as code
* can version control it
Benefits: Saves times, version control so it allows for rollbacks, and allows for backups of your infrastructure
* Just like terraform
* Great solution for disaster recovery
    
### Elastic Beanstalk
* Designed to deploy less complex applications
* Helps reduce the manage required for building and deploying applications
* Use to quickly provision an AWS environment that require little to no management
* Can deploy from repositoris or from uploaded code files
* Supported platforms: 
    * Docker, Java Node.js, PHP, Python, Ruby
* Select what you need (services), upload your code, deploy the application    
    
## Analytics Services
### Kinesis
* real-time data processing/ streaming dashboards
* Aggregation refers to the storage of multiple records in a Kinesis Data Streams record. Aggregation allows customers to increase the number of records sent per API call, which effectively increases producer throughput.

* Components: 
    * Stream
    * Producers (data creators)
    * Consumers (data consumers) = Iot Sensors, Mobile devices
    * Shards (processing power) = each shard can process 2MB of read data/second and 1MB of write/second
* Benefits: 
    * Real-time processing
    * Parallel processing: Can process the same data concurrently
    * Durable
    * Scales: Can stream a few megabytes to several terabytes per hour
    
* When to use: 
    * Gaming: 
    * Real-time analytics: IOT sensors
    * Application alerts: can trigger events based off of logs
    * Log/Event Data Collection: Can collect stock market data, and use it to perform buying and trades predictions
    * Mobile Data capture: can push data to Kinesis from countless number of devices
    
### Elastic Map Reduce (EMR)
**OVERVIEW:**
_EMR uses the hadoop framework to process data in a cluster made up of master and slave nodes; 
two phases map and reduce phase and data once reduced should be stored in something like S3 cause it doesn't persist in the cluster_

* Service that deploys out Ec2 instances based off of Hadoop big data framework
* Has access to underlying OS 
* Add user data into Ec2 instances
* Can resize the cluster at any time (scalable)
* Parallel Processing for faster processing of data

###### Master Node: 
* Manages the slave nodes and coordinates the distribution of data and tasks
* Also tracks the status of tasks and monitors the health

###### Types of Slave Nodes: 
* Core Node - run tasks and stores data in the Hadoop Distributed File System (HDFS) on the cluster, they do the heavy-lifting with the data
* Task noe: a slave node that has software components which only run tasks (optional)

###### Mapping phase
* splits the large data file for processing
* During phase it is split into 128kb chunks

###### Reduce
* Shuffle and sort puts all similar nodes together and reduces all data together
* Reduced data needs to be stored (like in S3) as data processed by EMR cluster is not persistent


## Container Services
* ECS is a container management service that supports Docker
* Allows to manage a fleet of Docker containers on a clust of Ec@ instances
* Primary used to create distributed applications 
*Start, stop, monitor and scale every container separately 
* Create micro services


Why?
* Create application architecture comprised of independent tasks or processes
* Batch and ETL jobs
* Continuous Integration and deployment

Components: 
1. Dockerfile
2. Docker Image
3.  Container Registry


* Task Definition: A JSON formatted file that contains the "blueprint" for the app including: 
    * which container/image to use
    * which container registry the image is locatined
    * which prots should be open on the container service
    * what data volumes should be used with the containers
    
* Cluster of instances: 
    * ECS Agent that is responsible for starting/stopping tasks
    * Tasks: actual representation of the Task definition


## Certification Concepts

### Best Practices for Implementation & Development
* Design for failure and create self-healing application environments
* Rigoursly test to find single points of failure and apply high availability
* Always enable RDS Multi-AZ failover
* Decouple applications  
* Cache static content on Amazon CloudFront
* Protect data at rest using encrypted file systems 
* Connect to instances inside of VPC using a Bastion host or VPN connection
* Use IAM roles on Ec2 instances instead of using API keys

### Monitoring
* Use CloudWatch to shut down inactive instances
* Use AWS Config to see detailed configuration information about an AWS env

### Elasticity and Scalability
* Proactive Cycle Scaling: occurs at a fixed interval
* Proactive Event-based scaling: occurs in anticipation of an event
* Plan to scale out rather than up
* Scalable service should become more cost effective as it grows
* Use tools like Auto Scaling and ELB
* RDS requires scaling in differnet ways: 
    * utilize read replicas to offload heavy read only traffic
    * increase instance size to handle increase in load
    * utilize elasticache clusters for caching database session information
 
##Security
### Shared Security Responsibility Model
* AWs responsible for certain parts and customer is responsible for certain parts
* EX: Ec2: 
    1. AWS: responsible for facilities, physical security of hardware and network infrastructure
    2. User: Software, AMIS, OS, applications, data-in-transit, data-at-rest, data stores, credentials and policies and configurations
    
### Platform compliance and security services:
AWS cloud infrastructure is architected to be flexible and secure with world-class protection
* Secure access - HTTPS, SSL/TLS
* Built-in firewalls
* Perfect forward secrecy
* Centralized key management
* CloudHSM
* Trust Advisor - for premier support AWS will identify security holes
* Multi-factor auth
* Private subnets
* Encrypted data storage
* Security Logs
* AWS identity and access management

### Incorporating Common Conventional Security Products
* OS-Side Firewalls: IPTABLES, FirewallD, Windows firewall
* AntiVirus

### DDos Mitigation
* Firewalls: 
    * Security Groups
    * Network access control lists
    * Host-based firewalls
* Traffic shaping/rate limiting
* Take advantage of CloudFront to absorb DOS/DDos flooding attacks
* Ingress filtering on all incoming traffice onto their network

### Encryption Solutions
* S3 has built-in fetures that allow you to encrypt your data: 
    * AES-256 bit encryption that encrypts data-at-REST in an S3 bucket
    * AWS decrypt the data and sent to you when downloaded
* EBS encrypted volumes; 
    * Snapshots can be encrypted
    * can select to have all data encrypted and stored on EBS
* RDS encryption: 
    * Encrypts underlying storage space for instance
    * Automated backups are encrypted and snapshots
    * Read replicas are encrypted 
    * RDS provides SSL endpoints to encrypt a connection to a DB instancs

### Complex access control
* IAM policies gives flexibility to create extreme granular control
    * On EC2: can create permissions for instances such as start, reboot, terminate, and stop all the way down to the instance ID
    * On EBS: Attach, delete and detach
    * Can also include services like RDS, S3 etc. 
* Multi-factor auth when requesting certain resources

### AWS CloudWatch
* Use CloudWatch and CloudTrail to monitor changes inside the AWS environment
* Requests are signed with an HMAC-SHA1 signature, calculated from the request and the user's private key
* Can have CloudWatch notify with via SNS for any changes in environment

### CloudHSM
* HSM (Hardware Security Module) is a dedicated physical machine/appliance isolated in order to store security keys and other types of encription keys used within an application
* The key is used within the domain of the HSM appliance instead of being exposed outside the appliance 
* AN HSM client is used to expose the APIs of the HSM
* The security key is only used within the HSM
* The appliance is physically isolated from other resources
* Types of keys to store:
    * Keys to encrypt file systems
    * Keys to enrypt DBs
    * Keys to to provide DRM
    * Used with S3 encryption
* When to use: 
    * Compliance requirements require it
    * Internal security policy
* Not even AWS engineers have access to the keys, only access to "manage" the applicance

### Disaster Recovery
* Recovery Time Objective (RTO): Time it takes to restore operations back to its regular service as defined by companies operational level agreement (i.e. If the RTO is 4 hours, you have 4 hours to restore service back to an acceptable level)
* Recovery Point Objective (RPO): Acceptable amount of data loss measured in time. (Ex. if system goes down at 10pm and RPO is 2 hours then you should recover all data as part of the application a it was before 8pm)
* Three examples on how to use AWS for disaster recovery: 
    * Pilot Light: A minimum version of production env that is running on AWS. This allows for replication from on-premise servers to AWS. DNS is switched from on-premise to AWS. Important to keep up to date AMI and instance configs if following pilot light protocol
    * Warm Standby: Larger version on Pilot Light and would most likely be running business critical applications in "standby". This type of config could also be used as a test area for applications.
    * Multi-Site Solution: Clones production ENV, which can be either cloud or on-premise. Has active-active config meaning instances size and capacity are all running in full standby and can easily convert at flip of switch. Methods like this could also be used to "load balance" using latency based routing or Route 53 failover in event of an issue.
     

### How to prepare for Test
* Read white papers
* Study Note cards
* Pass final exam three times above 75%
* Go back and take the section quizes and get 100% 
* Look at labs again
* Use Orion Papers for diagrams



