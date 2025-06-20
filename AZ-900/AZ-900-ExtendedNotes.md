## AZ-900 Extended Notes

### Compute Services

- **VMSS (Virtual Machine Scale Sets)**: Manage group of identical virtual machines.
- **MMD (Microsoft Managed Desktop)**: Automates provisioning, patching, and updates for desktop environments.
- **Azure App Service**: Host websites or web applications (PaaS).
- **Azure Batch**: Large-scale parallel/batch processing.
- **Azure Functions**: Serverless compute for event-driven tasks.
- **Availability Set**: Logical group of VMs for high availability against hardware or update failures.

---

### Storage Services & Redundancy

- **LRS (Locally Redundant Storage)**: 3 copies in a single datacenter.
- **ZRS (Zone-Redundant Storage)**: 3 copies across 3 availability zones in one region.
- **GRS (Geo-Redundant Storage)**: LRS + async replicate 3 copies to secondary region.
- **RA-GRS**: GRS + Read access to secondary region.
- **GZRS**: ZRS + Geo-replication.
- **RA-GZRS**: GZRS + Read access to secondary region.

#### Redundancy Summary Table
| Type      | Copies | Location                      | Use Case                             |
|-----------|--------|-------------------------------|--------------------------------------|
| LRS       | 3      | 1 datacenter                  | Low-cost, single-region workloads    |
| ZRS       | 3      | 3 zones in 1 region           | High availability                    |
| GRS       | 6      | 3 + 3 in another region       | Regional disaster recovery           |
| RA-GRS    | 6+read | Same as GRS + read access     | Reporting/Read-only access           |
| GZRS      | 6      | ZRS + region                  | High durability and HA               |
| RA-GZRS   | 6+read | GZRS + read                   | Critical apps with global reads      |

---

### Pricing & Expenditure Models

- **OpEx (Operational Expenditure)**: Ongoing cost for services.
- **CapEx (Capital Expenditure)**: One-time cost for physical assets.

#### Pricing Models
- **Pay-as-you-go**: Pay only for used resources.
- **Spot Instances**: Discounted pricing for unused capacity; may be interrupted.
- **Reserved Instances**: 1-3 year commitment with discounted pricing.
- **Consumption-based**: Ideal for serverless; pay for executions/requests.

---

### Data Services & Analytics

- **Azure Cosmos DB**: Globally distributed NoSQL database, supports SQL, MongoDB, Cassandra, Gremlin, Table APIs.
- **Azure HDInsight**: Open-source analytics (Hadoop, Spark, Hive, Kafka).
- **Azure Synapse Analytics**: Unified data warehouse and big data analytics platform.
- **Azure Analysis Services**: OLAP engine for BI tools like Power BI.
- **Power BI**: Visualize data and share insights.
- **Azure Monitor**: Full-stack monitoring platform.
- **Azure Stream Analytics**: Real-time event processing from Event Hubs/IoT.
- **Azure Event Hubs**: High-throughput event ingestion.

---

### AI & ML

- **Azure Machine Learning**: Build/train ML models.
- **Machine Learning Designer**: No-code ML pipelines.
- **Azure Cognitive Services**: Prebuilt APIs for vision, language, speech.
- **Azure Computer Vision**: Extract features from images.
- **LUIS**: Natural Language Understanding (NLU) service.
- **QnA Maker**: Convert FAQs into conversational bots.

---

### IoT

- **Azure IoT Hub**: Bi-directional communication between cloud and devices.
- **Azure IoT Central**: IoT app platform for reduced development overhead.
- **Azure Digital Twins**: Model and simulate real-world environments.
- **Azure Sphere**: Secure microcontroller + OS + cloud services.

---

### Governance & Management

- **Azure Blueprints**: Combine templates, policies, and RBAC for environment setup.
- **Azure Policy**: Enforce rules like allowed regions, VM types, etc.
- **ARM (Azure Resource Manager)**: Template-driven deployment and management.
- **Azure Advisor**: Personalized recommendations on cost, security, reliability, performance, and operations.
- **Azure TCO Calculator**:
  1. Define workloads
  2. Define assumptions
  3. Generate report

---

### Hybrid & Multi-Cloud

- **Azure Arc**: Manage on-prem, multi-cloud, and edge resources with Azure tools.
- **Azure Stack**:
  - **Hub**: Full Azure in disconnected environments
  - **Edge**: Edge computing + AI/ML
  - **HCI**: Hyperconverged infrastructure for VMs

---

### Network & Security

#### Network Gateways
| Service               | Purpose                                                  |
|------------------------|----------------------------------------------------------|
| NAT Gateway            | Outbound internet access with static IP                 |
| App Gateway + WAF      | HTTP load balancer with Web Application Firewall        |
| Virtual Network Gateway| Enables VPN/ExpressRoute                                |
| Local Network Gateway  | Represents on-prem in hybrid setup                      |
| On-prem Data Gateway   | Connect on-prem data sources (e.g. Power BI)            |
| Data Box Gateway       | Transfer large/ongoing data to Azure                    |
| Azure Stack Edge       | Local compute + data processing + Azure sync            |

---

### Planes in Azure

- **Control Plane**: Manages Azure resources (create, update, delete)
  - Interfaces: Azure Portal, CLI, PowerShell, ARM
- **Data Plane**: Operates on the data inside resources
  - Examples: Reading from Blob storage, querying SQL

---

### Reliability vs Resilience

- **Reliability**: Ensure service availability (SLAs, AZs, failover)
- **Resilience**: Recover from failure (backups, geo-replication, self-healing)

---

### Roles in RBAC

- **Owner**: Full access + can assign roles.
- **Contributor**: Full access, can't assign roles.

---

### Microsoft Adoption Framework

- A structured approach for cloud adoption, governance, and strategy.
