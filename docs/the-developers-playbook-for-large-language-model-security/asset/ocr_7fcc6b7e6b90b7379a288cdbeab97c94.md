# The Log4Shell Vulnerability

At the start of this chapter, I shared a story about my CISO calling in the middle of the night and filling me in on a major problem. That quickly ballooned into one of the biggest stories in supply chain security ever. These are the details of that story.

In November 2021, a critical zero-day remote code execution vulnerability was discovered in Log4j, a Java logging library used by an incredible number of applications and services. Tracked as CVE-2021-44228 and dubbed “Log4Shell,” this vulnerability allowed attackers to gain full control and remote access to vulnerable servers.

![](bbox=[0.172, 0.275, 0.265, 0.365])

Zero-day vulnerabilities are unknown software flaws that come to light before developers can create a patch (i.e., they have zero days to prepare). They pose a significant security risk because attackers can exploit these vulnerabilities before a fix is available. The urgency and potential impact of zero-day exploits make them a critical concern in cybersecurity, requiring immediate attention to protect systems and data from compromise. Zero-day vulnerabilities are a favored target for sophisticated cyberattacks, including espionage and cyber warfare.

The Log4j library allows data logging from many sources, including untrusted data from users. The vulnerability arose from improper input validation, enabling crafted requests to trigger malicious Java code execution on the server. Attackers could send payloads over the internet, SMS, and chat apps. When such untrusted inputs were innocently written to Log4j, it could allow remote code execution, allowing the attacker to gain full shell access to the server—thus the name Log4Shell.

# Impact

Due to Log4j’s ubiquitous use, Log4Shell’s impact was massive. Within days of the disclosure, millions of internet-facing systems were nefariously scanned for the flaw. Successful exploits surged, with botnets, cryptominers, ransomware groups, and state-sponsored hackers all leveraging Log4Shell.

Consequences included:

+   - Data theft from compromised servers
+   - Installation of malware, backdoors, and cryptominers
+   - Ransomware attacks shutting down operations
+   - Cascading supply chain breaches as access opened networks of partners
+   - Burdensome, urgent, out-of-cycle patching exercises across cloud and on-prem infrastructure