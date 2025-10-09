# AZ-104 Notes

---
# Manage Identities and Governance in Azure
## Understand Entra ID
- Microsoft Entra ID overview  
- Microsoft Entra ID P1 vs P2 features  
- Privileged Identity Management (PIM)  
- Just-in-Time (JIT) Access  
- Microsoft Entra Domain Services (Entra DS)  
- Usage of Entra DS for Azure VMs and on-prem PCs  

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
|------|--------------|---------|----------|
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

✅ Confirm the user appears in the **All Users** list.

---

## Create a Security Group
**Path:** Entra admin center → *Identity → Groups → All Groups → + New group*  

**Example Configuration:**
- Group type: **Security**  
- Group name: **Marketing**  
- Membership type: **Assigned**  
- Owners: Admin account  
- Members: Kibble K  

✅ Verify the **Marketing** group appears in *All Groups*.

---

## Assign Licenses to a Group
1. Open **Marketing** group → *Manage → Licenses*.  
2. In **Microsoft 365 Admin Center**, go to *Billing → Licenses*.  
3. Choose a license → *Groups → + Assign license*.  
4. Select **Marketing** → *Assign*.  

✅ Message confirms successful license assignment.

**Key Point:**  
Group-based licensing automatically assigns licenses to all members.

---

## Remove or Restore a User
### Remove
- Go to **Users → All Users**.  
- Select checkbox next to the user (e.g., Kibble K).  
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

| Feature | **Security Group** | **Microsoft 365 Group** |
|----------|--------------------|--------------------------|
| Purpose | Manage access to resources | Enable collaboration |
| Includes | Permissions only | Permissions + collaboration tools |
| External Users | No | Yes |
| Shared Mailbox/Calendar | No | Yes |
| Created By | Admin | Users or Admins |
| Example | Access to Azure VM | Department collaboration in Teams |

---

## Membership Types

| Type | Description | Example Use |
|-------|-------------|--------------|
| **Assigned** | Members added manually | Small static teams |
| **Dynamic** | Members auto-added based on rules (e.g., department) | All users in HR |

**Dynamic Groups:**
- Automatically include users matching certain attributes.  
- Updates when user properties change.  
- Reduces manual work but requires careful rule design.

---

## Create a Microsoft 365 Group
**Path:** Entra admin center → *Identity → Groups → + New group*  

**Example Configuration:**
- Group type: **Microsoft 365**  
- Group name: **Accountant**  
- Membership type: **Assigned**  
- Owners: Admin account  
- Members: Add at least one member  

✅ Verify **Accountant** appears in *All Groups* (refresh if needed).

**Microsoft 365 Group Features:**
- Shared Outlook mailbox  
- Shared calendar  
- SharePoint site  
- Integration with Teams  

---

## Key Takeaways
- **User types:** Cloud, Directory-synced, Guest  
- **Group types:** Security (access) and Microsoft 365 (collaboration)  
- **Group-based licensing** = auto license assignment  
- **Deleted users** = recoverable for 30 days (soft-delete)  
- **Dynamic groups** = membership based on user attributes  

---
---