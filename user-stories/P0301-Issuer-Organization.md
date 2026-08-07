---
pivot_code: P0301
title: Issuer Organization
category: SSL
description: Compare SSL/TLS certificate issuer organizations across malicious domains to identify infrastructure operated under certificates from the same issuing authority or organization.
tags: [ssl, tls, certificate, issuer, infrastructure-clustering]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0301 - Issuer Organization

**As a** cyber threat intelligence analyst  
**I want** to compare the issuing organizations of SSL certificates used by my malicious IOCs  
**So that** I can identify patterns in certificate usage that reveal additional adversary infrastructure.

## Acceptance Criteria
- System retrieves certificate data primarily from the ssl-crt.sh Enricher and supplements with certificate information from VirusTotal
- When comparing multiple IOCs, the system clusters on the Issuer Organization field (P0301)
- Statistically significant overlaps in certificate issuers are surfaced as clusters with counts and matching IOCs
- The system handles common issuers (e.g., Let's Encrypt, Sectigo, DigiCert) appropriately while still surfacing meaningful clusters
- Analyst can use a shared issuer organization as a pivot for further hunting in certificate transparency logs or domain intelligence platforms

## Why This Pivot Matters
Threat actors frequently reuse the same certificate authorities or even the same automated issuance processes across campaigns. Clustering by issuer organization (especially when combined with other pivots) can surface related domains that were issued certificates around the same time or from the same account/automation pipeline. This technique has been particularly useful against groups like SmartApeSG that rely heavily on free certificate services.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Enrich via ssl-crt.sh Enricher<br/>+ VirusTotal Certificate Data]
    
    B --> C[3. Extract and Cluster<br/>by Issuer Organization]
    
    C --> D{4. Significant Issuer<br/>Clusters Found?}
    
    D -->|Yes| E[5. Issuer-Based Clusters<br/>Presented as Pivots]
    D -->|No| F[No Strong Issuer<br/>Overlap Detected]
    
    E --> G[6. Analyst Reviews Shared<br/>Certificate Issuers]
    G --> H[7. Pivot on Issuer Org<br/>for Expanded Infrastructure<br/>Discovery]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style E fill:#c8e6c9,stroke:#388e3c
    style H fill:#fff9c4,stroke:#f9a825
    style F fill:#f5f5f5,stroke:#666
```