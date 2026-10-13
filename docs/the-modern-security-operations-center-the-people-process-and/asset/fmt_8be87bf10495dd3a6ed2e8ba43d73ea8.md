
| Users | Description |
| --- | --- |
| [Detail categories of users.] | [Describe how users access the system and their intended use of the system.] |

### 3.5. Flow Diagram

[Provide connectivity diagram or system input and output flowchart to delineate the scope of this risk assessment effort.]

## 4. Vulnerability Statement

[Compile and list potential vulnerabilities applicable to the system assessed.]

| Vulnerability | Description |
| --- | --- |
| [List vulnerabilities.] | [Describe vulnerability and its impact.] |

## 5. Threat Statement

[Compile and list the potential threat sources applicable to the system assessed.]

| Threat Source | Threat Actions |
| --- | --- |
| [List threat sources.] | [List and/or describe actions that can be taken by threat source; e.g., identity theft, spoofing, system intrusion.] |

## 6. Risk Assessment Results

[List the observations (vulnerability/threat source pairs). Each observation should include

*   Observation number and brief description of observation (e.g., Observation 1: User system passwords can be guessed or cracked)
*   Discussion of the threat source and vulnerability pair
*   Identification of existing mitigating security controls
*   Likelihood discussion and evaluation (e.g., High, Medium, or Low likelihood)
*   Impact analysis discussion and evaluation (e.g., High, Medium, or Low impact)
*   Risk rating based on the risk-level matrix (e.g., High, Medium, or Low risk level)
*   Recommended controls or alternative options for reducing the risk]

| Item Number | Observation | Threat-Source/Vulnerability | Existing Controls | Likelihood | Impact | Risk Rating | Recommended Controls |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |

### Vulnerability Scanners

One of the most common tools used for assessing vulnerabilities is a vulnerability scanner. Vulnerabilities will be included in all assessment report types since vulnerabilities represent potential attack vectors. You will need to include vulnerability scanning as part of your assessment process. Vulnerability scanners can be automated to perform periodic or on-demand assessments, depending on how they are used. The quality of the results will depend on many factors, including the data seen by the scanner and how the scanner evaluates a target. For example, a credential-based vulnerability scanner would be able to log into an endpoint device and assess the device without its results being impacted by the endpoint device's enabled security tools such as a host firewall. A non-credential-based scanner would not be able to log into the endpoint, limiting its results to what can be seen and not blocked by enabled security tools such as the host firewall. [Chapter 9](#ch09.xhtml#ch09) covers vulnerability management best practices in more details, including how to use vulnerability scanners to address risk and how to understand the data the scanners produce. Use the steps from [Chapter 9](#ch09.xhtml#ch09) to leverage a vulnerability scanner as part of your assessment process.

> **Note**
>
> Best practice dictates using both credentialed and non-credentialed scanning when assessing devices. Credentialed assessments provide more accurate results, but non-credentialed assessments are closer to what a potential attacker would have access to. Both approaches provide their own form of value and should be leveraged equally.

### Assessment Program Weaknesses

One important concept regarding assessments is that they lack validation of the results. They show "potential" risk rather than actual validated risk. The results being considered potential risk can occur based on how the assessment is performed. Many times, the tools used for an assessment capture data and compare it against a list of known vulnerabilities rather than actually attempting to exploit the vulnerability. This approach can lead to false negatives due to other elements that are not evaluated but are essential to truly understanding the nature of the potential vulnerability. For example, a vulnerability scan may find that a server has many vulnerabilities; however, the server might exist within a contained lab environment and not be a real threat to the organization, or the vulnerabilities that were found might be based on limited data captured by the assessment tool due to the server's existing enabled security that limits what can be evaluated by the assessment tool. The best way to test any potential vulnerability to ensure that it is really a risk is to attempt to exploit it. Exploiting potential vulnerabilities is part of a penetration testing service.

> **Note**
>
> Assessments and penetration testing are services that help your organization consider risk that extends beyond what is addressed by meeting compliance requirements.

## Penetration Test

A penetration test, also referred to as a pentest, goes beyond an assessment by performing the same steps that an adversary would perform to exploit an identified vulnerability. It is common for an assessment to report many more potential vulnerabilities than a penetration test of the same scope actually discovers due to how both approaches validate a target. By following the steps used by an attacker, a pentest truly qualifies whether a target is vulnerable to a real-world attack and, if so, at what level. A pentest typically has a higher cost and more risk associated with its services than an assessment, but a pentest tends to produce more accurate results. I specifically use the language "tends to produce more accurate results" because the actual results received will depend on the scoping and expected goals. I have seen organizations invest thousands of dollars in penetration testing services that result in very little actionable outcomes. My goal in this section is to address some of those pitfalls that lead to poor penetration testing results.

> **Note**
>
> You should first perform an assessment and apply risk reduction steps before performing a penetration test, which helps to maximize the value of the penetration test.

### NIST Special Publication 800-115

NIST SP 800-115, introduced in [Chapter 3](#ch03.xhtml#ch03), identifies four phases of a penetration test: planning, discovery, attack, and reporting. The following is a summary of those phases.

> **Note**
>
> NIST SP 800-115, *Technical Guide to Information Security Testing and Assessment*, is available at [https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-115.pdf](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-115.pdf). I recommend at least perusing the table of contents to discover the full scope of what it has to offer for conducting penetration tests and assessments.

#### Phase 1: Planning

The planning phase involves establishing the rules and the scope of the penetration test and obtaining necessary approval for the penetration test before executing it. It is highly recommended to obtain approval from the highest level of leadership to ensure that all steps are authorized, in the event that something goes wrong. I have seen situations where a manager approved a penetration test that executive leadership was unaware of and the pentesting caused system failures. Both the manager and service provider were blamed for the system outages even though the penetration testers performed services within the agreed-upon scope of work. In the industry, having this approval is known as the "get out of jail free card." Make sure your get out of jail free card is signed by a C-level executive!

#### Phase 2: Discovery
