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
* Definition: Is an online bulk storage service that you can access from almost any device
