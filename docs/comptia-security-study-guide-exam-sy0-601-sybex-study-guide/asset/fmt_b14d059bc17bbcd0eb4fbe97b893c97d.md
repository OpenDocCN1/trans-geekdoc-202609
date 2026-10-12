
# Acquisition Tools and Forensic Suites

Acquisition tools and forensic suites provide the ability to collect forensic images and data and to analyze them using powerful capabilities like automatic recognition of images and documents, as well as timelining and other features. Hashing and validating ensures that acquired images are intact, and matching the source data helps ensure that the forensic data will be admissible in court.

Reporting occurs at the end of a forensic analysis and needs to be complete, with documented reasoning for each conclusion or statement made about the forensic evidence. A standard forensic reporting format helps ensure that readers know what to expect and that they can easily understand what is being presented.

Forensic techniques may be used for more than just investigations and incident response. They also have a role to play in both intelligence and counterintelligence activities. Intelligence organizations may acquire information using forensic techniques or work to combat other organizations' activities by examining the tools and artifacts that they leave behind.

## Exam Essentials

**Legal holds and e-discovery drive some forensic activities.** Organizations face legal cases and need to respond to legal holds, which require them to preserve and protect relevant information for the active or pending case. E-discovery processes also require forensic and other data to be provided as part of a legal case. Organizations must build the capability and technology to respond to these requirements in an appropriate manner to avoid losing cases in court.

**The order of volatility is used to determine what to acquire first.** Different system components and resources are more likely to be changed or be lost during the time a forensic acquisition takes. Thus, forensic practitioners refer to the order of volatility to determine what is the most volatile and what is the least volatile. `CPU cache` and registers are typically the most volatile, followed by the process table, `ARP cache`, kernel statistics, and similar data. Next, system `RAM`; temporary files and swap space, with data on the hard disk; remote logs; and finally backups are all less volatile. Your forensic acquisition process should take the order of volatility into account as well as the circumstances of your acquisition process to determine what to capture first.

**Cloud concerns must be dealt with before forensic response is needed.** Since cloud environments are typically hosted in third-party infrastructure, the ability to directly conduct forensics is frequently not available. Organizations may need to build in contractual capabilities, including right-to-audit clauses, regulatory and jurisdictional choices, and data breach notification requirements and timeframes.

**There are many options for acquisition tools, and selecting the right tool combines technical needs and skillsets.** Image acquisition tools provide the ability to copy disks and volumes using a bit-by-bit method that will capture the complete image, including unused, or slack, space. Tools range in complexity from the built-in Linux `dd` utility to free tools like `FTK Imager` that can handle both drives and memory acquisition. `WinHex`, a commercial tool, provides additional drive analysis features as well as acquisition capabilities. When network data needs to be acquired, `Wireshark` and other network analyzers play a role to capture and analyze data. Finally, specialized tools and practices may be required to acquire virtual machines and containers, and those practices and procedures need to be identified and practiced before a forensic examination becomes necessary to ensure the tools and capabilities are in place.

**Forensic suites provide features that make investigations easier and more complete.** A forensic suite like `Autopsy` provides tools to manage and organize investigations as well as a complete set of tools. Those tools typically include the ability to ingest, analyze, and automatically identify common forensic targets such as images, Office documents, text files, and similar artifacts. They also provide timelining capabilities, tools to assist with reporting and markup of the forensic data, and a wide range of other features useful for forensic examination. Although `Autopsy` is one example, commercial tools are broadly available with advanced features.

**Validating acquired data helps keep it admissible.** Hashing drives and images ensures that the acquired data matches its source. Forensic practitioners continue to commonly use `MD5` or `SHA1` despite issues with both hashing methods because adversarial techniques are rarely at play in forensic examinations. Checksums can be used to ensure that data is not changed, but they do not create the unique fingerprints that hashes are also used to provide for forensic artifacts.

**Forensic reports must be well organized and to the point.** Forensic analysis doesn't end when the technical examination of devices and drives is over. Forensic reports summarize key findings, then explain the process, procedures and tools, as well as any limitations or assumptions that impact the investigation. Next, they detail the forensic findings with appropriate evidence and detail to explain how conclusions were reached. They conclude with recommendations or overall conclusions in more detail than the summary provided.

## Review Questions

1.  Cynthia wants to make an exact copy of a drive using a Linux command-line tool. What command should she use?

    1.  `df`
    2.  `cp`
    3.  `dd`
    4.  `ln`

2.  Greg wants to use a tool that can directly edit disks for forensic purposes. What commercial tool could he select from this list?

    1.  `dd`
    2.  `memdump`
    3.  `WinHex`
    4.  `df`

3.  Gabby wants to capture the pagefile for a system. Where will she find the pagefile stored?

    1.  In memory
    2.  On disk
    3.  In a CPU register
    4.  In device firmware

4.  Which of the following is a memory forensics toolkit that includes `memdump`?

    1.  `FTK Imager`
    2.  `WinHex`
    3.  `dd`
    4.  `Volatility`

5.  Charles wants to obtain a forensic copy of a running virtual machine. What technique should he use to capture the image?

    1.  Run `dd` from within the running machine.
    2.  Use `FTK Imager` from the virtual machine host.
    3.  Use the VM host to create a snapshot.
    4.  Use `WinHex` to create a copy from within the running machine.

6.  Melissa wants to capture network traffic for forensic purposes. What tool should she use to capture it?

    1.  A forensic suite
    2.  `Wireshark`
    3.  `dd`
    4.  `WinHex`

7.  Frank is concerned about the admissibility of his forensic data. Which of the following is not an element he should be concerned about?

    1.  Whether the forensic source data has remained unaltered
    2.  Whether the practices and procedures would survive review by experts
    3.  Whether the evidence is relevant to the case
    4.  Whether the forensic information includes a timestamp

8.  What is the document that tracks the custody or control of a piece of evidence called?

    1.  Evidence log
    2.  Audit log
    3.  Event report
    4.  Chain of custody

9.  Isaac is performing a forensic analysis on two systems that were compromised in the same event in the same facility. As he performs his analysis, he notices that the event appears to have happened almost exactly one hour earlier on one system than the other. What is the most likely issue he has encountered?

    1.  The attacker took an hour to get to the second system.
    2.  One system is set to an incorrect time zone.
    3.  The attacker changed the system clock to throw off forensic practitioners.
    4.  The forensic tool is reading the timestamps incorrectly.

10. What legal concept determines the law enforcement agency or agencies that will be involved in a case based on location?

    1.  Nexus
    2.  Nonrepudiation
    3.  Jurisdiction
