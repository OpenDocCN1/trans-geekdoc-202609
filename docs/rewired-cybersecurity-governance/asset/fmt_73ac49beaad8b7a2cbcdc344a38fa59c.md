
### 5.3.1.3 Learnings

After the attack became known to the public, the Swiss government issued a technical report concerning the cybersecurity incident in conjunction with the national Reporting and Analysis Centre for Information Assurance (MELANI). The main objective of the report was to share relevant information with potentially vulnerable parties (both state and non‐state). In contrast to the earlier secrecy surrounding the event, the publication of an official cybersecurity incident report received far‐reaching approval. Information security experts were particularly enthusiastic about the compilation of indicators of compromise and security recommendations, which allowed other potentially vulnerable entities to detect and block related attacks.[^(25)](#c05.xhtml#c5-note-0025) Professor of Security Studies, Thomas Rid, for example, mentioned in a tweet: “[The] new RUAG report is a very big step on the part of the Swiss. Kudos to @GovCERT_CH for raising the bar on governmental attribution reports.”[^(26)](#c05.xhtml#c5-note-0026)

The report suggested that intrusion started as early as September 2014. Forensic analysis revealed that intruders relied on a type of malware belonging to the Turla family, a Trojan artifact believed to be of Russian origin. However, the report deliberately abstained from attributing the attack to a specific threat actor.[^(27)](#c05.xhtml#c5-note-0027) Attackers were said to have demonstrated great perseverance during stages of infiltration and lateral movement, as well as enormous focus on high‐value targets, including the Active Directory.[^(28)](#c05.xhtml#c5-note-0028) Retrieval and infiltration of the latter allowed intruders to command other hosts, and access (supposedly) proprietary data by escalating privileges and using appropriate permissions. In total, the malware writers were said to have exfiltrated 23 GB of data.[^(29)](#c05.xhtml#c5-note-0029) According to RUAG, this represented less than 0.01% of the volume of data managed by the defense contractor.[^(30)](#c05.xhtml#c5-note-0030)

[Figure 5.1](#c05.xhtml#c5-fig-0001) provides a summary of the attack timeline and report findings in a flowchart.

![Figure 5.1 Attack timeline and report findings. ¶ Source: Reporting and Analysis Centre for Information Assurance 2016, 1.](images/c05f001.gif)

[**Figure 5.1**](#c05.xhtml#R_c5-fig-0001) Attack timeline and report findings. ¶ *Source:* Reporting and Analysis Centre for Information Assurance 2016, 1.

The cybersecurity incident response strategy adopted in the RUAG case exhibited clear features of hierarchical governance. Government bodies and institutions with strong ties to the government were at the helm of counteraction and crisis management. Responses were coordinated in close consultation with relevant federal authorities, in particular the Attorney General's Office, the Reporting and Analysis Centre for Information Assurance, as well as the DDPS. Furthermore, the means and methods of remediation employed included black letter criminal law investigations, and traditional parliamentary procedures. The RUAG case suggest that when critical (national) infrastructures are at play (even when provided by a private entity), incident response measures involve traditional, hierarchical means of command and control. The initial secrecy surrounding the attack also supports this argument.

## 5.3.2 The Conficker Working Group

### 5.3.2.1 Background

The Conficker Working Group emerged in response to a highly prevalent computer worm named Conficker (sometimes also referred to as Downadup or Kido), the first variant of which surfaced in late 2008. In total, five variants of the Conficker worm have been recorded.[^(31)](#c05.xhtml#c5-note-0031) Released with the intention of creating a large botnet (i.e. a network of compromised systems susceptible to external control), the Conficker malware infected many unpatched personal, business, and government computers across the globe. It exploited a buffer overflow vulnerability in the server service on Windows machines, which allowed remote code execution on the basis of a specially crafted remote procedure call (RPC) request.[^(32)](#c05.xhtml#c5-note-0032)

### 5.3.2.2 Events

The Conficker worm used a variety of techniques for propagation and exploitation, including the Domain Name System, encrypted peer‐to‐peer communications, and auto‐run capabilities for pushing and pulling executable payloads over the internet.[^(33)](#c05.xhtml#c5-note-0033) Post‐installation, the malicious software executed the following steps:

1. Conficker copied itself into the system directory `%systemroot%\system32` using a random name, and registered itself as a service. It also added itself into the registry.
2. Next, it checked for the infected host's internet protocol (IP) address using websites, including: [www.getmyip.org](http://www.getmyip.org), [http://getmyip.co.uk](http://getmyip.co.uk), and [http://checkip.dyndns.org](http://checkip.dyndns.org).
3. With the IP address identified, the worm then downloaded and set up a small HTTP server on the infected machine.
4. Once the HTTP server was set up, the worm started scanning for other vulnerable systems and began sending the infected machine URL to the targets identified.
5. The targeted machines then downloaded the worm from the URL sent and started completing the same steps as outlined above.[^(34)](#c05.xhtml#c5-note-0034)

Following the emergence and speedy propagation of the worm in late 2008, a group of diverse stakeholders came together in early 2009 to contain the malicious software. Without an official sponsor or set structure, the Conficker Working Group represented an ad‐hoc organization of like‐minded entities.[^(35)](#c05.xhtml#c5-note-0035) Containment efforts were supported by software providers, academic researchers, antivirus vendors, law‐enforcement units, and domain name registrars and registries.[^(36)](#c05.xhtml#c5-note-0036)

One of the first mitigation strategies launched by the working group was the sink‐holing and preemptive registration of domain names on which the worm relied for command and control. The contribution of the Internet Corporation for Assigned Names and Numbers (ICANN), a member of the Conficker Working Group, was essential in this regard. Concerned about the pervasiveness and impact of the malicious software, ICANN agreed to waive domain name registration fees for domains used by the worm, thereby effectively supporting the group's efforts to curtail communication between the malware writers and Conficker‐infected systems.

According to a 2011 “Lessons Learned” report, commissioned by the Department of Homeland Security, the Conficker Working Group considered its biggest success to be the disruption of botnet communications. Although successful in that regard, the working group did not manage to “remediate infected computers and eliminate the threat of the botnet,”[^(37)](#c05.xhtml#c5-note-0037) which tainted its achievements to some extent.

### 5.3.2.3 Learnings

In the case of the Conficker worm, mitigation activities exhibited strong traits of multistakeholder‐based governance. Response strategies followed a collaborative logic, with trust‐based cooperation between public and private entities. Unstructured, complex problem‐settings and heterogeneous stakeholder interests were bridged by means of skills‐based coordination and communication.[^(38)](#c05.xhtml#c5-note-0038) The example of the Conficker Working Group suggests that when a threat is pervasive enough, diverging stakeholder interests can be aligned and containment strategies executed jointly.

## 5.3.3 Symantec's Cybersecurity Practices

### 5.3.3.1 Background
