# Manage Identities and Governance in Azure

## Understand Microsoft Entra ID

- **Microsoft Entra ID**: Cloud identity for authentication, authorization, and Single Sign-On (SSO) across Microsoft 365, Azure, and external apps  
- **P1**: Strong access control, monitoring, MFA, conditional access, self-service features  
- **P2**: Adds advanced risk protection (ID Protection) and temporary admin control (PIM)  
- **PIM**: Controls admin privileges using Just-in-Time (JIT) access, approval workflows, MFA, and auditing  
- **Just-in-Time (JIT) Access**: Provides temporary elevated access to reduce security risk  
- **Entra DS**: Managed Active Directory in Azure for domain join, Group Policy, and legacy app support without deploying domain controllers; works for Azure VMs and optionally on-prem PCs

---

## Understand Users and Groups in Microsoft Entra ID

- **User Accounts:** Each person accessing Azure resources needs an Entra ID user account for authentication and authorization  
- **User Types:**  
  - **Cloud Identity:** Created directly in Entra ID  
  - **Directory-Synchronized:** Synced from on-prem Active Directory  
  - **Guest:** External collaborators invited via email or other orgs  
- **Group Types:**  
  - **Security Group:** Used to assign access permissions to resources  
  - **Microsoft 365 Group:** Used for collaboration (email, Teams, SharePoint)  
- **Membership Types:**  
  - **Assigned:** Manually added members  
  - **Dynamic:** Automatically added based on rules or attributes  
- **Group-Based Licensing:** Automatically applies licenses to all members in a group  
- **User Lifecycle:** Users can be deleted and restored within 30 days (soft delete)  
- **Roles Required:** Global Admin, User Admin, or Partner Tier Support to manage users/groups  
- **Best Practice:** Use groups for access control, dynamic membership for automation, and guest accounts for temporary collaboration  

---
## Azure Policy – Quick Summary

- **Purpose:** Ensures Azure resources comply with organizational standards and regulatory requirements  
- **Policy Definition:** Written in JSON; defines rules and effects on resources  
- **Initiatives (Policy Sets):** Group multiple policies for easier management and compliance tracking  
- **Scope Levels:** Management Group → Subscription → Resource Group → Resource; higher-level policies inherit downward  
- **Assignments:** Apply policies or initiatives to specific resources or scopes; can include exemptions, parameters, and enforcement mode  
- **Exemptions:** Temporarily or permanently exclude resources from evaluation  
- **Attestations:** Manual confirmation of compliance where automation is not possible  
- **Remediations:** Automatically fix noncompliant resources  
- **Evaluation:** Triggered on assignment, updates, or resource changes; scans run automatically every 24 hours or manually  
- **Compliance States:** Compliant, Non-compliant, Error, Conflicting, Protected, Exempted, Unknown  
- **Enforcement Modes:** Enabled (active enforcement), Disabled (evaluation only, safe testing)  
- **Best Practices:** Start with disabled mode, deploy using rings, use Event Grid for automated compliance reactions

---
## Azure RBAC – Quick Summary

* **RBAC Purpose:** Controls **who** can do **what** and **where** in Azure, enforcing least privilege

* **Security Principals (Who):**
  * **User:** Individual user accounts
  * **Group:** Collection of users
  * **Service Principal:** App or service identity

* **Role Definitions (What):**
  * **Built-in roles:** Owner, Contributor, Reader, User Access Administrator
  * **Custom roles:** Can be created with specific permissions
  * **Permissions:** Defined as `Actions` (allowed) and `NotActions` (blocked)

* **Scope (Where):**
  * **Management Group → Subscription → Resource Group → Resource**
  * Permissions assigned at higher levels **inherit** downward

* **Role Assignment:**
  * Combines **Who + What + Where** to grant access
  * Removing the assignment immediately revokes access

* **RBAC Model:**
  * **Allow model:** Users can only perform allowed actions
  * **Effective permissions:** Actions − NotActions

* **Best Practice Tip:** Remember **“RBAC = WHO + WHAT + WHERE = Access”**

