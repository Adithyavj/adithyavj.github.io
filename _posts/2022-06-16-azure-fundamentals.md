---
title: Microsoft Azure Fundamentals
author: Adithya Vijay
date: 2022-06-16 14:30:00 +0550
categories: [Blogging, Programming]
tags: [development programming cloud azure]     # TAG names should always be lowercase
---

## Introduction
This blog will contain the concepts of Microsoft Azure Fundamentals required to 
take the AZ-900 certification exam.

## Cloud Concepts (20-25%)  [MODULE - I]

Cloud computing is the delivery of computing services over the internet, enabling faster innovation, flexible resources, and economies of scale. Resources can be provisioned and released very easily.  

### Cloud Models

There are different cloud model:  

1. Public cloud
- It is owned by cloud services or hosting provider
- They provide resources and services to multiple organizations and users.
- Users access via secure network connection (over the internet)
- No need of deep technical skill to use the public cloud. 
2. Private cloud
- It is owned by an organization. Limited to that organization and they are responsible to purchase of hardware, network, updates, security etc
- Organizations create a cloud environment in their datacenter
- Organization is responsible for operating the services they provide.
- Does not provide access to users outside the organization.
3. Hybrid cloud
- Combination of public and private clouds. 
- Deep techincal skills are required to operate the private cloud and ensure that both clouds can operate togehter efficiently.

| Public Cloud                                                  | Private Cloud                                                       | Hybrid Cloud                                                         |
|---------------------------------------------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------|
| Organizations pay  only for what they use in the cloud        | Organizations are  responsible for hardware maintenance and updates | Organizations control  security, compliance,  or legal requirements  |
| Is available to the  public                                   | No access to the public                                             | Services running on public cloud is  accessible to anyone            |
| No capital expenditures  are necessary to scale  up resources | Hardware must be purchased for start-up and maintenance             | Most flexible cloud                                                  |
| Applications can be quickly provisioned and deprovisioned     | Organizations have complete  control over resources and security    | Organization determines which application will run where             |
  

### Cloud benifits and considerations 

Some of the main benifits of moving to the cloud are:
1. High avialability - Ability to keep resources up and running for long periods of time with very little down time
2. Scalability - 
Scaling out/in (horizontal scaling) this means adding more resource/servers/VM's as you need them.
Scaling up/down (vertical scaling) - adding to existing resources either by adding more CPU/memory.
3. Global reach - Being able to access and put the resources around the world
4. Agility - Ability to react quickly to work load demands. Allocate more resources based on demand.
5. Fault tolerance - Ability to remain up and running if a service or component has a failure or no longer working.
6. Elasticity - Similar to scalability. Ability to automatically increase/decrease resources as needed.
7. Customer latency capabilities - The server needs to be as close to the customers as possible to reduce the latency for them accessing resources. With global reach, we can put the resources as close to the customers as possible.
8. Predictive cost considerations - We can quote how much we are going to spend before actually spending it.

### Expenditure Models

Capital Expenditure (CapEx)
    - Up-front spending of money on physical infrastructure.
    - Building inhouse data centers is a CapEx model. (We need to buy land, buy physical resources etc)
    - Costs from CapEx have a value that reduces over time

Operational Expenditure (OpEx)
    - Spending and billing of services or products as needed.
    - This is the model used in cloud.
    - Expenses are deducted in the same year.

### Consumption-based model - (pay as you consume.)  

It is another huge benifit of the cloud.
Cloud service providers operate on a consumption-based model, which means the end users only pay for the resources that they use. Whatever they use is what they pay for.
- Better cost prediction
- Prices for individual resources and services are provided.
- Billing is based on actual usage.

### Cloud services
There are three cloud service models:
1. IaaS - (Infrastrucutre-as-a-Service)
2. PaaS - (Platform-as-a-Service)
3. SaaS - (Software-as-a-Service)

We can use a combination of these services based on requirements. eg:- We can 
use Microsoft 365 for your company's computer which is SAAS. In Azure we can host our VM's which is an IAAS model. We can use Azure SQL database which is a PAAS model

1. **Infrastrucutre as a Service (IaaS)**
Build pay-as-you-go IT infrastructure by renting servers, virtual machines, storage, networks, and operating systems from a cloud provider.
Paying for resources as you need them. Renting VM's and servers on the cloud and paying by what you actually use
eg:- We rent servers and storage, Firewall and security, renting physical datacenter or the building and we put all the resources on top of that. We can load VM's, storage, OS etc from the cloud solution provider.

2. **Platform as a Service (PaaS)**
The cloud solution provider is responsible for everything apart from the customers own application. They manage the server, infrastructure, OS, network, and even the service configuration.
Provides an environment for building, testing, and deploying software applications; without focusing on managing underlying infrastructure. Allows the company to be more efficient and productive.

3. **Software as a Service (SaaS)**
Users connect to and use cloud-based apps over the internet
eg: Microsoft Office 365, email, and calenders
Renting the software on monthly/yearly basis. The software provider will take care of everything else the server, OS, networking, infrastructure, hosted apps, etc

| Public Cloud                                                  | Private Cloud                                                       | Hybrid Cloud                                                         |
|---------------------------------------------------------------|---------------------------------------------------------------------|----------------------------------------------------------------------|
| Organizations pay  only for what they use in the cloud        | Organizations are  responsible for hardware maintenance and updates | Organizations control  security, compliance,  or legal requirements  |
| Is available to the  public                                   | No access to the public                                             | Services running on public cloud is  accessible to anyone            |
| No capital expenditures  are necessary to scale  up resources | Hardware must be purchased for start-up and maintenance             | Most flexible cloud                                                  |
| Applications can be quickly provisioned and deprovisioned     | Organizations have complete  control over resources and security    | Organization determines which application will run where             |


### Sharing Responsibility Model
As per the below table, for private cloud, the user is responsible for managing all the things from storage to Data and access.
In case of Iaas, Microsoft manages compute, networking and storage which is the physical hardware.
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
Azure offers more global regions than any other cloud provider
It has 60+ regions representing over 140 countries.
- Regions are made up of one or more datacenters in close proximity
- They provide flexibility and scale to reduce customer latency
- Preserve data residency with a comprehensive compliance offering.
- Select region close to us for low latency

### Region Pairs
Two regions in same geography seperated by atleast 300 miles is called region pairs
- At least 300 miles of separation between region pairs.
- Automatic replication for some services.
- Prioritized region recovery in the event of outage.
- Updates are rollout sequentially to minimize downtime.

### Availability Zones
They are seperate data centers. There are also availability sets - They are within the same data center. Both are used to protect from failures.
Availability zone - protect from data center failure
Availability set - protect from hardware failures within an auzre data center.
- Provide protection against downtime due to datacenter failure
- One Azure region can have multiple availability zones (upto 3).
- Physically separate datacenters within the same region
- Each datacenter is equipped with independent power, cooling, and networking.
- Connected throught private fiber-optic networks for very low latency between them.

### Availability Options
In the cloud there is a lot of flexibility to plan for backup and resiliency in case of a data center failure or other issues. We should get high 9 availability.
VM's have SLA's of 99.99%. The higher the SLA, the better.
Single VM - 99.9%
Availability zones - 99.99%
Region Pairs - highest SLA

### Core Azure Resources
Azure resources are components like storage, virtual machines, and networks that are available to build cloud solutions.
eg: - Virtual Machines, Storage accounts, Virtual networks, App services, SQL Databases, Functions
- Compute
- Networking
- Storage
- Databases

### Resource Groups
A resource group is a container to manage and aggregate resources in a single unit. Grouping the resources into a logical group by project type/project life cycle. So when the project is over, we can de-allocate the resources in that resource group
- Resources can exist in only one resource group
- Resources can exist in different regions.
- Resources can be moved to different resource groups.
- Applications can utilize multiple resource groups.

### Azure Resource Manager (ARM)
ARM provides a management layer that enables you to create, update, and delete resources in your Azure subscription. It enables to automatically deploy and configure resources using different automation and scripting tools like azure powershell, azure cli, azure portal, rest API's and client SDKs. Automation helps maintain consistency and standards across deployments.

### Azure Subscriptions
An Azure subscription provides you with authenticated and authorized access to Azure accounts.
- Billing boundary: Generate seperate billing reports and invoices for each subscription.
- Access control boundary: Manage and control access to the resources that users can provision with specific subscriptions.

[Azure portal](https://portal.azure.com)

### Azure compute services
Azure *compute* is an on-demand computing service that provides computing resources such as disks, processors, memory, networking, and operating systems.
eg: VM, App services, Container instances, Azure kubernetes services, Windows Virtual Machines.

1. Azure virtual machines
Azure virtual machines (VM) are software emulations of physical computers. 
- They include a virtual processor, memory, storage, and networking.
- VM is an IaaS offering that provides total control and customization.
Virtual machine scale sets allows to automatically manage fluctuations and workloads in the cloud. (Elastic benefit discussed earlier)

> Another type of computing resource is serverless computing. It is different from VM's and doesn't require storage and an OS. They run as needed when needed. eg: Azure App Service, Azure functions, Azure logic Apps

2. Azure App Services
Azure app services is a fully managed platform to build, deploy, and scale web apps and API's quickly.
- Works with .NET, .NET Core, Node.js, Java, Python, or PHP
- PaaS offering with enterprise-grade performance, security, and compliance requirements.

3. Azure Functions
Small pieces of code that can be launced without worrying about the application infrastructure. A function is triggerred by a specific type of event such as changes in data, responding to messages, running on a schedule etc. They are designed for short run and are little tasks that are stateless.

4. Azure Logic Apps
Logic apps provide automated access and data across cloud without writing code. Every logic app workflow starts with a trigger which fires when a specific event happens or when new data becomes available.

> The above 2 tools run instantly in short bursts

#### Azure Container Services  

Azure containers are a light-weight, virtualized environment that does not require operating system management like VM's, and can respond to changes on demand.

5. Azure Container Instances  
A PaaS offering that runs a container in Szure iwthout the need to manage a VM or additional services. Can be event driven or long running

6. Azure Kubernetes Service  
An orchestration service for managing containers with distributed architectures and large volumes of containers. When the app grows, we will get multiple containers across different servers, we can use AKS for managing them. 

7. Windows Virtual Desktop
It is a desktop and app virtualization that runs in the cloud. It helps to replace physical computers and can enable companies to purchase virtual desktops to it's employees and this can be managed remotely.
- Create a full desktop virtualization environment without having to run additional gateway servers.
- Publish unlimited host pools to accomodate diverse workloads.
- Reduce costs with pooled, multi-session resources.

#### Azure Networking Services  

8. Azure Virtual Networks (VNet)
Enable many type of Azure resources like VM's to securely communicate with each other, the internet, and on-premises networks. A Virtual Network is scoped to a single region however, multiple Virtual networks from different regions can be connected together using virtual network peering

9. Virtual Private Network Gateways (VPN)
It is a distinct type of Virtual network gateway that sends encrypted traffic between an Azure virtual network and an on-premises location over the public internet. It provides a more secure connection from on-premises to azure over the internet.

10. Azure Express Route
 It is a dedicated private connection from on-premises network to azure through a direct link that is setup with the connection provider. It is expensive and meant for large enterprise customers.

#### Azure Database Services

11. Azure Cosmos Database
It is a globally distributed db service that elastically and independently scales throughput and storage. It is a NoSQL database. It is the first and only service to offer five 9's SLA. 99.999% SLA

12. Azure SQL Database
It is a relational database as a service (DaaS) based on the latest stable version of the Microsoft SQL Server.

13. Azure Database for MySQL
It is a fully managed MySQL database service for app developers

14. Azure Database for PostgreSQL
It is a relational database service based on the open-source Postgres database engine

15. Azure Database Migration Service
A database migration service is a fully managed service designed to enable seamless migrations
from multiple db sources to azure with minimal downtime.

16. Azure SQL Managed Instance
Many organizations have SQL database on premises. We can move them into the cloud without touching the code, structure and security. This SQL database will run the same software and will be managed, patched and maintained by azure. This is done by Azure SQL Managed instance.
It allows existing SQL Server customers to lift and shift their on-premises applications to the cloud with minimal application and database changes.
- Fully managed and evergreen platform as a service.
- Preserves all PaaS capabilities (automatic patching and version updates, automated backups, and high availability) all these drastically reduce management overhead in TCO (total cost of ownership)
- Exchange existing license for discounted rates on SQL Managed Instance using the Azure Hybrid Benefit. It has a 99.9 uptime.

17. Azure Marketplace
It is the place where customers can find, try, purchase, and provision applications and services from hundreds of leading service providers, which are all certified to run on Azure.
- Open source container platforms
- VM and database images.
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
Cloud-based to develop, train, and deploy machine learning models. Machine learning Studio (drag and drop service)
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
Automation tools to build workflows from github to azure automatically using opensource devops repository.
helps to automate software workflows to build, test, and deploy from within GitHub.
4. Azure DevTest Labs
Quickly create environments in Azure while minimizing waste and controlling cost.

### Azure Management Tools
1. Azure Portal
2. Azure PowerShell: set of commandlets that allow to manage azure resources directly from the powershell command
3. Azure Mobile App: Diagnose and fix issues. Can run commands from the mobile apps.
4. CLI: cross platform command line program that connects azure, exectues admin commands on azure resources.
5. Azure REST API: 
6. Azure Cloud Shell : browser based scripting env. in the azure portal. Provides flexibility. Offers powershell and bash
7. Azure Resource Manager (ARM): Allows automatic creation of resources using scripting tools like powershell, cli, rest api etc

Everything done through UI can be done using powershell/bash. Like creating VM, Resource etc.

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
As soon as we launch a resource in azure like a VM, azure collects metrix and log information. Metrix will say how the resources are performing and logs record when the resource is created or modified. Metrix will tell us how the resource is performing, how much it is consuming (network bandwidth)
- Application insights
- Log analytics
- Smart Alerts
- Automation Actions
- Customized Dashboards

## Azure General Security and Network Security (10-15%)

## Identity, governance, privacy, and compliance (20-25%)

## Azure pricing and lifecycle (Cost management and Service level agreements) (10-15%)

