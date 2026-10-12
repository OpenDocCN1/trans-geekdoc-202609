
# Vulnerability Scan Reports

Vulnerability scan reports provide analysts with a significant amount of information that assists with the interpretation of the report. These reports provide detailed information about each vulnerability that they identify. [Figure 5.12](#c05.xhtml#c05-fig-0012) shows an example of a single vulnerability reported by the Nessus vulnerability scanner.

![FIGURE 5.10 Nikto web application scanner](images/c05f010.png)

[**FIGURE 5.10**](#c05.xhtml#R_c05-fig-0010) Nikto web application scanner

![FIGURE 5.11 Arachni web application scanner](images/c05f011.png)

[**FIGURE 5.11**](#c05.xhtml#R_c05-fig-0011) Arachni web application scanner

![FIGURE 5.12 Nessus vulnerability scan report](images/c05f012.png)

[**FIGURE 5.12**](#c05.xhtml#R_c05-fig-0012) Nessus vulnerability scan report

Let's take a look at this report, section by section, beginning in the top left and proceeding in a counterclockwise fashion.

At the very top of the report, we see two critical details: the *name of the vulnerability*, which offers a descriptive title, and the *overall severity* of the vulnerability, expressed as a general category, such as low, medium, high, or critical. In this example report, the scanner is reporting that a server is running an outdated and insecure version of the SSL protocol. It is assigned to the high severity category.

Next, the report provides a *detailed description* of the vulnerability. In this case, the report provides a detailed description of the flaws in the SSL protocol and explaining that SSL is no longer considered acceptable for use.

The next section of the report provides a *solution* to the vulnerability. When possible, the scanner offers detailed information about how system administrators, security professionals, network engineers, and/or application developers may correct the vulnerability. In this case, the reader is instructed to disable SSL 2.0 and 3.0 and replace their use with a secure version of the TLS protocol.

In the section of the report titled "See Also," the scanner provides *references* where administrators can find more details on the vulnerability described in the report. In this case, the scanner refers the reader to several blog posts, Nessus documentation pages, and Internet Engineering Task Force (IETF) documents that provide more details on the vulnerability.

The *output* section of the report shows the detailed information returned by the remote system when probed for the vulnerability. This information can be extremely valuable to an analyst because it often provides the verbatim output returned by a command. Analysts can use this to better understand why the scanner is reporting a vulnerability, identify the location of a vulnerability, and potentially identify false positive reports. In this case, the output section shows the specific insecure ciphers being used.

The *port/hosts* section provides details on the server(s) that contain the vulnerability as well as the specific services on that server that have the vulnerability. In this case, the server's IP address is obscured for privacy reasons, but we can see that the server is running insecure versions of SSL on both ports 443 and 4433.

The *vulnerability information* section provides some miscellaneous information about the vulnerability. In this case, we see that the SSL vulnerability has appeared in news reports.

The *risk information* section includes useful information for assessing the severity of the vulnerability. In this case, the scanner reports that the vulnerability has an overall risk factor of High (consistent with the tag next to the vulnerability title). It also provides details on how the vulnerability rates when using the Common Vulnerability Scoring System (CVSS). You'll notice that there are two difference CVSS scores and vectors. We will use the CVSS version 3 information, as it is the more recent rating scale. In this case, the vulnerability has a CVSS base score of 7.5 and has the CVSS vector:

```
CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
```

We'll discuss the details of CVSS scoring in the next section of this chapter.

The final section of the vulnerability report provides details on the vulnerability scanner plug-in that detected the issue. This vulnerability was reported by Nessus plug-in ID 20007, which was published in October 2005 and updated in March 2019.

## Understanding CVSS

The *Common Vulnerability Scoring System (CVSS)* is an industry standard for assessing the severity of security vulnerabilities. It provides a technique for scoring each vulnerability on a variety of measures. Cybersecurity analysts often use CVSS ratings to prioritize response actions.

Analysts scoring a new vulnerability begin by rating the vulnerability on eight different measures. Each measure is given both a descriptive rating and a numeric score. The first four measures evaluate the exploitability of the vulnerability, whereas the last three evaluate the impact of the vulnerability. The eighth metric discusses the scope of the vulnerability.

### Attack Vector Metric

The *attack vector metric* describes how an attacker would exploit the vulnerability and is assigned according to the criteria shown in [Table 5.1](#c05.xhtml#c05-tbl-0001).

[**TABLE 5.1**](#c05.xhtml#R_c05-tbl-0001) CVSS attack vector metric

| Value | Description | Score |
| --- | --- | --- |
| Physical (P) | The attacker must physically touch the vulnerable device. | 0.20 |
| Local (L) | The attacker must have physical or logical access to the affected system. | 0.55 |
| Adjacent Network (A) | The attacker must have access to the local network that the affected system is connected to. | 0.62 |
| Network (N) | The attacker can exploit the vulnerability remotely over a network. | 0.85 |

### Attack Complexity Metric

The *attack complexity metric* describes the difficulty of exploiting the vulnerability and is assigned according to the criteria shown in [Table 5.2](#c05.xhtml#c05-tbl-0002).

[**TABLE 5.2**](#c05.xhtml#R_c05-tbl-0002) CVSS attack complexity metric

| Value | Description | Score |
| --- | --- | --- |
| High (H) | Exploiting the vulnerability requires "specialized" conditions that would be difficult to find. | 0.44 |
| Low (L) | Exploiting the vulnerability does not require any specialized conditions. | 0.77 |

### Privileges Required Metric

The *privileges required metric* describes the type of account access that an attacker would need to exploit a vulnerability and is assigned according to the criteria in [Table 5.3](#c05.xhtml#c05-tbl-0003).

[**TABLE 5.3**](#c05.xhtml#R_c05-tbl-0003) CVSS privileges required metric

| Value | Description | Score |
| --- | --- | --- |
| High (H) | Attackers require administrative privileges to conduct the attack. | 0.270 (or 0.50 if Scope is Changed) |
| Low (L) | Attackers require basic user privileges to conduct the attack. | 0.62 (or 0.68 if Scope is Changed) |
| None (N) | Attackers do not need to authenticate to exploit the vulnerability. | 0.85 |

### User Interaction Metric

The *user interaction metric* describes whether the attacker needs to involve another human in the attack. The user interaction metric is assigned according to the criteria in [Table 5.4](#c05.xhtml#c05-tbl-0004).

[**TABLE 5.4**](#c05.xhtml#R_c05-tbl-0004) CVSS user interaction metric

| Value | Description | Score |
| --- | --- | --- |
| None (N) | Successful exploitation does not require action by any user other than the attacker. | 0.85 |
| Required (R) | Successful exploitation does require action by a user other than the attacker. | 0.62 |

### Confidentiality Metric
