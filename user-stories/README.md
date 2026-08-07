# User Stories

This directory contains user stories that describe the functional requirements and acceptance criteria for each pivot in the Defender's ThreatMesh Framework. Each user story follows the format: "As a [role], I want [capability], So that [benefit]."

User stories help analysts and developers understand:
- **What** each pivot accomplishes
- **Why** the pivot matters in threat hunting
- **How** the pivot should work (acceptance criteria and workflow)

## Available User Stories

### Domain Registration (P0101.x)
- **[P0101 - Registration](P0101-Registration.md)**: Compare registration details across malicious domains using RDAP and VirusTotal enrichment data to identify infrastructure patterns and cluster adversary operations.
  - [P0101.003 - Registration: Registrant](P0101.003-Registration-Registrant.md): Identify shared registrant names across malicious domains
  - [P0101.004 - Registration: Registrant Email](P0101.004-Registration-Registrant-Email.md): Detect infrastructure clusters based on registrant email addresses

### Domain Characteristics (P0102.x)
- **[P0102 - Domain](P0102-Domain.md)**: Analyze and compare domain name characteristics (TLD, substrings, length, and structure) across malicious domains to identify naming patterns and cluster related adversary infrastructure.

### DNS Infrastructure (P0103.x)
- **[P0103 - DNS](P0103-DNS.md)**: Compare DNS configuration and nameserver patterns across malicious domains to identify shared hosting and infrastructure relationships.
  - [P0103.004 - DNS: SOA RName](P0103.004-DNS-SOA-RName.md): Identify shared DNS responsible person email addresses in SOA records

### Network Intelligence (P0201-P0203)
- **[P0201 - Reverse Lookup](P0201-Reverse-Lookup.md)**: Use reverse DNS lookups and IP-to-domain mappings to discover additional infrastructure sharing the same hosting resources.
- **[P0202 - Proximity](P0202-Proximity.md)**: Identify malicious domains hosted on nearby IP addresses or network ranges to uncover related infrastructure.
- **[P0203 - AS](P0203-AS.md)**: Compare Autonomous System (AS) numbers and hosting providers across malicious domains to identify infrastructure clustering patterns.

### Certificate Analysis (P0301-P0303)
- **[P0301 - Issuer Organization](P0301-Issuer-Organization.md)**: Identify SSL/TLS certificate issuer patterns across malicious domains to discover infrastructure using similar certificate authorities or self-signed certificates.
- **[P0302 - Subject Alternate Name (SAN)](P0302-Subject-Alternate-Name(SAN).md)**: Analyze Subject Alternate Names in SSL/TLS certificates to discover related domains and infrastructure.
- **[P0303 - Not Before Date](P0303-Not-Before-Date.md)**: Compare SSL/TLS certificate issuance dates to identify infrastructure provisioned during the same operational window.

### HTTP Analysis (P0401.x)
- **[P0401 - HTTP](P0401-HTTP.md)**: Compare HTTP-level characteristics (page titles, shared resources, response patterns, resource names, etc.) across malicious domains, primarily using URLScan enrichment data, to identify infrastructure operated as part of the same campaign or kit.

## Structure

Each user story document includes:
- **Metadata**: YAML frontmatter with pivot code, title, category, description, tags, and status
- **User Story**: Role-based requirement statement
- **Acceptance Criteria**: Specific, testable conditions that define success
- **Why This Pivot Matters**: Context and justification for the pivot
- **Workflow**: Mermaid diagram showing the analytical process

## Usage

User stories serve multiple purposes:
1. **Development Guide**: Define requirements for implementing pivots in analysis tools
2. **Analyst Training**: Help new analysts understand when and how to use each pivot
3. **Communication**: Provide clear language for discussing pivots with stakeholders
4. **Documentation**: Record the intended behavior and value of each pivot

## Related Resources
- See the main [matrix](../matrix.md) for the complete pivot taxonomy
- See [examples/](../examples/) for real-world applications of these pivots
- See [pivot-tactics/](../pivot-tactics/) for strategic groupings of related pivots
