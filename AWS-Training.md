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
* Availabile storage classes are: 
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
        * Could take up to a few hours or a day to retreive
        * iii 99.99999999999% durability
* Each Storage class ha varying arttributes things like: 
    * Storage cost
    * Object availability
    * Object durability
    * Frequency of access
* All objects assigned a storage class (Standard is default)     
* If you want to change the class you must set the proper class on upload  or change in permissions
* If you want to change to Glacier class you have to use object Lifecycles and may take up to 1-2 days to take effect


#### Objects:
* Files stored in a bucket are objects
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

### Elastic Cloud Compute (EC2)
