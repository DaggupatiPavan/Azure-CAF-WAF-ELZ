# 02 — Azure Well-Architected Framework (WAF)

> Note: In this document, WAF means **Well-Architected Framework**, not Web Application Firewall.

## 1. What is WAF?

Azure Well-Architected Framework is a design framework for evaluating and improving the quality of Azure workloads.

The five pillars are:

```text
                  WAF
                   |
      +------------+------------+
      |            |            |
 Reliability    Security    Cost Optimization
      |            |            |
      +------------+------------+
                   |
       +-----------+-----------+
       |                       |
Operational Excellence   Performance Efficiency
```

## 2. Reliability

### Question

> Will the workload continue operating and recover appropriately when failures occur?

Consider:

- Availability Zones
- Redundancy
- Health probes
- Load balancing
- Autoscaling
- Backup
- Disaster recovery
- RTO
- RPO
- Multi-region design where required

### Interview phrase

> I design for failure rather than assuming infrastructure will always be available.

## 3. Security

### Question

> Can unauthorized users, applications or networks access the workload?

Consider:

- Microsoft Entra ID
- RBAC
- Managed Identity
- Key Vault
- NSGs
- Azure Firewall
- Defender for Cloud
- Private Endpoints
- Encryption
- Secrets management
- Network segmentation

## 4. Cost Optimization

### Question

> Are we getting the required business value without unnecessary cloud spend?

Consider:

- Right sizing
- Autoscaling
- Reservations
- Savings Plans
- Storage lifecycle policies
- Non-production shutdown
- Budgets
- Cost allocation
- Tags

## 5. Operational Excellence

### Question

> Can the team deploy, observe, troubleshoot and operate the workload safely?

Consider:

- CI/CD
- Infrastructure as Code
- Automated testing
- Monitoring
- Logging
- Alerting
- Incident response
- Runbooks
- Standardization
- Safe deployment strategies

## 6. Performance Efficiency

### Question

> Can the workload meet performance requirements as demand changes?

Consider:

- Horizontal scaling
- Caching
- Load testing
- Capacity planning
- Database optimization
- CDN
- Queue-based architecture
- Performance monitoring

## 7. WAF Is About Trade-offs

The pillars are not independent.

Example:

```text
More redundancy
      |
      +--> Reliability improves
      |
      +--> Cost may increase
```

Another example:

```text
Aggressive caching
      |
      +--> Performance may improve
      |
      +--> Data freshness may decrease
```

A good architecture makes these trade-offs intentionally based on business requirements.

## 8. WAF Review Process

```text
Understand business requirements
             |
             v
Define functional + non-functional requirements
             |
             v
Review five WAF pillars
             |
             v
Identify risks / gaps
             |
             v
Prioritize improvements
             |
             v
Implement + measure
             |
             v
Review again
```

## 9. Interview Scenario

### Question

How would you review a production AKS workload?

### Answer structure

**Reliability**

- Multi-node/node-pool design
- Availability Zones where appropriate
- HPA
- Health probes
- Backup/DR requirements

**Security**

- Managed Identity
- Key Vault
- Network policies
- Private cluster/networking where appropriate
- Image scanning

**Cost**

- Right-sized node pools
- Autoscaling
- Workload requests/limits
- Non-prod optimization

**Operations**

- CI/CD
- GitOps if applicable
- Azure Monitor
- Log Analytics
- Alerts
- Runbooks

**Performance**

- Resource requests/limits
- HPA
- Load testing
- Application/database bottleneck analysis

## Official References

https://learn.microsoft.com/en-us/azure/well-architected/
https://learn.microsoft.com/en-us/azure/well-architected/pillars
