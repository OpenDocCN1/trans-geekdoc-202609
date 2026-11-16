
## Software Supply Chain Security

Today, large software development teams are often referred to as software factories because of the increasing similarities in modern, large-scale software development methodologies to traditional mass production, making the concept of the supply chain highly relevant.

Software supply chain security is an increasingly pivotal aspect of cybersecurity. It involves a series of measures designed to ensure the integrity and security of software throughout its lifecycle, from development to deployment. The field includes scrutinizing third-party components, such as libraries and packages, for vulnerabilities; ensuring the security of code repositories; and safeguarding continuous integration and delivery processes.

The essence of software supply chain security is to identify, manage, and mitigate risks that might compromise software at any stage of its development or deployment. Tight management is crucial because any breach in the supply chain can lead to severe data breaches, loss of customer trust, and significant financial and reputational damage. Recent high-profile breaches have shown that vulnerabilities in the supply chain can have far-reaching effects, impacting countless users and multiple organizations.

As organizations increasingly rely on open source components and third-party software, the complexity and interconnectedness of the software supply chain grow. Consequently, developers, security professionals, and business leaders must understand the risks and implement strategies to safeguard their software supply chains. This includes rigorous vetting of third-party components, maintaining an up-to-date inventory of all elements used in the software (often through a software bill of materials), regular scanning for vulnerabilities, and adopting a comprehensive, proactive approach to security.

Now, let's look at a few examples of serious breaches, their consequences, and lessons learned from them.

## The Equifax Breach

In March 2017, researchers disclosed a serious vulnerability (CVE-2017-5638) in the popular Apache Struts web framework. The vulnerability allowed remote code execution via malicious input, and the MITRE Corporation (which we'll learn more about later in this chapter) assigned it a maximum severity score of 10. Equifax, one of the largest consumer credit reporting agencies, used Struts in one of its public web portals. However, the company failed to patch the disclosed vulnerability for over two months, exposing their systems. In May 2017, hackers exploited the unpatched Struts flaw to breach Equifax systems and exfiltrate sensitive personal and financial data related to 148 million consumers. Equifax did not discover the breach until July 2017. This massive breach resulted in over $1 billion in losses for Equifax.

### Impact

The Equifax breach affected nearly half the US population and had enormous consequences:

- Sensitive PII, such as SSNs, addresses, and birth dates, was stolen, enabling identity theft.
- Multiple class-action lawsuits were filed against Equifax.
- Hundreds of millions of dollars in settlement money was paid for damages to affected consumers.
- Equifax senior executives were fired and suffered major reputation damage.

### Lessons learned

The incident highlighted critical software security issues:

- Patch open source components quickly, especially if they are internet facing.
- Understand your external attack surface and third-party risks.
- Use multilayer security controls to limit breach impacts.
- Implement incident response planning for “when,” not “if.”

The Equifax breach was a seminal event that demonstrated the immense risks unpatched software posed to companies and private citizens. Key lessons include quickly applying patches, restricting component access, monitoring systems, and planning incident responses.

## The SolarWinds Hack

In December 2020, a major cyberattack was uncovered targeting SolarWinds, a software company that provides IT management tools used by thousands of organizations globally. Hackers had inserted malicious code into the SolarWinds Orion network monitoring software, which was then distributed unknowingly to SolarWinds's customers as software updates between March and June 2020.

This supply chain attack took advantage of the widespread use of SolarWinds software to infiltrate the networks and systems of high-profile targets like US government agencies, major technology companies including Microsoft and FireEye, and other large corporations and organizations. The hackers, suspected to be part of a sophisticated Russian cyber espionage operation, managed to avoid detection for almost a year through stealthy techniques to impersonate legitimate user activity and blend in with normal network traffic.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_126_0.png)

Attackers compromised SolarWinds's build pipeline to insert the malicious code. Securing your build pipelines is crucial to the overall security of your software. Failure to do so can impact your customers—not just you!

### Impact

The SolarWinds hack had an unprecedented impact in terms of scale and number of affected victims. By infiltrating the software supply chain, the attackers gained far-reaching access to thousands of downstream customers. Beyond SolarWinds, the access enabled by the compromised Orion software also opened pathways to breach the networks of their customers and partners. Estimates indicate that over one hundred US companies and government agencies were affected.

The full impact is still being uncovered, but consequences include:

- Sensitive government and corporate data theft
- Access to core infrastructure and internal communications
- Cascading breaches across interconnected partners and supply chains
- Significant costs for incident response and remediation

### Lessons learned

The SolarWinds attack highlighted major risks in increasingly interconnected software supply chains and the need for better security practices, including:

- Multifactor authentication, privileged access management, and logging to help detect unusual access
- Software verification, code audits, and enhanced supply chain controls by vendors
- Improved compartmentalization between systems to limit lateral movement
- Assuming breach and engaging in more proactive threat hunting
- Faster coordination and information sharing across the public and private sector

The SolarWinds hack demonstrates the potential scale and impact of supply chain cyberattacks by leveraging trusted third-party software to breach countless downstream targets. More vigilance and collaboration on software supply chain security will be crucial.

## The Log4Shell Vulnerability

At the start of this chapter, I shared a story about my CISO calling in the middle of the night and filling me in on a major problem. That quickly ballooned into one of the biggest stories in supply chain security ever. These are the details of that story.

In November 2021, a critical zero-day remote code execution vulnerability was discovered in Log4j, a Java logging library used by an incredible number of applications and services. Tracked as CVE-2021-44228 and dubbed “Log4Shell,” this vulnerability allowed attackers to gain full control and remote access to vulnerable servers.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_127_0.png)

Zero-day vulnerabilities are unknown software flaws that come to light before developers can create a patch (i.e., they have zero days to prepare). They pose a significant security risk because attackers can exploit these vulnerabilities before a fix is available. The urgency and potential impact of zero-day exploits make them a critical concern in cybersecurity, requiring immediate attention to protect systems and data from compromise. Zero-day vulnerabilities are a favored target for sophisticated cyberattacks, including espionage and cyber warfare.

The Log4j library allows data logging from many sources, including untrusted data from users. The vulnerability arose from improper input validation, enabling crafted requests to trigger malicious Java code execution on the server. Attackers could send payloads over the internet, SMS, and chat apps. When such untrusted inputs were innocently written to Log4j, it could allow remote code execution, allowing the attacker to gain full shell access to the server—thus the name Log4Shell.

### Impact

Due to Log4j’s ubiquitous use, Log4Shell’s impact was massive. Within days of the disclosure, millions of internet-facing systems were nefariously scanned for the flaw. Successful exploits surged, with botnets, cryptominers, ransomware groups, and state-sponsored hackers all leveraging Log4Shell.

Consequences included:

- Data theft from compromised servers
- Installation of malware, backdoors, and cryptominers
- Ransomware attacks shutting down operations
- Cascading supply chain breaches as access opened networks of partners
- Burdensome, urgent, out-of-cycle patching exercises across cloud and on-prem infrastructure
