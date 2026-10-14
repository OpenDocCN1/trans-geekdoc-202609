
* **.vbox:** This is the machine settings file extension. Prior to version 4.0, it was `.xml`.

* Virtual PC:

    * **.vhx:** These are the actual virtual hard disks. They are obviously quite important to a forensic examination.

    * **.bin files:** These contain the memory of the virtual machine, so these absolutely must be examined.

    * **.xml files:** These files contain the virtual machine configuration details. There is one of these for each virtual machine and for each snapshot of a virtual machine. These files are always named with the GUID used to internally identify the virtual machine in question.

##### Cloud

A cloud has been defined as “a pool of virtualized computer resources.”

People often speak of the cloud as if there were only one cloud, or at least one type of cloud. This impression is inaccurate. There are multiple clouds and multiple types of clouds. Any organization with the appropriate resources can establish a cloud, and it may establish it for diverse reasons, leading to different types of clouds.

Public clouds are defined by the NIST as those clouds that offer their infrastructure or services to either the general public or at least a large industry group.

Private clouds are those used specifically by a single organization without offering the services to an outside party. There are, of course, hybrid clouds that combine the elements of a private and public cloud. These are essentially private clouds that have some limited public access.

Community clouds are a midway point between private and public. These are systems wherein several organizations share a cloud for specific community needs. For example, several computer companies might join to create a cloud devoted to common security issues.

A cloud system depends on several parts. Each of these could be a location for evidence:

* **Virtual storage:** The virtual servers are hosted on one or more actual/physical servers. The hard drive space and RAM of those physical servers is partitioned for the various virtual servers’ usage.

* **Audit monitor:** There is usually an audit monitor that monitors usage of the resource pool. This monitor will also ensure that one virtual server does not/cannot access data of another virtual server.

* **Hypervisor:** The hypervisor mechanism is the process that provides the virtual servers with access to resources.

* **Logical network perimeter:** Since the cloud consists of virtual servers, not physical ones, there is a need for a logical network and a logical network perimeter. This perimeter isolates resource pools from each other.

Individual cloud implementations might have additional utilities, such as administration consoles that allow a network administrator to monitor, configure, and administer the cloud.

There are two issues with cloud forensics. The first is jurisdictional. Often cloud data is replicated across servers in different countries, each with its own laws. Then there is the technical issue of getting the data. It is very unlikely that you would be able to image the entire cloud in question. So you will probably have to perform a logical copy of the data in question or even a live analysis.

### Summary

In this chapter, you have seen the basics of computer forensics. The most important things you have learned are to make a forensics copy to work with and to document everything. You simply cannot over document. You have also learned how to retrieve browser information and recover deleted files, and you have learned some commands that may be useful forensically. You have explored the forensic value of the Windows Registry and even cloud forensics.

### Test Your Skills

#### Multiple Choice Questions

**[1](#app02.xhtml#ch14ans1).** In a computer forensics investigation, what describes the route that evidence takes from the time you find it until the case is closed or goes to court?

**A.** Rules of evidence

**B.** Law of probability

**C.** Chain of custody

**D.** Policy of separation

**[2](#app02.xhtml#ch14ans2).** Ian is performing a forensic examination on a Linux server. He is trying to recover emails. Where does Linux store email server logs?

**A.** `/var/log/mail.*`

**B.** `/etc/log/mail.*`

**C.** `/mail/log/mail.*`

**D.** `/server/log/mail.*`

**[3](#app02.xhtml#ch14ans3).** Why should you note all cable connections for a computer you want to seize as evidence?

**A.** To know what outside connections existed

**B.** In case other devices were connected

**C.** To know what peripheral devices exist

**D.** To know what hardware existed

**[4](#app02.xhtml#ch14ans4).** Pedro is examining a Windows 7 computer. He has extracted the index.dat file and is examining that file. What is in the Index.dat file?

**A.** Internet Explorer information

**B.** General Internet history, file browsing history, and so on for a Windows machine

**C.** All web history for Firefox

**D.** General Internet history, file browsing history, and so on for a Linux machine

**[5](#app02.xhtml#ch14ans5).** What is the name of the standard Linux command that is also available as a Windows application that can be used to create bitstream images and make a forensic copy?

**A.** `mcopy`

**B.** `image`

**C.** `MD5`

**D.** `dd`

**[6](#app02.xhtml#ch14ans6).** When cataloging digital evidence, the primary goal is to do what?

**A.** Make bitstream images of all hard drives.

**B.** Preserve evidence integrity.

**C.** Avoid removing the evidence from the scene.

**D.** Prohibit the computer from being turned off.

**[7](#app02.xhtml#ch14ans7).** Mahmoud is using a range of Windows utilities to extract information from a computer he is triaging. He has just used the `Openfiles` command. The command `Openfiles` shows what?

**A.** Any files that are opened

**B.** Any shared files that are opened

**C.** Any system files that are opened

**D.** Any files open with ADS

**[8](#app02.xhtml#ch14ans8).** “Interesting data” is what?

**A.** Data relevant to your investigation

**B.** Pornography

**C.** Documents, spreadsheets, and databases

**D.** Schematics or other economic-based information

**[9](#app02.xhtml#ch14ans9).** Which of the following are important to the investigator regarding logging?

**A.** The logging methods

**B.** Log retention

**C.** Location of stored logs

**D.** All of the above

#### Exercises

**Exercise 14.1:** DiskDigger

Download DiskDigger and search your computer for deleted files. Attempt to recover one file of your choice.

**Exercise 14.2:** Making a Forensic Copy

This exercise requires two computers. You must also download either Kali Linux or Knoppix. (Both are free.) Then attempt to make a forensic copy of computer A by sending its data to computer B.

**Exercise 14.3:** OSForensics

Download a trial copy of OSForensics from [https://www.osforensics.com/osforensics.html](https://www.osforensics.com/osforensics.html).

Using tutorials at [https://www.osforensics.com/faqs-and-tutorials/video_demonstrations.html](https://www.osforensics.com/faqs-and-tutorials/video_demonstrations.html), perform basic forensics on your own computer with OSForensics.

## Chapter 15. Cybersecurity Engineering

Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

*   Understand basic systems engineering concepts

*   Understand how to integrate systems engineering into cybersecurity

### Introduction
