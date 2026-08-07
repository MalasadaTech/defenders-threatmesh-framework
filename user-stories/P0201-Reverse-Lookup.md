---
pivot_code: P0201
title: Reverse Lookup
category: IP
description: Identify additional adversary infrastructure by finding other domains that resolve to the same IP address(es) as known malicious domains, indicating shared hosting or infrastructure.
tags: [ip, reverse-lookup, shared-hosting, infrastructure-clustering]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0201 - Reverse Lookup

**As a** cyber threat intelligence analyst  
**I want** to identify other domains that share the same IP address as my malicious IOCs  
**So that** I can discover additional adversary infrastructure hosted on the same servers or infrastructure.

## Acceptance Criteria
- System resolves domains to IP addresses using the DNS Enricher and supplements with IP data from VirusTotal, URLScan, and OTX passive DNS
- When comparing multiple IOCs, the system identifies statistically significant overlaps in resolved IP addresses
- Shared IP addresses are surfaced as high-value clusters (often overlapping with P0103.003 - DNS: IP Address logic)
- Analyst can easily pivot from a shared IP to hunt for additional domains in threat intelligence platforms
- Results distinguish between dedicated IPs and heavily shared hosting providers where appropriate

## Why This Pivot Matters
Reverse IP lookups remain one of the most direct ways to uncover related infrastructure. When multiple malicious domains resolve to the same IP (especially non-shared or cloud-hosted IPs), it is a strong indicator of common ownership or operational control. This technique is particularly effective against actors who reuse the same bulletproof hosting or VPS providers across campaigns.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Resolve IPs via DNS Enricher<br/>+ VirusTotal + URLScan + OTX]
    
    B --> C[3. Cluster Domains<br/>by Shared IP Addresses]
    
    C --> D{4. Significant Shared<br/>IP Clusters Found?}
    
    D -->|Yes| E[5. High-Value Clusters<br/>Presented as Pivots]
    D -->|No| F[No Strong Reverse<br/>Lookup Clusters]
    
    E --> G[6. Analyst Reviews Shared IPs<br/>and Associated Domains]
    G --> H[7. Use Shared IPs or Related Domains<br/>for Expanded Infrastructure<br/>Discovery]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style E fill:#c8e6c9,stroke:#388e3c
    style H fill:#fff9c4,stroke:#f9a825
    style F fill:#f5f5f5,stroke:#666
```