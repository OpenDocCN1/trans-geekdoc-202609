
The CSF is meant as a guide. The interesting thing about these implementation tiers is that they are not meant as a maturity diagram. The expectation is that they are to be left up to the organization based on its unique business and risk tolerance. All individual business units within the organization should operate at the maximum risk tolerance allowed. In healthcare, patient care should be the number one priority and security should be delivered as a best effort given individual resource restraints. Security programs shouldn’t consume more resources (manpower, money, and so on) than absolutely necessary because that would impact the primary mission.

---

![image](note.jpg) **NOTE** The complete CSF can be found at `http://nist.gov/cyberframework`.

## Detect

Conventional wisdom would have this section start with the identify phase. We will start in the middle, however, because as of this writing this is a giant hole, or vulnerability, in healthcare. Plus, if there is one aspect of a security program that it is better to be good at than another this is it. The “Anatomy of a Cyberattack” section previously described some common steps that an attacker takes. All those steps not only take time but also leave a trail, which enables a robust detection ability to make up for some deficiencies in other areas of the process.

This may immediately raise a few questions. Where is the starting point? What is affordable? This segues into a discussion about the building blocks for deploying a detection capability, as shown in [Figure 11-3](#ch11.html#ch11fig3).

![image](f0289-01.jpg)

---

**Figure 11-3** Elements of detection in order of complexity

### Logging

Logging is the most basic element of detection that every organization should be doing. Most of the devices on your network have built-in functionality to perform logging, and this functionality is probably already being used to perform health and status monitoring on most of these devices. Syslog is the most common format for the logs, but vendors sometimes choose to log in another format. Regardless, this should be fairly straightforward to set up. A central repository, called a *log aggregation point*, is needed to collect these logs. A storage area network (SAN) is most likely already in existence, and a slice of that storage can be used. Try to pull every log that can be collected without an extreme workload. These logs could also utilize cloud computing if that is used in the environment today. The goal is to get the logs into a central location as easily as possible to provide a base of information used later in the program.

### Log Searching

Now that logs are centrally stored somewhere, the next step in the detection process can be executed. Collecting all the logs may seem a little overwhelming, as the typical healthcare network puts out millions of log events a day. This is where the searching capability comes into play. There are numerous tools on the marketplace that can provide this functionality. Some notable vendors are Splunk, McAfee, Alert Logic, and HP, all of which come with preconfigured alerting functionality, graphical interfaces, and various training resources.

---

![image](note.jpg) **NOTE** Do not forget about open source tools such as OSSEC or Syslog-ng. These are great tools with good community support that will work for a smaller organization with a limited budget.

Once the tools are installed, the people with network monitoring responsibilities can begin by getting familiar with the ebb and flow of the network. Repeatable patterns in the data will begin to emerge, leading to the next step, which is eliminating the routine traffic from view. This removes a great deal of noise from the log searching. Next is to look for unusual occurrences such as failures, errors, administrative access, and changes. This hunting process may seem daunting at first, but with time it can be done effectively. An example might be an IP from the DMZ using administrative accounts on the access control system in another network segment. This odd behavior is the kind of thing that should be sought out and addressed.

Within the CSF, the detect phase has three parts: anomalies and events, security continuous monitoring, and detection processes. The functionality described in the preceding paragraph covers all three of these categories. Your organization would be at tier three of the CSF, within this part of the program, provided you

- Are collecting logs from the entire organization
- Have a repeatable process for searching
- Have a repeatable process for using the output in the incident response process

---

![image](tip.jpg) **TIP** In the United States, the HIPAA security rule doesn’t currently have any required controls for monitoring, but there are addressable ones that you would have covered at this point, such as `164.308(a)(5)(ii)(B)`, Protection from Malicious Software.

### Security Information and Event Management (SIEM)

Taking detection to a more sophisticated level involves additional tools, processes, and people and will consume a great deal more resources. The biggest tool needed is a security information and event management (SIEM) system. SIEM systems start by ingesting all of the logs just like the log management systems previously described, but then they add intelligence analytics on top that would have been done manually without it. They are able to correlate all the logs that are related during network activity. Alerting is done off of this using common, behavior-based use cases built in to the system. Custom use cases can also be created and added to the system in order to alert based on specific things in the environment. Use cases will be covered in the next section. Along with alerting of potential incidents, policy violations, compliance, and so on, is reporting capability through a dashboard.

Tools like this can absolutely catapult the detection capabilities of an organization, but there is more to the puzzle. People and processes need to be in place to maximize the benefit of tools like this. Most often when these tools have been deployed people aren’t using them because they didn’t have the necessary supporting structure. In these cases, a good log management solution would have provided the same functional benefit at a much lower resource consumption. People needed to run these devices would need skills in areas such as SIEM management, database management, and threat intelligence. Separate people, usually referred to as analysts, would be needed to spend ample time hunting through the alerts to find the incidents that need to be worked through the incident management process. All of these systems and job duties require solid, repeatable processes and procedures to be generated.

This level of commitment is not for the faint of heart. Best practices for any organization thinking of this must have a solid plan around risk tolerance, resource availability, and total cost of ownership for this endeavor. If the organization is very large and has highly valuable assets, then this is something that might be a good investment. With the right plan and funding, this can be extremely valuable in hunting and remediating the items discussed earlier in the anatomy of a cyberattack. If the organization is small, there are ways to get this functionality. For example, there are many vendors that will perform this service using their tools, providing the benefit at a fraction of the cost of doing it in house. Owning the centralized logging gives you all the information and provides options for getting SIEM functionality. If the outsourced engagement for monitoring via a SIEM is not working out, then switching vendors will have minimal impact. The logs collected are the basis for any monitoring that takes place and these are what should always be controlled by the organization.
