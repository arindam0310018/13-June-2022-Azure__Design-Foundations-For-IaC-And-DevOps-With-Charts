# AZURE CHARTS: DESIGN FOUNDATION FOR IAC AND DEVOPS!!!

Greetings my fellow Technology Advocates and Specialists.

In this Session, I will provide you real-time insights on how to use __AZURE CHARTS__ as __Design Foundation for IaC (Infrastructure-As-Code)__ and __DevOps Automation__. 

| __IMPORTANT TO NOTE:-__ |
| --------- | 
| Once Design Foundation is ready, __putting into IaC (Terraform/Powershell) and executing using Azure DevOps Pipeline becomes relatively easy.__  |

| __WHAT IS COVERED:-__ |
| --------- | 
| Azure Charts. |
| Category of Azure Services. |
| Which Azure Services Supports Private Link. |
| Which Azure Services Supports Managed Identity. |
| Design Resource Group(s). |
| Design Network Framework. |
| Azure Night Sky. |
| Azure Services SLA. |
| Azure Services Reservation. |

| __AZURE CHARTS:-__ |
| --------- | 
| Link to [Azure Charts](https://azurecharts.com/) | 
| First Look on Azure Charts:- |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/but3tmcromfqhdff9jyx.png) |

| __CATEGORIES OF AZURE SERVICES:-__ |
| --------- | 
| When you are designing the foundation to ease Writing IaC and Executing over Azure DevOps Pipeline, it is very important to understand which Azure Services falls under which Category. |
| This will then help you to design Resource Group Structure, AAD Group Layout, RBAC Model and Network Framework which is our Foundation.  |
| Link to [Azure Services Categories Overview](https://azurecharts.com/overview) in __Azure Charts__:  |
| First Look on __Azure Services Categories Overview__ in __Azure Charts__:- |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9m187izou878hm7awc7r.png) |

| __WHICH AZURE SERVICES SUPPORTS PRIVATE LINK:-__ |
| --------- |
| Browse to [Private Link Support](https://azurecharts.com/overview/?f=privatelink) to view which Azure Services Supports Private Link. |
| Below is how it looks:- |   
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/em66xjv7pwbofg91glk9.png) |

| __WHICH AZURE SERVICES SUPPORTS MANAGED IDENTITY:-__ |
| --------- |
| Browse to [Managed Identity Support](https://azurecharts.com/overview/?f=managedidentity) to view which Azure Services Supports Managed Identity. |
| Below is how it looks:- |   
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jqz74sjppp3tcxd4y4pr.png) |

| __DESIGN RESOURCE GROUP(S):-__ |
| --------- |
| Consider a Project Scenerio, where we have to deploy below Azure Services (Using IaC and Azure DevOps Pipelines):- 1) __Azure App Plan,__ 2) __Azure App Services,__ 3) __Virtual Machine,__ 4) __Data Factory,__ 5) __Databricks,__ 6) __Azure SQL,__ 7) __Azure Active Directory B2C,__ 8) __Key Vault,__ 9) __API Management,__ 10) __Service Bus,__ 11) __Application Gateway,__ 12) __Bastion,__ 13) __Azure Storage__ and 14) __Data Lake Store__ |
| __Questions:__ |
| 1) How would you __Design the Resource Group(s)__ ? |
| If the Required Azure Services needs to be Deployed in __Shared Subscription__ then __1 Resource Group containing all Azure Services__ makes Sense as Resource Group(s) then becomes the __Logical Boundary__ between Projects in the Same Subscription. But what Happens when Each Project has Dedicated Subscription. Then Design of the Resource Group(s) plays a vital role for Day to Day Operations    |
| 2) Why Do we __Need to Design Resource Group(s)__ ? |
| This is needed because of the following reasons:- |
| - __Sub-Team(s) within the Same Application Development:__ Different Resource Group with Different Azure Services provides the Logical Boundaries among Sub-Teams.   |
| - __Role Based Control (RBAC):__ Key Security Feature as which Sub-Team(s) requires what level of permissions on which Resource Groups. |
| - __Application User Look and Feel Segregation:__ Developers and Operation Support will only be concerned on the visibility and access of their respective Resource Group(s)  |
| This is where Azure Services Categories in Azure Charts helps us in __DESIGNING RESOURCE GROUP(S)__ |

| For the Purpose of this Session, Consider the Naming Convention of Resource Group(s) as: __[NAME OF THE COMPANY]-[PROJECT NAME]-[ENVIRONMENT NAME]-[AZURE SERVICE CATEGORY NAME]-RG__ |
| --------- |

| __NOTES ON RBAC:-__ |
| --------- |
| __Scope of RBAC__ = Resource Group. |
| __RBAC Attached to__ = Azure Active Directory (AAD) Group. |
| __AAD Group Design__ will be based on the __Target Operating Model (TOM).__  |

| __NAME OF THE RESOURCE GROUP__ | __AZURE SERVICES__  | __ROLE BASED ACCESS CONTROL__ | __NOTES (IF ANY)__ |
| --------- | --------- | --------- | --------- |
| AM-BLOGPOST-TEST-SHARED-RG | Azure App Service Plan, Key Vault | Contributor, Reader | __Point(s) to Note:__ __(1)__ Several Azure App Services can use the Same Azure App Service Plan, hence __SHARED RESOURCE GROUP__. __(2)__ Key Vault (Keys, Secrets and Certificates can be consumed by one or multiple Azure Services, hence __SHARED RESOURCE GROUP__. __(3)__ Azure App Service Plan does not have its own defined Built-in RBAC. __(4)__ Key Vault Access will be managed by Access Policies and not RBAC. |
| AM-BLOGPOST-TEST-COMPUTE-RG | Azure App Services, Virtual Machines | Contributor, Reader, Virtual Machine Administrator Login, Virtual Machine Contributor | __Point(s) to Note:__ __(1)__ Azure App Services and Virtual Machines belongs to __Compute__ Category in Azure Charts, hence __COMPUTE RESOURCE GROUP__. __(2)__ Azure App Service does not have its own defined Built-in RBAC. |
| AM-BLOGPOST-TEST-ANALYTICS-RG | Data Factory, Databricks | Contributor, Reader, Data Factory Contributor | __Point(s) to Note:__ __(1)__ Data Factory and Databricks belongs to __Analytics__ Category in Azure Charts, hence __ANALYTICS RESOURCE GROUP__. __(2)__ Databricks does not have its own defined Built-in RBAC. |
| AM-BLOGPOST-TEST-DATABASE-RG | Azure SQL | SQL Managed Instance Contributor, SQL Server Contributor, SQL Security Manager | __Point(s) to Note:__ __(1)__ Azure SQL belongs to __Database__ Category in Azure Charts, hence __DATABASE RESOURCE GROUP__. |
| AM-BLOGPOST-TEST-IDENTITY-RG | Azure Active Directory B2C (AAD B2C) | Contributor, Reader | __Point(s) to Note:__ __(1)__ Azure AD B2C belongs to __Identity and Security__ Category in Azure Charts, hence __IDENTITY RESOURCE GROUP__. __(2)__ Azure AD B2C is a Separate Service from Azure AD which does not have its own defined Built-in RBAC. |
| AM-BLOGPOST-TEST-INTEGRATION-RG | API Management, Service Bus | API Management Service Contributor, API Management Service Operator Role, API Management Service Reader Role, Azure Service Bus Data Owner, Azure Service Bus Data Receiver, Azure Service Bus Data Sender.  | __Point(s) to Note:__ __(1)__ API Management and Service Bus belongs to __Integration__ Category in Azure Charts, hence __INTEGRATION RESOURCE GROUP__. |
| AM-BLOGPOST-TEST-NETWORK-RG | Application Gateway, Bastion | Contributor, Reader | __Point(s) to Note:__ __(1)__ Application Gateway and Bastion belongs to __Network__ Category in Azure Charts, hence __NETWORK RESOURCE GROUP__. __(2)__ Application Gateway and Bastion does not have its own defined Built-in RBAC. |
| AM-BLOGPOST-TEST-STORAGE-RG | Azure Storage, Data Lake Store | Storage Account Contributor, Storage Blob Data Contributor, Storage Blob Data Reader | __Point(s) to Note:__ __(1)__ Azure Storage Account and Data Lake Store belongs to __Storage__ Category in Azure Charts, hence __STORAGE RESOURCE GROUP__. |

| __DESIGN NETWORK FRAMEWORK:-__ |
| --------- |
| Designing a Framework for Network becomes very much easy once we have defined the Resource Group Structure. |
| One __Virtual Network__ with One or More Address Space. |
| One __Route Table__ attached to all Subnets. |
| One __Network Security Group__ per __Subnet__. |
| For the Purpose of this Session, Consider the Network Naming Convention as: __[NAME OF THE COMPANY]-[PROJECT NAME]-[ENVIRONMENT NAME]-[AZURE SERVICE CATEGORY NAME]-[VNET/ROUTE-TABLE/SUBNET]-[NSG]__ |
| Virtual Network Name: __AM-BLOGPOST-TEST-VNET__ |
| Route Table Name: __AM-BLOGPOST-TEST-ROUTE-TABLE__ |

| __NAME OF THE RESOURCE GROUP__ | __NAME OF SUBNETS__  | __NAME OF NETWORK SECURITY GROUP__ | __NOTES (IF ANY)__ |
| --------- | --------- | --------- | --------- |
| AM-BLOGPOST-TEST-SHARED-RG | AM-BLOGPOST-TEST-SHARED-SUBNET | AM-BLOGPOST-TEST-SHARED-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-COMPUTE-RG | AM-BLOGPOST-TEST-COMPUTE-SUBNET | AM-BLOGPOST-TEST-COMPUTE-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-ANALYTICS-RG | AM-BLOGPOST-TEST-ANALYTICS-SUBNET | AM-BLOGPOST-TEST-ANALYTICS-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-DATABASE-RG | AM-BLOGPOST-TEST-DATABASE-SUBNET | AM-BLOGPOST-TEST-DATABASE-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-IDENTITY-RG | AM-BLOGPOST-TEST-IDENTITY-SUBNET | AM-BLOGPOST-TEST-IDENTITY-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-INTEGRATION-RG | AM-BLOGPOST-TEST-INTEGRATION-SUBNET | AM-BLOGPOST-TEST-INTEGRATION-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-NETWORK-RG | AM-BLOGPOST-TEST-NETWORK-SYSTEMS-SUBNET | AM-BLOGPOST-TEST-NETWORK-SYSTEMS-SUBNET-NSG  | - |
| AM-BLOGPOST-TEST-STORAGE-RG | AM-BLOGPOST-TEST-STORAGE-SUBNET | AM-BLOGPOST-TEST-STORAGE-SUBNET-NSG  | - |


| __AZURE NIGHT SKY:-__ |
| --------- |
| Link to [Azure Night Sky](https://azurecharts.com/stars) | 
| On Realtime, it educates and provides Uses cases as how to look into Azure Services together. Each __Use Case__ is Populated with the Caption __Learning Path__ or __Solution__ highlighting the required Azure Services. Examples Listed Below:- |
| Use Case #1: __GEOSPATIAL DATA PROCESSING AND ANALYTICS__ |
| Type: __Solution__ |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/p6v2sjquekit4c577am8.png) |
| Use Case #2: __DATA SCIENCE AND MACHINE LEARNING WITH AZURE DATABRICKS__ |
| Type: __Solution__ |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u5h4vybf6312tlndp1ro.png) |
| Use Case #3: __INTRODUCTION TO SECURING DATA AT REST ON AZURE__|
| Type: __Learning Path__ |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m41hnl0gzayoqov44gdk.png) | 
| Use Case #4: __Modern Analytics Architecture With Databricks__ |
| Type: __Solution__ |
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cokd1t4d0osn52fofgn5.png) |

| __AZURE SERVICES SLA:-__ |
| --------- | 
| Browse to [Azure Services SLA](https://azurecharts.com/sla) to view Azure SLA Board. |
| Below is how it looks:- |   
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/b9dwsmqb0bxztth34h4n.JPG) |

| __AZURE SERVICES RESERVATIONS:-__ |
| --------- | 
| Browse to [Azure Services Reservations](https://azurecharts.com/overview/?f=reservation) to view Reservation Support for Azure Services. |
| Below is how it looks:- |   
| ![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/2e4oub4fo70ea2efsakd.png) | 

Hope You Enjoyed the Session!!!

__Stay Safe | Keep Learning | Spread Knowledge__
