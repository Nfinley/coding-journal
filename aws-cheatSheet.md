# CHEAT SHEET
1. IAM
    * IAM is Identity and Access Management and can use it ti securely control individual and group access to AWS resources
    * IAM Role is something that another entity can "assume."
    * IAM by default has a non-explcit **DENY** on all permissions 
    * STS - Security Token Service - Used to generate temporary credentials to grant access to your AWS Resources. Three components:  
    * STS API call return three components: Access Key ID, Secret Access Key and Security Token
2. VPC (Virtual Private Cloud)
    * You have complete control over your virtual networking environment, including selection of your own IP address ranges, creation of subnets, and configuration of route tables and network gateway
    * Networking components inside a VPC: IGW, Route Table, NACL, Subnets (public/private), Security Groups (for resources), NAT Gateway
    * NACL: Provides inboud/outbound security rules to subnets and rules are evaluated by rule number, from lowest to highest, and executed immediately when a matching allow/deny rule is found.
3. EC2 (Elastic Compute Cloud): Provides reliable computing capacity - servers in data centers
    * Three classes for purchase, Spot (chepeast but loss data if lose instance), Reservered (75% off but pay for 1-3 years) or On-demand (hourly cost)
    * Instance types: Storage (Dense storage used for file servers) or Memory Optimized (high compute power, in-memory dbs) and General/Graphics purpose
    Types: 
    1. Family: categorizing based on what they are optimized to do
    2. Type: A sub-category for each family
    3. vCpu: The number of virtual CPUs the instance type uses
    4. Memory: Amount of RAM instance type uses
    5. Instance Storage: Local instance storage volume
    6. EBS-Optimized Available: Whether EBS is an option for instance type 
    7. Network performance: rating based on its data transfer rate (bandwidth capability)
4. EBS (Elastic Block Store):  storage volume for an EC2 instance like a hard drive  
    * Data stored on EBS volumes are automatically and redundantly stored in multiple physical volumes in the same Availability Zone as part of the normal operations of the EBS service and at no additional charge.
    * IOPS = Input/Output per second: The amount of data that can be written to or retrieved from EBS per second
    * EBS encrypted volumes; 
      * Snapshots can be encrypted
      * can select to have all data encrypted and stored on EBS
5. Cloud Watch (Primary monitoring service)
    * EC2 Monitoring
    1. System Status Checks: 
        * Loss of network, software issues on physical host, hardware issues on host
        * SOLVE: Generally starting and restarting instance
    2. Instance Status Checks: 
        * Failed system status checks, misconfigured networking or startup config, incompatible kernel
        * SOLVE: Generally a reboot or solving file system config
6.  S3 (simple storage service)
    * Different types of storage include: Standard, S-IA, RRS, and Glacier. 
    * Standard gives 99.99999999999% durability and 99.99% availability (most expensive)
     * Can provide static web hosting (also use as a failover)
     * Can trigger events, allow versioning, move files to glacier with lifecycle policies
     * Permissions: you can control who can view , access etc on bucket and object level
7. SQS (simple Queue Service): Allows for decoupled applications
    * Send messages between servers using queues and retrieve them by polling. Long > 0 (1-20 seconds) and Short < 0
    * All messages gauranteed once but when using standard order not guarenteed (order preserved in FIFO)
    * Long polling you will get all messages and is cheaper with short polling you not gauranteed all messages
8. SNS (simple Notification Service): 
    * Aws service that allows you to automate the sending of email or text message, notifications based on events that happen in your AWS account
    * Two types of clients - publishers and subscribers - also referred to as producers and consumers
    * Publishers communicate asychronously with subscribers by producing and sending messages
9. SWF (Simple Workflow): Coordinates and manages the execution of activities that can be run async across multiple computing devices
    * Four components: Workflow, activities, tasks and workers
10. Bastion Host and Nat Gateway: A bastion host is used is used as a "gateway" for traffic that is destined for instances located in a private subnet, whereas a NAT gateway provides instances in a private subnet with a route to the internet.
11. CloudTrail
    * API Logging service that logs **ALL** calls made to AWS
12. CloudFormation: Architecture as code 
    * Benefits: Saves times, version control so it allows for rollbacks, and allows for backups of your infrastructure
    * Only charges for the resources you use
13. Cloud HSM: 
    * HSM (Hardware Security Module) is a dedicated physical machine/appliance isolated in order to store security keys and other types of encription keys used within an application
14. Transit Storage serivces (Import/Export, Snowball... )
    * Single Operation Upload - Can handle up to 5BG but only used below 100MB
    * Multi-Part Upload (Suggested for 100MB or larger)
    * AWS Import/Export - You literally send aWS a hard drive snail mail and they import the data within one business day (benefits: migrate large data quickly)
    * Snowball: Petabyte-scale data transport solution
    * Storage Gateway: 
        * Gateway-Cached Volumes: Bulk data lives in cloud and frequent data is cached on-premise
        * Gateway-Stored Volumes: Store all data locally, and periodically take snapshots of data as backups and store on S3
15. Route 53
    * Configure and manage web domains for websites or application you host on aWS
    * Performs three functions: 
        1. Domain registration
        2. Domain Name System (DNS) service - translates friendly domain names like example.com into IP Addresses like 192.0.2.1. 
        3. Health checking - sends automated requests over the Internet to your application
16. CloudFront: is a global CDN which delivers content from an "origin" location to an "edge" location (AWS CDN data center)
    * Lower latency and content load time for customers
    * Can handle up to 100,000 requests per second 
    * Origin location can be: 
        * An S3 Bucket
        * ELB that distributes to EC2
17. VPN (Virtual Private Network)
    * Enables the ability to extend a subnet from one geographic location to another geographic location on two seperate networks
    * Essentially extending the on-premise network to the cloud or the cloud to the on-premise network
18. AWS Direct Connect: 
    * AWS Direct Connect is a service that provides a dedicated network connection between your data center and one of AWS's Direct Connect locations. 
    * One of the main benefits of Direct Connect is a low-latency connection.
19. RDS (relational database service)
    * Benefits: Fully-managed RDS( no access to underlying operating system)and automatic backups, auto-recovery
    * Aurora: Homegrown MySql and is five times better performance and lower price point 
    * Always enable Multi AZ failover in production (fault-tolerance and high availability)
    * AWS provides automated backups of RDS databases, which are point-in-time snapshots.
    * Read Replica: 
        * Allow for all read-only traffic to be redirected from primary database to the read replica
        * Greatly improve the performance on the primary database
        * You can create and have multiple read replicas for a primary database
        * They allow for elasticity in RDS - you can scale up and scale down on demand
        * Use for high volume, non-cached (read-heavy)
20. DynamoDB
    * Key-value, schemaless, noSQL database that is fully managed
    * All you need to provide is throughput capacity ans AWS takes care of the rest
    * Fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale
    * It's flexible data model and reliable performance make it a great fit for mobile web, gaming, ad-tech, IoT, and many other applications
21. ElastiCache
    * In memory cache engine
    * Available engines to power include: 
      * Redis
      * Memcached
    * Great for large, high-performance or high-taxing queries and can store them inside of a cache (Elastic Cache cluster) to be accessed later
    * Reduces load on the database, which increases performance
    * Can use for managing web sessions, and also caching dynamic generated data  
22. Auto-Scaling
    * Auto-Scaling automates the process of adding or removing EC2 instances based on traffic demand (using cloudWatch alarms)
    * Will auto terminate or create EC2 based on your traffic
    * It is a service and can span multiple availability zones and subnets but will always remain in your VPC
    * Components: 
        1. Launch Config = Needs to know what type of AMI, the Ec2 Template used
            i. Make sure public IP address will be assigned
            ii. Bash Script to test http (See above)
            iii. When selecting a security group make sure it has the port open that you need
        2. Auto Scaling Group = all the rules and settings that govern when an Ec2 server is auto added or removed
            i. Make sure to attach your load balancer within the ADVANCED DETAILS section
23. Elastic Load Balancer
    * For architecture to be considered highly available and fault tolerante - it **MUST** have an ELB traffic to and ASG with a min of two instances located in separate availability zones
    * An ELB evenly distributes traffic between EC2 instances that are associated with it
    * Increases the fault tolerance of your apps
    * It detects unhealthy instance and routes traffic only to healthy instances
    * ELB are **NOT** available on free tier
    * Charged per hour or partial hour the load balancer is running and charged per GB of dta transfered through the load balancer
    * Security: You need to make sure you have the correct security groups set up to allow the proper traffic based on what the load balancer is set to receive
    * Proper ports must have allow rules ie: HTTP/PORT 80
    * Health Checks are required to ensure ELB's do not serve traffic to unhealthy EC2's
24. VPC Flow Log
    * Allows you to collect information about the IP traffic going to and from network interfaces
    * Not a real-time stream about 10-15 minutes
    * They can be created on VPC, Subnet or Network Interface
    * can set log capture to All, rejected or accepted
    * Consist of network traffic for a specific **5-Tuple** 
    * 5-Tuple set of five different values that comprise a TCP/IP connection
        * 1 source IP address, 2 source port number, 3 destination IP addresss, 4 destination port number and 5 protool
    * Benefits: 
        * Troubleshoot why traffic not reaching an Ec2
        * Added security layer by allowing you to monitor the traffic that reaches EC2
25. ECS (Elastic Container Service)
     * ECS is a container management service that supports Docker
     * Allows to manage a fleet of Docker containers on a cluster of Ec2 instances
     * Primary used to create distributed applications 
     * Start, stop, monitor and scale every container separately 
     * Create micro services
26. Kinesis
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
27. EMR (elastic Map reduce)
    * _EMR uses the hadoop framework to process data in a cluster made up of master and slave nodes; 
    two phases map and reduce phase and data once reduced should be stored in something like S3 cause it doesn't persist in the cluster_
28. API Gateway
    * Front-door for application allowing access to data/logic/functionality from your back-end services
    * Fully-managed service that allows you to create and manage your own APIs for your application
    * Benefits: 
        * DDos protection via CloudFront (gives benefit of lower latency and less traffic on servers)
        * SDK generation for iOS, Android and JS
        * Supports Swagger (API dev tool)
        * API Gateway Cache for redundant calls