
1. Cyber criminals steal personally identifiable data, such as SSN, date of birth, credit card, etc., from a compromised financial institution (second threat vector in [Figure 2.15](#c02.xhtml#c2-fig-0015)).

2. Criminal sells the data to other criminals who presumably will use it to defraud financial institutions and their customers.

3. A cybersecurity threat intelligence vendor analyst discovers the data for sale, investigates the criminal, and publishes a report of the criminal's activity as a cyber “threat actor.”

4. The threat analyst forwards both the report and the data to the US Department of Homeland Security (DHS) sponsored Financial Industry Information Sharing and Analysis Centers (FS‐ISAC).

5. FS‐ISAC shares both threat and fraud data with members. The targeted enterprise discovers that data was exfiltrated from their systems, but does not know which one.

6. The targeted enterprise uses information in the threat intelligence vendor actor report information to tune cybersecurity protection systems to automatically detect and alert on the threat actor tactics in the intelligence report.

7. The compromised data is incorporated into fraud analysis and prevention systems of all banks, with the result that competitors realize from whom the data was stolen.

![Figure 3.19 Common Scenario Event](images/c03f019.jpg)

[**Figure 3.19**](#c03.xhtml#R_c3-fig-0019) Common Scenario Event

Only after the activity sequence in [Figure 3.19](#c03.xhtml#c3-fig-0019) is completed does the response depicted in [Figure 3.18](#c03.xhtml#c3-fig-0018) begin. In this case, the targeted enterprise finds threat actor tactics in its activity logs via observation or alert and Level 1 would have confirmation that public‐facing sites must be compromised. Then they would immediately escalate to admins for confirmation, who would escalate to the engineers, a conference call would be convened, and a containment decision made. For example, a containment decision might be to shut down the website while the application and infrastructure engineering and operations work overtime to secure their environment. The crisis committee is then convened. At the meeting of the crisis committee, several other enterprise actions may be taken. For example:

* The enterprise Help Desk sets up a special task force to deal with customer complaints,

* A forensics specialist is brought in to identify the point of intrusion,

* Public relations issues a press release, and

* Legal makes arrangements for identity theft protection services for impacted customers and writes letters to them with the details.

While the crisis steps are being taken, SecOps works closely with the technology groups. While the application groups focus on the SQL Injection vulnerability, SecOps and the VPN engineers and admins study the initial threat vector (the second row in [Figure 2.15](#c02.xhtml#c2-fig-0015)) to look for ways to disrupt it. Obviously, threat actors cannot be stopped from sending malicious URLs to staff homes. Perhaps more obviously, trying to train the user community to stop clicking on email does not work. Even if enterprise controls reinforced the training, staff cannot be prevented from falling prey to accidental or malicious malware installs on their home devices. So more network and desktop specialists are brought in to help to examine the next step in the threat vector, and ask “Is it possible to prevent a threat actor from piggybacking on an authorized user connection to the enterprise VPN?” Zero trust technology may provide some way to disallow multiple simultaneous TCP/IP sessions from the same user. If enterprise users can be limited to one session without negative impact, this could thwart a piggy‐back rider. The VPN desktop client could be configured to prevent local network traffic flow on the home machine while it is running, thus disconnecting the threat actor. Perhaps an auto‐termination of sessions left idle for more than a few minutes will help as well. Those controls can be quickly configured and be tested by skilled penetration testers to see if they can figure out a way to exploit the staff’s home computer access even with these new controls in place. If the fix can be implemented and successfully tested, the root cause is determined, and the risk of event recurrence is likely reduced.

For some cyber‐defenders, this is not where the incident ends, but where it begins. This is often the case for the cyber forensics specialist (who may be generically referred to as `CyberForensics` or `cyberforensics`), especially when they have been hired only after the time of crisis has passed. There may still be a significant amount of technology activity in event cleanup, so it is important for them to establish the facts of the case as soon as possible before audit trails or potential malware samples may inadvertently be destroyed or disturbed. Like police at a murder scene, their first task is to make sure no evidence is destroyed. That said, cyberforensics investigators do not necessary collect all the evidence personally. They will know what they are looking for, but need to rely on local standards and procedures to figure out how to find it. `CyberForensics` itself refers to the set of tools, techniques, activity, and goals of the investigation process (Bayuk [2010a](#c03.xhtml#c3-bib-0002), pp. 1–5). [Figure 3.20](#c03.xhtml#c3-fig-0020) depicts the `CyberForensics` mainstay: `CyberForensics` facilitates investigation by preserving evidence that strengthens cases.

Of course, a lead investigator plays a major role, but like all cybersecurity processes, there will be a lot of people involved in various directing and supporting roles. [Figure 3.21](#c03.xhtml#c3-fig-0021) enriches the definition from the investigator’s perspective. Investigators support the CISO or another executive, such as legal or technology management, who may have ordered the investigation. They examine systems in the initial scope of the event and determine what data is available that may be useful in identifying the full extent of the intrusion and its source. From that analysis comes an initial list of system components from which various types of forensic data are harvested and assembled for preservation and analysis. Any unexpected files found on the system are suspected to be malware and subjected to reverse engineering, that is reading the code if it is visible or automatically decoding compiled binary programs to see what commands the malware may have executed at the operating system level.

![Figure 3.20 Cyber Forensics Mainstay](images/c03f020.jpg)

[**Figure 3.20**](#c03.xhtml#R_c3-fig-0020) Cyber Forensics Mainstay

![Figure 3.21 Cyber Forensics Investigation](images/c03f021.jpg)

[**Figure 3.21**](#c03.xhtml#R_c3-fig-0021) Cyber Forensics Investigation

This initial data gathering data step is typically repeated as data from the systems initially identified is likely to include activity logs that highlight additional steps in the threat vector and thereby expand the scope of the investigation. [Figure 3.22](#c03.xhtml#c3-fig-0022) shows the desired output of the iterative analysis. In the best case, a tool like reverse engineering malware will help an investigator understand how the malware threat vector works and that shows them where to look to additional malware that may have been used in the attack. Reverse engineering may also lead to clues in the code that, in combination with threat intelligence, can help identify the threat actor as well. Application data flow analysis may uncover crimes like fraud. Of course, the major output is evidence preservation and chain of custody that can be used in court to prove that the evidence presented therein is the same as that collected at the time of investigation.
