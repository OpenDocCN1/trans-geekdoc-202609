
## 6. Order of Volatility

The order of volatility deals with the order in which an incident or investigation would occur. The general rule when dealing with computer systems is to always move from most to least volatility.

## 7. Systems Designed to Facilitate Incident Response

Although this may seem counterintuitive to some, systems should be designed with incident response built in. Security professionals should be involved at each step of the SDLC process. Any time new systems are designed or purchased, someone should be asking if the appropriate secure controls have been implemented. One approach as specified in the NIST documents consists of the following: implementation, monitoring, compliance, strategy, policy, and awareness.

### Digital Forensics Tasks

The term *digital forensics* describes a structured, step-by-step process and analysis of data stored, processed, or retrieved on a computer system in a legal, approved way so that any evidence can be used in court as needed. The forensic process typically addresses the following items:

*   Identification
*   Preservation
*   Collection
*   Examination
*   Analysis
*   Presentation
*   Decision

Although law enforcement has been practicing forensics for many years, private companies are just starting to see the value of digital forensics. Digital forensics can be broken down into three broad categories:

1.  **Computer Forensics** The examination of physical media to obtain information for evidence
2.  **Software Analysis** The review of malware, viruses, and other dangerous software for analysis and potential identification of the author
3.  **Network Analysis** The analysis of network traffic and logs to identify the source and effect of the event

Security professionals should look carefully at the policies and procedures that define how forensic activities are to be carried out. Forensic analysis of compromised systems, cell phones, smartphones, iPads, digital cameras, and USB thumb drives must be addressed. Any existing policy must specify how evidence is to be handled. The *chain of custody* helps protect the integrity and reliability of the evidence by providing an evidence log that shows every access to evidence, from collection to appearance in court.

Many different models are used for forensics. [Figure 7.3](#c07.xhtml#c07-fig-0003) provides an overview of the model used by the Department of Homeland Security.

![FIGURE 7.3 Computer forensics and incident responses model](images/c07f003.jpg)

[**FIGURE 7.3**](#c07.xhtml#c07-fig-anc-0003) Computer forensics and incident responses model

Forensic specialists must know how to record evidence at the scene by taking photographs, documenting their activities in an investigator's notebook, interviewing suspects and witnesses, and knowing the proper procedures for collecting or seizing suspected systems or media. Doing the right thing is required to protect the chain of custody and legality of the evidence. Forensic procedures must document the complete journey of the evidence (from its beginning to the end) and be able to answer these questions:

*   Who collected the evidence?
*   How and where was it collected?
*   Who took possession of the evidence?
*   How was it stored and was it secured while in storage?
*   Who took it out of storage and why was it removed?

This process, also known as electronic discovery, or *e-discovery*, deals with the review of electronic information for the purpose of recovery of evidence. The e-discovery process is all about how you find and extract documents and data stored in electronic format. The trend toward its use will only intensify in the future. Although most investigations may not go to court, computer forensic specialists must collect, review, and preserve structured data that may come from electronic records, contracts, and forms as well as a large amount of unstructured data like emails, chat sessions, and even electronic file fragments. During an investigation, formal records make up an essential part of the discovery process, but this is only half of the picture in today's electronic world. It is becoming increasingly common to ask for copies of selected email and other electronic communications for court cases and legal hearings. The data retention policy should specify how long information is stored. As an example, the IRS can ask for tax records as long as seven years after the tax year. Therefore, most accountants advise businesses to keep tax records for seven years.

[Table 7.1](#c07.xhtml#c07-tbl-0001) lists some common document retention times.

[**TABLE 7.1**](#c07.xhtml#c07-tbl-anc-0001) Common document and data retention policy time

| Document | Time |
| --- | --- |
| Employment contracts and partnership agreements | Permanent |
| Deeds | Six years |
| Trademarks | Life of trademark plus 25 years |
| Copyright | 120 years after author's death |
| Patent deeds | 25 years |

Because the collection of electronic information is such an important concern, the International Organization on Computer Evidence (`www.ioce.org`) was created in 1995 to develop international principles for the procedures relating to evidence discovery. The goal was to develop standards and practices that would be recognized as legal among many countries and states. These principles are summarized as follows:

*   When dealing with digital evidence, all the generally accepted forensic and procedural principles must be applied.
*   Upon seizing digital evidence, actions taken should not change the digital evidence.
*   When it is necessary for a person to access original digital evidence, the person should be trained for that particular purpose.
*   All activity relating to the seizure, access, storage, or transfer of digital evidence must be fully documented, preserved, and available for review.
*   The individual is responsible for all actions taken with respect to digital evidence while the digital evidence is in his possession.
*   Any agency that is responsible for seizing, accessing, storing, or transferring digital evidence is responsible for compliance with these principles.

Because electronic information can so easily be changed, a rigid methodology is to be followed and the "original" is not used for analysis. Best practices in handling the media include the following:

*   The original copy is secured and kept in an unchanged state.
*   The original copy is hashed.
*   The original copy is used to make two bit-level copies.
    *   The primary image is used as a library/control copy.
    *   The second copy is used as a working image and is analyzed.
*   Both copies are hashed upon creation to ensure that they are exact copies.
*   The original copy and the primary copy are secured in a controlled area.

Once a forensic copy has been created, an analyst will begin the process of moving from most volatile to least volatile information. Items such as volatile memory, RAM, system event logs, security logs, files, deleted files, and slack space will be examined. You will need to establish and review system, audit, and security logs. This process must be done correctly, because once the evidence is contaminated, it cannot be decontaminated; therefore, it is important to have a structured forensic process. The general steps of the forensic process are as follows:

1.  **Identify and Acquire** The information must be identified and retrieved. Once it is in the custody of the investigator, a copy is usually created. The standard practice dictates that a bit-level copy be made. A bit-level copy is an exact duplicate of the original data. This allows the investigator to examine the copy while leaving the original intact.
