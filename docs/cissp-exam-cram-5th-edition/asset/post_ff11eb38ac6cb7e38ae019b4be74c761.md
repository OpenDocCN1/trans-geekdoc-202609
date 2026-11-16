
- 4. Investigation: Determine what the problem is and who is responsible to mitigate.
- 5. Eradication: Eliminate the problem.
- 6. Recovery: Clean up any residual effects.
- 7. Follow-up and resolution: Improve security measures to prevent or reduce the impact of future occurrences.

Incident response and forensics are very similar, except that incident response is more focused on finding the problem and returning to normal activities, whereas forensics is more focused on legal aspects and potentially prosecuting the accused. Also, only some organizations can justify forensic investigation due to the potential cost.

## Digital Forensics, Tools, Tactics, and Procedures

Governments, the military, and law enforcement have practiced forensics for many years, but forensics is a much younger science for private industry. Its growth in recent years is due to the increased role of computers in the workplace and the types of information and access these computers maintain. There are four types of digital forensics:

- Software forensics: This type of forensics includes analysis of malware and other types of malicious code, such as bots, viruses, worms, and Trojans. Organizations such as McAfee and Symantec perform such duties, and tools like decompilers and disassemblers are used.
- Network forensics: This type of forensics includes review of network traffic and communication. Tools used include sniffers like Wireshark and Snort.
- Computer forensics: This type of forensics includes review of hard drives, solid-state drives, and computer media, such as CDs, DVDs, and USB thumb drives. Tools used include hex editors, Encase, and FTK.
- Hardware/embedded device forensics: This type of forensics includes review of smartphones, tablets, routers, and other hardware devices.

## Tip

Hardware forensics continues to grow in importance as our reliance on electronic devices increases. One report from a former Pentagon analyst alleges that a large amount of foreign-made Telco gear has built-in backdoors (see www.zdnet.com/former-pentagon-analyst-china-has-backdoors-to-80-of-telecoms-7000000908/).

Digital forensics is a complex field and includes the following stages:

- 1. Plan and prepare to be creating procedures and policies and conducting training.
- 2. Secure and isolate the scene to prevent contamination.
- 3. Record the scene by taking photographs and recording data in an investigator's notebook.
- 4. Interview suspects and witnesses.
- 5. Systematically search for other physical evidence.
- 6. Collect or seize the suspect system or media.
- 7. Package and transport evidence.
- 8. Submit evidence to a lab for analysis.

Before discussing the steps of digital forensics in more detail, let’s examine the overall concepts and targets of forensic activities. Digital forensics defines a precise methodology to preserve, identify, recover, and document computer or electronic data. Growth in this field is directly related to the ever-growing popularity of electronics.

Computers are some of the most commonly targeted items, but they are not the only devices subject to forensic analysis. Smartphones, tablets, digital cameras, iPods, USB drives, and just about any other electronic device can also be analyzed. Attempted hacking attacks and allegations of employee computer misuse have added to the need for organizations to examine and analyze electronic devices. Mishandling concerns can cost organizations millions of dollars. Organizations must handle each event in a legal and defensible manner. Digital forensics follows a distinct and measurable process that has been standardized.

## Standardization of Forensic Procedures

In March 1998, the International Organization on Computer Evidence (IOCE; www.ioec.org) was appointed to draw up international principles for procedures related to digital evidence. The goal was to harmonize methods and practices among nations and guarantee the ability to use digital evidence collected by one country in the courts of another country. The IOCE has established the following six principles to govern these activities:

- When dealing with digital evidence, all generally accepted forensic and procedural principles must be applied.
- Upon seizing digital evidence, actions taken should not change that evidence.
- When it is necessary for a person to access original digital evidence, that person should be trained in the techniques to be used.
- All activity relating to the seizure, access, storage, or transfer of digital evidence must be fully documented, preserved, and available for review.
- An individual is responsible for all actions taken with respect to digital evidence while the digital evidence is in his or her possession.
- Any agency that is responsible for seizing, accessing, storing, or transferring digital evidence is responsible for compliance with these principles.

## Digital Forensics

Digital forensics can be subdivided into three stages:

- 1. Acquisition: Acquisition is usually performed by means of a bit-level copy. A bit-level copy is an exact duplicate of the original data, made using a write blocker, that allows an examiner to scrutinize the copy while leaving the original intact.
- 2. **Authentication**: An investigator must show that the original data is unchanged and has not been tampered with; the investigator must be able to prove that the bit-level copy is an exact copy. Authentication can be accomplished through the use of checksums and hashes, such as MD5 and SHA.

**Tip** Message digests, such as MD5 and SHA, are used to ensure the integrity of files and data and to ensure that no changes have occurred.

- 3. **Analysis**: An investigator must be careful while examining the data and ensure that all actions are thoroughly documented. The investigator recovers evidence by examining files, state information, drive slack space, file slack space, free space, hidden files, swap data, Internet cache, and other locations, such as the Recycle Bin. Copies of the original disks, drives, or data are usually examined to protect the original evidence.

### Acquisition

Acquisition refers to assuming possession of evidence or contracting to assume possession. In many instances, a forensic analyst is asked to acquire hard drives, computers, media, or other items on site. Just as with any other investigation, an analyst in a digital forensics case should make careful notes about what physical evidence is recovered and show the chain of custody for all evidence acquired. Physical evidence and digital forensics can help build a relationship between an incident scene, a victim, and a suspect (see Figure 8.7).

![](img/cd307d33c10f35ada49ea76811ef60ad_646_0.png)

**Figure 8.7** Relationship of Evidence to Suspect

During the acquisition stage, the following processes occur:

- Documentation and collection of the evidence
- Protection of the chain of custody
- Identification, transportation, and storage
- Approved duplication and copying

During collection and handling of evidence, it is important to record everything. You can use a digital camera to record the layout of the scene. You need to document the condition of the computer systems, attachments, cables, physical layout, and all electronic media. You can also use a camera to take pictures of any screen settings visible on a running system. You should also document internal storage devices and hardware configuration, including hard drive make, model, size, jumper settings, location, and drive interface as well as internal components such as the sound card, video card, and network card.

> **Tip**
>
> The handling of evidence is of special importance to a forensic investigator. This is addressed through the *chain of custody*, a process that helps protect the integrity and reliability of the evidence by providing an evidence log that shows every access to evidence, from collection to appearance in court.

A forensic analyst needs to keep adequate records and build a proper chain of custody. Although the chain of custody is something that those in law enforcement are familiar with, it might be new to many IT professionals but will surely be called into question for all digital evidence in the court of law as well. Chain of custody is used to address the reliability and credibility of evidence. Chain of custody is the process of documenting the journey of any and all evidence while keeping it under control. Chain of custody should be able to answer the following questions:

- Who collected the evidence?
- Where was the evidence collected?
- When did possession of the evidence occur?
- How was the evidence stored and protected (that is, what software tool was used)? Is this a best practice tool used by the industry? Is the professional trained on use of the tool? How many times has the professional used the tool?
- If evidence was removed from storage, why, by whom, and for how long was it taken from storage?

**Caution**

Computer evidence is very volatile; it is therefore of utmost importance to protect the chain of custody throughout the entire evidence lifecycle.

Even though many forensic investigations might not lead to court cases or legal showdowns, some do, so you must always maintain the integrity of evidence. After collecting and recording evidence, it is likely that you have reached the point at which you might need hard drives or fixed disks for
