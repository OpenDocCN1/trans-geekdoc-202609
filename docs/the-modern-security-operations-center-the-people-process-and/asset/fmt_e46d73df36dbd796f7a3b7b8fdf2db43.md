
The previous section defined SOC roles found in SOCs around the world. Another approach (among many) to exploring these roles and alternative names for them is the U.S. government resource known as the National Initiative for Cybersecurity Education (NICE) Cybersecurity Workforce Framework (NICE Framework). I include this reference as an alternative to how I see job roles within the SOC, since different people will interpret job titles differently.

The NICE Framework is part of the Cybersecurity and Infrastructure Security Agency’s National Initiative for Cybersecurity Careers and Studies (NICCS) and is described on the NICCS website as “a nationally focused resource that establishes a taxonomy and common lexicon to describe cybersecurity work, and workers, regardless of where, or for whom, the work is performed.” You can use the NICE Framework to develop job requirements for recruiting, to prepare questions for interviewing potential candidates, and to get an idea of the skills associated with common cybersecurity job tiles. The rest of this section describes how to drill down to specific job roles on the NICE Framework web page at `https://niccs.cisa.gov/workforce-development/cyber-security-workforce-framework`.

### NICE Framework Components

The NICE Framework is composed of the following components:

*   Seven categories representing a high-level grouping of common cybersecurity functions
*   Thirty-three Specialty Areas representing distinct areas of cybersecurity work
*   Fifty-two Work Roles representing the most detailed groupings of cybersecurity work and composed of specific knowledge, skills, and abilities (KSAs) required to perform tasks in a Work Role

[Figure 4-1](#ch04.xhtml#ch04fig01) shows the seven categories of the NICE Framework as presented on the NICSS website. Notice that the description for each category focuses on the type of work from a high level regarding the type of skillsets people have that work within the category’s field of focus. The descriptions are developed this way to accommodate multiple specific skillsets that may fall under a more generic category. For example, suppose I need an analyst for my incident management SOC service and I want to identify specific job requirements for purposes of recruiting an analyst. I would start with the Protect and Defend category based on the description “Identifies, analyzes, and mitigates threats to internal information technology (IT) systems and/or network” that indicates people in this category have skills in evaluating and responding to events based on security logs or other event logs, which is what incident management is all about. Categories are outcome focused, meaning the field of work, so I would need to drill down deeper to identify associated job roles.

![FIGURE 4-1 NICE Framework Seven Categories](Images/04fig01.jpg)

**FIGURE 4-1** NICE Framework Seven Categories

To better understand the job skills in the Protect and Defend category, I can click the category’s Specialty Area button. [Figure 4-2](#ch04.xhtml#ch04fig02) shows the Protect and Defend category and its four Specialty Areas. Because I am looking for a description of the skills of an analyst for my incident management service, I can narrow down the Specialty Areas to two of the four based on their descriptions: Cyber Defense Analysis and Incident Response. I believe the Vulnerability Assessment and Management Specialty Area could also be useful but would be more relevant to the vulnerability management service than the incident management service for which I need to recruit an analyst. The Incident Response role would be the best choice, but the Cyber Defense Analysis could also do the job based on the number of similar skills as seen with an Incident Response job role. In order to see the specific skills associated with a job role, I will need to click into that role.

![FIGURE 4-2 NICE Framework Protect and Defend Category with Four Specialty Areas](Images/04fig02.jpg)

**FIGURE 4-2** NICE Framework Protect and Defend Category with Four Specialty Areas

Next, I’ll go with my first pick, which is Incident Response specialty area. To see the details of a specialty area, I click the specialty area to bring up the Work Role details. [Figure 4-3](#ch04.xhtml#ch04fig03) shows some of the details of the Cyber Defense Incident Responder Work Role, including a description of the role and the required abilities. As [Figure 4-3](#ch04.xhtml#ch04fig03) indicates, details regarding the knowledge, skills, and tasks of a Cyber Defense Incident Responder can be displayed by clicking the drop-down arrows. The language used by NICE to explain the job role is much more specific, allowing a better understanding of what tasks this type of employee would be expected to know how to do.

![FIGURE 4-3 NICE Framework Cyber Defense Incident Responder Work Role Details](Images/04fig03.jpg)

**FIGURE 4-3** NICE Framework Cyber Defense Incident Responder Work Role Details

Clicking the Knowledge tab in the Incident Responder job role reveals tons of knowledge concepts, as shown in [Figure 4-4](#ch04.xhtml#ch04fig04). These concepts can be extremely useful when creating a job profile for the candidate you plan to recruit for. In [Chapter 3](#ch03.xhtml#ch03), I pointed out that many SOC managers who are responsible for starting a new SOC service don’t know what skills they will need until the service goes live, making it challenging to develop a job profile for a service before it exists. Using the NICE Framework not only can help you develop requirements for job roles based on industry trends but also provides you with a validation point for the type of job titles you should seek out based on what the NICE Framework lists as expected skills associated with a job title.

![FIGURE 4-4 NICE Framework Cyber Defense Incident Responder Knowledge Tab Details](Images/04fig04.jpg)

**FIGURE 4-4** NICE Framework Cyber Defense Incident Responder Knowledge Tab Details

I highly recommend using the NICE Framework if you don’t know the type of skills a person needs to have to work for your SOC service. This same concept can apply as you develop interview questions for potential candidates.

### Role Tiers

Roles within each SOC service can be broken down into different tiers or skill levels, which signify associated responsibilities. For example, a first-tier SOC analyst may be responsible for detecting, identifying, and troubleshooting security events that come into the SOC. Often this is the tier that communicates with the affected party. Responsibilities include detection, classification, and escalation of events. A second-tier analyst may have mitigation responsibilities over any event escalated by a first-tier SOC analyst. If the event requires even further support, a more-experienced third-tier analyst may be involved to remediate the situation. The third-tier analyst might also build tools and processes to improve capabilities within the SOC, including the processes followed by lower-tier analysts. Higher-tier roles have higher compensation but require deeper technical skills and experience. The same tiered approach can apply to other job roles with SOC services, such as a first-tier developer handling basic coding while a higher-tier developer would have responsibilities over the project’s direction.
