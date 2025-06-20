## AZ-900 Exam Quick Reference

### Core Azure Concepts

| Term               | Summary                                               |
|--------------------|--------------------------------------------------------|
| Region             | Geographical area (e.g., East US).                   |
| Availability Zone  | Physically separate DCs (data center) in a region (for HA). |
| Availability Set   | Protects against hardware failure in a single DC (update + fault domain). |
| Resource Group     | Logical container for resources.                     |
| Azure Resource Manager (ARM) | Deployment and management service.              |
| Subscription       | Billing container for resources.                    |

### Azure Compute

| Service              | Purpose                              |
|----------------------|--------------------------------------|
| VMs                  | IaaS virtual machines.               |
| VMSS (Scale Sets)    | Auto-scale identical VMs.            |
| Azure Functions      | Serverless code execution.           |
| Azure App Service    | Host web apps (PaaS).                |
| Azure Batch          | Run large-scale parallel tasks.      |
| Azure Kubernetes Service (AKS) | Container orchestration.            |

### Azure Storage

| Type | Description |
|------|-------------|
| LRS  | 3 copies in one datacenter. |
| ZRS  | 3 copies in different zones in 1 region. |
| GRS  | LRS + secondary region (geo-redundant). |
| RA-GRS | GRS + read access to secondary. |
| GZRS | ZRS + GRS. |

| Tool   | Use                                |
|--------|-------------------------------------|
| AzCopy | Transfer data to/from Azure Storage. |

### Networking

| Term                  | Description                            |
|-----------------------|----------------------------------------|
| VNet                  | Virtual network.                       |
| VNet Peering          | Connect VNets (same or diff. regions). |
| VPN Gateway           | Connect on-prem to Azure over IPsec.  |
| NAT Gateway           | Outbound-only internet access.         |
| App Gateway           | L7 load balancer with WAF.             |
| Local Network Gateway | On-prem representation.                |
| Azure Firewall        | Managed, stateful firewall.            |
| NSG                   | ACL for network traffic.               |

### Monitoring & Analytics

| Tool               | Purpose                               |
|--------------------|----------------------------------------|
| Azure Monitor      | Collect metrics/logs.                 |
| Application Insights | App performance monitoring.          |
| Azure Advisor      | Best practices & cost tips.           |
| Azure Service Health | Service issue alerts.                |
| Log Analytics      | Analyze monitoring data.              |
| Azure Sentinel     | SIEM tool (security analytics).       |

### AI & ML Services

| Service              | Use                           |
|----------------------|-------------------------------|
| Cognitive Services   | Prebuilt AI (vision, speech, etc.). |
| Computer Vision / Custom Vision | Image recognition.     |
| Azure Machine Learning | Build/train models.          |
| Machine Learning Designer | Drag-and-drop ML pipeline. |

### IoT Services

| Service         | Use                               |
|------------------|------------------------------------|
| IoT Hub          | Central message hub for devices.  |
| IoT Central      | Simplified IoT app builder.       |
| Azure Sphere     | Secure MCU + OS + cloud security. |
| Digital Twins    | Real-world object modeling.       |

### Hybrid & Edge

| Term            | Description                              |
|------------------|------------------------------------------|
| Azure Arc        | Manage on-prem/multi-cloud resources.    |
| Azure Stack Edge | Azure-sent HW for edge compute & storage.|
| Data Box         | Azure HW for large offline data transfers.|

### Pricing & Support

| Term             | Description                               |
|------------------|-------------------------------------------|
| Pricing Tiers    | Free, Basic, Standard, Premium (depends on service). |
| Spot Pricing     | Unused compute at discount; may be evicted. |
| Reserved Pricing | 1 or 3-year commitment = discount.        |
| Consumption-based| Pay-as-you-go.                            |

### Security & Identity

| Service             | Use                                        |
|---------------------|---------------------------------------------|
| Azure AD            | Identity provider (SSO, MFA, RBAC).         |
| Security Center     | Unified security management.                |
| Service Trust Portal| Compliance reports.                         |
| Microsoft Trust Center | Transparency & privacy policies.        |

### Integration Tools

| Service         | Use                                  |
|------------------|---------------------------------------|
| Logic Apps       | Automate workflows.                  |
| Event Hubs       | Event ingestion for big data.        |
| Stream Analytics | Real-time data stream processing.    |
| Azure Data Factory | ETL (data integration pipeline).    |

### Data Services

| Service           | Purpose                                   |
|--------------------|-------------------------------------------|
| Azure Cosmos DB    | Globally distributed NoSQL DB.            |
| Azure SQL          | Managed SQL DB.                          |
| Azure Synapse      | Analytics + big data + warehousing.      |
| Azure Databricks   | Spark-based big data/ML platform.        |
| Power BI           | Data visualization and reporting.        |

### Misc. Concepts

| Concept                   | Description                                         |
|---------------------------|-----------------------------------------------------|
| Azure Plane               | Control plane (manage resources), Data plane (use resources). |
| Azure Portal / CLI / PowerShell / Cloud Shell | Management tools. |
| Application Gateway + WAF Policy | Protect web apps from common exploits.      |
| Azure Policy              | Enforce rules (e.g., tagging, region limits).       |
