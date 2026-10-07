# 04 — Azure CAF / WAF / ELZ Architecture Diagrams

All diagrams use Mermaid and can be rendered directly in many GitHub Markdown contexts.

---

## Diagram 1 — CAF Adoption Journey

```mermaid
flowchart LR
    A[Strategy] --> B[Plan]
    B --> C[Ready]
    C --> D[Adopt]
    D --> E[Govern]
    D --> F[Secure]
    D --> G[Manage]
    C --> H[Azure Landing Zone]
```

### 30-second explanation

CAF provides the adoption roadmap. Strategy defines the business outcomes, Plan prepares the organization, Ready establishes the landing zone, Adopt delivers workloads, and Govern/Secure/Manage establish ongoing controls and operations.

---

## Diagram 2 — Azure Hierarchy

```mermaid
flowchart TD
    T[Microsoft Entra Tenant]
    T --> MG[Management Groups]
    MG --> P[Platform Management Groups]
    MG --> L[Landing Zone Management Groups]

    P --> I[Identity]
    P --> C[Connectivity]
    P --> M[Management]
    P --> S[Security]

    L --> PROD[Production Subscriptions]
    L --> NONPROD[Non-Production Subscriptions]

    PROD --> RG1[Resource Groups]
    NONPROD --> RG2[Resource Groups]

    RG1 --> R1[Azure Resources]
    RG2 --> R2[Azure Resources]
```

---

## Diagram 3 — Enterprise Landing Zone

```mermaid
flowchart TB
    T[Azure / Entra Tenant]

    T --> MG[Management Group Hierarchy]

    MG --> PLATFORM[Platform]
    MG --> WORKLOADS[Landing Zones]

    PLATFORM --> ID[Identity]
    PLATFORM --> CONN[Connectivity]
    PLATFORM --> MON[Management]
    PLATFORM --> SEC[Security]

    WORKLOADS --> PROD[Production]
    WORKLOADS --> NONPROD[Non-Production]
    WORKLOADS --> SANDBOX[Sandbox]

    CONN --> HUB[Hub / Virtual WAN]
    HUB --> SPOKES[Workload VNets]

    PROD --> APP1[Application Workloads]
    NONPROD --> APP2[Development / Test]
```

---

## Diagram 4 — Hub-Spoke Connectivity

```mermaid
flowchart LR
    ONPREM[On-Premises] --> ER[ExpressRoute / VPN]
    ER --> HUB[Hub VNet]

    HUB --> FW[Azure Firewall]
    HUB --> DNS[Private DNS]
    HUB --> GW[Gateway]

    HUB --> S1[Spoke VNet - App A]
    HUB --> S2[Spoke VNet - App B]
    HUB --> S3[Spoke VNet - App C]
```

---

## Diagram 5 — Production Application

```mermaid
flowchart TB
    USER[Users]
    USER --> FD[Azure Front Door]
    FD --> AGW[Application Gateway]
    AGW --> AKS[AKS]

    AKS --> ACR[Azure Container Registry]
    AKS --> KV[Key Vault]
    AKS --> DB[Azure Database]
    AKS --> MON[Azure Monitor]

    MI[Managed Identity] --> AKS
    MI --> KV
```

---

## Diagram 6 — CI/CD to AKS

```mermaid
flowchart LR
    DEV[Developer] --> GIT[Git Repository]
    GIT --> CI[CI Pipeline]
    CI --> TEST[Test + Security Scan]
    TEST --> BUILD[Build Container Image]
    BUILD --> ACR[ACR]
    ACR --> CD[CD / GitOps]
    CD --> AKS[AKS]
    AKS --> MON[Azure Monitor]
```

---

## Diagram 7 — WAF Review

```mermaid
flowchart TD
    W[Workload]
    W --> R[Reliability]
    W --> S[Security]
    W --> C[Cost Optimization]
    W --> O[Operational Excellence]
    W --> P[Performance Efficiency]

    R --> OUT[Identify gaps and trade-offs]
    S --> OUT
    C --> OUT
    O --> OUT
    P --> OUT

    OUT --> IMP[Prioritize Improvements]
    IMP --> MEASURE[Implement + Measure]
    MEASURE --> W
```

---

## Diagram 8 — Complete Enterprise View

```mermaid
flowchart TB
    CAF[Cloud Adoption Framework]

    CAF --> LZ[Enterprise Landing Zone]

    LZ --> MG[Management Groups]
    MG --> PLATFORM[Platform Landing Zone]
    MG --> WL[Workload Landing Zones]

    PLATFORM --> ID[Identity]
    PLATFORM --> NET[Connectivity]
    PLATFORM --> SEC[Security]
    PLATFORM --> OPS[Management]

    WL --> APP1[Application A]
    WL --> APP2[Application B]
    WL --> APP3[Application C]

    APP1 --> WAF[Well-Architected Review]
    APP2 --> WAF
    APP3 --> WAF

    WAF --> REL[Reliability]
    WAF --> SEC2[Security]
    WAF --> COST[Cost]
    WAF --> OP[Operations]
    WAF --> PERF[Performance]
```
