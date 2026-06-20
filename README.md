# Enterprise Cloud & AI Governance Deployment

## Project Overview
This project simulates the end-to-end deployment of a secure corporate cloud environment. It is divided into three phases, demonstrating practical execution of Microsoft's core cloud, security, and administrative frameworks.

### Phase 1: The Foundation (AZ-900 Focus)
**Objective:** Provision the core Azure infrastructure to establish a secure, software-defined network boundary for future enterprise deployments.

**Technical Execution:**
* 🏗️ **Resource Management:** Deployed a centralized Azure Resource Group (`rg-enterprise-foundation`) in the East US region to logically contain and manage the lifecycle of foundational assets.
* 🌐 **Virtual Networking (VNet):** Engineered a secure Virtual Network (`vnet-enterprise-primary`) utilizing a standard `10.0.0.0/16` IP address space to facilitate isolated internal routing and future subnetting.

**Project Evidence:**
* [View Azure Resource Group Deployment](./azure-rg-foundation.png)
* [View Virtual Network Deployment](./azure-vnet-deployment.png)

### Phase 2: Identity & Security Perimeter (SC-900 / SC-300 Focus)
**Objective:** Secure the cloud foundation by establishing robust identity management and a programmatic security perimeter.

**Technical Execution:**
* 💻 **Automated Identity Provisioning:** Executed a PowerShell automation script utilizing the Microsoft Graph API to programmatically deploy simulated corporate departments into Entra ID.
* 🔐 **Role-Based Access Control (RBAC):** Enforced the Principle of Least Privilege by assigning targeted `Network Contributor` permissions to specific administrative accounts.
* 🛑 **Zero Trust Architecture:** Disabled baseline security defaults to engineer a custom Conditional Access policy, strictly enforcing Multi-Factor Authentication (MFA) for privileged cloud identities.

**Project Evidence:**
* [View API Execution & Verification](./powershell-graph-api-provisioning.png)
* [View Azure RBAC Assignment](./azure-rbac-assignment.png)
* [View Conditional Access MFA Policy](./entra-conditional-access-mfa.png)

### Phase 3: AI SaaS Rollout & Data Governance (AB-900 / Purview Focus)
**Objective:** Establish a secure data boundary prior to deploying AI tools (like Microsoft 365 Copilot) to prevent unauthorized extraction of confidential corporate data.

**Technical Execution:**
* 🛡️ **Information Protection:** Engineered a Microsoft Purview Sensitivity Label (`Confidential-Finance`) to classify and encrypt highly sensitive financial datasets.
* 🤖 **AI Governance:** Configured specific data loss prevention (DLP) guardrails to block AI Copilot indexing on labeled files, ensuring artificial intelligence agents cannot bypass human security clearances. 

**Project Evidence:**
* [View Purview Data Governance Label](./purview-sensitivity-label.png)
