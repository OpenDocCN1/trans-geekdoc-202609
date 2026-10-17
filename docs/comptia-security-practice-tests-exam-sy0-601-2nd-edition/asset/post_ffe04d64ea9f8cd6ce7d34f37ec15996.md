
- **56. D.** The memdump tool is a command-line memory dump utility that can dump physical memory. Somewhat confusingly, memdump is also a flag in the very useful Volatility framework, where it can be used to dump memory as well. The remaining options were made up and are not Linux tools, although you can create a ramdump on Android devices.

- **57. B.** The Windows swapfile is `pagefile.sys` and is saved in the root of the `C:\` drive by default.

- **58. A.** The best way to capture a virtual machine from a running hypervisor is usually to use the built-in tools to obtain a snapshot of the system. Imaging tools are not typically capable of capturing machine state, and `dd` is not designed to capture VMs. Removing a server’s drives can be challenging due to RAID and other specific server configuration items, and doing so might impact all other running VMs and services on the system.

- **59. C.** A well-documented chain of custody can help establish provenance for data, proving where it came from, who handled it, and how it was obtained. Right to audit, timelines, and preservation of images do not establish provenance, although preservation is part of the chain of custody process.

- **60. B.** Digital forensics techniques are commonly used to analyze attack patterns, tools, and techniques used by advanced persistent threat (APT) actors for counterintelligence purposes. They may sometimes be used to determine what information was stolen, but this is not the most common use for digital forensic techniques, nor is their use as a training mechanism.

- **61. A.** Law enforcement is not typically part of organizational incident response teams, but incident response teams often maintain a relationship with local law enforcement officers. Security analysts, management, and communication staff as well as technical experts are all commonly part of a core incident response team.

- **62. A.** Even if you’re not familiar with `iptables`, you can read through these rules and guess which rule includes the right details. DROP makes sense for a block, and you should know that SSH will be a TCP service on port 22.

- **63. C.** `logger` is a Linux utility that will add information to the Linux syslog. It can accept file input, write to the system journal entry, send to remote syslog servers, and perform a variety of other functions. The other commands do not directly interface with the system log.

- **64. A.** Incident response plans don’t stop incidents from occurring, but they do help responders react appropriately, prepare the organization for incidents, and may be required for legal or compliance reasons.

- **65. D.** Degaussing a drive uses strong magnetic fields to wipe it and is the least likely to result in recoverable data. Deleted files can often be recovered because only the file index information will be removed until that space is needed and is overwritten. Quick formats work in a similar way and will leave remnant data, and files that are overwritten by smaller files will also leave fragments of data that can be recovered and analyzed.

- **66. D.** Henry’s most likely use for the video is to document the forensic process, part of the chain of custody and provenance of the forensic data he acquires. The order of volatility helps determine what devices or drives he would image first. There is no crime being committed, so establishing guilt is not relevant to this scenario, and the video will not ensure data is preserved on a drive during a forensic process.

- **67. B.** WinHex is the only disk editor in this list. Autopsy is a forensic analysis suite; `dd` and FTK Imager are both imaging tools. WinHex also provides the ability to read RAID and dynamic disks, perform data recovery, edit physical memory, clone disks, wipe files and drives, and a variety of other functions.

- **68. B.** Playbooks list the required steps that are needed to address an incident. A runbook focuses on the steps to perform an action or process as part of an incident response process. Thus, a playbook may reference runbooks. Business continuity (BC) plans and disaster recovery (DR) plans are not used for incident response, but they are used to ensure that a business stays online or can recover from a disaster.

- **69. C.** Passwords are typically stored using a hash, and best practices would have them stored using a password security–specific hash. Alaina can speed up her efforts if she knows what hashing algorithm and options were used on the passwords. The age and length of the passwords are not necessary, and passwords should not be stored in encrypted form—but the question also specifically notes they’re hashed passwords.

- **70. D.** An application block list would fit Vincent’s needs the best from the list provided. An approved list would prevent other tools from being installed, which may impede functionality while making the maintenance of the list challenging. A data loss prevention (DLP) solution attempts to prevent data from being sent or posted but does not prevent installations or downloads of games. A content filter might help, but workarounds are easy, including sending games via email or via a thumb drive.

- **71. B.** IPSec is not a tool used to capture network flows. sFlow, NetFlow, and IPFIX are all used to capture network flow information, which will provide the information Charlene needs.

- **72. C.** A system crash, or system dump, file contains the contents of memory at the time of the crash. The infamous Windows blue screen of death results in a memory dump to a file, allowing analysis of memory contents. The swapfile (pagefile) is used to store information that would not fit in memory but is unlikely to contain a currently running malware package, since files are swapped out when they are not in use. The Windows security log does not contain this type of information, nor does the system log.

- **73. C.** The Windows `tracert` command will show the route to a remote system as well as delays along the route. `traceroute` is the equivalent command in Linux. The `arp` command allows you to view and modify the Address Resolution Protocol (ARP) cache in Windows, and `netstat` has varying functions in different operating systems but generally shows statistics and information about network usage and status.

- **74. B.** PRTG and Cacti are both network monitoring tools that can provide bandwidth monitoring information. Bandwidth monitors can help identify exfiltration, heavy and abnormal bandwidth usage, and other information that can be helpful for both incident identification and incident investigations. If you encounter a question like this on the exam, even if you’re not familiar with either tool, you can use your knowledge of what Simple Network Management Protocol (SNMP) is used for to identify which of the categories is most likely correct.

- **75. D.** The Security+ exam outline focuses on right to audit clauses, regulatory and jurisdictional issues, and data breach notification laws as key elements to consider when planning on-site versus cloud forensic differences. Provenance is important regardless of where the forensic activity occurs.

- **76. A.** A variety of configuration changes could be pushed to mobile devices to help: setting passcodes, enabling full-disk encryption (FDE) on mobile devices via organizationally deployed mobile device management (MDM), or even preventing some sensitive files from being downloaded or kept on those devices could all help. Firewall rules, data loss prevention (DLP) rules, and URL filters will not prevent a stolen device from being accessed and the data being exposed.

- **77. B.** The `@` command for `dig` selects the Domain Name System (DNS) server it should query. In this case, it will query one of Google’s DNS servers at `8.8.8.8` for the DNS information for `example.com`.

- **78. C.** Greg should use the built-in hashing functions to compare either an MD5 or SHA-1 hash of the source drive to a hash using the same function run on the image. If they match, he has a valid and intact image. None of the other answers will provide validation that the full drive was properly imaged.

- **79. B.** The Linux `grep` command is a search tool that Adam can use to search through files or directories to find strings. `cat` is short for concatenate, and the command can be used to create files, to view their contents, or to combine files. `head` and `tail` are used to view the beginning or end of a file, respectively.

- **80. C.** Segmentation splits networks or systems into smaller units that align with specific needs. Segmentation can be functional, security based, or for other purposes. Removing potentially infected systems would be an example of isolation, using firewalls and other tools to stop the spread of an infection is containment, and adding security systems to prevent data loss is an example of implementing a security tool or feature.

- **81. B.** Unlike a disaster recovery plan that is written to help an organization recover from a person-made or natural disaster, a business continuity plan focuses on how to keep the business running when it is disrupted. Thus, Charlene’s BC plan would detail how to keep the organization running when a system outage occurs.

- **82. C.** OpenSSL can be used to generate a certificate using a command like this:

  ```
  openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt
  ```

  None of the other tools listed can be used to generate a certificate.

- **83. A.** The only password cracker listed is John the Ripper. John accepts custom wordlists, meaning that Cameron can create and use his own wordlist, as shown in option A.

- **84. A.** Autopsy does not have a built-in capability to create disk images. Instead, it relies on third-party tools for acquisition and then imports disk images and other media. Autopsy has built-in timeline generation, image filtering and identification, and communication visualization, among many other capabilities.
