
## ISO/IEC 27000
- Family of IT security standards
- Originally called ISO/IEC 17799

## ISO/IEC 27002
- Fourteen broad areas
- Information security policies
- Organization of information security
- Human resource security
- Asset management
- Access control
- Cryptography
- Physical and environmental security
- Operation Security
- Communications and operations management
- Information systems acquisition, development, and maintenance
- Supplier relationships
- Information security incident management
- Information security aspects of business continuity management
- Compliance

## ISO/IEC 27001
- Created in 2005, long after ISO/IEC 27002
- Specifies certification by a third party
  - COSO and COBIT do self-certification

## Other 27000 Standards
- Many more standards are being developed

Figure 2-29 The ISO/IEC 27000 Family of Security Standards (Study Figure)

notification laws, PCI-DSS, and FISMA. The functioning, placement, general nature of interactions between the IT security department and other organizational departments, and outsourcing to managed security service providers were discussed.

The chapter then looked at classic risk analysis, its problems, and ways to respond to risk. This led us to a discussion about security architecture, policies, standards, procedures, and best practices within the industry. We saw the need for oversight of existing policies, auditing, and sanctions to prevent internal fraud.

The chapter concluded with a discussion of a few well-known governance frameworks including COSO, COBIT, and ISO 27000. Frameworks help companies by providing a systematic way of approaching IT security planning, implementation, monitoring, and progressive improvement.

## Security @ Work
### Security in the Sharing Economy
When was the last time you hailed a taxi? Maybe a better question is whether you have ever hailed a taxi. If not, then you have likely requested an Uber using your phone. If you have used a ride service app or booked a vacation using Airbnb, then you have participated in the sharing economy, or a collaborative economy where goods and services are shared among participants in a peer-to-peer (P2P) network. While the concept of connecting peers who are interested in participating in transactions seems rudimentary, the companies cashing in on the sharing economy are no joke.

For example, Uber has disrupted countless taxi markets around the globe, and the company is worth billions of dollars. Airbnb is worth billions of dollars, too. Clearly, the sharing economy is having an impact. It's becoming an increasingly important part of the overall economy, too. However, there is more to be gained from the sharing economy than just a convenient ride or a cheaper place to stay the night. In fact, many experts believe that adopting practices from the sharing economy could be beneficial in other areas, specifically information security.

### Friend or Foe?
By their very nature, companies are competitive and secretive. They often invest heavily in producing a competitive advantage over rivals, which can take many forms—creation of disruptive new products, cultivation of a powerful brand, or development of an exceptional customer service reputation. None of these strategic plans requires sharing information or collaborating with competitors. However, all types of organizations are witnessing an increasing amount of cyber security threats.

A survey of more than 50 U.S. organizations found that 100 percent reported cyberattacks in the form of viruses, worms, and Trojan horses; 97 percent reported malware; and just under 60 percent indicated they had experienced at least one phishing attack.17 These incidents can result in millions of dollars in costs and can tarnish the brands of the organizations impacted. Announcing that a company has been breached can also result in follow-up attacks as hackers know that (1) the organization is vulnerable and (2) the organization is likely in a state of chaos as security practitioners try to determine the extent of the breach and recover from it. In light of these costs, many organizations choose to remain secretive about cyber incidents. However, is it possible that organizations would be better off sharing information about breaches with others—even competitors—as quickly as possible?

### Sharing is Caring
Let's briefly compare cyberattacks to actual warfare. If one country attacks a number of other countries, are the targeted countries better off responding in isolation, or would they fare better by collaborating to defeat the enemy? Even if they do not join forces, the very act of sharing information about the enemy's weaponry, tactics, and capabilities would surely help. This concept holds true with cyberattacks. Sharing information about attack methodologies, malware, and hacking groups helps companies improve their ability to defend against future attacks.

Companies like IBM that are working to promote information sharing about cyberattacks and to promote government regulations that encourage sharing attack information.18 For example, when a breach occurs in which personally identifiable information (PII) has been compromised, the targeted organization must publicly acknowledge the incident per state and federal regulations.19 The idea is that people should be aware that their data may have been leaked. Furthermore, the SEC requires that companies disclose information about material cyber risks (to inform investors about the potential implications of a cyberattack against a company's stock value). However, what constitutes a material cyber risk is not clearly defined. In short, while some regulations are in place, there are loopholes and wiggle room for organizations to not share—or share as little as possible—about the incident.

While there are clearly some benefits to increasing information sharing across organizations about cyberattacks, some detractors think that doing so will be ineffective or that it is a bad idea. For example, some argue that not announcing a breach, but collecting information about what hackers are doing, can lead to better insights that can be used to stop future attacks. In fact, government agencies are still breached despite their own information sharing about attacks; this provides little evidence that sharing information across other types of organizations will actually make a difference. With threats, and breaches on the rise, something needs to change, but it remains unclear how an environment of sharing could change the impact of and response to cyberattacks.

### Discussion Questions
- 1. Take a minute to consider this hypothetical scenario: You open up your laptop to find that your university e-mail account and your social media accounts have been compromised. The attackers indicate that they are going to post your stolen data on the web. After digging around, you are able to figure out some details about how they were able to access your system. The exploited vulnerability is one that most students at your school also have. Would you want to stand up at the beginning of each of your classes and share information about your breach to help other students avoid being compromised?
- 2. The article makes a comparison between cyberattacks and traditional warfare. Can you think of any ways in which cyberwar is actually different from traditional warfare?
- 3. Do you think that the SEC, state governments, and the federal government should articulate clearer regulations about disclosing cyberattack information? Why wouldn't the initial policies put in place be more clear/effective?
- 4. The article identifies some arguments against information sharing. Can you think of any other reasons why mandating cyberattack information sharing could be ineffective or harmful?

## Security Technology
### Top 10 Application Vulnerabilities
One of the difficulties IT security workers face when performing a classical risk analysis is accurately identifying and estimating threats to their firm. It is difficult to know which threats have the highest probability of affecting the firm. Even if it were possible to accurately assign probabilities to these threats, it would be even more difficult to assign accurate dollar losses associated with each threat.

The CVE database has information on many hundreds of software vulnerabilities. The variety, severity, and criticality of software vulnerabilities are constantly changing. Below is a list of the top 10 vulnerabilities that are likely to be threats to a firm in 2019.21 For those new to the field, it is a great starting point to learn more about vulnerabilities. You will read more about some of these vulnerabilities in later chapters.

Some threats may be more dangerous to certain types of companies. Certain threats may be especially dangerous over a given time period. For example, a known SQL-injection threat could be much more damaging to an online retailer during the peak holiday buying season than it would be to a brick-and-mortar store during the middle of summer.

### MITRE’s CVE Database
In an effort to identify some of the most harmful vulnerabilities, MITRE (www.MITRE.org) collaborates with several other top IT security organizations around the world to produce a continuously updated database of common vulnerabilities and exposures (CVE).20 This is a list of the most harmful vulnerabilities. This list gives IT security workers a good idea of which vulnerabilities probably need to be addressed as soon as possible. This list also helps programmers write more secure code.

| Rank | Name |
|------|------|
| 1 | jQuery File Upload RCE (CVE-2018-9206) |
| 2 | Magecart (CVE-2016-4010) |
| 3 | Wordpress DoS (CVE-2018-6989) |
| 4 | Drupalgeddon 2 (CVE-2018-7600) |
| 5 | Drupalgeddon 3 (CVE-2018-7602) |
| 6 | Telerik's RadAsyncUpload (CVE-2017-11357) |
| 7 | Spring Data Commons (CVE-2018-1273) |
| 8 | Cross Site Scripting (CVE-2018-1999024) |
| 9 | Flash Player Hack (CVE-2018-4878) |
| 10 | Spring OAuth Approval (CVE-2018-1260) |

Top 10 Most Dangerous Software Errors

## Security Ethics
### Securing Privacy
Some organizations have legal requirements to protect the customer data they collect and store, but the laws may be more limited than you think. The Gramm-Leach-Bliley (GLB) Act, passed by Congress in 1999, protects consumer financial data stored by financial institutions, which are defined as banks, securities firms, insurance companies, and organizations that supply financial advice, prepare tax returns, and provide similar financial services.

(continued)
