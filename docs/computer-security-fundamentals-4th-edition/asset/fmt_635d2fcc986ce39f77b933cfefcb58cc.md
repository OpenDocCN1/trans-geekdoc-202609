
Any IT certification can be one valuable indicator of a job applicant’s skill. It is not the only indicator and certainly should not be the only thing considered, but it is one factor. This brings us to forensic certifications. Is there a need for another one? First look at what cyber forensics certifications are currently available. All forensics certifications come in one of two types. The first type is vendor certifications. These usually are focused only on the product (or products) that vendor sells. The second type is conceptual certifications. These tests are not about a specific tool, but rather forensic concepts.

AccessData, the creator of the Forensic Toolkit, has multiple certifications for its product. So does Guidance Software, the creator of EnCase. Both of those vendor certifications are quite good. However, they are both vendor certifications. The emphasis is on the particular proprietary suite of tools rather than a general coverage of cyber forensics. If you are going to work with either tool, it is a very good idea to get the appropriate vendor certification, but that is not the same thing as a broad-based cyber forensics course/test.

The EC-Council has its Certified Hacking Forensics Investigator (CHFI) test, and it has been somewhat popular. However, as the name suggests, it has an emphasis on hacking and counter hacking. The EC-Council’s primary focus has always been hacking.

The SANS Institute offers a number of certifications, including the Certified Forensics Analyst (GCFA) and Certified Forensics Examiner (GCFE). Both of these are well respected in the industry. The only issue with either one is the cost. SANS courses and their certification tests are among the most expensive in the industry.

### Expert Witnesses

At some point, any forensic examiner might be called to testify in court. Being an expert witness is very different from being a witness of fact. To begin with, an expert witness is allowed to testify about things he did not see or hear. Second, an expert witness is allowed to make inferences and formulate theories.

However, there are definite limits to and requirements for expert testimony. You cannot simply get on the stand and essentially state, “Well, I am an expert and this is true because I say so.” There are some rules. The following sections give a brief overview of some of those rules.

#### Federal Rule 702

Federal Rule 702 defines what an expert witness is and the rules concerning when she can testify and what she can testify to. Essentially, Rule 702 states the following:

*   A witness who is qualified as an expert by knowledge, skill, experience, training, or education may testify in the form of an opinion or otherwise if:

    1.  The expert’s scientific, technical, or other specialized knowledge will help the trier of fact to understand the evidence or to determine a fact in issue;

    2.  The testimony is based on sufficient facts or data;

    3.  The testimony is the product of reliable principles and methods; and

    4.  The expert has reliably applied the principles and methods to the facts of the case.

What this means is that, first and foremost, the expert must be an expert in that specific topic or field. That person’s testimony must be useful to the judge or jury in understanding technical or specialized facts in the case. But just as important, the expert must base her opinions on reliable scientific methods.

#### Daubert

The Daubert standard is used in U.S. federal courts to determine whether or not an expert’s scientific testimony is based on reasoning or methodology that is scientifically valid and can properly be applied to the facts at issue. Under this standard, the factors that may be considered in determining whether the methodology is valid are (1) whether the theory or technique in question can be and has been tested; (2) whether it has been subjected to peer review and publication; (3) its known or potential error rate; (4) the existence and maintenance of standards controlling its operation; and (5) whether it has attracted widespread acceptance within a relevant scientific community. The Daubert standard is the test currently used in the federal courts and some state courts. This is very similar to Federal Rule 702.

### Additional Types of Forensics

Digital forensics is a growing field. Computer and phone forensics are the most widely encountered types of digital forensics, but not the only areas of digital forensics. In this section, you will see a brief overview of some other subdisciplines of digital forensics.

#### Network Forensics

The first, most fundamental thing to learn about network forensics is packet analysis. Before we continue, you may wish to review the material from [Chapter 2](#ch02.xhtml#ch02), “[Networks and the Internet](#ch02.xhtml#ch02),” to ensure that you are comfortable with basic networking.

Essentially, network forensics involves capturing the network packets traversing the network and examining them for evidence. Many things can be determined from network forensics: where a packet came from, what protocol it is using, what port it is using, and whether it is encrypted or not.

The following are some of the popular tools for network analysis:

*   **Wireshark:** [www.wireshark.org](http://www.wireshark.org)

*   **CommView:** [www.tamos.com/products/commview/](http://www.tamos.com/products/commview/)

*   **SoftPerfect Network Protocol Analyzer:** [www.softperfect.com](http://www.softperfect.com)

*   **EffeTech HTTP Sniffer:** [www.effetech.com/sniffer/](http://www.effetech.com/sniffer/)

*   **ngrep:** [http://sourceforge.net/projects/ngrep/](http://sourceforge.net/projects/ngrep/)

Any of these tools can work for network analysis.

#### Virtual Forensics

*Virtualization* is a broad term that encompasses many technologies. It is a way to provide various IT resources that are independent of the physical machinery of the user. The virtualization makes a logical IT resource that can operate independent of the end user’s operating system as well as hardware. The most basic issue for forensics is the situation where a suspect machine has a virtual machine running on it. There are also issues with getting data from cloud servers.

##### Virtual Machines

A virtual machine is an interesting concept and was the precursor of more broad-based virtual systems that we will discuss later in this chapter. A virtual machine essentially sets aside a certain portion of a computer’s hard drive and RAM (when executing) to run in complete isolation from the rest of the operating system. It is much like you are running an entirely separate computer; it simply shares the resources of the host computer. It is, quite simply, a virtual computer—thus, the name virtual machine.

Each vendor stores data in a slightly different manner. The following list shows the most forensically interesting files for three of the most widely used virtual machine vendors:

*   VMware Workstation:

    *   **.log files:** This is simply a log of activity for a virtual machine.

    *   **.vmdk:** This is the actual virtual hard drive for the virtual guest operating system. Virtual hard drives can be fixed or dynamic. Fixed virtual hard drives remain the same size. Dynamic virtual hard drives expand as needed.

    *   **.vmem:** This is a backup of the virtual machine’s paging file/swap file. This can be very important to a forensic investigation.

    *   **.vmsn:** These are VMware snapshot files, named based on the name of the snapshot. A VMSN file stores the state of the virtual machine when the snapshot was created.

    *   **.vmsd:** A VMSD file contains the metadata about the snapshot.

*   Oracle VirtualBox:

    *   **.vdi:** These are VirtualBox disk images called virtual disk images.

    *   **/.config/VirtualBox:** This is a hidden file that contains configuration data.
