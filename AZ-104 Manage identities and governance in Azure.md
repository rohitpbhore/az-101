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
