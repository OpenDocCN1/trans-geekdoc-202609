
## Business Impact Analysis (BIA)

The purpose of a BIA is to determine what people, process, and technology must be available to sustain the business. The disaster recovery team can associate values with the loss of people, process, and technology to determine the types of redundancy that should be used as a countermeasure to the risk of loss. For example, a SOC’s datacenter would be critical to the operation of the SOC. A BIA would represent how critical the datacenter is based on the daily loss that would occur if the datacenter were to go down, how the SOC going offline would impact the business, and potential risk reduction items. Including BIA documents within the DRP will inform the team of the impact of losing any person, system, or data due to a disaster.

## Step-by-Step Disaster Recovery Plan

This plan informs the team where all other disaster recovery data is located as well as the location of the backup of the plan. The DRP also includes contact information for every member of the disaster recovery team, specifies where the team is supposed to meet, and specifies any backups to the meeting location and contacts in case the primary location or any team member is lost or unavailable during a disaster. It is recommended to store a backup of the DRP at a different facility from where the primary plan is stored. Another recommendation is to have a backup facility that is at another location that would likely not be impacted by a disaster that would compromise the primary disaster meeting place. The specifics of how far away the backup facility should be located would be based on your organization’s business requirements and risk tolerance. The steps included in the DRP must accommodate all the items pointed out in ISO/IEC 27031. This includes documenting the knowledge needed to restore the business as well as the facilities, technology, data, and suppliers that are critical to the business.

> **Note**
>
> It is critical that all documentation is dated and tested to ensure the disaster recovery plan is effective and up to date. You do not want to find an out-of-date DRP during a real disaster!

## Security Considerations

Another important topic to cover regarding planning the design of a SOC is what security technology and processes will be used to protect the SOC. If a key tool such as the time server or logging system is compromised by an adversary, many of the SOC services will be rendered useless. This type of failure not only could undermine the value of the SOC but also could cause future investment in and trust of the SOC to diminish.

Remember, adversaries know they are up against the defense of their identified target. They know companies install antivirus measures, deploy security tools on the network, and have people responsible for monitoring those tools. Adversaries have labs and develop methods to beat security and hide from administrators.

Some security topics that need to be part of the security planning for the SOC are as follows:

*   Policy and compliance
*   Network access control
*   Encryption
*   Internal security tools

> **Note**
>
> Security requirements for the SOC will be different than what exist for the organization. The SOC will contain sensitive information about the organization and therefore should not just adopt the organization’s security standards.

### Policy and Compliance

The term `compliance` means to meet some goal. That goal will vary by industry and how an organization operates. Some compliance goals are requirements pushed by local government, which if not followed will lead to fines (or possibly even incarceration in extreme cases) for those responsible for the organization’s compliance. Other compliance goals are mandated by the leadership of an organization, meaning there isn’t any legal obligation; however, the organization has made meeting the compliance goal an obligation for the organization. Some leaders will convert industry recommendations (known as guidelines) into mandated compliance goals with the intent of establishing a baseline of security practices within the organization. [Chapter 6](#ch06.xhtml#ch06), “[Reducing Risk and Exceeding Compliance](#ch06.xhtml#ch06),” covers common forms of mandated and recommended compliance as well as how to enforce compliance goals with policies, procedures, and standards.

Regarding building a SOC, there might be compliance goals that exist or are desired by the organization that must be met before the SOC can move to a go-live status. The most common pre-SOC compliance requirements are those required by local and federal governments as well as those aligned with business operations as stated within an organization’s policies. The Health Insurance Portability and Accountability Act (HIPAA) is an example of a U.S. law that mandates compliance by all organizations (“covered entities”) in the United States that handle protected health information (PHI). The Payment Card Industry Data Security Standard (PCI DSS) is an example of a standard that mandates compliance by all organizations that accept, process, store, or transmit credit card information. It is critical that the SOC identify all required compliance and ensure requirements are met pre-launch. [Chapter 6](#ch06.xhtml#ch06) will cover the most common legal and financial compliance requirements your SOC needs to be aware of.

`Policies` are high-level requirements the organization must follow and are set by leadership. `Procedures` contain the details for how to follow policies. Not only will the SOC need to adhere to all policies, but there might be adjustments to how the SOC will be developed and operate in order to be compliant with corporate policies. The SOC will need to verify any pre-launch compliance requirements with the SOC sponsor regardless of whether those requirements are legal or corporate driven. By doing so, the SOC will have executive support that all compliance has been met. I highly recommend ensuring that legal, financial, and other compliance identified by your SOC sponsor is addressed as early in the planning phase as possible to avoid disruption of later steps due to compliance violations. Compliance violations can prevent a SOC from going live!

> **Note**
>
> You will need a SOC sponsor that understands your organization’s compliance requirements. If you are unsure if your SOC sponsor would know all of those requirements, validate with other leadership. Do not assume you have met all compliance requirements without proper validation.

### Network Access Control

Network capacity planning and security requirements provide the basic foundation for developing the SOC’s network as well as how the SOC can secure the organization. A foundational security requirement for many modern SOCs is segmentation and controlling access to and between segments. Access control needs to be delivered in a least-privilege design, permitting only necessary services to access or leave a network segment. I recommend isolating device types based on their associated risk and dependencies, but very elaborate segmentation can be complicated to deploy and manage. My most basic device segmentation recommendation is to isolate guest users, employees, administrators, IoT devices, mobile devices, SOC tools, malware testing, and critical systems.

### Profiling
