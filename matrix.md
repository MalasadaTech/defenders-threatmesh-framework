# Defender's ThreatMesh Framework (DTF) Matrix

| Pivot Tactic ID         | Pivot Tactic Name          | Pivots                                                                     |
|-------------------------|----------------------------|----------------------------------------------------------------------------|
| [PTA0001](pivot-tactics/PTA0001/main.md) | Registration Similarity    | [P0101](pivots/P0101.md) - Same Registrar<br>[P0102](pivots/P0102.md) - Shared Name Servers<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0102.001](pivots/P0102.001.md) - Shared Name Server Domain<br>[P0103](pivots/P0103.md) - Similar Registration Dates<br>[P0104](pivots/P0104.md) - Registrant Overlap<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0104.001](pivots/P0104.001.md) - Registrant Email Overlap<br>[P0105](pivots/P0105.md) - Same TLD |
| [PTA0002](pivot-tactics/PTA0002/main.md) | Infrastructure Similarity  | [P0201](pivots/P0201.md) - IP Address Overlap<br>[P0202](pivots/P0202.md) - Shared AS<br>[P0203](pivots/P0203.md) - SSL Certificate Similarity<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0203.001](pivots/P0203.001.md) - SSL Issuer Organization<br>[P0204](pivots/P0204.md) - Similar DNS Records<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0204.001](pivots/P0204.001.md) - Shared CNAME<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0204.002](pivots/P0204.001.md) - Shared MX Records |
| [PTA0003](pivot-tactics/PTA0003/main.md) | Content Similarity         | [P0301](pivots/P0301.md) - Website Structure Similarity<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0301.001](pivots/P0301.001.md) - Page Title Match<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0301.002](pivots/P0301.002.md) - Embedded Code Similarity<br>~~[P0302](pivots/P0302.md) - Shared Resources~~<br>[P0303](pivots/P0303.md) - Same Resources<br>[P0304](pivots/P0304.md) - Keyword Similarity |
| [PTA0004](pivot-tactics/PTA0004/main.md) | Domain Name Similarity     | [P0401](pivots/P0401.md) - Substring Similarity<br>&nbsp;&nbsp;&nbsp;&nbsp;[P0401.001](pivots/P0401.001.md) - Prefix Matching |
| [PTA0005](pivot-tactics/PTA0005/main.md) | Behavioral Similarity      | [placeholder for future updates] |

**Note**: Pivots with a ~~strikethrough~~ do not have a corresponding file in the pivots directory and are currently placeholders.

Click a pivot tactic ID (e.g., [PTA0001](pivot-tactics/PTA0001/main.md)) for an overview or a pivot ID (e.g., [P0101](pivots/P0101.md)) for details.