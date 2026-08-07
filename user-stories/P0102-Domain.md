---
pivot_code: P0102
title: Domain
category: Domain Characteristics
description: Analyze and compare domain name characteristics (TLD, substrings, length, and structure) across malicious domains to identify naming patterns and cluster related adversary infrastructure.
tags: [domain, tld, substring, domain-length, naming-pattern, typosquatting, infrastructure-clustering]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0102 - Domain

**As a** cyber threat intelligence analyst  
**I want** to compare domain name characteristics (TLD, substrings, length, and structure) across multiple malicious domains  
**So that** I can identify naming patterns and conventions that help me discover additional adversary infrastructure.

## Acceptance Criteria
- System performs domain characteristic analysis as part of multi-IOC comparisons using the dedicated domain comparison module
- Automatically detects and surfaces statistically significant similarities for:
  - P0102.001 - Domain: TLD (shared top-level domains)
  - P0102.002 - Domain: Substring (common substrings or naming patterns)
  - P0102.004 - Domain: Length (similar domain name lengths)
  - P0102.003 - Domain: Subdomain (when applicable)
- Clusters are presented clearly with counts, percentages, and matching IOCs
- Analyst can use any identified domain characteristic (e.g., a shared substring or unusual TLD) as a pivot for further hunting
- Optional substring filter (`sstring`) is supported during comparison to focus analysis on specific patterns

## Why This Pivot Matters
Threat actors frequently reuse naming conventions, prefixes, suffixes, or TLD choices across campaigns. These patterns can be strong signals even when registration data is privacy-protected or heavily laundered. Substring and structural analysis is particularly effective for detecting typosquatting, campaign-specific branding, and affiliate program infrastructure. The IOC Comparer's domain module makes these patterns immediately visible during routine comparison workflows.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Run IOC Comparison]
    
    B --> C[3. Domain Comparison Module<br/>Extracts TLD, Length,<br/>and Common Substrings]
    
    C --> D[4. Cluster Analysis<br/>Identifies Majority Patterns<br/>across P0102 sub-pivots]
    
    D --> E{5. Significant Domain<br/>Patterns Detected?}
    
    E -->|Yes| F[6. Domain Characteristic<br/>Clusters Presented]
    E -->|No| G[No Strong Domain<br/>Patterns Identified]
    
    F --> H[7. Analyst Reviews Clusters<br/>and Selects Pivot Values]
    H --> I[8. Use Selected Patterns<br/>for Expanded Infrastructure<br/>Discovery and Hunting]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style F fill:#c8e6c9,stroke:#388e3c
    style I fill:#fff9c4,stroke:#f9a825
    style G fill:#f5f5f5,stroke:#666
```