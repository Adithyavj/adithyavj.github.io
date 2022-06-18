---
title: Microsoft Azure Fundamentals
author: Adithya Vijay
date: 2022-06-16 14:30:00 +0550
categories: [Blogging, Programming]
tags: [development programming cloud azure]     # TAG names should always be lowercase
---

## Introduction
This blog contains the concepts of Microsoft Azure Fundamentals required to 
take the AZ-900 certification exam.

## Cloud Concepts (20-25%)  [MODULE - I]

Cloud computing is the delivery of computing services over the internet, enabling faster innovation, flexible resources, and economies of scale. Resources can be provisioned and released very easily.  

### Cloud Models

There are different cloud models:  

1. Public cloud
- It is owned by cloud services or hosting providers.
- They provide resources and services to multiple organizations and users.
- Users access via secure network connection. (over the internet)
- No need of deep technical skill to use the public cloud. 
2. Private cloud
- It is owned by an organization. Limited to that organization and they are responsible for purchase of hardware, network, updates, security, etc
- Organizations create a cloud environment in their datacenter.
- Organization is responsible for operating the services they provide.
- Does not provide access to users outside the organization.
3. Hybrid cloud
- Combination of public and private clouds. 
- Deep techincal skills are required to operate the private cloud and ensure that both clouds can operate together efficiently.

| Public Cloud                                                  | Private Cloud                                                       | Hybrid Cloud                                                         |
|---------------------------------------------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------|
| Organizations pay  only for what they use in the cloud        | Organizations are  responsible for hardware maintenance and updates | Organizations control  security, compliance,  or legal requirements  |
| Is available to the  public                                   | No access to the public                                             | Services running on public cloud is  accessible to anyone            |
| No capital expenditures  are necessary to scale  up resources | Hardware must be purchased for start-up and maintenance             | Most flexible cloud                                                  |
| Applications can be quickly provisioned and deprovisioned     | Organizations have complete  control over resources and security    | Organization determines which application will run where             |
  

### Cloud benifits and considerations 

Some of the main benifits of moving to the cloud are:
1. High availability - Ability to keep resources up and running for long periods of time with very little down time.
2. Scalability - 
Scaling out/in (horizontal scaling) this means adding more resource/servers/VM's as you need them.
Scaling up/down (vertical scaling) - adding to existing resources either by adding more CPU/memory.
3. Global reach - Being able to access and put the resources around the world.
4. Agility - Ability to react quickly to work load demands. Allocate more resources based on demand.
5. Fault tolerance - Ability to remain up and running if a service or component has a failure or is no longer working.
6. Elasticity - Similar to scalability. Ability to automatically increase/decrease resources as needed.
7. Customer latency capabilities - The server needs to be as close to the customers as possible to reduce the latency for them accessing resources. With global reach, we can put the resources as close to the customers as possible.
8. Predictive cost considerations - We can quote how much we are going to spend before actually spending it.

### Expenditure Models

**Capital Expenditure (CapEx)**  

- Up-front spending of money on physical infrastructure.
- Building inhouse data centers is a CapEx model. (We need to buy land, buy physical resources etc)
- Costs from CapEx have a value that reduces over time.

**Operational Expenditure (OpEx)**  

- Spending and billing of services or products as needed.
- This is the model used in cloud.
- Expenses are deducted in the same year.

### Consumption-based model - (pay as you consume)  

It is another huge benifit of the cloud.
Cloud service providers operate on a consumption-based model, which means the end users only pays for the resources that they use. Whatever they use is what they pay for.
- Better cost prediction.
- Prices for individual resources and services are provided.
- Billing is based on actual usage.

### Cloud services
There are three cloud service models:
1. IaaS - (Infrastructure-as-a-Service)
2. PaaS - (Platform-as-a-Service)
3. SaaS - (Software-as-a-Service)

We can use a combination of these services based on requirements. eg:- We can 
use Microsoft 365 for the company's computer which is SaaS. In Azure we can host our VM's which is an IaaS model. We can use Azure SQL database which is a PaaS model.

1. **Infrastructure as a Service (IaaS)**
Build pay-as-you-go IT infrastructure by renting servers, virtual machines, storage, networks, and operating systems from a cloud provider.
Paying for resources as you need them. Renting VM's and servers on the cloud and paying by what you actually use.  
eg:- We rent servers and storage, firewall and security, renting physical datacenter or the building and we put all the resources on top of that. We can load VM's, storage, OS etc from the cloud solution provider.

2. **Platform as a Service (PaaS)**
The cloud solution provider is responsible for everything apart from the customers own application. They manage the server, infrastructure, OS, network, and even the service configuration.
Provides an environment for building, testing, and deploying software applications; without focusing on managing underlying infrastructure. Allows the company to be more efficient and productive.

3. **Software as a Service (SaaS)**
Users connect to and use cloud-based apps over the internet.  
eg: Microsoft Office 365, email, and calenders   
Renting the software on monthly/yearly basis. The software provider will take care of everything else the server, OS, networking, infrastructure, hosted apps, etc

### Sharing Responsibility Model
As per the below table, for private cloud, the user is responsible for managing all the things from storage to Data & access.  
In case of IaaS, Microsoft manages compute, networking and storage which is the physical hardware.  
In case of PaaS, the customer focuses on their applications and data. Microsoft manages the infrastructure underneath.  
In case of SaaS, the customer manages data and access, Microsoft manages everything else.  

| **On-Permises (Private Cloud)** | **IaaS**        | **PaaS**        | **SaaS**        |
|---------------------------------|-----------------|-----------------|-----------------|
| _Data & Access_                 | _Data & Access_ | _Data & Access_ | _Data & Access_ |
| _Applications_                  | _Applications_  | _Applications_  | Applications    |
| _Runtime_                       | _Runtime_       | Runtime         | Runtime         |
| _OS_                            | _OS_            | OS              | OS              |
| _VM_                            | _VM_            | VM              | VM              |
| _Compute_                       | Compute         | Compute         | Compute         |
| _Networking_                    | Networking      | Networking      | Networking      |
| _Storage_                       | Storage         | Storage         | Storage         |


## Core Azure Services (15-20%) [MODULE - II]

### Azure Architectural Components

### Regions
Azure offers more global regions than any other cloud provider.  
It has 60+ regions representing over 140 countries.
- Regions are made up of **one or more datacenters** in close proximity.
- They provide flexibility and scale to reduce customer latency.
- Preserve data residency with a comprehensive compliance offering.
- Select region close to us for low latency.

### Region Pairs
Two regions in same geography seperated by atleast 300 miles is called region pairs.
- At least 300 miles of separation between region pairs.
- Automatic replication for some services.
- Prioritized region recovery in the event of outage.
- Updates are rollout sequentially to minimize downtime.

### Availability Zones
They are in seperate data centers.  
There are also **availability sets** - They are within the same data center.  
Both are used to protect from failures.  
Availability zone - protect from data center failure.  
Availability set - protect from hardware failures within an auzre data center.
- Provide protection against downtime due to datacenter failure.
- One Azure region can have multiple availability zones **(upto 3)**.
- Physically separate datacenters within the same region.
- Each datacenter is equipped with independent power, cooling, and networking.
- Connected through private fiber-optic networks for very low latency between them.

### Availability Options
In the cloud there is a lot of flexibility to plan for backup and resiliency in case of a data center failure or other issues. We should get high 9 availability.  
VM's have SLA's of 99.99%. The higher the SLA, the better.  
Single VM - 99.9%  
Availability zones - 99.99%  
Region Pairs - highest SLA  

### Core Azure Resources
Azure resources are components like storage, virtual machines, and networks that are available to build cloud solutions.  
eg: - Virtual Machines, Storage accounts, Virtual networks, App services, SQL Databases, Azure Functions  
The main types of Azure resources are: 
- Compute
- Networking
- Storage
- Databases

### Resource Groups
A resource group is a container to manage and aggregate resources in a single unit. Grouping the resources into a logical group by project type/ project life cycle. So when the project is over, we can de-allocate the resources in that resource group.
- Resources can exist in only one resource group.
- Resources can exist in different regions.
- Resources can be moved to different resource groups.
- Applications can utilize multiple resource groups.

### Azure Resource Manager (ARM)
ARM provides a management layer that enables you to create, update, and delete resources in your Azure subscription. It enables to automatically deploy and configure resources using different automation and scripting tools like azure powershell, azure cli, azure portal, rest API, and client SDKs. Automation helps maintain consistency and standards across deployments.

### Azure Subscriptions
An Azure subscription provides you with authenticated and authorized access to Azure accounts.
- Billing boundary: Generate seperate billing reports and invoices for each subscription.
- Access control boundary: Manage and control access to the resources that users can provision with specific subscriptions.

[Azure portal](https://portal.azure.com)

### Azure compute services
Azure *compute* is an on-demand computing service that provides computing resources such as disks, processors, memory, networking, and operating systems.  
eg: VM, App services, Container instances, Azure kubernetes services, Windows Virtual Machines.  

1. Azure Virtual Machines  
Azure virtual machines (VM) are software emulations of physical computers. 
- They include a virtual processor, memory, storage, and networking.
- VM is an IaaS offering that provides total control and customization.
Virtual machine scale sets allows to automatically manage fluctuations and workloads in the cloud. (Elastic benefit discussed earlier)

> Another type of computing resource is **serverless computing**. It is different from VM's and doesn't require storage and an OS. They run as needed when needed.  
eg: Azure App Service, Azure functions, Azure logic Apps

2. Azure App Services  
Azure app services is a fully managed platform to build, deploy, and scale web apps and API's quickly.
- Works with .NET, .NET Core, Node.js, Java, Python, or PHP
- PaaS offering with enterprise-grade performance, security, and compliance requirements.

3. Azure Functions  
Small pieces of code that can be launced without worrying about the application infrastructure. A function is triggerred by a specific type of event such as changes in data, responding to messages, running on a schedule etc. They are designed for short run and are little tasks that are stateless.

4. Azure Logic Apps  
Azure Logic apps provide automated access and data across the cloud without writing code. Every logic app workflow starts with a trigger which fires when a specific event happens or when new data becomes available.

> The above 2 tools Azure Functions and Logic Apps run instantly in short bursts.

#### Azure Container Services  

Azure containers are a light-weight, virtualized environment that does not require operating system management like VM's, and can respond to changes on demand.

5. Azure Container Instances  
A PaaS offering that runs a container in Azure without the need to manage a VM or additional services. Can be event driven or long running.

6. Azure Kubernetes Service  
An orchestration service for managing containers with distributed architectures and large volumes of containers. When the app grows, we will get multiple containers across different servers, we can use AKS for managing them. 

7. Windows Virtual Desktop  
It is a desktop and app virtualization that runs in the cloud. It helps to replace physical computers and can enable companies to purchase virtual desktops to it's employees and this can be managed remotely.
- Create a full desktop virtualization environment without having to run additional gateway servers.
- Publish unlimited host pools to accomodate diverse workloads.
- Reduce costs with pooled, multi-session resources.

#### Azure Networking Services  

8. Azure Virtual Networks (VNet)  
Enable many type of Azure resources like VM's to securely communicate with each other, the internet, and on-premises networks. A Virtual Network is scoped to a single region however, multiple Virtual networks from different regions can be connected together using **virtual network peering**.

9. Virtual Private Network Gateways (VPN)  
It is a distinct type of Virtual network gateway that sends encrypted traffic between an Azure virtual network and an on-premises location over the public internet. It provides a more secure connection from on-premises to azure over the internet.

10. Azure Express Route  
 It is a dedicated private connection from on-premises network to azure through a direct link that is setup with the connection provider. It is expensive and meant for large enterprise customers.

#### Azure Database Services

11. Azure Cosmos Database  
It is a globally distributed database service that elastically and independently scales throughput and storage. It is a NoSQL database. It is the first and only service to offer five 9's SLA. 99.999% SLA

12. Azure SQL Database  
It is a relational database as a service (DaaS) based on the latest stable version of the Microsoft SQL Server.

13. Azure Database for MySQL  
It is a fully managed MySQL database service for app developers.

14. Azure Database for PostgreSQL  
It is a relational database service based on the open-source Postgres database engine.

15. Azure Database Migration Service  
A database migration service is a fully managed service designed to enable seamless migrations
from multiple database sources to azure with minimal downtime.

16. Azure SQL Managed Instance  
Many organizations have SQL database on premises. We can move them into the cloud without touching the code, structure, and security. This SQL database will run the same software and will be managed, patched, and maintained by azure. This is done by Azure SQL Managed instance.
It allows existing SQL Server customers to lift and shift their on-premises applications to the cloud with minimal application and database changes.
- Fully managed and evergreen platform as a service.
- Preserves all PaaS capabilities (automatic patching and version updates, automated backups, and high availability) all these drastically reduce management overhead in TCO. (total cost of ownership)
- Exchange existing license for discounted rates on SQL Managed Instance using the Azure Hybrid Benefit. It has a 99.9 uptime.

17. Azure Marketplace  
It is the place where customers can find, try, purchase, and provision applications and services from hundreds of leading service providers, which are all certified to run on Azure.
- Open source container platforms
- VM and database images
- Application build and deployment software
- Developer tools
- Over 10,000+ listings

## Azure Core Solutions and Management Tools (10-15%) [MODULE - III]

### Azure Internet of Things
Internet of things (IoT) is the ability for devices to garner and then relay information for data analysis.

1. Azure IoT Central  
It is a fully managed global IoT SaaS solution that makes it easy to connect, monitor, and manage IoT assets at scale.

2. Azure IoT Hub  
It is central message hub for bi-directional communiation between IoT applications and the devices it manages. It is a managed service hosted in the cloud.

3. Azure Sphere  
A comprehensive IoT security solution including hardware, OS, and cloud components.
It is a secured, high-level application platform with built-in communication and security features for internet connected devices.

### Azure Big data and analytics
1. Azure Synapse Analytics  
A cloud-based enterprise data warehouse. 
2. Azure HDInsight  
A fully-managed, open-source analytics service for enterprises. It is analytics at large scale. Enables to create clusters like apache hadoop, apache kafka, apache storm etc
3. Azure Databricks  
A collaberative Apache Spark based analytics service. Support Python, R, Java, SQL etc

### AI & Machine Learning
1. Azure Machine Learning  
Cloud-based to develop, train, and deploy machine learning models. Machine learning Studio. (drag and drop service)
2. Cognitive Services  
Quickly enable apps to see, hear, speak, understand, and interpret a user's needs.
3. Azure Bot Service  
To create intelligent bots.
Develop intelligent, enterprise-grade bots.

### Azure Devops and GitHub
1. Azure DevOps  
Development in collaboration tools including azure repos, pipelines, kanban boards, and automated cloud-based load testing.
2. GitHub  
Provides hosting for software development and version control using git.
3. GitHub Actions for Azure  
Automation tools to build workflows from github to azure automatically using opensource devops repository. Helps to automate software workflows to build, test, and deploy from within GitHub.
4. Azure DevTest Labs  
Quickly create environments in Azure while minimizing waste and controlling cost.

### Azure Management Tools
1. Azure Portal
2. Azure PowerShell: set of commandlets that allow to manage azure resources directly from the powershell command.
3. Azure Mobile App: Diagnose and fix issues. Can run commands from the mobile apps.
4. CLI: cross platform command line program that connects azure, executes admin commands on azure resources.
5. Azure REST API: 
6. Azure Cloud Shell : browser based scripting environment in the azure portal. Provides flexibility. Offers powershell and bash.
7. Azure Resource Manager (ARM): Allows automatic creation of resources using scripting tools like powershell, cli, rest api etc

> Everything done through the azure portal UI can be done using powershell/bash. Like creating VM, Resource etc.

### Azure Resource Manager (ARM) templates
These templates are JSON files that can be used to create and deploy Azure infrastructure without having to write progamming commands.

### Azure Advisor
Microsoft takes a look at the deployed resources and makes recommendations based on best practises in categories like
- Reliability
- Security
- Performance
- Cost
- Operational Excellence

### Service Health
Health of azure resources and data centers around the world. Can filter by subscriptions, region, service. We can see planned maintenance, health history etc

### Azure Monitor
As soon as we launch a resource in azure like a VM, azure collects metrix and log information. Metrix will say how the resources are performing and logs record when the resource is created or modified. Metrix will tell us how the resource is performing, how much it is consuming. (network bandwidth)
- Application insights
- Log analytics
- Smart alerts
- Automation actions
- Customized dashboards

## Azure General Security and Network Security (10-15%) [Module - IV]

### Azure Security Tools & Features

To protect ourselves globally using Azure, we can use Azure security center and Azure Sentinel.

#### Azure Security Center 
It is one of the best tools in azure. Azure Security Center is a monitoring service that provides threat protection across both Azure and on-premises datacenters.
It provides continous monitoring.
- Provides security recommendations
- Detects and blocks malware
- Analyze and identify potential attacks
- Just-in-time access control for ports which helps reduce service attacks. (Only allows required traffic)
Has:
    1. Free Tier (Comes with basic subscription)
    2. Standard Tier (has advanced security) [Only standard tier supports on-premise env]

It provides an overall policy and compliance security score for selected directory and subscriptions.  
It is the hub for all security related stuff.

With the security center we get:
1. Policy Compliance - Run policies across management groups, subscriptions, or tenants.
2. Continuous Assessments - Assess new and deployed resources to ensure that they are configured properly.
3. Tailored Recommendations - Recommendations based on existing workload with instructions on how to implement them.
4. Threat Protection - Analyze attempted threats through alerts and impacted resource reports.

#### Azure Sentinel
It is a birds eye view across your entire enterprise.  
Azure Sentinel is a security information management (SIEM) and security automated response (SOAR) solution that provides security analystics and threat intelligence across an enterprise. Helps in threat protection using AI and automatic response.
Connector and integrations:
- Office 365
- Azure Active Directory
- Azure Advanced Threat Protection
- Microsoft Cloud App Security

#### Azure Key Vault
It is a centralized location in azure where we can store certificates, keys, application secrets etc. We can control who has access to and what permission to this. We also have a log of who access it and when. If we have any control access tokens, API secrets etc we can store them in the Azure Key Vault. Key Vault can be integrated with other services like storage.

- *Secret Management*
- *Key Management*
- *Certificate Management*
- Storing secrets backed by hardware security modules (HSMs)

#### Azure Dedicate Host (This entire host will be for your subscription)
It provides physical servers that host one or more Azure VM's that is dedicated to a single organization's workload.(Single azure subscription)  
Benefits of having a dedicated host:
- Hardware isolation at server level. (No other VM's will be deployed here other than your's)
- Control over maintenance event timing.
- Aligned with Azure Hybrid use benefits.  
> Virtual scale sets are not supported in dedicate hosts. Scale sets support up to 1,000 VM instances

### Azure Network Security

#### Defense in depth
This is a strategy that employs a series of mechanisms that are designed to slow the advance of an attack.
- A layered approach to securing computer systems.
- Provides multiple levels of protection. Even if one layer gets breached, there are other layers.
- Attacks against one layer are isolated from subsequent layers.  
This layered approach is implemented in both the physical data centers and the services inside azure.  
The layers are physical security, Identity & Access, Perimeter, Network, Compute, Application , and Data at the last layer.

#### Shared Security
Security is a shared responsibility between customer and cloud provider. 
In an on-premise data center the customer is responsible for everything.
In an IaaS model, azure is only responsible for the physical datacenter, network, and hosts/OS. You are responsible for the security for rest of the system
In PaaS, azure takes care of the physical systems, the OS, underlaying software. Rest is handled by customer. Application protection is shared by both parties here.
In SaaS, almost everything is secured by azure. There is shared responsibility for Identity and directory infrastructure. 

**In all the models, the customer is responsible for securing:-**
- Data governance and rights management
- Client endpoints
- Account and access management

How to protect the network layer in the Defense in depth:
#### Network Security Groups (NSGs)
NSGs filter network traffic to and from Azure resources on Azure Virtual Networks.
- Set inbound and outbound rules to filter by source and destination IP address, port, and protocol.
- Add multiple rules, as needed within subscription limits.
- Azure applies default, baseline security rules to new NSGs.
- Override default rules with new higher priority rules. We cannot delete rules. We can set priority level with a number, the higher value will have more priority. No 2 rules can have same priority.

How to protect the perimeter layer in the Defense in depth:
#### Azure Firewall
It is a fully managed cloud based network security service to protect virtual network resources. A stateful, managed Firewall as a Service (FaaS) that grants/denies server access based on originating IP address, in order to protect network resources.
- Applies inbound and outbound traffic filtering rules (http,https,ftp,rdp)
- Built-in high availability
- Unrestricted cloud scalability
- Uses Azure Monitor logging

**Azure Application Gateway** also provides a firewall, Web Application Firewall (WAF). WAF provides centralized, inbound protection for your web applications. It is a load balancer that includes a web application firewall.

#### Azure DDoS protection
A Distributed Denial of Service attack is when there is an overwelming amount of traffic send to azure network or resource, making apps slow or unresponsive.
Azure firewall just checks allowed and not allowed traffice, but DDoS protection checks if the traffic is *valid*. It prevents any unwanted traffic from coming in.
Two tiers:-
- Basic Service tier (It is automatically enabled in Azure)
- Standard Service tier - adds mitigation capabilities that are tuned to protect Azure Virtual Network resources.

Attacker --> Azure backbone --> Azure DDoS Protection --> Virtual Network

#### Reviewing Defense in Depth
Combining network security solutions
- *NSGs* with *Azure Firewall* to achieve defense in depth
- *Perimeter layer* protects your network boundaries with Azure DDoS protection and Azure Firewall
- Networking layer only permits traffic to pass between networked resources with NSG inbound and outbound rules.
- Network layer protection - Network Security Groups
- Perimter layer protection - Firewalls and DDoS protection

## Identity, governance, privacy, and compliance (20-25%) [Module - V]

### Azure Identity Services  

#### Authentication vs Authorization  

| Authentication                                                               | Authorization                                                                            |
|------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Identifies the person or service seeking access to a resource (username,pwd) | Determines an authenticated person's or service's level of access (Permission they have) |
| Requests legitimate access credentials                                       | Defines which data they can access, and what they can do with it                         |
| Basis for creating secure identity and access control principles             |                                                                                          |

#### Azure MFA's (Multi-Factor Authentication)
It provides additional security for your identities by requiring two or more elements for full authentication. Azure only supports something that you know and something that you possess types of MFA's (see below). It doesn't support biometrics (something that you are)
- Something you know (Username, password, security question)
- Something you possess (Mobile app like authenticator)
- Something you are (Face scan, finger print scan)

#### Azure Active Directory (AAD)
It is Microsoft Azure's cloud-based identity and access management service. It can be used for external resources like Office 365, Azure portal etc.
Azure Active Directory can be used for:-
- Authentication (employees sign-in to access resources)
- Single Sign-On (SSO) (sign in with a single click to access multiple resources)
- Application management (AAD can manage cloud and on-premise apps)
- B2B (Manage vendors in the app)
- B2C identity services (Manage guest users in the app)
- Device management (How cloud access corporate data)

#### Conditional Access
It is used by AAD to bring *signals* together to make decisions and enforce organizational policies. What data users can access based on their location, device, etc.  
Conditional access uses AAD to make decisions based on organizational policies.  
The signals are:-  
- User or Group Membership
- IP Location
- Device
- Application
- Risk Detection  

eg: Need to login from corporate device from corporate network, then can access data.
Conditional access is a great tool within AAD.

### Azure governance features

#### RBAC (Role-based access control)
Provides fine-grained access management for azure resources which gives admin control to grant rights that the user needs to do his job.
Enables access to azure portal and controlling access to resources.
RBAC is included in all azure subscriptions (No additional price). Only grant necessary permissions to users. This can be applied at the subscription level, management group level, resource group level or for individual resources.
Some of the different roles are:
- Owner (All permissions)
- Contributor (can't change roles)
- Reader (view permission only)

We can also create new roles if necessary.

#### Resource locks
As we add owners, contributors, readers, editors etc (ie, different roles). Resource locks help to prevent accidental deletion or modification of Azure resources thus *protect* resources.
It manages locks at subscription, resource group, or individual resource levels within Azure portal.  
Locktypes:
- Read-Only (We can read but can't update or delete) It is read only. Can't insert/update/delete
- Delete (Least restrictive - we can read, update but cannot delete)

Adding a lock is a great governance tool.

#### Tags
Provides metadata for azure resources. It is a great tool when it comes to reporting, billing etc.
- Logically organizes resources into a taxonomy.
- Consists of a name-value pair.
- Very useful for rolling up billing information.
- Tags don't have parent child relationships.  
- We can have upto 50 tags per resource

#### Azure Policy
Azure policy helps to enforce organizational standards and to access compliance at-scale. Provides governance and resource consistency with regulatory compliance, security, cost, and managements.
This helps to prevent users from selecting a really expensive VM or how to prevent users from selecting things that don't meet company standards. Deploy in certain regions only. These can be done using Azure policy. We can set the orgainzational standards and the policy will automatically enforce this across our subscriptions.
There are buit-in policy and initiative definitions under categories such as storage, networking, compute, security center, and monitoring.  
> Each blueprint can consist of zero or more ARM template artifacts

#### Azure Blueprints
Azure blueprints makes it possible for development teams to rapidly build and setup up new environments. Development teams can quickly build trust through organizational compliance with a set of built-in components (such as networking) in order to speed up development and delivery.  
It makes a blueprint of your azure environments. Very helpful for devops. They are different from ARM templates. When you deploy an ARM template, there is no relation between the deployed resource and where it came from. With Azure blueprint, the blueprint is related to the deployed resource.
- Role assignments
- Policy assignments
- Azure Resource Manager(ARM) templates
- Resource Groups

#### Cloud Adoption Framework (CAF)
This is a great tool if you are new to azure. Helps in cloud adoption. It shows the best practices from Microsoft employees, partners, and customers. Tools, guidance, and narratives for strategies and outcomes.
It is the Microsoft approach to implementing Azure.

### Azure privacy, compliance, and data protection standards

Security, privacy and compliance are the foundation of everything done in Microsoft.

**1. Security**: Secure by design. Built in intelligent security, Microsoft helps to protect against known and unknown cyberthreats, using automation and AI.  

**2. Privacy**: Committed to ensuring the privacy of organizations through contractual agreements, and by providing user control and transparency.  

**3. Compliance**: Microsoft respects local laws and regulations and provide comprehensive coverage of compliance offerings.  

#### Compliance Terms and Requirements
Azure provides most comprehensive set of compliance offerings (including certifications and attestations) of any cloud service provider. Some of the compliance offering include:
1. CJIS
2. HIPAA
3. CSA STAR Certification
4. EU Model Clauses
5. ISO/IEC 27018
6. NIST

#### Azure compliance Documentation
Microsoft offers a comprehensive set of compliance offerings to help organizations comply with national, regional, and industry specific requirements that govern the collection and use of data. It has Global, US Government, Industry, and regional offerings.

#### Privacy statements
Provides opennes and honesty about how Microsoft handles the user data collected from its products and services. The Microsoft privacy policy explains:
- What data Microsoft processes
- How Microsoft processes it
- What purposes the data is used for

#### Online service terms and Data protection Addendum
Online Services Terms: The licensing terms define the terms and conditions for the products and online services you purchase through microsoft volume licensing programs.

Data Protection Addendum: The DPA sets forth the obligations, with respect to the processing and security of Customer Data and Personal Data, in connection with the online services.

#### Trust Center
This is the home base of everything related to privacy, compliance, and trust. It has a lot of information for business managers, admins, engineers, privacy officers, and legal teams.
Access trust center [here](https://www.microsoft.com/trustcenter)

#### Azure Sovereign Regions (US Govt services)
This is a completely seperate physical instance of Azure. It meets all the security and compliance needs of US federal agencies, state and local governments, and their solution providers. It is physically isolated from non-US govt. deployments. Accessible only to screened, authorized personnel.

#### Azure Sovereign Regions (Azure China)
Microsoft is China's first foreign public cloud service provider, in compliance with govt. regulations. It is physically seperated from other Azure instances and is operated by 21Vianet. All data stays within China to ensure compliance.

## Azure pricing and lifecycle (Cost management and Service level agreements) (10-15%) [Module - VI]

### Methods for managing costs

#### Factors affecting costs
There are 6 primary factors affecting costs:
Resouce type, services and location have definite direct impact on cost

1. Resource Type  
Costs are resource-specific, so the usage that a meter tracks and the no. of meters associated with a resource, depend on the resource type.  
2. Services  
Azure usage rates and billing periods can differ between Enterprise, Web Direct, and CSP(Cloud solution providers) customers. If third party is managing our Azure, we have to pay their cost also.  
3. Location  
The Azure infrastructure is globally distributed, and usage costs might vary between locations that offer Azure products, services, and resources
eg: Switzerland costs more to run a data center there. So cost here is high. East US is low.  
4. Bandwidth  
Depending on how data transfers are going, there is billing by zone. Different geographies are organized into Zones. Weather or not you have outbound or inbound data transfers outside your Zone, there can be additional charges.
eg:- West US --> Australia (will cost outbound changes)  
5. Reserved Instances  
With this we can save money. Reserving resources for one or three year plans can help reduce resource costs upto 72% on pay-as-you-go prices.  
6. Azure Hybrid Use Benefit  
This allows to use on-premises licenses on Azure at a reduced cost. We can bring licenses from on-premise to Azure.

#### Pricing Calculator
It is a tool that helps to estimate the cost of Azure products. The options in pricing calculator include Region, Tier, Billing options, Support options, Programs and offers, Azure dev/test pricing.

#### Total Cost of Ownership Calculator
A tool to estimate cost savings you can realize by migrating to Azure cloud.
A report compares the costs of on-premises infrastructure with the costs of using Azure products and services in the cloud.

#### Azure Cost Management
It allows to look at billing reports. We can drill down deeper if we've used tags. If we have budgets, you can use it to not let subscriptions go over certain spend. We can also setup alerts that will alert the managers or anyone incharge of the project as we approach the budget.
- Reporting
- Data enrichment
- Budgets
- Alerting
- Recommendation

#### Minimizing Costs - Options to reduce and control costs
1. Perform - Perform cost analysis. Use Azure Pricing & TCO calculators
2. Monitor - Monitor usage with Azure Advisor. Implement recommendations.
3. Use - Use spending limits
4. Use - Use Azure reservations and Azure Hybrid Benefit (HUB)
5. Choose - Choose low-cost locations and regions
6. Keep - Keep up-to-date with latest Azure customer and subscription offers
7. Apply - Apply tags to identify cost owners. Identify usage owners with tags

### Service Level Agreements and Service Lifecycles

#### Azure Service Level Agreement (SLA)
SLAs describe Microsoft's commitments for uptime and connectivity. When we deply a particular Azure service, there is a SLA. It is a contractual obligation that Microsoft is commiting that this service will be up and running a minimum time per month. If the service is down beyond the agreed time, then a credit is given to the user. Free and preview features don't offer SLA. SLA's are based on individual products and services.

#### SLA's for Azure products and services
Performance targets are expressed as uptime and connectivity guarantees. Performance-targets range from 99% to 99.999%. If a service fails to meet the guarantees, a percentage of the monthly service fees can be credited. The higher the SLA, the maximum downtime you will experience per month goes down 
eg: For SLA 99.999%, downtime is only 26s

#### Factors impacting SLAs  
The more services we add to the solution, the more complex it gets. As it becomes more complex, the SLA will go down. Free services and preview features don't have SLA's. We can increase SLA using availability zones and redundant systems. Composite SLA refers to SLA for service with multiple components/resources. The composite SLA can be calculated by multiplying the SLA for each resource.

| Lower your SLA                    | Raise your SLA     |
|-----------------------------------|--------------------|
| Adding more services              | Availability Zones |
| Choosing free or non-SLA services | Redundant systems  |

#### Azure preview program and feature lifecycle (public preview --> GA)
With Azure previews, users can test beta and other pre-release features, products, services, software, and regions to provide feedback
- Public Preview: All azure customers can evaluate the new features
- Generally available (GA): After public preview is completed, all customers can use the feature, and region availability will vary.
Never use preview features in production. They also don't have SLA's

#### Monitoring service and feature updates
Azure updates provides information about the azure products, services, and features in addition to product roadmaps and availability.
View details about all Azure updates and their status  
- Browse and search for updates
- Subscribe to Azure update notifications by RSS