---
pivot_code: P0303
title: Not Before Date
category: SSL
description: Identify clusters of malicious domains whose SSL certificates were issued within a narrow time window (e.g., 7 days), indicating coordinated infrastructure deployment.
tags: [ssl, tls, certificate, not-before, validity, infrastructure-clustering]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0303 - Not Before Date

**As a** cyber threat intelligence analyst  
**I want** to compare the "Not Before" issuance dates of SSL certificates across my malicious IOCs  
**So that** I can detect coordinated campaigns where multiple domains were issued certificates within a short time window.

## Acceptance Criteria
- System collects certificate "Not Before" dates from the ssl-crt.sh Enricher and VirusTotal
- When comparing multiple IOCs, the system applies date window clustering (typically within a 7-day window) on certificate issuance dates
- Significant clusters of certificates issued in close temporal proximity are surfaced with date ranges and matching IOCs
- The system distinguishes between high-volume automated issuers and more targeted issuance patterns
- Analyst can use a tight issuance window as a strong temporal pivot for discovering additional campaign infrastructure

## Why This Pivot Matters
Adversaries often spin up large numbers of domains in short bursts for campaigns. When many of these domains receive SSL certificates within a narrow time window, it creates a powerful temporal signal. Clustering on "Not Before" dates has proven effective for linking infrastructure that would otherwise appear unrelated, especially when combined with other pivots such as domain characteristics or hosting data.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Retrieve Certificate Dates<br/>via ssl-crt.sh + VirusTotal]
    
    B --> C[3. Apply Date Window Clustering<br/>on Not Before Values]
    
    C --> D{4. Significant Issuance<br/>Window Clusters Found?}
    
    D -->|Yes| E[5. Temporal Clusters<br/>Presented as Strong Pivots]
    D -->|No| F[No Tight Issuance<br/>Windows Detected]
    
    E --> G[6. Analyst Reviews Certificate<br/>Issuance Time Windows]
    G --> H[7. Use Date Clusters to Hunt<br/>for Additional Campaign Domains]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style E fill:#c8e6c9,stroke:#388e3c
    style H fill:#fff9c4,stroke:#f9a825
    style F fill:#f5f5f5,stroke:#666
```