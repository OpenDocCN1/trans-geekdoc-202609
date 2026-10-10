
# A common term often used with computer forensics and investigations today is *e-discovery,* which is the discovery of electronic information in legal cases or government investigations that involves being able to search through electronic records to find relevant evidence. Many products today, such as Microsoft Exchange Server, have e-discovery features that allow you to search through an employee’s mailbox and place a legal hold on relevant e-mail messages that could be evidence. The legal hold protects the electronic data from being deleted. In this example, you can also use the e-discovery feature of Microsoft Exchange to extract relevant messages related to a case.

## Data Recovery

Many people use computer forensics professionals and tools for data recovery because the tools allow for locating and recovering deleted data.

## Nonrepudiation

It is essential that an investigator be able to prove the integrity of the evidence that is found. This is why it is critical that the suspect’s drive is run through a hashing process in order to generate hash values for the drive and files so that the investigator can concretely say, “This is what the suspect’s drive looked like when we seized it, and here is the evidence we found within that drive.” If the defense team claims that the evidence was planted on the drive after seizure, the investigator can show the hash values of the drive with the evidence on the drive and compare that to the original hash values during seizure.

## Strategic Intelligence/Counterintelligence

Computer forensics can also be used in strategic intelligence, or counterintelligence, where information is collected and analyzed to help prevent acts such as terrorism, espionage, and sabotage.

# CERTIFICATION OBJECTIVE 21.02

# Collecting Digital Evidence

Now that you understand the concepts behind evidence and the different types of evidence, let’s move on to how you are going to collect and analyze digital evidence.

## Understanding the Process

When conducting an investigation that requires you to work with digital evidence, ensure that you follow a process to collect the relevant evidence without modifying it. Working with digital evidence requires special skills to ensure you do not contaminate the it. This section outlines the basic steps to finding digital evidence.

### Seize the Evidence

The first step to working with digital evidence is to seize the evidence. Evidence could exist on the hard drive of a desktop computer, server, laptop, or even a mobile device, so you may be responsible for collecting evidence from each of these electronic devices. Seizing the evidence means going to the location of the suspect’s electronic device containing the evidence, disconnecting the power from the electronic device, and taking the device back to your forensics lab. In a corporate case, this may involve waiting for a time after hours when the employee is not around and then taking the employee’s workstation. Or, depending on the nature of the violation, you may seize the electronic device immediately. When dealing with a public investigation, it is important that law enforcement obtain a search warrant for any items that need to be seized.

It is critical during seizure of the evidence that you document the scene, including making your own notes, labeling the evidence with tags, and taking pictures, as discussed earlier in the chapter.

### Acquire the Evidence (Data Acquisition)

Once the evidence has been seized, you can then *acquire* the evidence. Acquiring the evidence involves taking an image of the evidence so that you can do your investigation from a copy of the evidence and not from the original evidence. It is critical that you acquire a bit-level copy (raw sector-by-sector copy) of any drives on the suspect’s system by using *forensically sound* imaging software, which is software that is designed for computer forensics and does not make any modifications to the source drive.

*Artifacts* is the term used to describe the items that exist in digital content that can be used as evidence. Examples of artifacts are things like Internet searches, deleted files, registry keys, and event logs.

### Static Images

When acquiring the image, you typically will take the drive out of the suspect’s system and then connect the drive to your forensics workstation. The forensics workstation is a system you set up with your forensics software and with no connection to the network or Internet.

The proper method to connect the suspect’s drive to your forensics workstation is to connect a *write blocker* to your workstation (usually via USB). The write blocker will have interfaces for IDE (Integrated Drive Electronics), SATA (Serial Advanced Technology Attachment), and SCSI (Small Computer System Interface) drives to connect to the write blocker. The write blocker is a device that does not allow modification to any drives connected to it (see [Figure 21-4](#ch21.xhtml#ch21fig4)).

![Image](f0833-01.jpg)

FIGURE 21-4  

Always use a write blocker when connecting the suspect’s drive to your forensics workstation.

## INSIDE THE EXAM

### Importance of Imaging a Drive

For the Security+ certification exam, and for the real world, remember that it’s critical to ensure you create a bit-level copy of a suspect’s drive, known as a *system image* or *drive image,* instead of relying on a normal file copy operation. The reason is that a bit-level copy of the drive copies the drive sector by sector, as opposed to a logical file copy operation. A file copy will copy just the files, not the entire disk, and won’t capture the deleted files that remain on the disk after they are deleted.

Creating an image of a drive captures the entire drive (because it copies each sector), including deleted files and hidden information on disk. Always remember to create multiple images of the drive and use different imaging tools in case one of the images becomes corrupt. After creating the image, you will perform your investigation on the image and not the original drive.

![Image](exam.jpg)

**For the Security+ exam, and in real life, always remember to connect the evidence drive to the system in read-only mode using a hardware write blocker, or by using a software feature that enables readonly mode.**

### Live Images

Although most times you will be dealing with static images, you may sometimes need to do a live acquisition. With static images, you are unable to capture the contents of memory because the power was removed from the system when it was seized. Before seizing the evidence, plan whether you need to do a live acquisition or a static acquisition. The benefit of the live acquisition is that you can obtain the contents of memory by running your imaging software on the live system and dumping the contents of memory to an image on a disk or across the network. The drawback of the live acquisition is that you are modifying the system when you run your software—you must verify ahead of time with the lead investigator that this is acceptable.

Performing a live acquisition allows you to perform two very important tasks:

- **Capture the contents of memory** As mentioned, with a live acquisition, you can capture the contents of memory before the suspect’s system is turned off. Forensic Toolkit (FTK) is a popular live analysis tool that allows you to capture the contents of memory to a remote location.
- **Capture the contents of an encrypted drive** These days, full drive encryption is becoming more common, so that when the system is powered off, the drive is automatically encrypted. When the system boots up, if the correct key is supplied, the drive is decrypted and access to the files is granted. From a forensics point of view, drive encryption poses a problem, so if you suspect that the drive is encrypted, you should do a live acquisition before pulling the power.
