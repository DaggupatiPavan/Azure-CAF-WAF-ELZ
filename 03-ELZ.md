# 03 — Enterprise Landing Zone (ELZ)

## 1. What is an Azure Landing Zone?

An Azure landing zone is a scalable foundation for governing, securing and operating Azure workloads.

Microsoft's current landing-zone model has two major components:

```text
Azure Landing Zone
       |
       +----------------------+
       |                      |
       v                      v
Platform Landing Zone   Workload Landing Zones
```

## 2. Platform Landing Zone

The platform landing zone provides centralized capabilities shared by workloads.

Typical areas:

```text
Platform
 |
 +-- Identity
 |
 +-- Connectivity
 |
 +-- Management
 |
 +-- Security
 |
 +-- Shared Services
```

## 3. Workload Landing Zone

A workload landing zone is where an application/workload is deployed.

Example:

```text
Landing Zone
 |
 +-- E-commerce Production
 |      |
 |      +-- AKS
 |      +-- Azure SQL
 |      +-- Storage
 |
 +-- E-commerce NonProd
        |
        +-- AKS
        +-- Azure SQL
        +-- Storage
```

## 4. Enterprise Hierarchy

```text
Microsoft Entra Tenant
        |
        v
Management Groups
        |
        +-------------------------+
        |                         |
        v                         v
    Platform                Landing Zones
        |                         |
   +----+----+               +----+----+
   |    |    |               |         |
Identity Connectivity      Prod      NonProd
Management Security
```

The exact management-group hierarchy should be adapted to organizational requirements. Avoid creating management groups merely to mirror the organizational chart.

## 5. Why Management Groups?

Management groups allow governance to be applied above subscriptions.

Example:

```text
Management Group
       |
       +-- Azure Policy
       |
       +-- RBAC
       |
       +-- Compliance controls
       |
       v
Multiple subscriptions
```

This creates inherited governance.

## 6. Subscription Strategy

Subscriptions can provide:

- Billing boundaries
- Administrative boundaries
- Workload isolation
- Quota boundaries
- Environment separation
- Governance boundaries

Example:

```text
Application A
 |
 +-- Prod Subscription
 +-- NonProd Subscription

Application B
 |
 +-- Prod Subscription
 +-- NonProd Subscription
```

Do not assume this exact model fits every organization.

## 7. Connectivity

A large enterprise typically needs centralized connectivity.

Common patterns:

### Hub-Spoke

```text
                  On-Premises
                       |
                 ExpressRoute/VPN
                       |
                    Hub VNet
                 /      |                      /       |                   Spoke A   Spoke B   Spoke C
            App A     App B     App C
```

Hub commonly hosts shared connectivity/security services.

### Virtual WAN

For larger distributed environments, Azure Virtual WAN can provide a managed networking architecture.

## 8. Governance

Important controls:

### Azure Policy

Examples:

```text
Allowed regions
Required tags
Allowed resource SKUs
Security configurations
Diagnostic settings
```

### RBAC

Controls who can perform which actions at a given scope.

Scopes include:

```text
Management Group
Subscription
Resource Group
Resource
```

## 9. Identity

Use Microsoft Entra ID and Azure RBAC.

Prefer:

```text
Application
   |
Managed Identity
   |
Entra ID
   |
Azure Resource
```

instead of embedding long-lived credentials in applications.

## 10. Security

Typical enterprise controls:

- Microsoft Defender for Cloud
- Azure Firewall
- NSGs
- DDoS Protection where appropriate
- Key Vault
- Private Endpoints
- Private DNS
- Centralized logging
- Security monitoring

## 11. Management

Central management commonly includes:

- Azure Monitor
- Log Analytics
- Alerts
- Automation
- Backup
- Update management capabilities
- Cost Management

## 12. Subscription Vending

Subscription vending means creating standardized subscriptions through an automated process.

Example:

```text
Application team request
          |
          v
Subscription vending workflow
          |
          +-- Create subscription
          +-- Assign management group
          +-- Apply policies
          +-- Configure RBAC
          +-- Configure networking
          +-- Configure monitoring
          +-- Apply tags
          |
          v
Ready-to-use subscription
```

This is highly relevant for Platform Engineering.

## 13. Infrastructure as Code

A mature landing-zone implementation should be automated.

Typical technologies:

- Terraform
- Bicep
- ARM templates
- Azure Verified Modules

Conceptually:

```text
Git
 |
 v
Pull Request
 |
 v
Validation
 |
 v
Plan
 |
 v
Approval
 |
 v
Apply
 |
 v
Azure Landing Zone
```

## 14. Enterprise Landing Zone vs Workload Landing Zone

| Area | Platform Landing Zone | Workload Landing Zone |
|---|---|---|
| Identity | Centralized | Consumes identity |
| Connectivity | Centralized | Uses approved connectivity |
| Governance | Defines guardrails | Operates within guardrails |
| Security | Shared controls | Workload-specific controls |
| Monitoring | Central platform capabilities | Workload telemetry |
| Applications | Usually no | Yes |

## 15. Interview Scenario

### Question

Why not put all applications into one subscription?

### Answer

> A single subscription can create operational, governance, quota, access and blast-radius challenges at enterprise scale. Subscription boundaries can provide isolation for billing, administration, quotas, workload ownership and governance. The exact subscription model should be based on organizational and workload requirements rather than applying one rigid pattern everywhere.

## Official References

https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/
https://learn.microsoft.com/en-us/azure/architecture/landing-zones/
