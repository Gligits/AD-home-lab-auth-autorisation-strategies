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

![Frame 135 (2)](https://github.com/user-attachments/assets/cbc22e0f-b500-4992-852f-47bb6bd60c96)



#### Types of trusts (from Windows Server 2003) :

Each type of trust is designed for a specific scenario.
The choice of trust depends on the organization’s needs for resource sharing and security.


### Parent/Child Trust
When Division A created its network, they started with the **Europe Domain**, which is the root of the division. Then, they added the **France Domain** to manage country-specific resources. When the **France Domain** was created, a **parent/child trust** was automatically established between **Europe Domain** and **France Domain**.

----------------------------------------------------------------------------------------------------------------------------
The parent/child trust allows users and resources to flow between both domains without needing manual approval. For example, an employee in the **France Domain** can access a printer or file located in the **Europe Domain** because the domains trust each other. This trust is **transitive**, meaning that if a third child domain is added under **France**, it will also inherit this trust.
----------------------------------------------------------------------------------------------------------------------------




### Tree-Root Trust
In **Division A**, the company decides to add another **tree** of domains to manage a new region Asia:
- **Asia Domain** is created as the root of a new tree in the same forest as the **Europe Domain**.

When the **Asia Domain** was added, a **tree-root trust** was automatically created between the **Asia Domain** and the **Europe Domain** (which is the forest root).

----------------------------------------------------------------------------------------------------------------------------
This type of trust allows the root domains of two **trees** within the same forest to trust each other. This means users in the **Asia Domain** can access resources in the **Europe Domain**, and vice versa. The trust is also transitive, meaning subdomains created under the **Asia tree** will also trust those in the **Europe tree**.
----------------------------------------------------------------------------------------------------------------------------




### Shortcut Trust
In **Division A**, there are multiple domains in the forest, including **France Domain** and **Italy Domain**. Normally, when a user in the **France Domain** wants to access a resource in the **Italy Domain**, they must go through the forest root, then down into the **Italy Domain**.

However, to speed up connections, the network administrator creates a **shortcut trust** directly between the **France Domain** and the **Italy Domain**.

----------------------------------------------------------------------------------------------------------------------------
A shortcut trust allows users from these two domains to communicate directly without going through the forest root, improving resource access performance. It avoids longer paths and optimizes resource management between domains.
----------------------------------------------------------------------------------------------------------------------------



### Forest Trust
Both **Division A** and **Division B** manage their own forests:
- **Europe Forest** (Division A).
- **America Forest** (Division B).

An interdivision project is launched to share some resources between the two divisions. Administrators decide to establish a **forest trust** between the **Europe Forest** and the **America Forest**.

--------------------------------------------------------------------------------------------------------------------------
A forest trust is manually configured to allow users in one forest to access resources in another forest. This enables, for example, an employee from **Division A** (Europe) to access files or databases in **Division B** (America). This trust is **transitive**, meaning that all domains within each forest can also trust each other.
---------------------------------------------------------------------------------------------------------------------------



### External Trust
TechCorp collaborates with another company, **PartnerCorp**, which has its own external domain called **Partner Domain**. However, both companies don’t want a full forest-to-forest relationship.

They create an **external trust** between TechCorp’s **Europe Domain** and PartnerCorp’s **Partner Domain**.

----------------------------------------------------------------------------------------------------------------------------
An external trust is used to connect two specific domains from different forests. Unlike a forest trust, it is **non-transitive**, meaning the trust does not extend to other domains in either forest. Only the two specific domains (in this case, **Europe Domain** and **Partner Domain**) can trust each other.
----------------------------------------------------------------------------------------------------------------------------

### Realm Trust

In another scenario, TechCorp uses a **UNIX server** with the Kerberos authentication system. They want to allow authentication between their Windows domains (like **Europe Domain**) and this UNIX server.

A **realm trust** is established to enable authentication between TechCorp’s Active Directory and the UNIX server.

---------------------------------------------------------------------------------------------------------------------------
A realm trust allows a trust relationship between a Windows Active Directory domain and another system using Kerberos, like a UNIX server. It enables secure cross-system authentication for users.
---------------------------------------------------------------------------------------------------------------------------



