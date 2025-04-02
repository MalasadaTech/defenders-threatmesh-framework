# Defender's ThreatMesh Framework

The Defender's ThreatMesh Framework is a specialized tool designed to empower hunt analysts in uncovering additional adversary infrastructure. By pivoting on characteristics of known malicious infrastructure—such as domain name patterns, registration details, or network behaviors—this framework provides a structured approach to expand visibility into threat actors' operations. Inspired by MITRE ATT&CK, it focuses solely on discovery, offering pivot tactics and pivots to reveal hidden connections in the wild.

## Overview
- **Purpose**: Enable hunt analysts to identify more adversary infrastructure by leveraging pivots from existing data.
- **Structure**: Pivot tactics (PTAXXXX) group related pivots (PXXYY), supported by real-world examples (EXXXXX).
- **Usage**: Use the [matrix](matrix.md) to explore pivot tactics and pivots.

## Getting Started
Check the [matrix](matrix.md) for a full list of pivot tactics and pivots with links to detailed pages. Each entry is designed to guide you through pivoting strategies, backed by practical detection methods.

## Examples
Real-world examples (EXXXXX) illustrate how analysts can deploy these pivots to uncover additional adversary infrastructure. Sourced from threat intelligence reports and blogs, these instances—like phishing waves using prefixed domains or registrar overlaps—provide context and hunting tips to enhance your pivot-based investigations. See the [examples/](examples/) directory for details.

## Contributors
This framework is a collaborative effort, built by a community of threat hunters and analysts. Special thanks to all who have contributed their expertise. For a full list of contributors and their contributions, see [contributors.md](contributors.md).

## License
This project is licensed under the [MIT License](LICENSE).
