# 01 — Azure Cloud Adoption Framework (CAF)

## 1. What is CAF?

The Microsoft Cloud Adoption Framework for Azure is Microsoft's collection of guidance, methodologies and tools that helps organizations plan, prepare, adopt, govern, secure and manage Azure.

### Interview definition

> CAF is the organizational and technical roadmap for adopting Azure successfully. It helps an enterprise establish strategy, prepare people and processes, build the Azure foundation, adopt workloads, govern the environment, secure it and operate it over time.

## 2. CAF Adoption Phases

```text
Strategy
   |
   v
Plan
   |
   v
Ready
   |
   v
Adopt
   |
   +------> Govern
   |
   +------> Secure
   |
   +------> Manage
```

### Strategy

Question:

> Why are we adopting Azure and what business outcomes do we expect?

Examples:

- Reduce datacenter cost
- Improve scalability
- Modernize applications
- Improve time to market
- Meet resilience requirements

### Plan

Convert strategy into an actionable adoption plan.

Consider:

- People
- Skills
- Application inventory
- Migration waves
- Dependencies
- Timelines
- Budget

### Ready

Prepare Azure foundation and landing zones.

Typical areas:

- Tenant and identity
- Management groups
- Subscriptions
- Networking
- Governance
- Security
- Monitoring

### Adopt

Move or build workloads.

Common approaches:

```text
Rehost
Refactor
Rearchitect
Rebuild
Replace
Retain
Retire
```

### Govern

Establish organizational guardrails.

Examples:

- Azure Policy
- RBAC
- Resource naming
- Tags
- Allowed regions
- Compliance
- Cost controls

### Secure

Protect identity, network, data and workloads.

Examples:

- Microsoft Entra ID
- Defender for Cloud
- Key Vault
- Private Endpoints
- Network security
- Security monitoring

### Manage

Operate and optimize the environment.

Examples:

- Azure Monitor
- Log Analytics
- Alerts
- Backup
- Automation
- Cost management
- Incident management

## 3. CAF vs Landing Zone

CAF is broader.

```text
CAF
 |
 +-- Strategy
 +-- Plan
 +-- Ready
 |     |
 |     +-- Landing Zone
 |
 +-- Adopt
 +-- Govern
 +-- Secure
 +-- Manage
```

A landing zone is one of the key outputs of the Ready stage.

## 4. Interview Scenario

### Question

A company wants to migrate 300 applications to Azure. What do you do first?

### Strong answer

> I would not immediately provision application resources. I would start with CAF to define business outcomes, the adoption plan, operating model and governance requirements. Then I would build the Azure landing-zone foundation, including identity, management groups, subscription structure, networking, security, governance and monitoring. After that, applications can be migrated through defined workload landing zones.

## 5. Important CAF Principle

Do not think:

> CAF = migration only.

Think:

> CAF = the broader Azure adoption and operating journey.

## Official Reference

https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview
