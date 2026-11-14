Malware detected by antivirus (AV) or IDS, endpoint security → snapshot taken of virtual machine → device quarantined using Network Access Control (NAC) → memory analyzed → file reputation analyzed → file detonated in sandbox → geolocation looked up → file on endpoints hunted for → hash blocked → URL blocked

Process optimization for purple teaming is also possible. There are many great open source IR collaboration tools. Some of my favorites are from TheHive Project. TheHive is an analysis and security operations center (SOC) orchestration platform, and it has SOC workflow and collaboration functions built in. All investigations are grouped into cases, and cases are broken down into tasks. TheHive has a Python API that allows an analyst to send alerts and create cases out of different sources such as a SIEM system or e-mail. TheHive Project has also made some supplementary tools such as Cortex, an automation tool for bulk data analysis. Cortex can pull IOCs from TheHive’s repositories. Cortex has analyzers for popular services such as VirusTotal, DomainTools, PassiveTotal, and Google Safe Browsing, to name just a few. TheHive Project also created Hippocampe, a threat-feed-aggregation tool that lets you query it through a REST API or a web UI.

Organizations that have healthy budgets or organizations that prohibit the use of open source tools have many commercial products available to assist them with automation and orchestration of their processes and attack-and-defense activities. Tools like Phantom’s commercial version, Verodin, ServiceNow, and a wide variety of commercial SIEMs and log aggregators can be integrated to optimize processes.

# Summary

Becoming a master in any skill will always take passion and repetitive practice. Purple teaming allows for cyber-sparring between your offensive and defensive security teams. The result is that both teams refine their skill sets, and the organization is much better off for it. Purple team efforts combine red teaming attacks and blue team responses into a single effort where collaboration breeds improvement. No organization should assume that its defenses are impregnable. Testing the effectiveness of both your attack and defense capabilities protects your investment in cybersecurity controls and helps set a path forward toward maturation.

# For Further Reading

+   - A Symbiotic Relationship: The OODA Loop, Intuition, and Strategic Thought (Jeffrey N. Rule) www.dtic.mil/dtic/tr/fulltext/u2/a590672.pdf
+   - AttackIQ FireDrill https://attackiq.com/
+   - Carbon Black Response https://www.carbonblack.com/products/cb-response/