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

## Phase 2: Identity & Zero-Trust Security (SC-900 Focus)
*(Conditional Access, Entra ID RBAC, and MFA configurations coming soon)*

## Phase 3: AI Governance & Data Loss Prevention (AB-900 Focus)
*(Microsoft Purview and Copilot administration policies coming soon)*
