---
pivot_code: P0401
title: HTTP
category: HTTP
description: Compare HTTP-level characteristics (page titles, shared resources, response patterns, resource names, etc.) across malicious domains, primarily using URLScan enrichment data, to identify infrastructure operated as part of the same campaign or kit.
tags: [http, urlscan, page-title, shared-resources, infrastructure-clustering, web-analysis]
created_date: 2026-05-01
last_updated: 2026-05-01
status: active
---

# P0401 - HTTP

**As a** cyber threat intelligence analyst  
**I want** to compare HTTP-level signals across multiple malicious domains  
**So that** I can identify shared web infrastructure, page patterns, and resource reuse that reveal additional adversary-controlled sites.

## Acceptance Criteria
- System primarily enriches domains with HTTP and web page data via the URLScan Enricher
- When performing multi-IOC comparisons, the system runs the URLScan comparison module to detect similarities in:
  - P0401.001 - HTTP: Title
  - P0401.003 - HTTP: Shared Resources
  - P0401.004 - HTTP: Same Resources
  - P0401.006 - HTTP: Same Resource Name
  - (and other HTTP characteristics as they are implemented)
- Statistically significant overlaps in page titles, external resources, resource hashes, or URL patterns are surfaced as clusters
- The system presents clear HTTP-based pivots with supporting context from the scans
- Analyst can use discovered shared titles, resources, or filenames as new pivots for further hunting

## Why This Pivot Matters
HTTP-level observables (especially page titles, embedded third-party resources, and reused filenames or assets) often expose the tooling, kits, or operational patterns used by threat actors. These signals can link domains even when they use different registrars, nameservers, or hosting providers. URLScan provides rich, publicly available data on live web behavior that is difficult for operators to fully sanitize at scale, making HTTP pivots particularly valuable for expanding infrastructure maps during active campaigns.

## Workflow

```mermaid
flowchart TD
    A[1. Analyst provides multiple<br/>malicious domain IOCs] 
    --> B[2. Enrich via URLScan<br/>for HTTP and Page Data]
    
    B --> C[3. Extract HTTP Characteristics<br/>Titles, Resources, Hashes, URLs]
    
    C --> D[4. URLScan Comparison Module<br/>Identifies Overlaps in<br/>HTTP Signals]
    
    D --> E{5. Significant HTTP<br/>Pattern Clusters Found?}
    
    E -->|Yes| F[6. HTTP-Based Clusters<br/>Presented as Pivots]
    E -->|No| G[No Strong HTTP<br/>Patterns Detected]
    
    F --> H[7. Analyst Reviews Shared<br/>Titles and Resources]
    H --> I[8. Use Discovered HTTP Patterns<br/>to Find Additional Campaign<br/>Infrastructure]
    
    style A fill:#e3f2fd,stroke:#1976d2
    style F fill:#c8e6c9,stroke:#388e3c
    style I fill:#fff9c4,stroke:#f9a825
    style G fill:#f5f5f5,stroke:#666
```