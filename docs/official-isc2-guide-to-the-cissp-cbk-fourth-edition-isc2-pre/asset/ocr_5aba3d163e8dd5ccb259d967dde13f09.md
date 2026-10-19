| Division | Class | Description |
|---|---|---|
| D | - | Evaluated but does not meet security requirements |
| C | C1 | Discretionary Security Protection:
- Basic Discretionary Access Control (DAC) |
|  | C2 | Controlled Access Protection:
- Improved DAC
- Individual accountability through login procedures and audit trails
- Resource isolation
- Essential system documentation and user manuals |
| B | B1 | Labeled Security Protection:
- Mandatory Access Control (MAC) over some subjects and objects
- Informal statement of the security policy model
- Data sensitivity labels and label exportation
- All discovered flaws must be removed or otherwise mitigated |
|  | B2 | Structured Protection:
- DAC and MAC enforcement extended to all subjects and objects
- Security policy model clearly defined and formally documented
- Covert storage channels are identified and analyzed
- Objects are carefully structured into protection-critical and non-protection-critical
- Design and implementation enable more comprehensive testing and review
- Authentication mechanisms are hardened from compromise
- Trusted management segregates administrator and operator privileges
- Strict configuration management |
|  | B3 | Security Domains:
- Can satisfy reference monitor requirements
- Structured to exclude code not essential to security policy enforcement
- Significant system engineering directed toward minimizing complexity
- Trusted management provides security administrator function
- Audits all security-relevant events
- Automated imminent intrusion detection, notification, and response
- Trusted system recovery procedures
- Covert timing channels are identified and analyzed |
| A | A1 | Verified Design:
- Functionally identical to B3 but more formal design and verification |