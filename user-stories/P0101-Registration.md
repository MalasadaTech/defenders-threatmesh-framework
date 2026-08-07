---
pivot_code: P0101
title: Registration
category: Domain Registration
description: Compare registration details across malicious domains using RDAP and VirusTotal enrichment data to identify infrastructure patterns and cluster adversary operations.
tags: [registration, rdap, virustotal, whois, comparison, infrastructure-clustering, infrastructure-discovery]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0101 - Registration

**As a** cyber threat intelligence analyst  
**I want** to compare registration details between two or more malicious domains  
**So that** I can identify any patterns that exist and use them to discover additional adversary infrastructure based on registration similarities.

## Acceptance Criteria
- System enriches domains with registration data using the RDAP client (primary source for registrar, creation date, registrant, registrant email, and nameservers) and the VirusTotal client (supplementary whois/registration fields)
- When an analyst runs a comparison across multiple IOCs, the system automatically analyzes registration fields for statistically significant similarities
- Similarities are surfaced using the established P0101 sub-pivot clustering logic (Registrar, Registration date, Registrant, Registrant email, Name Server, Name Server Domain)
- Registration-based clusters and similarities are clearly presented to the analyst as actionable infrastructure pivots
- Analyst can easily use any identified registration pattern value for further hunting or pivoting

## Why This Pivot Matters
Domain registration data remains one of the most reliable sources for linking infrastructure even when other observables are heavily obfuscated. By comparing registration attributes (who registered the domains, when, through which registrar, and with what nameservers), analysts can uncover operational patterns used by the same threat actor or affiliate programs. The combination of RDAP (direct authoritative data) and VirusTotal (historical and supplemental context) provides robust coverage for this type of analysis.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Enrich via RDAP Client<br/>+ VirusTotal Client]
    
    B --> C[3. Extract Registration Fields<br/>Registrar, Dates, Registrant,<br/>Emails, Nameservers]
    
    C --> D[4. Comparison Engine<br/>Clusters Similarities<br/>across P0101 sub-pivots]
    
    D --> E{5. Significant Registration<br/>Patterns Detected?}
    
    E -->|Yes| F[6. High-Value Clusters<br/>Presented as Pivots]
    E -->|No| G[No Strong Registration<br/>Patterns Found]
    
    F --> H[7. Analyst Reviews Clusters<br/>and Selects Pivot Values]
    H --> I[8. Use Selected Registration<br/>Patterns for Further<br/>Infrastructure Discovery]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style F fill:#c8e6c9,stroke:#388e3c
    style I fill:#fff9c4,stroke:#f9a825
    style G fill:#f5f5f5,stroke:#666
```