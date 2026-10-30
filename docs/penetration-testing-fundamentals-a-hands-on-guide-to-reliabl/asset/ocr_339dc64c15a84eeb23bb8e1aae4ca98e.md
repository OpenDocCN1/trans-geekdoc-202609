test, it is obvious that PCI standards are being tested; however, there could be additional standards that should also be tested.

Once these concepts are addressed, PCI DSS has a rather simple three-phase approach, but each phase has specific requirements. You can see a summary of those in Table 2-1.

# TABLE 2-1 PCI DSS Phases and Requirements

| Pre-Engagement | Actual Test | Post-Engagement |
|---|---|---|
| Scope | Application layer | Remediation |
| Documentation | Network layer | Retesting identified vulnerabilities |
| Rules of engagement | Segmentation | Cleaning up |
| Environment | How to handle cardholder data | Reporting |
| Success criteria | Post-exploitation |  |
| Pass vulnerability scans |  |  |

# NIST 800-115

The National Institute of Standards and Technology is a U.S. organization that formulates a number of standards, many of which are of interest to cyber security. Of particular interest to penetration testers is NIST 800-115, Technical Guide to Information Security Testing and Assessment. As the title of this standard suggests, it is a general guide for testing, not just penetration testing.

The standard includes some items that are not relevant to penetration testing, such as document review, log review, and similar items. These issues are more appropriately covered in a security audit. It should be noted that it is entirely appropriate to have an audit precede and direct the focus of a penetration test.

NIST 800-115 uses three phases:

+   - Planning
+   - Execution
+   - Post-Execution

This may seem like a rather simplified plan, but these phases are each robust and detailed. We will look at each phase in more detail in the following sections.

# Planning

Planning is one of the items that separates penetration testing from hacking. Hacking may or may not be planned, and if planned, the plan may be very flexible. However, professional penetration testing should be approached like an engineering project, which means that a detailed plan is critical.