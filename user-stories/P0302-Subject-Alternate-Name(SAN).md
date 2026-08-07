---
pivot_code: P0302
title: Subject Alternate Name (SAN)
category: Certificate Analysis
description: Identify extra/unrelated domains in a certificate's Subject Alternative Name (SAN) list as high-value pivots for infrastructure discovery.
tags: [tls, certificate, san, pivot, infrastructure-discovery]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0302 - Subject Alternate Name (SAN)

**As a** cyber threat intelligence analyst  
**I want** to automatically check the TLS Subject Alternative Names (SANs) of a malicious domain IOC  
**So that** I can identify additional domains controlled by the same adversary and expand my infrastructure mapping.

## Acceptance Criteria
- System retrieves certificate enrichment data (e.g., from VirusTotal) for the IOC
- Automatically identifies and highlights any SAN entries that do **not** contain the primary domain base name
- Presents a clean list of “extra” SAN domains as high-value pivots
- Analyst can easily select any extra SAN to use as a new IOC for further hunting

## Workflow

```mermaid
flowchart TD
    A[**1.** Malicious Domain IOC<br/>e.g. scoredon.com] 
    --> B[**2.** Query VirusTotal<br/>Certificate Enrichment]
    
    B --> C[**3.** Extract TLS Certificate<br/>SAN List]
    
    C --> D[**4.** Filter SANs that do NOT<br/>contain primary domain<br/>base name]
    
    D --> E{**5.** Extra / Unrelated<br/>SANs Found?}
    
    E -->|Yes| F[**6.** High-Value Pivot<br/>List of Extra Domains]
    E -->|No| G[No Additional Pivots<br/>from this Certificate]
    
    F --> H[**7.** Present to Analyst<br/>Review & Select Pivots]
    H --> I[**8.** Use Selected SANs as New IOCs<br/>for Infrastructure Clustering]

    style A fill:#e3f2fd,stroke:#1976d2
    style F fill:#c8e6c9,stroke:#388e3c
    style I fill:#fff9c4,stroke:#f9a825
    style G fill:#f5f5f5,stroke:#666