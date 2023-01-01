# AZ-104: Manage identities and governance in Azure -

## 1. Configure Azure Active Directory

### Advantages -
- enabling single sign-on access
- UX experience and device support
- benefits of secure remote access
- advantages of cloud extensibility
- advanced protection for sensitive data
- reduced costs, self-service options

### Components and concepts of Azure AD -
- Identity - An identity is an object that can be authenticated. The identity can be a user with a username and password. Identities can also be applications or other servers that require authentication by using secret keys or certificates. Azure AD is the underlying product that provides the identity service.
- Account - An account is an identity that has data associated with it. To have an account, you must first have a valid identity. You can't have an account without an identity.
- Azure AD account - The Azure AD account is also called a work or school account.
- Azure tenant (directory) - represents a single organization. can create multiple tenants or instances.
- Azure subscription - subscription is used to pay for Azure cloud services. It is linked to a credit card. Each subscription is joined to a single tenant. You can have multiple subscriptions.
	
### Active Directory Domain Services (AD DS) vs Azure Active Directory - 
- AD is a full identity solution
- AD is designed for internet-based applications that use HTTP and HTTPS
- AD is based on HTTP and HTTPS protocols
- AD tenants can't be queried by using LDAP.
- AD uses the REST API over HTTP and HTTPS
- AD doesn't use Kerberos authentication.
- AD implements HTTP protocols, such as SAML, WS-Federation, and OpenID Connect for authentication and OAuth.
- AD includes federation services, and many third-party services like Facebook.
- AD is a managed service (need to manage only users, groups, and policies). 
- If you deploy AD DS with virtual machines by using Azure, you manage many other tasks, including deployment, configuration, virtual machines, patching, and other backend processes.
	
	
### Azure AD editions - 
- Free 	
- Microsoft 365 Apps 	
- Premium P1 	
- Premium P2
	
### Azure Active Directory join - SSO to devices, applications, and services from anywhere.
#### Benifits
- SSO - Joined devices offer SSO access to your Azure-managed SaaS apps and services.
- Enterprise state roaming - users can securely synchronize their user settings and app settings data to joined devices. reduces the time to configure a new device.
- Access to Microsoft Store for Business - In Microsoft Store inventory applications pre-selected by your organization.
- Restriction of access - Allow user access to apps from only joined devices.
- Seamless access to on-premises resources - Joined devices have seamless access to on-premises resources.
- create conditional access rules that enforce access from devices to meet organization standards
- Join or Register device.
- You can use the identity to enable or disable the device.
		
### SSPR (self-service password reset)
- Azure AD account with Global Administrator privileges to manage it
- uses a security group to limit the users who have this privileges
	
## 2. Configure user and group accounts
Azure AD supports group accounts to help you organize user accounts for easier administration.
### Create users and groups
#### Cloud identity - 
- user accounts defined in your Azure AD organization and also in external Azure AD instance.
- When a cloud identity is removed from the primary directory, the user account is deleted.
#### Directory-synchronized identity - 
- defined in an on-premises AD
- synchronization activity occurs via AD Connect to bring these user accounts in to Azure.
- source for these accounts is Windows Server Active Directory.
#### Guest user -
- defined outside Azure
- Example, user accounts from other cloud providers and Microsoft accounts like an Xbox LIVE account
- source for guest user accounts is Invited user.
- useful when external vendors or contractors need access
      
### Manage user and group properties
- User accounts can also be added to Azure AD through Microsoft 365 Admin Center, Microsoft Intune admin console, and the Azure CLI.
- A user with Global administrator or User administrator privileges can preset profile data in user accounts, such as the main phone number for the company.

### Perform bulk user updates
- Only Global administrators or User administrators have privileges to create and delete user accounts in the Azure portal.
- Can be done with CSV
- Address errors by downloading the results file

### Create group accounts
#### Security groups
- used to manage member and computer access to shared resources for a group of users.
- You can create a security group for a specific security policy and apply the same permissions to all members of a group
- to set permissions for all group members at the same time
- implemented only by an Azure AD administrator
#### Microsoft 365 groups
- provide collaboration opportunities
- members have access to a shared mailbox, calendar, files, SharePoint site, and more.
- enable group access for guest users outside your Azure AD organization
				
### Access rights
#### Assigned
#### Dynamic user 
- dynamic membership rules to automatically add and remove group members.
- When member attributes meet the rule requirements, the member is added/removed to the group
#### Dynamic device
- Security groups only
- automatically add and remove devices in security groups
- When device attributes meet the rule requirements, the member is added/removed to the group

### Create administrative units
- useful to restrict administrative scope by using administrative units for your organization
- helpful for organizations that have many independent divisions.
- only the Global Administrator or Privileged Role Administrator users can manage AUs.
- Members and admins of an administrative unit can exercise their default user permissions to browse other users, groups, or resources outside of their administrative unit.
			
## 3. Configure subscriptions
Access to Azure resources and services is obtained through Azure subscriptions.
![Azure Subscriptions](https://learn.microsoft.com/en-us/training/wwl-azure/configure-subscriptions/media/azure-subscriptions-e855533e.png "Azure Subscriptions")

### Identify Azure regions
- datacenters located around the globe are organized and made available to end users by region
- available in more than 60 regions in 140 countries.
- more global regions than any other cloud provider.
- Regions provide you with the flexibility and scale needed to bring applications closer to your users.
- regions are paired with another region within the same geography to make a regional pair (or paired regions)
- Regional pairs help to support always-on availability
#### Characteristic
- Physical isolation
	- Azure prefers at least 300 miles of separation between datacenters in a regional pair.
	- reduces the likelihood of natural disasters, civil unrest, power outages, or physical network outages affecting both regions at once.
- Platform-provided replication
	- services like Geo-Redundant Storage provide automatic replication to the paired region.
- Region recovery order
	- During a broad outage, recovery of one region is prioritized out of every pair.
- Sequential updates
	- system updates are rolled out to paired regions sequentially
	- updates minimizes downtime, reduces bugs, and logical failures
- Data residency
				
#### Things to consider - 
- Some services or Azure Virtual Machines features are available only in certain regions, such as specific Virtual Machines sizes or storage types.
- Some global Azure services that don't require region, eg, AD, Traffic Manager, and Azure DNS.
	
### Implement Azure subscriptions 
- An Azure subscription is a logical unit of Azure services that's linked to an Azure account
- Subscriptions help you control how resource usage is reported, billed, and paid.
- Every Azure cloud service belongs to a subscription.
- Each subscription can have a different billing and payment configuration.
- Multiple subscriptions can be linked to the same Azure account.
- More than one Azure account can be linked to the same subscription.
- Billing for Azure services is done on a per-subscription basis.
- Programmatic operations for a cloud service might require a subscription ID.
- Users and services authenticate with Azure AD before they access resources.
- Azure free subscription is an excellent way for new users to get started

#### Microsoft Cost Management
- view aggregated costs by organization to understand where costs are accrued
- prevent cost thresholds or limits from being surpassed

#### Resource Tags
- tags to your Azure resources to logically organize them by categories
- useful for sorting, searching, managing, and doing analysis on your resources.

## 4. Configure Azure Policy
Azure Policy is a service in Azure that enables you to create, assign, and manage policies to control or audit your resources. You apply the policies to your resources by using management groups.
### Management Groups
- You can use management groups as containers to manage access, policy, and compliance across your subscriptions.
- By default, all new subscriptions are placed under the top-level management group, or root group.
- All subscriptions within a management group automatically inherit the conditions applied to that management group.
- A management group tree can support up to six levels of depth.
- In this scenario, the organization has a single top-level management group. Every directory under the root group is folded into the top-level group.
![Azure Management Groups](https://learn.microsoft.com/en-us/training/wwl-azure/configure-azure-policy/media/management-groups-aa92c04a.png "Azure Management Groups")
- All subscriptions within a management group inherit the conditions applied to the management group
- Organize your subscriptions into management groups to help meet compliance rules for individual departments and teams.
- Use management groups to do cost reporting by department or for specific business scenarios. 
- You can use management groups to report on budget details across subscriptions.

### Azure Policy
- You can use policies to enforce rules on your resources to meet corporate compliance standards and service level agreements. 
- Azure Policy runs evaluations and scans on your resources to make sure they're compliant.
- Apply policies at scale
- Perform remediation

## 5. Configure role-based access control
- RBAC lets you determine what operations specific users can do on specific resources, and control what areas of a resource each user can access.
- purpose of a role assignment is to control access.
- Access is revoked by removing a role assignment.
- Three types of roles are available for access management in Azure
	- Classic subscription administrator roles - manage Azure AD resources like users, groups, and domains
	- Azure role-based access control (RBAC) roles - Manages access to Azure resources
	- Azure Active Directory (Azure AD) administrator roles - Manages access to Azure AD resources
- The following diagram illustrates how you can apply Azure AD administrator roles and Azure RBAC roles in your organization.
![Apply role-based access control](https://learn.microsoft.com/en-us/training/wwl-azure/configure-role-based-access-control/media/role-based-authentication-b3dda7ae.png "Apply role-based access control")

## 6. Create Azure users and groups in Azure Active Directory
There are different ways you can assign access rights:
	- Direct assignment: Assign a user the required access rights by directly assigning a role that has those access rights.
	- Group assignment: Assign a group the required access rights, and members of the group will inherit those rights.
	- Rule-based assignment: Use rules to determine a group membership based on user or device properties.
	
## 7. Secure your Azure resources with Azure role-based access control
Here are some scenarios you can implement with Azure RBAC.
- Allow one user to manage virtual machines in a subscription and another user to manage virtual networks
- Allow a database administrator group to manage SQL databases in a subscription
- Allow a user to manage all resources in a resource group, such as virtual machines, websites, and subnets
- Allow an application to access all resources in a resource group
### How does Azure RBAC work?
1. Security principal (who) - A security principal is just a fancy name for a user, group, or application to which you want to grant access.
2. Role definition (what you can do) - A role definition is a collection of permissions.
3. Scope (where) - Scope is to where the access applies.
The following example shows how the Marketing group has been assigned the Contributor role at the sales resource group scope.
![role-based access control](https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/media/2-rbac-overview.png "role-based access control")

## 8. AD self-service password reset
- users can reset their passwords in a web browser or from a Windows sign-in screen to regain access
- SSPR reduces the load on admin and help desk.
