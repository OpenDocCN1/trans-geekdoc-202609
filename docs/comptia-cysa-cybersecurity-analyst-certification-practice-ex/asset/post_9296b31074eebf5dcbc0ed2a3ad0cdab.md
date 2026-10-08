
expertise means the company doesn't have its own internal CSIRT team?

- A. Retain an incident response provider.
- B. Cross-train all employees in incident response techniques.
- C. None. The company has no ability to respond to incidents.
- D. Empower the night security guard to watch over the data center.

+ **A** is correct. The choice the company has is to retain an external incident response provider.

+ B, C, and D are are incorrect because cross-training all employees to be an effective IR team is not reasonable. C is incorrect because having no ability to respond is unacceptable. D is incorrect because the night security guard is likely unable or unwilling to perform incident response.

## 16. What are the main challenges for the technical role of incident response? (Choose two.)

- A. Having the necessary technical expertise to address the incident
- B. Licensing the proper software tools
- C. Granting or delegating the authority for unforeseen decisions
- D. Overcoming personality differences and in-house rivalries

+ **A and C** are correct. The two challenges are ensuring the technical expertise is at hand, for any reasonably likely incident (depending on what platforms and applications your environment is running) and delegating the authority to members of that team or to immediately accessible managers. Time cannot be wasted for executives to allow a plug to be pulled.

+ B and D are incorrect. Software licenses and personality differences are important obstacles but are hardly challenges in overcoming the urgency of responding to an incident.

## 17. A company that has grown quickly in size has not yet developed a proper communication escalation process in the event of a security incident. Instead, managers of the cybersecurity team post their analysis and findings on the company's internal blog site. In an effort to maintain confidentiality, the blog posts are kept hidden, with no link on the front page. What is the shortcoming of this communication process?

- A. Disclosure based on legislative requirements
- B. Possible inadvertent release of information
- C. No encryption
- D. Little opportunity for discussion and questions

+ **B** is correct. Even though the blog posts are not widely published, their confidentiality is based on the false assurance of “security through obscurity.” Anyone who discovers the accessible posts is a potential leaker or abuser of that information.

+ A, C, and D are incorrect. A is incorrect because no legislative requirements were mentioned. C is incorrect because encryption would not be the primary issue here. D is incorrect because blog posts allow for comments.

# Determining the Impact of Incidents

This chapter includes questions on the following topics:

- Criteria for classifying threats to the network
- How to determine the severity level of an incident
- Best practices for prioritizing security incident response
- The most common types of sensitive and protected data

Incident response is very rarely, if ever, a straightforward activity. Like any other job where you are “putting out fires,” the job of incident response involves constantly measuring severity and then acting accordingly. That is to say, you fight the fire you determine your attention first—you act based on priority.

Prioritizing an incident is a product of several factors, such as the scope of impact (including downtime), what kind of data is affected, and what type of threat you are dealing with. There are other factors as well. How to best identify these factors and thus prioritize your incident response steps are the topics covered in this chapter.

# QUESTIONS

## 1. In terms of skill and determination, what type of adversary is regarded as the most capable and resourceful?
A. Script kiddie
B. Advanced persistent threat
C. Haxor
D. Zero-day

## 2. A company has recently installed an IDS that's capable of detecting a broad set of malicious traffic and operates on signature-based identification. Which of the following types of threats will this IDS identify? (Choose all that apply)
A. Zero-day
B. Threats labeled by CVE
C. Unknown threats
D. EICAR file
E. Known threats

## 3. A cybersecurity team is responding to an incident. To prioritize their actions, an analyst requests a list of essential business processes from the CIO. Select from the following factors which one the analyst is most concerned with to prioritize the team's response.
A. Downtime
B. System process criticality
C. Recovery time
D. Economic

## 4. Of the following metrics, which ones rely on a company being able to endure a certain amount of downtime? (Choose all that apply.)
A. Designated acceptable downtime (DAD)
B. Key performance indicators (KPIs)
C. Maximum tolerable downtime (MTD)
D. Recovery time objective (RTO)

## 5. Multiple factors can affect the severity of an incident. Which of the following factors does not necessarily impact an incident’s severity?
A. Downtime
B. Probability of corruption
C. MTD
D. System process criticality
E. None of the above

## 6. Of the many factors that affect incident severity, which of the following takes the cybersecurity team the longest time to detect issues for or determine the scope of its impact?
A. Data integrity
B. System process criticality
C. Recovery time
D. Type of data

## 7. What is the desired relationship when comparing RTO and MTD?
A. The RTO should be longer than the MTD.
B. The RTO should be shorter than the MTD.
C. The RTO and MTD should be roughly the same.
D. The RTO should as close to zero as possible.
E. The MTD needs to be twice the RTO.
F. The RTO needs twice the MTD.

## 8. The United States Privacy Act of 1974 created rules regarding the collection, storage, and use of what kind of data?
A. Financial
B. Intellectual property
C. PII
D. Payment card information

## 9. Which of the following is not a PCI DSS goal or requirement?
A. Regularly monitor and test networks.
B. Maintain an information security policy.
C. Build and maintain a secure network.
D. Enforce employee security training.
E. Protect cardholder data.

## 10. Select from the following data types that fall under “intellectual property.” (Choose all apply.)
A. The patent behind a company’s best-selling product
B. Trademark
C. Secret recipe
D. Details about a company’s marketing campaign

## 11. An analyst is reviewing DLP logs of sensitive documents attached to outgoing emails. The analyst discovers a secret document titled “Hilltop Organization Chart,” apparently from Hilltop Cabinets, sent to its primary competitor, a company called Sanctuary Sinks. What type of data does this cover?
A. Mergers and acquisitions
B. Accounting data
C. Corporate confidential
D. Intellectual property

## 12. A new virus MSB347, dubbed “Wildfire,” is sweeping through organizations, infecting systems by a previously unknown vulnerability. Wildfire identifies and exfiltrates any spreadsheet documents with large dollar amounts. The documents are covertly sent to a known adversarial country. What is this type of malware?
A. APT exploit
C. Financial exfiltration malware
D. Economic threat

## 13. What is the particular criminal threat when data related to a company’s intent to integrate with another company is mishandled?
A. Leaked information could lead to trading based on privileged knowledge.
B. Shareholders of both companies could vote to stop the merger.
C. Leaked trade secrets could lead to increased competition.
D. Violations of HIPAA requirements.

## 14. Which of the following factors determines some noted event will be considered a security incident?
A. Downtime
B. Scope of impact
C. Economic
D. Types of data affected

## 15. In the context of long-term effects from a security incident, particularly to a company’s reputation and ability to gain potential business, which factor is the most impactful on an incident’s severity?
A. Recovery time
B. integrity
C. Economic
D. System process criticality

## 16. For which of the following types of data is it suggested that a company take additional steps, beyond policy and legal guidance, to protect the data’s confidentiality from unauthorized eyes? Not protecting the selected data type might jeopardize the company’s sustainability.
A. HR personnel information
