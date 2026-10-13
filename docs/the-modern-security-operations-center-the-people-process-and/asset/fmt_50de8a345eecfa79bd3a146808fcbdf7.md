
*Chain of custody* is a term used in forensic practices referring to the logical sequence that records the custody, control, transfer, analysis, and disposition of physical or electronic evidence in legal cases. Documenting each step in the chain of custody of evidence is essential because if uninterrupted custody cannot be proven, the evidence might be rendered inadmissible. This means chain of custody occurs at the point of collection and is maintained until the artifact is returned to the owner.

The first key part of the chain of custody process is identifying what can be collected. What should *not* be collected is any evidence that you are not authorized to collect or that is not relevant to the case you are building. For evidence that you can’t collect but could apply to the case, you will want to seek a warrant from the proper legal authority to collect the artifact. For artifacts that are not relevant, you will need to mark them as processed and not relevant in your Prepare/Extracted list. Doing so ensures they are not collected when the extraction process begins as well as includes their existence in the first responder artifact collection process. A prepare/extracted list is a document the first responder uses to report everything that exists within the crime scene to clearly define what does and does not need to be collected.

Whatever is relevant needs to be documented in a relevant data list. Documentation must include pictures, descriptions, and other recording allowing for a complete picture of the artifact that will be investigated. It is ideal to upload all of this documentation to a forensics case management tool if one is available. As data is gathered about an artifact, it is very possible that new artifacts or leads to new artifacts of interest will be discovered. For example, you can identify a computer and find other devices, such as a phone, are connected to it, leading to new potential evidence. Now you will need to repeat the documentation process and treat the phone as a new item with its own relevant data list. This entire process is repeated until no more artifacts need to be addressed. [Figure 8-28](#ch08.xhtml#ch08fig28) shows the steps taken prior to extracting artifacts from a crime scene.

![FIGURE 8-28 Chain of Custody Documentation Bag Example](Images/08fig28.jpg)

**FIGURE 8-28** Chain of Custody Documentation Bag Example

### Chain of Custody Process

Chain of custody occurs during the entire forensic investigation process, which can be broken down into the following four steps:

1.  **Collection:** Artifacts are documented, collected, and secured until they can be transported to a place of examination.

2.  **Examination:** There are different approaches that can be taken to examine artifacts. The entire examination process must be documented so that any questions about what was performed to find any evidence can be clearly answered.

3.  **Analysis:** The analysis is the overall result of the examination. Analysis is designed to answer questions that are brought up in a specific case.

4.  **Reporting:** The final step is to develop a summary of all documentation of the collection, examination, and analysis process. The reporting must include all tools used, who was involved and what was their role, and any issues that occurred during the entire process.

Securing artifacts during the collection phase is commonly done with a sealed bag that has a label designed for digital forensics, as shown in [Figure 8-29](#ch08.xhtml#ch08fig29). Any interaction with the sealed artifact is documented on the label, including transporting it to a new location or pulling it for examination. Sealed artifacts that are not being used must be stored in a secure location, such as a safe, and the secure location must have an access log to document all details of any access to the location.

![FIGURE 8-29 Chain of Custody Documentation Bag Example](Images/08fig29.jpg)

**FIGURE 8-29** Chain of Custody Documentation Bag Example

> **Note**
>
> NIST SP 800-86, *Guide to Integrating Forensic Techniques into Incident Response*, provides a sample chain of custody tracking form you can download as your template for tracking artifacts.

The examination of artifacts needs to include various forms of documentation, including video recording, photography of steps taken, and a written report explaining exactly what was done and by whom. Anybody involved with the examination should be prepared to appear in a court proceeding if the only defense necessarily needs explanation about the examination process or how a conclusion was made during the analysis phase of the forensic process. All of these details will be included in the final report; however, live questioning might be required after the report is provided and used in a court of law.

To prove chain of custody, all examiners need to be prepared to answer the following questions:

*   Where is the proof for the evidence found?
*   How did you acquire the evidence?
*   When was the evidence gathered?
*   Who handled the evidence?
*   How was the evidence secured when not handled?
*   Why did that specific person handle the evidence?
*   Are there any gaps in monitoring or securing the evidence?

More detailed questions will be asked about the specifics of the case; however, the previous questions are examples of the general types of questions that may be posed to a witness to establish whether a proper chain of custody was maintained. What is key is having proper chain of custody performed and documented to ensure all evidence is admissible in court.

#### Working with Evidence

Evidence can be anything that can help to prove a case. Technology that has any form of data storage or memory can contain evidence. This includes computers, mobile devices, answering machines, memory drives, digital cameras, printers, networking hardware, servers, and IoT equipment.

There are a few fundamental principles that must always be followed when working with digital evidence. Make sure to follow all of these key points anytime you are working with evidence that could be used for legal action:

*   Never work with the original
*   Make one or more bit-level copies
*   Validate the copies with the original using hash validation
*   Secure the original and copies
*   Enable write block (not allowing the ability to edit a file) when investigating a copy of the evidence
*   Document everything

The last point is critical in rebutting any claim that the forensic team obtained evidence illegally or mishandled evidence during the investigation process. Most professionals use software to document the entire forensic process, allowing for simple access to any step that was taken, including a place to save notes, images, and other details obtained during that step of the forensic investigation.

One popular open-source option for documenting the forensic process is `Autopsy`. `Autopsy` is available in `Kali Linux` and can be accessed by going to **Applications > Forensics** and choosing **Autopsy**. Once `Autopsy` is running, you simply go to `http://localhost:9999/autopsy` and access the main GUI, shown in [Figure 8-30](#ch08.xhtml#ch08fig30).

![FIGURE 8-30 Autopsy Main Page](Images/08fig30.jpg)

**FIGURE 8-30** Autopsy Main Page

From the main page, you can open an existing case or create a new case. For this example, I’ll create a new case and start investigating a computer. Once I create a host entry for the computer, I can upload images, make notes about what I have done with the computer, upload hashes to verify I have not changed anything as I investigate the copy of the computer, and add any other notes. [Figure 8-31](#ch08.xhtml#ch08fig31) shows some of these options in `Autopsy`.

![FIGURE 8-31 Autopsy Usage Example](Images/08fig31.jpg)
