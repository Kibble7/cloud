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
