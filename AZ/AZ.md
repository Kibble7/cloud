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