# Azure CAF, WAF & Enterprise Landing Zone Guide

> A practical Azure architecture guide for DevOps, Platform Engineering, Cloud Engineering, and Azure architecture interviews.

## 1. The Big Picture

```text
Cloud Adoption Framework (CAF)
            |
            v
   Azure Landing Zone
            |
            +-----------------------------+
            |                             |
            v                             v
 Platform Landing Zone          Workload Landing Zones
            |                             |
 Identity / Connectivity /        Applications / Data /
 Management / Security            AKS / VMs / PaaS
            |                             |
            +--------------+--------------+
                           |
                           v
                 Azure Workloads
                           |
                           v
              Well-Architected Review
                           |
          +--------+-------+-------+-------+--------+
          |        |       |       |       |
       Reliable  Secure  Cost   Operations Performance
```

## 2. What Each Concept Means

| Concept | Simple meaning | Main question |
|---|---|---|
| CAF | Microsoft's cloud adoption guidance | How should the organization adopt Azure? |
| Landing Zone | Azure foundation and guardrails | What foundation should workloads deploy into? |
| Enterprise Landing Zone | Enterprise-scale landing-zone architecture | How do we govern Azure across many subscriptions/workloads? |
| WAF | Workload architecture quality framework | Is this workload reliable, secure, cost-effective, operationally excellent and performant? |

Microsoft's current CAF adoption roadmap includes Strategy, Plan, Ready, Adopt, Govern, Secure, and Manage.

## 3. Recommended Learning Order

1. [CAF](01-CAF.md)
2. [WAF](02-WAF.md)
3. [Enterprise Landing Zone](03-ELZ.md)
4. [Architecture Diagrams](04-Architecture-Diagrams.md)
5. [Official References](05-References.md)

## 4. Core Azure Hierarchy

```text
Microsoft Entra tenant
        |
        v
Management Groups
        |
        v
Subscriptions
        |
        v
Resource Groups
        |
        v
Azure Resources
```

## 5. Platform vs Workload Landing Zones

### Platform Landing Zone

Centralized services shared by workloads:

- Identity
- Connectivity
- Management
- Security
- Governance
- Shared services

### Workload Landing Zone

Environment where an application team deploys and operates its workload.

Examples:

- Production application
- Non-production application
- AKS platform
- Data platform
- Customer-facing API

## 6. Interview Mental Model

Use this sequence when answering an enterprise Azure architecture question:

```text
1. Business requirements
        |
2. CAF / adoption strategy
        |
3. Landing-zone foundation
        |
4. Management groups + subscriptions
        |
5. Identity + RBAC
        |
6. Networking + connectivity
        |
7. Governance + Azure Policy
        |
8. Security + monitoring
        |
9. Workload deployment
        |
10. WAF assessment
```

## 7. Senior DevOps / Platform Engineer Focus

Prioritize these topics:

- Management group hierarchy
- Subscription strategy
- Hub-spoke / Virtual WAN connectivity
- Azure Policy
- RBAC
- Microsoft Entra ID
- Managed Identity
- Key Vault
- Azure Firewall
- Private Endpoints / Private DNS
- Azure Monitor / Log Analytics
- AKS
- ACR
- Infrastructure as Code
- Subscription vending
- Governance
- Cost management
- Disaster recovery
- WAF trade-offs

## 8. Quick Interview Answer

**Question: How would you establish Azure for a large enterprise?**

> I would start with the Cloud Adoption Framework to define the cloud strategy, operating model and adoption plan. Then I would establish an Azure landing-zone foundation with management groups, subscriptions, identity, connectivity, governance, security and centralized management. Platform landing zones would provide shared services and guardrails, while workload landing zones would provide isolated environments for application teams. Finally, I would assess individual workloads using the Well-Architected Framework across reliability, security, cost optimization, operational excellence and performance efficiency.

## Official Microsoft References

See [05-References.md](05-References.md).
