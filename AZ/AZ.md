# AZ-104: Manage Identities and Governance in Azure

## Manage Identities and Governance in Azure

### Microsoft Entra ID

- Central identity service for Microsoft 365, Azure, Intune, Dynamics 365
- Provides authentication, authorization, and Single Sign-On (SSO)
- Works with on-premises AD DS and external logins (Google, Facebook, etc.)
- Can be configured using Azure Portal or Visual Studio
- Used in Azure Web Apps to restrict access to users in a selected Entra tenant

### Microsoft Entra ID P1 vs P2

**Common features (P1 & P2)**

- Requires extra license (included in Microsoft Enterprise Mobility + Security)
- 99.9% SLA uptime
- Advanced features beyond Free or Office 365 editions:
  - Self-service group management
  - Advanced security reports & alerts
  - Multi-Factor Authentication (MFA)
  - Microsoft Identity Manager (MIM) integration
  - Password reset with writeback
  - Cloud App Discovery
  - Conditional Access (device, group, location)
  - Microsoft Entra Connect Health

**P1 Key Features**

- Conditional Access based on user/device/location
- MFA for cloud and on-prem apps
- Self-service group & password management
- Security reports and anomaly detection
- Connect Health monitoring

**P2 Additional Features (All P1 + Extra Security)**

- Entra ID Protection: detects and responds to user and sign-in risks, supports risk-based conditional access
- Privileged Identity Management (PIM):
  - Just-in-Time (JIT) access for admins
  - Temporary elevation of privileges
  - Approval workflows and audit trails

**Feature Comparison Table**

| Feature | P1 | P2 |
|---------|----|----|
| Self-service group & password reset | ✅ | ✅ |
| MFA & Conditional Access | ✅ | ✅ |
| Connect Health & Security reports | ✅ | ✅ |
| ID Protection (risk policies) | ❌ | ✅ |
| Privileged Identity Management (PIM) | ❌ | ✅ |

### Privileged Identity Management (PIM)

- Controls, monitors, and limits access to privileged accounts (admins)
- Reduces risk of accidental or malicious misuse
- Key features:
  - Just-in-Time (JIT) access – temporary admin role activation
  - Approval workflow – manager approval required for some roles
  - MFA enforcement – admins authenticate to activate roles
  - Audit & reporting – logs all privilege activations
  - Role assignment management – controls who can activate which roles and for how long
  - Notifications – alerts for security teams or managers

**Example workflow**

- Global Admin wants to reset another admin’s password
- Requests role in PIM
- Authenticates with MFA
- Access granted for 1 hour
- Access expires automatically

### Just-in-Time (JIT) Access

- Reduces security risk by avoiding always-on admin privileges
- Workflow:
  - Admin requests elevated access for a specific task
  - Request goes through approval and policy checks
  - Access granted temporarily, automatically removed when time expires

### Microsoft Entra Domain Services (Entra DS)

- Managed Active Directory in Azure, provides domain services (Group Policy, domain join, Kerberos) without domain controllers
- Works with Entra ID P1 or P2 and compatible with on-prem AD
- Integrates with Entra Connect so users can use the same credentials on-prem and in cloud
- Can run as a cloud-only service (no local AD required)

**Benefits**

- No need to deploy or manage domain controllers
- No AD replication required
- No Domain Admin or Enterprise Admin groups needed
- Supports LDAP, NTLM, and Kerberos-based apps in Azure

**Limitations**

- Only base computer objects supported
- Schema cannot be extended
- Flat OU structure
- Built-in GPOs only, limited targeting

**Usage**

- Main use: Add Azure VMs to a domain without managing domain controllers
- Secondary use: Can work for on-prem PCs if network connectivity is set up (VPN/ExpressRoute)
