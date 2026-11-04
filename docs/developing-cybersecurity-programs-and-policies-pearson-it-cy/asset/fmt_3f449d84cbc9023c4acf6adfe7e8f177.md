
* Maintain and use a knowledge base of information
* Use Internet search engines for research
* Run packet sniffers to collect additional data
* Filter the data
* Seek assistance from others
* Keep all host clocks synchronized
* Know the different types of attacks and attack vectors
* Develop processes and procedures to recognize the signs of an incident
* Understand the sources of precursors and indicators
* Create appropriate incident documentation capabilities and processes
* Create processes to effectively prioritize security incidents
* Create processes to effectively communicate incident information (internal and external communications)

### Containment, Eradication, and Recovery
The containment, eradication, and recovery phase includes the following activities:
* Evidence gathering and handling
* Identifying the attacking hosts
* Choosing a containment strategy to effectively contain and eradicate the attack, as well as to successfully recover from it

NIST Special Publication 800-61 Revision 2 also defines the following criteria for determining the appropriate containment, eradication, and recovery strategy:
* The potential damage to and theft of resources
* The need for evidence preservation
* Service availability (for example, network connectivity as well as services provided to external parties)
* Time and resources needed to implement the strategy
* Effectiveness of the strategy (for example, partial containment or full containment)
* Duration of the solution (for example, emergency workaround to be removed in four hours, temporary workaround to be removed in two weeks, or permanent solution)

### Post-Incident Activity (Postmortem)
The post-incident activity phase includes lessons learned, how to use collected incident data, and evidence retention. NIST Special Publication 800-61 Revision 2 includes several questions that can be used as guidelines during the lessons learned meeting(s):
* Exactly what happened, and at what times?
* How well did the staff and management perform while dealing with the incident?
* Were the documented procedures followed? Were they adequate?
* What information was needed sooner?
* Were any steps or actions taken that might have inhibited the recovery?
* What would the staff and management do differently the next time a similar incident occurs?
* How could information sharing with other organizations be improved?
* What corrective actions can prevent similar incidents in the future?
* What precursors or indicators should be watched for in the future to detect similar incidents?
* What additional tools or resources are needed to detect, analyze, and mitigate future incidents?

## Tabletop Exercises and Playbooks
Many organizations take advantage of tabletop (simulated) exercises to further test their capabilities. These tabletop exercises are an opportunity to practice and also perform gap analysis. In addition, these exercises may allow them to create playbooks for incident response. Developing a playbook framework makes future analysis modular and extensible. A good playbook typically contains the following information:
* Report identification
* Objective statement
* Result analysis
* Data query/code
* Analyst comments/notes

There are significant long-term advantages for having relevant and effective playbooks. When developing playbooks, focus on organization and clarity within your own framework. Having a playbook and detection logic is not enough. The playbook is only a proactive plan. Your plays must actually run to generate results, those results must be analyzed, and remedial actions must be taken for malicious events. This is why tabletop exercises are very important.

Table-top exercises could be technical and also at the executive level. You can create technical simulations for your incident response team and also risk-based exercises for your executive and management staff. A simple methodology for an incident response tabletop exercise includes the following steps:
1. **Preparation:** Identify the audience, what you want to simulate, and how the exercise will take place.
2. **Execution:** Execute the simulation and record all findings to identify all areas for improvement in your program.
3. **Report:** Create a report and distribute it to all the respective stakeholders. Narrow your assessment to specific facets of incident response. You can compare the results with the existing incident response plans. You should also measure the coordination among different teams within the organization and/or external to the organization. Provide a good technical analysis and identify gaps.

## Information Sharing and Coordination
During the investigation and resolution of a security incident, you may also need to communicate with outside parties regarding the incident. Examples include, but are not limited to, contacting law enforcement, fielding media inquiries, seeking external expertise, and working with Internet service providers (ISPs), the vendor of your hardware and software products, threat intelligence vendor feeds, coordination centers, and members of other incident response teams. You can also share relevant incident indicator of compromise (IoC) information and other observables with industry peers. A good example of information-sharing communities includes the Financial Services Information Sharing and Analysis Center (FS-ISAC).

Your incident response plan should account for these types of interactions with outside entities. It should also include information about how to interact with your organization’s public relations (PR) department, legal department, and upper management. You should also get their buy-in when sharing information with outside parties to minimize the risk of information leakage. In other words, avoid leaking sensitive information regarding security incidents with unauthorized parties. These actions could potentially lead to additional disruption and financial loss. You should also maintain a list of all the contacts at those external entities, including a detailed list of all external communications for liability and evidentiary purposes.

## Computer Security Incident Response Teams
There are different incident response teams. The most popular is the Computer Security Incident Response Team (CSIRT). Others include the following:
* Product Security Incident Response Team (PSIRT)
* National CSIRT and Computer Emergency Response Team (CERT)
* Coordination center
* The incident response team of a security vendor and Managed Security Service Provider (MSSP)

In this section, you learn about CSIRTs. The rest of the incident response team types are covered in the subsequent sections in this chapter.

The CSIRT is typically the team that works hand in hand with the information security teams (often called InfoSec). In smaller organizations, InfoSec and CSIRT functions may be combined and provided by the same team. In large organizations, the CSIRT focuses on the investigation of computer security incidents, whereas the InfoSec team is tasked with the implementation of security configurations, monitoring, and policies within the organization.

Establishing a CSIRT involves the following steps:
**STEP 1.** Defining the CSIRT constituency.
**STEP 2.** Ensuring management and executive support.
**STEP 3.** Making sure that the proper budget is allocated.
**STEP 4.** Deciding where the CSIRT will reside within the organization’s hierarchy.
**STEP 5.** Determining whether the team will be central, distributed, or virtual.
**STEP 6.** Developing the process and policies for the CSIRT.
