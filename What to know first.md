# Active Directory Basics

#### What is Active Directory?
A directory service developed by Microsoft for Windows domain networks That manages permissions and access to networked resources.
  
#### Key Components of Active Directory
- **Domain**: A logical group of network objects (computers, users, devices) that share the same Active Directory database.
- **Domain Controller**: A server that responds to security authentication requests within a Windows Server domain.
- **Organizational Units (OUs)**: Containers within a domain that can hold users, groups, computers, and other OUs.

### Forest Root
This is the first domain created in a forest, and it serves as the central point of management and trust for all other domains within the forest. This domain is at the top of the forest's hierarchy, and all transitive trust relationships pass through it. **There is only one forest root for each forest**

### Tree Root
A forest can contain multiple trees. Each tree is a collection of domains that are related in a hierarchical (parent/child) relationship. The domain at the top of each tree is called the tree root. For example, if you have a tree with a "Europe Domain" and its child domains "France Domain" and "Germany Domain" the Europe Domain is the tree root.

**A forest can have multiple tree roots, but only one forest root**

#### Authentication in Active Directory
The process of verifying the identity of a user or device.
Kerberos is the primary authentication protocol used in Active Directory, which uses tickets to allow nodes to prove their identity securely.

#### Authorization in Active Directory
The process of granting or denying access to resources based on permissions.
Role-Based Access is a method of regulating access to resources based on the roles of individual users within an organization.
The notion of groups means a collections of user accounts that can be assigned permissions collectively.

