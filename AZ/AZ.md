# AZ-104 Notes

---
# Manage Identities and Governance in Azure

## Table of Contents
- [Microsoft Entra ID](#microsoft-entra-id)
- [Microsoft Entra ID P1 vs P2](#microsoft-entra-id-p1-vs-p2)
- [Privileged Identity Management (PIM)](#privileged-identity-management-pim)
- [Just-in-Time (JIT) Access](#just-in-time-jit-access)
- [Microsoft Entra Domain Services (Entra DS)](#microsoft-entra-domain-services-entra-ds)

---

## Microsoft Entra ID
- Central identity service for Microsoft 365, Azure, Intune, Dynamics 365  
- Provides authentication, authorization, and Single Sign-On (SSO)  
- Works with on-prem AD DS and external logins (Google, Facebook, etc.)  
- Configurable via Azure Portal or Visual Studio  
- Used in Azure Web Apps to restrict access to users in a selected Entra tenant  

---

## Microsoft Entra ID P1 vs P2

### Common Features (P1 & P2)
- Extra license required (part of Microsoft Enterprise Mobility + Security)  
- 99.9% SLA uptime  
- Advanced features:
  - Self-service group management  
  - Advanced security reports & alerts  
  - Multi-Factor Authentication (MFA)  
  - Microsoft Identity Manager (MIM) integration  
  - Password reset with writeback  
  - Cloud App Discovery  
  - Conditional Access (device, group, location)  
  - Microsoft Entra Connect Health  

### P1 Key Features
- Conditional Access based on user/device/location  
- MFA for cloud and on-prem apps  
- Self-service group & password management  
- Security reports and anomaly detection  
- Connect Health monitoring  

### P2 Additional Features
- Includes all P1 features  
- Entra ID Protection: detects user/sign-in risks and allows risk-based conditional access  
- Privileged Identity Management (PIM):
  - Just-in-Time (JIT) access for admins  
  - Temporary admin privileges  
  - Approval workflows and audit trails  

### Feature Comparison Table

| Feature | P1 | P2 |
|---------|----|----|
| Self-service group & password reset | ✅ | ✅ |
| MFA & Conditional Access | ✅ | ✅ |
| Connect Health & Security reports | ✅ | ✅ |
| ID Protection (risk policies) | ❌ | ✅ |
| Privileged Identity Management (PIM) | ❌ | ✅ |

---

## Privileged Identity Management (PIM)
- Controls and limits access to privileged accounts (admins)  
- Reduces risk of misuse  
- Key Features:
  - Just-in-Time (JIT) access – temporary role activation  
  - Approval workflow – manager approval for some roles  
  - MFA enforcement  
  - Audit & reporting  
  - Role assignment management  
  - Notifications  

**Example**
- Admin wants to reset another admin’s password  
- Requests role in PIM  
- Authenticates with MFA  
- Access granted for 1 hour  
- Access expires automatically  

---

## Just-in-Time (JIT) Access
- Reduces security risk by avoiding always-on admin privileges  
- Admin requests elevated access for a task  
- Request goes through approval/policy checks  
- Access granted temporarily and removed automatically  

---

## Microsoft Entra Domain Services (Entra DS)
- Managed Active Directory in Azure  
- Provides Group Policy, domain join, Kerberos without domain controllers  
- Works with Entra ID P1 or P2 and compatible with on-prem AD  
- Can run cloud-only (no local AD required)  

### Benefits
- No need to deploy or manage domain controllers  
- No AD replication required  
- No Domain Admin or Enterprise Admin groups needed  
- Supports LDAP, NTLM, Kerberos apps  

### Limitations
- Only base computer objects supported  
- Schema cannot be extended  
- Flat OU structure  
- Built-in GPOs only, limited targeting  

### Usage
- Main: Add Azure VMs to domain without managing domain controllers  
- Secondary: Can work for on-prem PCs if VPN/ExpressRoute is set up  


---

---

# Create, Configure, and Manage Users & Groups in Microsoft Entra ID

## Table of Contents
- [Understand User Management](#understand-user-management)  
- [View Users](#view-users)  
- [Define User Types](#define-user-types)  
- [Create a New User](#create-a-new-user)  
- [Create a Security Group](#create-a-security-group)  
- [Assign Licenses to a Group](#assign-licenses-to-a-group)  
- [Remove or Restore a User](#remove-or-restore-a-user)  
- [Understand Groups](#understand-groups)  
- [Types of Groups](#types-of-groups)  
- [Membership Types](#membership-types)  
- [Create a Microsoft 365 Group](#create-a-microsoft-365-group)  
- [Key Takeaways](#key-takeaways)  
- [Manage Licenses](#manage-licenses)  
- [Custom Security Attributes](#custom-security-attributes)  
- [SCIM (System for Cross-Domain Identity Management)](#scim-system-for-cross-domain-identity-management)  

---

## Understand User Management
- Each person accessing Azure resources must have a user account in Microsoft Entra ID.  
- The account stores authentication info and issues access tokens for authorization.  
- Manage users via **Microsoft Entra admin center** → *Identity → Users*.  
- You can only work with one directory at a time but can switch using:  
  - **Directory + Subscription panel**, or  
  - **Switch directory** button in the toolbar.  

---

## View Users
- Navigate to **Identity → Users → All Users**.  
- **User Types:**
  - **Member:** Internal organization user  
  - **Guest:** External invited user  

---

## Define User Types

| Type | Description | Source | Example |
|------|-------------|--------|---------|
| **Cloud Identity** | Created and managed directly in Entra ID | Microsoft Entra ID | Admin or manually created users |
| **Directory-Synchronized Identity** | Synced from on-prem Active Directory using Entra Connect | Windows Server AD | Employees managed via on-prem AD |
| **Guest User** | External collaborator invited from another org or Microsoft account | Invited user | Vendor, contractor, or partner |

**Notes:**
- Removing a user deletes their Azure access completely.  
- Guest accounts are ideal for temporary access.  
- Directory-synced users depend on on-prem AD lifecycle.  

---

## Create a New User
**Path:** Entra admin center → *Identity → Users → All Users → + New user*  

**Example Values:**
- User principal name: `KibbleK`  
- Name: Kibble K  
- First name: Kibble  
- Last name: K  
- Password: Unique password  

**Note:** Confirm the user appears in the **All Users** list.

---

## Create a Security Group
**Path:** Entra admin center → *Identity → Groups → All Groups → + New group*  

**Example Configuration:**
- Group type: **Security**  
- Group name: **Marketing**  
- Membership type: **Assigned**  
- Owners: Admin account  
- Members: Kibble K  

**Note:** Verify the **Marketing** group appears in *All Groups*.

---

## Assign Licenses to a Group
1. Open **Marketing** group → *Manage → Licenses*.  
2. In **Microsoft 365 Admin Center**, go to *Billing → Licenses*.  
3. Choose a license → *Groups → + Assign license*.  
4. Select **Marketing** → *Assign*.  

**Note:** Message confirms successful license assignment.  
**Key Point:** Group-based licensing automatically assigns licenses to all members.

---

## Remove or Restore a User
### Remove
- Go to **Users → All Users**.  
- Select the checkbox next to the user (e.g., Kibble K).  
- Choose **Delete user → OK**.

### Restore
- Go to **Users → Deleted users**.  
- Select the user → **Restore user → OK**.  
- Verify restored user under *All Users*.

**Notes:**
- **Soft-delete period:** 30 days (recoverable).  
- **Permanent deletion:** After 30 days, cannot be restored.  
- **Roles required:** Global Admin, User Admin, Partner Tier-1/2 Support.  

---

## Understand Groups
- Groups organize users for easier permission management.  
- Access is granted to all group members at once.  
- Groups serve as **security boundaries**.  
- Membership can be **assigned** or **dynamic** (rule-based).  

---

## Types of Groups

| Feature | Security Group | Microsoft 365 Group |
|---------|----------------|-------------------|
| Purpose | Manage access to resources | Enable collaboration |
| Includes | Permissions only | Permissions + collaboration tools |
| External Users | No | Yes |
| Shared Mailbox/Calendar | No | Yes |
| Created By | Admin | Users or Admins |
| Example | Access to Azure VM | Department collaboration in Teams |

---

## Membership Types

| Type | Description | Example Use |
|------|------------|-------------|
| **Assigned** | Members added manually | Small static teams |
| **Dynamic** | Members auto-added based on rules (e.g., department) | All users in HR |

**Dynamic Groups:**
- Automatically include users matching certain attributes.  
- Updates when user properties change.  
- Reduces manual work but requires careful rule design.  

---

## Create a Microsoft 365 Group
**Path:** Entra admin center → *Identity → Groups → + New group*


---
---

# Describe the Core Architectural Components of Azure

## Table of Contents
- [Azure Accounts & Subscriptions](#azure-accounts--subscriptions)
- [Azure Physical Infrastructure](#azure-physical-infrastructure)
- [Regions & Availability Zones](#regions--availability-zones)
- [Region Pairs](#region-pairs)
- [Sovereign Regions](#sovereign-regions)
- [Resources & Resource Groups](#resources--resource-groups)
- [Azure Subscriptions](#azure-subscriptions)
- [Management Groups](#management-groups)
- [Hierarchy Overview](#hierarchy-overview)
- [Quick Memory Tips](#quick-memory-tips)

---

## Azure Accounts & Subscriptions

- You need an **Azure account** to use Azure services.  
- A new account includes **one subscription** by default.  
- Add more subscriptions for dev, test, or departments.  
- **BYOS (Bring Your Own Subscription)** is used in labs — always clean up to avoid costs.

**Scope Levels:**  
Azure Account → Subscription → Resource Group → Resources  

---

## Azure Physical Infrastructure

**Azure Infrastructure = Physical + Management**

- **Physical:** Datacenters with servers, power, cooling, and networking.  
- **Management:** Tools and controls for managing those datacenters.  
- Datacenters are grouped into **Regions** and **Availability Zones**.

---

## Regions & Availability Zones

### Regions
- A **region** is an area with one or more connected datacenters.  
- Choose a region when creating resources.  
- Some services are **global** (like Entra ID, DNS, Traffic Manager).  
- Examples: East US, West Europe, Southeast Asia.

### Availability Zones
- Physically separate datacenters within a region.  
- Each has independent power, cooling, and networking.  
- Used for **fault isolation** and **high availability**.  
- Most regions have **3 Availability Zones**.

| Type | Description | Example |
|------|--------------|----------|
| Zonal | Pinned to one zone | VM |
| Zone-redundant | Replicated across zones | SQL DB, Load Balancer |
| Non-regional | Global service | Entra ID, DNS |

---

## Region Pairs

- Two regions in the same area, about 300 miles apart.  
- Provide **backup and disaster recovery**.  
- Updates happen in one region at a time.  
- Data stays within the same geography (except Brazil South).  

**Example:** West US ↔ East US  

---

## Sovereign Regions

- Dedicated Azure regions for **government or legal compliance**.  
- **Examples:**
  - US Gov regions (Gov Virginia, DoD Central)
  - China regions (operated by 21Vianet)

---

## Resources & Resource Groups

- **Resource:** The basic Azure component (VM, DB, app, network).  
- **Resource Group:** A container for related resources.  
  - A resource belongs to **only one group**.  
  - Resource groups **cannot be nested**.  
  - Group actions (delete, permissions) affect all inside.  

**Use Cases:**
- Temporary test environments → easy cleanup.  
- Grouping by access or policy → easier control.  

---

## Azure Subscriptions

- A **subscription** is a unit for **billing, management, and access control**.  
- Linked to a single Azure account (identity in Entra ID).  
- One account can have multiple subscriptions.  

**Use Cases:**
- Separate billing per department.  
- Divide environments: dev, test, production.  
- Apply different access or policy controls.  

---

## Management Groups

- Container for **multiple subscriptions**.  
- Used for large-scale **policy and access management**.  
- Subscriptions **inherit** policies and permissions from their management group.  
- Can be **nested** up to 6 levels deep.  

**Use Cases:**
- Apply one policy (like allowed regions) to all subscriptions.  
- Assign RBAC roles once across all child subscriptions.  

**Limits:**
- 10,000 management groups per directory.  
- 6 levels deep (excluding root and subscription).  
- Each group/subscription has only one parent.  

---

## Hierarchy Overview

Resource → Resource Group → Subscription → Management Group → Directory  

**Example Structure:**  
- Root Management Group  
  - IT  
    - Dev/Test Subscription  
    - Production Subscription  
  - Marketing  
    - Apps Subscription  

---

## Quick Memory Tips

- **Region** → Location  
- **Zone** → Local backup  
- **Pair** → Regional backup  
- **Sovereign** → Government or special use  

---
---
