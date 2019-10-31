# AWSCSAProNotes
A very unstructured, 3 months of delightful notes (gosh, it took long)

❗❗❗ **If you find some mistakes/errors, please correct them before being a salty boi🧂 (then you can be one 😉)** ❗❗❗
❗❗❗ **CTRL + F -> Search For The Service** ❗❗❗

Materials (Prioritized)

1. Linux Academy Course
2. BrainCert Practice Tests
3. TutorialsDojo
4. Udemy Jon Bonso Practice Tests
5. Some Core Deep Dives

Miscellaneous
* Rehost(Lift and Shift)
      + This strategy involves lifting a part of the application or a complete application from on-premise or existing cloud environment to a new cloud environment AS IS
* Replatform(Lift, Tinker and Shift)
      + Similar to Rehost but, a portion of the application or the entire application is optimized or a little before moving to the cloud
* Refactor(Rearchitect)
      + Rearchitect entails making major changes in the application configuration as well as application code for migration
* Repurchase(Drop and Shop)
      + Dropping the application and Moving to a complete new Solution
* OSI Layers: (1) Physical, (2) Data Link, (3) Networking, (4) Transport, (5) Session, (6) Presentation, (7) Application
* Support Tiers: 
    + Basic
      * 2 Core Trusted Advisor Checks
      * Basic Support plan customers are restricted to customer support and service limit increase cases
      * If you have the Basic support plan, you can't create a technical support case
    + Developer
      * 7 Core Trusted Advisor Checks
      * No AWS Support API
      * 1 Primary Contact who contacts with AWS Support
    + Business
      * All Core Trusted Advisor Checks
      * AWS Support API
      * Access to Infrastructure Event Management for additional fee
    + Enterprise
      * All Core Trusted Advisocer Checks
      * AWS Support API
      * All proactive programs
      * Designated Technical Account Manager (TAM) to proactively monitor your environment and assist with optimization
* Instance Types: Dr Mc GIFT PX
    + D = Density(HDD)
    + R = RAM
    + M = Main(General Purpose)
    + C = Compute
    + G = GPU(Machine Learning, Graphic Intense)
    + I = IOPS
    + F = FPGA(Field Programmable Gate Array)
    + T = Thin
    + P = Parallel(General Purpose GPU)
    + X = Xtreme(In-Memory)

5 Pillars (OS-RPC)

* Operational Excellence
* Security
* Reliability
* Performance Efficiency
* Cost Optimization

Trusted Advisor (CS-FPS)

* Cost Optimization
* Security
* Fault Tolerance
* Performance
* Service Limits

Disaster Recovery

* Backup/Restore
* Pilot Light
  - Critical data is being replicated
  - Other services will be provisioned when a disaster happens
  - AMIs are prebaked
* Warm Standby
  - Active-Passive approach(Route 53 fail-over)
  - Scaled down versioned of production
  - Traffic is not active
* Multi Site
  - Active-Active approach
  - Traffic is distributed

VPC

* Only S3 and DynamoDB supports Gateway VPC Endpoint
* To secure your Interface Endpoint, use Security Groups. But to secure Gateway Endpoint, use VPC Endpoint Policies
* IPSec provides authentication, encryption and integrity protection. It doesn't provide E2E security
* PrivateLink endpoints can now be accessed across both intra-region and inter-region
* A VPC can only have one VGW
* NAT Gateway doesn't support IPv6, egress internet gateway supports IPv6
* Priority: Local, Longest Prefix(Highest bit 32>18), Static Routes(ie. Static VPN), DX over BGP, VPN over BGP
* Flowlog: Attached to VPC, subnet, or ENI and only shows metadata
* Direct connections are not encrypted(You can do it with DX + VPN)
* Direct Connect Gateway supports up to 10 VPCs
* A link aggregation group (LAG) is a logical interface that uses the Link Aggregation Control Protocol (LACP) to aggregate multiple connections at a single AWS Direct Connect endpoint, allowing you to treat them as a single, managed connection, also increasing bandwith performance by bundling them
* CloudHub is used for connecting multiple customer network(CGW) to a single VPC(VGW)
* Transit VPC is used for connecting multiple customer networks(CGW) to multiple VPC(VGW), connecting multiple regions or connecting multiple accounts
* Transit Gateway (New Gen Transit VPC)
  - You can attach VPCs, AWS Direct Connect gateways, or VPN connections to a transit gateway
  - Attaching VPCs and VPN connections to Transit Gateway
  - VPCs shouldn't overlap
  - Route propogation priority is same with VPN
* VIF (Virtual Interface - Direct Connect)
  - Use a public virtual interface on AWS public endpoints, such as an Amazon Elastic Compute Cloud (Amazon EC2) or Amazon Simple Storage Service (Amazon S3), with dedicated network performance
  - Use a private virtual interface on AWS private services, such as an Amazon Virtual Private Cloud (Amazon VPC), with dedicated network performance, use a private virtual interface
* You cannot use Direct Connect to connect to VPC endpoints of VPC DNS using a Private VIF
* Route Propagation needs to be done in VGW with Direct Connect

IAM

* There are two types of federation
  - Web Identity Federation (AssumeRoleWithWebIdentity)
    + Used for access from mobile to services such as S3 and DynamoDB by API calls
    + Google, Facebook etc.
    + Store temporary credentials on mobile
    + Utilize S3 for federated user information (bucket/app1/user1)
    + No Console Support
    + By using Cognito, you don't have to write code that interacts with a web IdP (Google, Facebook etc.)
  - SAML 2.0-based Federation (AssumeRoleWithSAML)
    + Used with Active Directory
    + For both Authorization and Authentication
    + Best suited for SSO for enterprise consumer
  - OAuth 2.0
    + For Authorization
  - OpenID Connect
    + For Authentication
    + Best suited for SSO for consumer
* Power User Access: Provides full access to AWS services and resources, but does not allow management of Users and groups

AWS Bill Services

* Bills
  - The bills page gives you access to the most up-to-date information on your costs and usage, including your monthly bill and a detailed breakdown of the AWS services you are using. To further analyze your bill, you can also download a CSV or PDF file
* AWS Cost Management
  - The AWS Cost Management dashboard lets you view the status of your month-to-date AWS expenditure, pinpoint the services that account for the majority of your overall expenditure, and understand at a high level how your costs are trending
* AWS Cost Explorer
  - AWS Cost Explorer helps you visualize, understand, and manage your AWS costs and usage over time. This is done via an intuitive interface that enables you to quickly create custom reports (including charts and tabular data) that enable you to analyze your cost and usage data, both at a high level and for highly-specific requests
* Budgets
  - AWS Budgets lets you set custom cost and usage budgets that alert you when those thresholds are exceeded. You can also receive daily, weekly, or monthly budget portfolio updates via emailed AWS Budgets Reports
* Cost & Usage Report
  - The Cost & Usage Report is your one-stop-shop for accessing the most granular data about your AWS costs and usage. You can also load your cost and usage information into Amazon Athena, Amazon Redshift, AWS QuickSight, or a tool of your choice

AWS Organizations

* Two organization type: Consolidated Billing(Isn't used for policies to restrict user access, must enable All Features for that) and All Features(Default)
* Two account types: Master Account and Member Account
* The master account has the responsibilities of a payer account and is responsible for paying all charges that are accrued by the member accounts
* You can't change an organization's master account
* Master Account can
  - Create accounts in the organization
  - Invite other existing accounts to the organization
  - Remove accounts from the organization
  - Manage invitations
  - Apply policies to entities (roots, OUs, or accounts) within the organization
* SCPs don't apply to master account even if they are set on root level
* Policies attached to root effects all organization
* By default, SCPs are FullAWSAccess
* Explicit deny overrides explicit allow
* Depth level can be up to five
* Member accounts' root user can be restricted
* SCPs can include Allow and Deny simultaneously
* You can't switch an organization with all features enabled back to consolidated billing features only
* If you explicitly deny a service in an SCP without allowing anything, only that service is denied others are allowed

Route 53

* Use CNAME with Alias=No for RDS, EB
* Use A record with Alias=Yes for Cloudfront, ELB, S3, API Gateway, Interface Endpoint
* Use A record with Alias=No for EC2

EC2

* Rebooting an Amazon EC2 instance will not change the IP of the machine. If you perform a Stop and start, the public IP of the machine will change
* When affinity is set to Host, an instance launched onto a specific host always restarts on the same host if stopped

CloudFront

* Route 53 needs to be ALIAS
* CloudFront supports WebSocket-based applications
* You can use external domains
* Use signed URLs or cookies to restrict access
* Web distribution for Live Streaming, Adobe Flash Media Server's RTMP for media in S3
* When using AWS origin (S3, EC2, ALB), no transfer out cost
* You can use geo-restriction
* CloudFront supports content that can be sent using the HTTP or WebSocket protocols
* Use third-party geo-restriction for further security (Signed url's are used)
* Not caching POST, PUT, DELETE and PATCH
* Need to use custom SSL to serve CloudFront from custom URL
* Use Field-Level Encrpytion to strengthen security by only making relevant components to be able to decrypt
* File size limit is 20 GB
* Writing access logs to S3
* Supports IPv6
* Use OAI to make S3 private and allow only CloudFront URLs
* Charged for transfer out
* Charged for submitting data to origin through CloudFront
* Charged for HTTPS
* CloudFront doesn't support 4096-bit SSL certificates
* Recommended TLSv1.1_2016
* Origin Response Timeout and Origin Protocol Policy are only available with custom domains
* Min TTL and Max TTL just set the range that Cloudfront will allow the request headers to change TTL. If no headers are passed the Default TTL will be used
* Lambda@Edge is an extension of AWS Lambda, a compute service that lets you execute functions that customize the content that CloudFront delivers (Change headers, change quality etc.)
* Lambda@Edge can show content based on device (Mobile, PC, PS4 etc.)
* Lambda@Edge needs to be in us-east-1
* Forwarding custom headers only applies to web distributions
* Caching by queries, cookies and headers are disabled by default
* By default, CloudFront will not forward HTTP Host: headers through to your origin servers
* Signed cookies don't work with RTMP

S3

* Bucket name needs to be DNS Compliant (lower case, no underscore, no periods, shouldn't end with dash, must start with letter or number)
* File size can be up to 5 TB
* Web hosting and bittorrent don't work with IPv6
* Tiers
  - Standard (99.99% A, Millisecond First Time Latency, No retrieval fee)
  - Standard-IA(99.9% A, Millisecond First Time Latency, 30 day minimum storage charge, Min 128 KB storage charge)
  - One Zone-IA(99.5% A, 30 day minimum storage charge, Min 128 KB storage charge)
  - Intelligent Tiering
  - Glacier
  - Glacier Deep Archive
* Bucket owners can delete a versioned file with its ID
* Objects in versioning disabled buckets have null version ID and it remains the same if versioning is enabled afterwards
* You can use object locking to prevent an object from being deleted or overwritten for a fixed amount of time or indefinitely
* Presigning is made by presign command of S3 API. Presigning IAM user needs to have the permissions to access the object otherwise object will throw access denied. If permissions are removed after the presigning, URL won't work
* View access logs for the bucket and its objects (Server Access Logging)
* Read after write for PUTS, eventual consistency for others
* Glacier objects are visible through S3 only
* Single operation max is 5GB, for greater than 5GB to 5TB use multipart upload
* No cost for data in, data out to same region EC2 or cloudfront
* CRR needs both source and destination to enable versioning and to be in different regions
* Deletion, lifecycle, SSE-C aren't replicated (KMS is replicated only if configured)
* Archive files before uploading (costwise and 32k storage overhead per file)
* Glacier archives can't be modified, only deleted
* Can be queried by Athena
* Transfer acceleration creates a new endpoint
* Each prefix can achieve up to 3,500/5,500 requests per second
* If you enable Requester Pays on a bucket, anonymous access, bittorrent, soap requests to that bucket are not allowed, you must authenticate all requests involving Requester Pays buckets
* Requesters must include x-amz-request-payer
* Trusted Advisor and AWS Config(Large number of buckets) checks S3 Bucket Permissions
* Folder level permissions for Active Directory is accomplished by aws.username in group policies
* Cloudwatch Logs Exporting to S3 buckets that are encrypted with AES-256 is supported. Exporting to S3 buckets encrypted with SSE-KMS is not supported
* S3 Website format
  - (bucket-name).s3-website-(AWS-region).amazonaws.com
  - (bucket-name).s3-website.(AWS-region).amazonaws.com
* S3 Endpoints
  - s3.amazonaws.com
  - s3.us-east-1.amazonaws.com
  - s3.dualstack.us-east-1.amazonaws.com
  - account-id.s3-control.us-east-1.amazonaws.com
  - account-id.s3-control.dualstack.us-east-1.amazonaws.com

RDS

* Oracle, MSSQL, PostgreSQL, MySQL, MariaDB
* Default parameter group doesn't allow dynamic configuration changes
* RDS is limited to 16TiB, Aurora is limited 64TB
* AWS recommends to use INNOdb. MyISAM doesn't support PITR and snapshot restore
* Free between same AZ EC2 - RDS
* Choose Enhanced Monitoring for processes, threads, read/write kbs
* Multi-AZ is synchronous
* Reservation DB needs to match -> DB engine, DB instance class, Multi-AZ deployment option, license model and Region
* Aurora supports MySQL and PostgreSQL
* Use Aurora's backtrack for faster recovery
* Sizing of Aurora: Provisioned, Parallel Query, or Serverless
* Static parameters needs RDS to be reeboted, meanwhile, dynamic parameters doesn't
* Option Group doesn't need RDS to be rebooted
* Amazon RDS on VMware supports Amazon RDS for MySQL, PostgreSQL, and Microsoft SQL Server databases in customer-owned private cloud environments
* Aurora size can be up to 64 TB(Consider AWS to be 32 for PostgreSQL 16 for MSSQL)

EBS

* RAID 0 for performance (IOPS), RAID 1 for fault tolerance (avoid booting from raid volume)
* Can't encrypt root volume after launching the instance (need to encrypt through snapshot)
* Copy snapshot for different regions, share snapshot between accounts
* SSD -> small but frequent I/O size, better for database operations
  - gp2 (General Purpose) -> System boot volumes, Virtual desktops
  - io1 (Provisioned IOPS) -> Large database workloads such as MongoDB, Cassandra, MySQL etc.
  - (IOPS) 50:1 (GiB)
* HDD -> large but infrequent I/O size, better for throughput
  - st1 (High Throughput) -> Streaming, Big Data, Data warehouses, Log processing
  - sc1 (Cold HDD) -> Infrequently accessed and throughput-oriented storage, Lowest storage cost
  - (IOPS) 3:1 (GiB)
* Maximum IOPS and throughput are guaranteed only on Nitro-based instances
* Maximum throughput is achieved with EBS optimization support
* Storage blocks that were restored from snapshots must be initialized, this action takes time and cause a significant increase in the latency of an I/O operation the first time block is accessed
* Taking snapshots can have a noticeable effect on the performance of the Amazon EBS volume
* An in-progress snapshot is not affected by ongoing reads and writes to the volume
* Minimum 500 GB Throughput Optimized and Cold HDD
* Supports Lifecycle Management for scheduling snapshotting with tags

EFS

* Amazon EFS is a file storage service for use with Amazon EC2. Amazon EFS provides a file system interface, file system access semantics (such as strong consistency and file locking), and concurrently-accessible storage for up to thousands of Amazon EC2 instances
* Supports AWS VPN and Inter-Region VPC Peering
* Higher throughput but higher latency than EBS
* Two performance modes at creation: General Purpose and Max I/O
* Every file system object (i.e. directory, file, and link) is redundantly stored across multiple Availability Zones
* Amazon EFS is designed to be highly durable. You can use AWS Backup to schedule automatic, incremental backups of your Amazon EFS file systems
* Use DataSync for migration over internet
* FSx is a storage product that allows third-party file systems to be presented as a service within AWS
  - Is SSD like EFS
  - Used with Microsoft Windows
  - Supports a version allowing managed SMB protocol(instead of NFS) storage for Windows networks and Lustre, a file system designed for temporary high performance shared access for big data/analytics workloads
  - Sits only in one AZ but data can be replicated across multiple instances using S3 or DFS replication
  - Can't use Simple Directory
* You can use DataSync to transfer files between two EFS file systems

EC2

* Three placement groups(HPC); cluster(performance), partition and spread(resilience)
* Cluster can span VPCs in the same region and availability zone
* Partitions can be in different AZs in the same region
* Spread can span multiple AZs in the same region
* Don't modify placement group capacity afterwards (don't add new instances)
* Don't use different types of instances in placement group (performance wise)
* Detailed monitoring for 1 min CW periods
* EC2s can be booted with nvme (instance storage) but they can't be stopped, only terminated
* Cold HDDs can't be boot volumes
* Reserved Instances:
  - Can be scoped for either AZ(Reserves capacity) or Region(Doesn't reserve capacity)
* Enhanced networking for high-performance

DynamoDB

* Users can pick whether to use eventual consistency or strong consistency
* DynamoDB Streams for table changes (use it for replications, backup, events)
* Global tables for inter-region data storage
* Primary key consists partition key and an optional sort key
* Global secondary index and local secondary index
* LSI rely on the original partition key and must have a sort key (must be composite)
* LSI shares tables throughput
* LSI can't be added to existing table
* GSI use different partition key and sort key (sort key is optional)
* GSI have their own provisioned throughput
* LSI support eventual or strong consistency, GSI support only eventual consistency
* Read Capacity Unit: 4 KB
* Write Capacity Unit: 1 KB
* 1000 WCU or 3000 RCU; 10 GB = 1 partition
* Use DAX for high available in-memory cache performance (10x)
* Time to Live (TTL) for DynamoDB lets you define when items in a table expire so that they can be automatically deleted from the database
* Scan goes through the entire page, while Query filters based on the primary key values
* Scan is more inefficient than Query
* You might want to run parallel scans when the table size is bigger than 20 GB or table's provisioned read throughput is not being fully used

ASG

* Difference between LC and LT
  - Multiple security groups
  - Additional network interfaces
  - Additional storage volumes
  - Advanced configurations: elastic graphics, elastic inference, T2/T3 unlimited
  - You can modify and reused LTs; they can be the starting point for a new LT or version them with updates

ELB

* ALB(Layer 7), NLB(Layer 4), CLB(Layer 4-7 & For EC2-Classic)
* HTTP/2 is supported through TLS only with ALB, not others
* ALB and NLB can target IP Addresses, CLB can't
* All of them supports cross-zone load balancing
* Only NLB doesn't support sticky sessions
* Only NLB can have static IP
* Only NLB can preserve source IP address
* NLB doesn't support WAF
* CLB doesn't support WebSockets, others do
* All of them supports TLS termination
* Only CLB doesn't support SNI
* Use ALB to configure rules based on IP addresses, HTTP headers, and custom URI strings for protecting
* Can use ALB for targets in Peered VPC, EC2-Classic and on-premises locations reachable over AWS Direct Connect or VPN connection
* Use NLB for Layer 4 features (TCP, TCP+UDP, UDP, TLS)
* Target groups support EC2, IP and Lambda
* ELB's TTL is 60 seconds when scaling happens (Adding new IPs). Therefore you need a third-party solution to re-resolve on critical operations
* ELB's health check stops sending connections, ASG's health check terminates instance when it fails
* For unbroken end-to-end encrypted connection, pick a TCP listener and don't install SSL on ELB

KMS

* KMS only uses symmetric keys, while CloudHSM allows both symmetric and asymmetric keys
* KMS manages keys, CloudHSM doesn't
* CloudHSM supports FIPS-140-2 type 3
* Data Keys are the keys which encrypts data
* You use CMKs(Master Keys) to generate, encrypt, and decrypt the data keys that you use outside of AWS KMS to encrypt your data. This strategy is known as envelope encryption

Elasticache

* Managed and in-memory
* For lowering latency
* A Redis shard is a subset of the cluster’s keyspace, that can include a primary node and zero or more read-replicas (shards are available only with Redis Clustered Mode)
* The shards add up to form a cluster
* You can also cache MongoDB and Cassandra
* Supports reserved nodes
* Memcached
	  - Simple data types
    - No partitioning
    - No resharding
    - Multithreaded (Large nodes with multiple cores or threads)
    - No snapshot
    - No HA (No replication)
    - No encryption
	  - Scale in and out
  Redis
    - Complex data types
    - Partitioning
    - Resharding
    - No multithread
    - Can take snapshots (Persistence)
    - High Availability
    - Supports encryptions
    - Supports sorting
  	- Clustered (supports online resharding, supports data partitioning)
  	- Non-clustered
    - Supports automatic failover
* Lazy Loading a caching strategy that loads data into the cache only when necessary
* Write Through strategy adds data or updates data in the cache whenever data is written to the database.
* Can cache DynamoDB and RDS

Elastic Beanstalk

* PaaS
* All at Once(One env), Rolling(One env - Replace Instances), Rolling with Batch(One env - Replace Instances), Immutable(One env - New ASG), Blue-Green(Two env)
* RDS, Auto Scaling, Load Balancer, CloudFront, DynamoDB, Elasticache, EFS, S3 can be integrated
* Doesn't work with custom server executable
* Docker, Go, .NET, Java, Node.js, Ruby, PHP, Python, Tomcat, Glassfish

Kinesis

* Kinesis Video Streams
	  - Capture, process, and store video streams
    - HLS supports live playback and archive
    - Can be integrated with third-party libraries
  Kinesis Data Streams
  	- Capture, process, and store data streams
    - You can continuously add various types of data such as clickstreams, application logs, and social media to a Kinesis stream from hundreds of thousands of sources
    - Can output to Kinesis Firehose
  Kinesis Data Firehose
  	- Load data streams into AWS data stores
    - Loading into Amazon S3, Amazon Redshift, Amazon Elasticsearch Service, or Splunk(Also Kinesis Data Analytics)
    - Amazon Kinesis Data Firehose allows you to use an AWS Lambda function to prepare and transform incoming raw data in your delivery stream before loading it to destinations
  Kinesis Data Analytics
  	- Analyze data streams with SQL or Java from Data Streams and Firehose
    - Output to dashboard
* Synchronously replicates data over AZs
* To scale up processing,
    - Increase the instance size
    - Increase the number of instances up to maximum number of open shards
    - Increase the number of shards (add parallelism)
* KCL tracks the shards in the stream using an Amazon DynamoDB table and adapts to changes in the number of shards that result from resharding.
* When using KCL, ensure that EC2 number doesn't exceed the number of shards
* Need to use different partition keys while operationg PUT command for each shard so you don't underprovision others
* A shard ingests 1 MiB data, 1000 data record/sec and consumer consumes 2 MiB comsumption data per shards

Lambda

* Limits
  - Memory: 128 MB to 3008 MB
  - /tmp: 512 MB
* If 3 asynchronous invokes throw errors, invocations will be sent to Lambda DLQ
* You can deploy custom runtime Lambda with bootstrap executable
* AWSLambdaBasicExecutionRole needed to upload logs to Cloudwatch Logs
* AWSLambdaVPCAccessExecutionRole needed when you want to access a resource in a VPC
* Layers are immutable, can be up to 5 and cannot exceed 250 MB

API Gateway

* API Gateway provides built-in authorization, restriction, throttling, security, fault tolerance, request/response mapping, and performance optimizations
* Lambda, Step Function, EB, EC2, DynamoDB, S3, Outside AWS
* You can mock an API Gateway
* Only supports HTTPS
* Doesn't support multi-region deployments
* Can be protected with WAF
* 29 seconds of integration timeout
* You can configure CORS
* ApiID.execute-api.region.amazonaws.com/stage/prod
* Supports WebSockets
* You can enable API caching in API Gateway to cache your endpoint's responses. With caching, you can reduce the number of calls made to your endpoint and also improve the latency of requests to your API
* Endpoint Types
  - Edge-optimized
  - Regional(By default)
  - Private(In VPC)
* Cloudwatch API Gateway Logging
  - Understanding common customer locations, which may change geographically based on the proximity of your backend
  - Understanding how customer input requests may have an impact on how you partition your database
  - Understanding the semantics of abnormal behavior, which can be a security flag
  - Understanding errors, latency, and cache hits/misses to optimize configuration
* Method Request and Method Response are API Gateway(interface with frontend) level functions, meanwhile, Integration Request and Integration Response are backend
* You can cache responds including queries

SQS

* Standard Queues
  - Guarantee at least once delivery of the messages
  - Do not retain the order of delivery of the messages
  FIFO Queues
  - Guarantee only once delivery of the messages
  - Guarantee the order of the delivery of the messages
* SQS can be configured with interface VPC Gateway
* FIFO Queues cannot subscribe to an SNS topic, Cloudwatch Event, S3 Event Notifications, Lambda DLQ
* Attributes
  - Amazon SQS Message Retention (Def: 4 days, Max: 14 days, Min: 60 sec)
  - Amazon SQS Visibility Timeout - After ReceiveMessage Request, temporary disappear (Def: 30 sec, Max: 12 h, Min: 0)
  - Amazon SQS Delay Seconds - Let you postpone the delivery of new messages to a queue for a number of seconds (0 -> 900 sec)
* You can't convert standard SQS to FIFO SQS. You need to delete and create it
* Apache ActiveMQ migrates to AWS MQ(supports WebSocket)
* IBM MQ migrates to EC2
* Without batching, FIFO queues support up to 300 messages per second(Therefore, FIFO doesn't scale well)

SNS

* HTTP/S subscribers of SNS topics need to have public endpoints, as SNS does not support calling private endpoints
* HTTP, HTTPS, Email, Email-JSON, Amazon SQS, Lambda, Platform application endpoint

Storage Gateways

* File Gateway 
  - supports a file interface into S3 and combines a service and a virtual software appliance
  - only supports VMware and Hyper-V
  - NFS and SMB
  - Can utilize lifecycle policies, cross-region replication, object locking(Write Once, Read Many) and versioning
  - Any modifications such as file edits, deletes or renames are stored as new versions, they don't overwrite or delete previous versions
* Volume gateway provides an iSCSI target, which enables you to create block storage volumes and mount them as iSCSI devices from your on-premises or EC2 application servers.
  - Cached Volume retains frequently accessed data subsets locally. Store data to S3 (1 GiB to 32 TiB)
  - Storage Volume asynchronously takes backup to S3 (1 GiB to 16 TiB)
* Tape gateway is a cloud-based Virtual Tape Library (VTL). It presents your backup application with a VTL interface, consisting of a media changer and tape drives. You can create virtual tapes in your virtual tape library using the AWS Management Console. Target is VTL devices as iSCSI targets.
* This service is used for disaster recovery, backup, migration and capacity increase purposes
* Storage Gateway volumes are only accessible from the AWS Storage Gateway and cannot be directly accessed using Amazon S3 APIs

Secrets Manager

* Supports automatic rotation
* Supports generating random secrets
* Can't store unencrypted data
* Costs more than Parameter Store

AWS DataSync

* Move data between on-premises and AWS by S3 and EFS

WAF

* Cross-site scripting, Geo match, IP Addresses, Size constraints, SQL injection, String and regex matching
* Can protect ELB, CloudFront, API Gateway, EC2
* AWS Firewall Manager simplifies your administration and maintenance tasks across multiple accounts and resources for AWS WAF rules, AWS Shield Advanced protections, and Amazon VPC security groups
* Firewall Manager also supports configuring VPC Security Group policies
* In order to use Firewall Manager, account must be in an organization

Shield

* To use advanced, you need to subscribe for one year
* Advanced version has,
  - Notifications
  - Dedicated response team
  - Handling of layer 3,4 and 7 attacks
  - DDoS cost protection
  - Directly works on Elastic IP or ELB
  - Support for seeing history of 13 months

OpsWork

* OpsWork creates stacks consist of layers
* Supports on-premise instances
* There are three layers
  - OpsWorks (EC2)
  - ECS (Cluster)
  - RDS (MySQL and PostgreSQL are supported)
* There are three resources
  - Elastic IPs
  - Volumes
  - RDS
* Supports memcached and ganglia

CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CodeStar

* CodeStar simplifies all services by serving a single UI

* CodeCommit supports these providers
  - CodeCommit
  - ECR
  - S3
  - GitHub

* CodeBuild supports these providers
  - CodeBuild
  - Jenkins

* CodeDeploy supports deployments on
  - EC2/On-Premises
  - Lambda
  - ECS

* AWS CodeDeploy integrates with Elastic Load Balancing

CloudFormation

* Parameters, resources, mappings, conditions, and outputs
* Resources section is the only part required in template
* DeletionPolicy either retain(prevent deletion) or snapshot(take snapshot before deletion)
* WaitCondition(Used with ELB and AutoScaling) or DependsOn is used instead of DependentCondition(Tricky Information)
* You can create Custom Resource Types with Lambda if it's unsupported
* StackSets
  - A stack set lets you create stacks in AWS accounts across regions by using a single AWS CloudFormation template
  - An administrator account is the AWS account in which you create stack sets. A stack set is managed by signing in to the AWS administrator account in which it was created
    + Account needs to have AWSCloudFormationStackSetAdministrationRole
  - A target account is the account into which you create, update, or delete one or more stacks in your stack set
    + Accounts need to have AWSCloudFormationStackSetExecutionRole 
* Stack Role is an IAM role assigned to the stack. Any modifications to the stack are then done using that role, not the permissions of the principal doing the updates
* The AWS Serverless Application Model (SAM) is an abstraction layer in front of CloudFormation that makes it easy to write serverless applications in AWS
* You can run any runtime supported by AWS Lambda(.Net Core[C#/PowerShell], Go, Java, Node.js, Python, Ruby, Custom Runtime)
* During deployment, SAM transforms and expands the SAM syntax into AWS CloudFormation syntax
* Any resource that you can declare in an AWS CloudFormation template you can also declare in an AWS SAM template
* Using SAM Local, Lambda and API Gateway can be run locally through the use of Docker containers and this is useful for testing purposes
* SAM benefits
  - Single-deployment configuration
  - Built-in best practices
  - Local debugging and testing
  - Deep integration with development tools(CodePipeline etc.)
* SAM features
  - AWS::Serverless::Function
  - AWS::Serverless::API
  - AWS::Serverless::SimpleTable
  - AWS::Serverless::Application
  - AWS::Serverless::LayerVersion
* SAM commands
  - init
  - local
  - package
  - logs
  - publish
  - deploy (CreateChangeSet, ExecuteChangeSet)

Timestream

* Amazon Timestream is a fast, scalable, fully managed time series database service for IoT and operational applications that makes it easy to store and analyze trillions of events per day at 1/10th the cost of relational databases

EMR

* Structured Data -> Redshift, Unstructured Data -> EMR
* Sometimes people use both -- use EMR Hadoop to transform data, then use Redshift for querying the data
* Runs in a single AZ
* Hive for SQL queries
* Master Node, Core Node and Task Node
* Cannot change Master Node type after creation
* With instance fleets, you specify target capacities for On-Demand Instances and Spot Instances within each fleet. When the cluster launches, Amazon EMR provisions instances until the targets are fulfilled. While a cluster is running, if Amazon EC2 reclaims a Spot Instance because of a price increase, or an instance fails, Amazon EMR tries to replace the instance with any of the instance types that you specify. This makes it easier to regain capacity during a spike in Spot pricing. Instance fleets allow you to develop a flexible and elastic resourcing strategy for each node type

Service Catalog

* AWS Service Catalog allows IT administrators to create, manage, and distribute catalogs of approved products to end users, who can then access the products they need in a personalized portal
* Enables you to create and manage catalogs of IT services that are approved for use on AWS
* Product is actually a CloudFormation template
* Portfolio is where products, permissions, restrictions etc. are defined
* The users don't have to have AWS permissions, instead, they have Service Catalog permissions which resemble CloudFormation Stack Roles
* Both internal and external users can use

RedShift

* Leader Node and Compute Node
* Compute Nodes can be On-Demand and Reserved Instances(Can't use Spot)
* Compute nodes have 2 or 16 slices which are processing units
* Classic resize allows changing node type, elastic resize doesn't
* Leader Node is free
* You can run analytic queries against petabytes of data stored locally in RedShift and directly against exabytes of data stored in S3
* Only supports Single-AZ deployments (You can run data warehouse clusters in multiple AZ's by loading data into two Amazon Redshift data warehouse clusters in separate AZs from the same set of Amazon S3 input files)
* Redshift Spectrum is a feature of Amazon Redshift that enables you to run queries against exabytes of unstructured data in Amazon S3, with no loading or ETL required
* You can run RedShift Spectrum together with EMR
* If you’re using Amazon EMR and have a Hive Metastore already, you just have to configure your Amazon Redshift cluster to use it, so, if you’re already using EMR to process a large data store, you can use Redshift Spectrum to query that data right at the same time without interfering with your Amazon EMR jobs
* Can use INSERT INTO(S3), ETL or Data Pipeline to load data into RedShift
* Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery(Only in one region by default)

Inspector

* Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS
* Works with Inspector Agent
* Integrates with SNS

AWS Batch

* Has scheduler integrated

GuardDuty

* Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts and workloads
* Monitors CloudTrail, VPC Flow, DNS Logs
* Integrates with event management, workflow systems or Lambda

ElasticSearch

* Lets you search, analyze and visualize your data in real-time.
* Is managed ELK
* There are master nodes(three are recommended, below that, master can't be elected) and data nodes
* Can be scaled both horizontally and vertically
* Always consider core count as performance resource
* Can use EBS or Instance Storage as storage
* Ingest structured or unstructed data using Logstash, Kinesis Firehose, Data Streams(w/ Lambda Event Handler), AWS IoT, S3(w/ Lambda Event Handler) or CloudWatch Logs
* Support as target by DMS
* Kibana for visualization
* ES uses Amazon Cognito to offer username/password protection for Kibana(Optional)
* You can deploy your Amazon ES instances across multiple AZs (up to three) for HA
* You can either launch the domain in a VPC or use public endpoint
* You cannot switch between VPC and public endpoint architecture
* Use cases
  - Log Analytics
  - Realt-Time Application Monitoring
  - Security Analytics
  - Full Text Search
  - Click-Stream Analytics

Application Discovery Service

* Collects and presents configuration, usage and behaviour data from your servers to help you plan your migration
* Monitors CPU, Mac Adresses etc.
* With agents, you can monitor processes and network maps
* Agentless mode only works with VMWare

SMS

* AWS Server Migration Service (SMS) is an agentless service which makes it easier and faster for you to migrate thousands of on-premises workloads to AWS
* VMware vSphere vCenter, Hyper-V and Azure are supported
* Each server volume replicated is saved as a new AMI
* AWS SMS creates a new EBS snapshot with each replication
* The migration operation is called replication (incremental)
* Non-VM is not supported

DMS

* Can target S3, Redshift and DynamoDB(from Apache Cassandra), ElasticSearch
* Supports both homogenous(Oracle to Oracle) and heterogenous(Oracle to Aurora) migrations
* Continuous replication can be done
* Replication between on-premises is not supported
* SCT can be used for heterogenous migrations to convert schemas
* CDC can bu used for capturing changes(synchronization)

SCT

* SCT can be used for heterogenous migrations to convert schemas
* SCT can also scan application source for embedded SQL statements and convert them as part of a database schema conversion

Snowball, Snowball Edge, Snowmobile

* Snowball < 72 GB, Snowball Edge < 83 GB, Snowmobile < 100 PB
* Transfer is completed approx. in one week
* Snowball Edge has these feature unlike standard Snowball
  - Durable local storage
  - Local compute with AWS Lambda
  - EC2 compute instances
  - Use in a cluster of devices
  - Use with AWS IoT Greengrass
  - Transfer files through NFS with a GUI

AWS Glue

* AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics

Step Functions

* Enhanced/serverless version of SWF
* Can call scripts running on EC2(Therefore, supports "serverful")

CloudTrail

* Actions taken by a user, role, or an AWS service in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs are recorded as events.
* CloudTrail focuses on auditing API activity.
* A trail enables CloudTrail to deliver log files to an Amazon S3 bucket
* View events in Event History, up to 90 days.
* Two type of trails
  - All Regions(Default w/ console)
  - One Region(Default w/ CLI and API)
* Specify an S3 bucket to output logs
* You can create an organizational trail that will log all events for all AWS accounts in an organization created by AWS Organizations. Organization trails must be created in the master account
* By default, bucket is encrypted by AES-256
* Integrated with SNS
* Publishes logs every five minutes
* Management events(API Calls) are logged by default, data events(S3 and Lambda) are not
* Integrity Validation for changes in CloudTrail logs

AppStream

* Amazon AppStream 2.0 is a fully managed application streaming service. It allows for a desktop application to be streamed and used inside a web browser from any device
* While the two AWS services are somewhat similar, it’s important to remember that Amazon AppStream 2.0 is focused on hosting individual applications on AWS, while Amazon WorkSpaces creates virtual desktops that can be used to create entire working environments for you and your team

Config

* Multi-account, multi-region data aggregation gives you an enterprise-wide view of your Config Rule compliance status and you can associate your AWS organization to quickly add your accounts
* Config Records details of changes to your AWS resources to provide you with a configuration history and automatically deliver it to an S3 bucket
* Receive notifications whenever a resource is created, modified or deleted
* Works on on-premise and other cloud providers
* Supports Configuration Snapshots
* Can be integrated with SNS, Cloudwatch Events and CloudTrail(Capture API calls to Config)

Directory Service

* AWS Directory Service for Microsoft Active Directory, also known as AWS Managed Microsoft AD, enables your directory-aware workloads and AWS resources to use managed Active Directory in the AWS Cloud
* AWS Managed Microsoft AD is built on actual Microsoft Active Directory and does not require you to synchronize or replicate data from your existing Active Directory to the cloud
* You can use standard Active Directory administration tools and take advantage of built-in Active Directory features, such as Group Policy and single sign-on (SSO)
* With AWS Managed Microsoft AD, you can easily join Amazon EC2 and Amazon RDS for SQL Server instances to your domain, and use AWS Enterprise IT applications such as Amazon WorkSpaces with Active Directory users and groups

Rekognition

* Amazon Rekognition makes it easy to add image and video analysis to your applications. You just provide an image or video to the Rekognition API, and the service can identify the objects, people, text, scenes, and activities, as well as detect any inappropriate content
* Supports JPEG and PNG, MPEG-4 and MOV
* Upload images as S3 Objects or byte array
* Upload videos via Kinesis Video Stream
* Amazon Rekognition Video stream processor analyzes videos
* Video analysis output should be sent to Kinesis Data Streams

Lex

* Amazon Lex is a service for building conversational interfaces into any application using voice and text

Systems Manager

* Supports hybrid environments(Need to install TLS in on-premise VMs to communicate SSM)
* OpsCenter
  - OpsCenter provides a central location where operations engineers and IT professionals can view, investigate, and resolve operational work items (OpsItems) related to AWS resources
    + EC2 Instance State-change - Stopped or Terminated
    + AWS Health - RDS Maintenance Scheduled etc.
* Resource Groups
  - You can create unlimited, single-region groups in your account, use your groups to view group-related insights, and automate tasks on group resources. Groups can be based on resource types and tag queries, or AWS CloudFormation stacks
* Automation
  - Define common IT tasks as a collection of steps in an SSM document, and execute all steps on a collection of AWS resources at scale
* Inventory
  - AWS Systems Manager Inventory provides visibility into your Amazon EC2 and on-premises computing environment, you can use Inventory to collect metadata from your managed instances
    + OS Versions
    + Applications
* State Manager
  - Bootstrap instances with specific software at start-up
  - Download and update agents on a defined schedule, including SSM Agent
* Maintenance Window
  - Can register tasks for
    + Run Command
    + Automation
    + Lambda
    + Step Functions
* Patch Manager
  - AWS Systems Manager Patch Manager automates the process of patching managed instances with both security related and other types of updates
  - Can be used with Maintenance Window for scheduling
* Distributor
  - Allows you to package agents and install them to EC2 Instances with SSM installed

Amazon Connect

* AWS Connect if you’re looking to improve your contact center experience, regardless of size, you can benefit from using Connect, and the scalable, open, dynamic, and easy, self-service configuration

Amazon Artifact

* Enables you to download AWS security compliance reports such as ISO and PCI reports

AWS Control Tower

* Helps you set up and govern a secure, compliant, multiaccount AWS environment

AWS RAM

* Enables you to share specified AWS resources that you own with other accounts
* You can share
  - Capacity Reseervations
  - Subnets
  - Traffic Mirror Targets
  - Transit Gateways
  - Licence Configurations
  - Aurora Clusters
  - Route 53 Forwarding Rules

Data Pipeline

* A managed ETL service
* Native integration with S3, DynamoDB, RDS, EMR, EC2 and RedShift
* Supports Task Runners which act like SWF or Step Functions
* Between
  - DynamoDB to S3
  - RDS MySQL to S3
  - RDS MySQL to RedShift

ECS

* Default Network Mode is Bridge
* Host and awsvpc network modes provide the most performance because host uses instance ports directly(you can't run multiple instantiations of the same task on a single container) and awsvpc uses ENIs directly
* Task Execution role is to pull images from ECR or publish logs to Cloudwatch
* Task role is to give permissions to container for them to access AWS Services

X-Ray

* Active tracing with AWS X-Ray should be enabled to provide distributed tracing capabilities as well as to enable visual service maps for faster troubleshooting
* X-Ray helps you identify performance degradation and quickly understand anomalies including latency distributions
* Can be used on EC2(w/ Agent), ECS(w/ Agent), Lambda, EB, API Gateway, ELB
* Logs are retained for 30 days

CloudSearch

* A fully managed service that makes it easy to set up, manage and scale a search solution for your website or application
* Single-AZ or Multi-AZ(Max. 2)
* Integrates with API Gateway

AppSync

* Hosts GraphQL HTTP requests and responses to mobile users
* Data from AWS AppSync is real-time when devices are connected, and data is available offline as well
* Data sources can be Amazon DynamoDB, Amazon Elasticsearch Service, or AWS Lambda

Pinpoint

* Targeted Push Notifications for Mobile Apps. Amazon Pinpoint makes it easy to run targeted campaigns to drive user engagement in mobile apps
* Pinpoint helps you understand user behavior, define which users to target, determine which messages to send, schedule the best time to deliver the messages, and then track the results of your campaign
* Some of the features offered by Amazon Pinpoint are:
  - Understand User Behavior
  - Create Targeted Campaigns
  - Measure Results

QuickSight

* Provides ML Insights for discoverting hidden trends and outliers
* Data from S3, EC2, RDS, Athena or on-premise DB
* Has a wide library of visualizations, charts and tables
* Schedule automatic email-based reports
* Super fast by parallel calculations
* High available
* Has stories
* If you have your data in Elasticsearch, Kibana works fine. If you have a diverse set of data or need wonderful AI insights and all sorts of other features, then Quicksight is good

Cognito

* Web or mobile
* Cognito Identity Pool allows anonymous logins
* Identity Pool also includes existing User Pool
* Both of them supports Facebook, Google etc. federated login mechanisms
* Use Identity Pool to make mobile application access S3, DynamoDB etc.
