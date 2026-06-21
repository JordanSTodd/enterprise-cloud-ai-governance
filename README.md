# Enterprise Cloud & AI Governance Deployment

## Project Overview
This project simulates the end-to-end deployment of a secure corporate cloud environment. It is divided into three phases, demonstrating practical execution of Microsoft's core cloud, security, and administrative frameworks.

### Phase 1: The Foundation & Governance (AZ-900 Focus)
**Objective:** Provision the core Azure infrastructure to establish a secure, software-defined network boundary, and apply strict governance controls to protect foundational assets.

**Technical Execution:**
* 🏗️ **Resource Management:** Deployed a centralized Azure Resource Group (`rg-enterprise-foundation`) in the East US region to logically contain and manage the lifecycle of foundational assets.
* 🌐 **Virtual Networking (VNet):** Engineered a secure Virtual Network (`vnet-enterprise-primary`) utilizing a standard `10.0.0.0/16` IP address space to facilitate isolated internal routing and future subnetting.
* 🔒 **Cloud Governance:** Deployed an Azure Resource Lock (`Delete` type) to the foundational resource group, strictly preventing accidental or unauthorized deletion of mission-critical cloud infrastructure.
* 📉 **Financial Governance:** Engineered an automated cloud spend guardrail by deploying a strict `$1.00` Azure Budget Alert (`Zero-Cost-Guardrail`) to instantaneously trigger email notifications upon any billing deviations.

**Project Evidence:**
* [View Azure Resource Group Deployment](./azure-rg-foundation.png)
* [View Virtual Network Deployment](./azure-vnet-deployment.png)
* [View Azure Resource Lock](./azure-resource-lock.png)
* [View Cost Management Budget Guardrail](./azure-budget-alert.png)

### Phase 2: Identity & Security Perimeter (SC-900 / SC-300 Focus)
**Objective:** Secure the cloud foundation by establishing robust identity management and a programmatic security perimeter.

**Technical Execution:**
* 💻 **Automated Identity Provisioning:** Executed a PowerShell automation script utilizing the Microsoft Graph API (`New-MgUser`) to programmatically deploy simulated corporate departments into Entra ID.
* ⚙️ **Dynamic Group Automation:** Engineered an Entra ID Dynamic Security Group (`Auto-Finance-Team`) utilizing attribute-based queries (`user.department -eq "Finance"`) to automate user lifecycle management and access provisioning.
* 🔐 **Role-Based Access Control (RBAC):** Enforced the Principle of Least Privilege by assigning targeted `Network Contributor` permissions to specific administrative accounts.
* 🛑 **Zero Trust Architecture:** Disabled baseline security defaults to engineer a custom Conditional Access policy (`Require-MFA-Privileged-Roles`), strictly enforcing Multi-Factor Authentication (MFA) for privileged cloud identities.
* ⏱️ **Privileged Access:** Configured Privileged Identity Management (PIM) for the `Global Administrator` role, enforcing Just-In-Time (JIT) access with a maximum `2-hour` activation window, requiring Azure MFA and written justification.
* 🛡️ **Attack Surface Reduction:** Deployed a Conditional Access policy (`Block-Legacy-Authentication`) targeting all cloud apps to strictly block legacy authentication protocols (e.g., Exchange ActiveSync), mitigating MFA bypass vulnerabilities while retaining a break-glass admin exclusion.
* 📋 **Identity Lifecycle Management:** Deployed an automated quarterly Access Review (`Quarterly-Finance-Access-Audit`) targeting the `Auto-Finance-Team` to continuously audit standing privileges, ensuring access is programmatically revoked if denied by the reviewer.

**Project Evidence:**
* [View API Execution & Verification](./powershell-graph-api-provisioning.png)
* [View Dynamic Group Automation](./entra-dynamic-group.png)
* [View Azure RBAC Assignment](./azure-rbac-assignment.png)
* [View Conditional Access MFA Policy](./entra-conditional-access-mfa.png)
* [View Privileged Identity Management Guardrails](./pim-jit-activation.png)
* [View Legacy Authentication Block Policy](./ca-block-legacy-auth.png)
* [View Automated Access Review Configuration](./entra-access-review.png)

### Phase 3: AI SaaS Rollout & Data Governance (AB-900 / Purview Focus)
**Objective:** Establish a secure data boundary prior to deploying AI tools (like Microsoft 365 Copilot) to prevent unauthorized extraction and exfiltration of confidential corporate data.

**Technical Execution:**
* 🛡️ **Information Protection:** Engineered a Microsoft Purview Sensitivity Label (`Confidential-Finance`) to classify and encrypt highly sensitive financial datasets, ensuring artificial intelligence agents cannot bypass human security clearances.
* 🛑 **Data Loss Prevention (DLP):** Designed an enterprise-wide DLP policy (`Block-External-Financial-Data`) to monitor and block the transmission of high-risk data. 
* ⚙️ **DLP Logic Enforced:** Configured pattern-matching for Sensitive Information Types (SITs) targeting `U.S. Bank Account` and `Credit Card Number` parameters within a custom rule (`Enforce Financial Data Protection`), programmatically blocking external sharing while satisfying mandatory Microsoft user notifications.

**Project Evidence:**
* [View Purview Data Governance Label](./purview-sensitivity-label.png?v=1)
* [View Data Loss Prevention Logic Setup](./purview-dlp-policy.png)
