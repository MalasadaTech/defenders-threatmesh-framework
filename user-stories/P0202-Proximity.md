---
pivot_code: P0202
title: Proximity
category: IP
description: Identify additional adversary infrastructure by analyzing IP addresses in close numeric or routing proximity to known malicious IPs, often revealing other domains on the same subnet or ASN routing path.
tags: [ip, proximity, subnet, asn-route, infrastructure-discovery]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0202 - Proximity

**As a** cyber threat intelligence analyst  
**I want** to examine IP addresses and routing paths in close proximity to my malicious IOCs  
**So that** I can discover additional adversary-controlled infrastructure on neighboring IPs or within the same hosting footprint.

## Acceptance Criteria
- System collects IP proximity and ASN routing data, primarily from URLScan (domain_asn_routes) and supplemented by IPInfo and Cymru enrichers
- When comparing multiple IOCs, the system surfaces statistically relevant overlaps in IP proximity or ASN-level routing paths
- Proximity-based clusters are presented clearly with context (e.g., same /24 subnet, same ASN route)
- Analyst can use identified neighboring IPs or routes as pivots for further hunting
- The system provides appropriate caveats when proximity signals appear in large shared hosting ranges

## Why This Pivot Matters
Sophisticated actors sometimes spread infrastructure across neighboring IPs within the same provider or ASN to maintain resilience while staying operationally close. Proximity pivots can reveal "sibling" infrastructure that would otherwise be missed by exact IP or domain matching. This technique has proven effective in campaigns such as Gootloader and various SEO poisoning operations.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Collect IP Proximity Data<br/>URLScan ASN Routes + IPInfo + Cymru]
    
    B --> C[3. Analyze Numeric and<br/>Routing Proximity Between IOCs]
    
    C --> D{4. Significant Proximity<br/>Clusters Detected?}
    
    D -->|Yes| E[5. Proximity-Based Clusters<br/>Presented to Analyst]
    D -->|No| F[No Strong Proximity<br/>Signals Found]
    
    E --> G[6. Analyst Reviews Neighboring<br/>IPs and Routing Paths]
    G --> H[7. Pivot to Discovered IPs<br/>for Additional Infrastructure<br/>Mapping]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style E fill:#c8e6c9,stroke:#388e3c
    style H fill:#fff9c4,stroke:#f9a825
    style F fill:#f5f5f5,stroke:#666
```