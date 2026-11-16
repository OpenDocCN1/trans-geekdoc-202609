
unique to every person.

When a biometric system is first used, the system must develop a database of information about each user. This is considered the enrollment period. When enrollment is complete, the system is ready for use. For example, if an enrolled employee places her finger on her company laptop’s fingerprint scanner, the scanner compares the ridges and creases on the employee’s finger to the fingerprint identified as belonging to that individual in the device’s database. This process is considered a one-to-one match of the individual’s biometric data.

In reality, a user’s unique attribute value is converted into a binary value and then hashed before being stored in an authentication server. Different biometric systems have varying levels of accuracy and sensitivity.

> **Note**
> 
> In organizations that implement strong security, a user may use multiple forms of authentication. A user might enter a password on his computer, use his fingerprint to unlock the phone and approve a text containing a one-time password, and then enter that one-time password into his computer. Microsoft MFA and others provide this type of functionality. This type of defense-in-depth approach is useful for increasing security and reducing risk.

Attributes are measured by the percentage of Type I and Type II errors they produce:

- **Type I errors**: These errors occur when individuals who should have been allowed access were not; these errors are compiled into the *false rejection rate* (FRR). The FRR is often called the insult rate because valid users are insulted that they were denied access even though they are legitimate users.

- **Type II errors**: These errors occur when individuals or subjects got in but should not have been allowed access; these errors are compiled into the *false acceptance rate* (FAR). Consider a situation where I, the author of this book and not an employee of your organization, show up at your work site and attempt to authenticate to one of the organization’s systems. If I were allowed in, that would be an example of a Type II error.

Together, the FRR and FAR can be used to determine the overall accuracy of a system. Suppose you have been asked to assess similar biometric devices. In this situation, you can use the crossover error rate (CER) to select the best system for your organization. This rate is determined by mapping the point at which Type I errors equal Type II errors. As illustrated in Figure 6.8, the lower the CER, the more accurate the biometric system. For example, if system A has a CER of 4, and system B has a CER of 2, system B has the greater accuracy.

![](img/cd307d33c10f35ada49ea76811ef60ad_469_0.png)

## FIGURE 6.8 Crossover Error Rate

### ExamAlert

Before you take the CISSP exam, make sure you understand the difference between Type I and Type II errors and the CER. The FAR is considered the most critical error rate to examine, and the CER is

The following are some of the most common biometric authentication systems. These systems are listed in order of best response times and lowest error rates:

- **Hand geometry recognition**: This type of biometric system uses the unique geometry of a user’s fingers and hand—shape, length, and width—to determine the user’s identity. It is one of the most mature biometric techniques.

- **Iris recognition**: An iris recognition system is an accurate biometric system because there are more than 400 points of reference when matching the irises of an individual’s eyes. This type of system typically works by taking a picture of the iris and comparing it to one stored in a database. Benefits include high accuracy, passive scanning, and no exchange of bodily fluids.

- **Retina pattern recognition**: This is another ocular-based technology that scans the blood vessels in the back of the eye. It requires users to place their eye close to the reader. Although retina-based biometric systems are considered very accurate, drawbacks include the fact that the retina can change due to medical conditions like diabetes and pregnancy and the fact that bodily fluids can be exchanged due to the need for proximity. Because of privacy concerns related to revealed medical conditions, retina scans are not readily accepted by users.

- **Fingerprint recognition**: This method is widely used for access control to facilities and items such as laptops and smartphones. It works by distinguishing up to 30 to 40 details about the peaks, valleys, ridges, and minutiae of the user’s fingerprint. However, many commercial systems limit the number that is matched to around 8 to 10.

- **Facial recognition**: This method requires a user to place her face in front of a camera. The facial scan device performs a mathematical comparison with the face prints (eigenfeatures) it holds in a database to allow or block access. These systems have grown in popularity over the past few years and are included on a number of smartphones and tablets.

- **Voice recognition**: Voice analysis for identification and authentication can be used for telephone applications. It has been around for several decades. The 1992 movie Sneakers includes the line, "Hi, my name is Werner Brandes. My voice is my passport. Verify me." However, voice recognition is vulnerable to replay attacks.

Different biometric systems have varying levels of accuracy. For example, the accuracy of fingerprint-scanning systems is based on fingerprint patterns and minutiae. Fingerprint patterns include arches, loops, and whorls, and minutiae include ridge endings, bifurcations, and short ridges (see Figure 6.9).

Although the number of minutiae varies from finger to finger, the information can be stored electronically in file sizes that are usually between 250 and 1,000 bytes. When a user logs in, the stored file containing the minutiae is compared to the finger being scanned.

![](img/cd307d33c10f35ada49ea76811ef60ad_471_0.png)

## FIGURE 6.9 Fingerprint Patterns and Minutiae

A number of considerations are important when deploying a biometric system:

- **Employee buy-in:** Users might not like or want to interact with the system, and the performance of the system will suffer. Some individuals oppose biometric authentication systems for privacy-related reasons. Some users find biometric devices too Big Brotherish. Some might not like the idea that the organization’s new retina scanner could be used to detect medical conditions, such as pregnancy. Users who perform physical labor or work in an unclean environment might find fingerprint scanners frustrating. Sanitization can be an issue with biometrics because users often have to touch authentication devices. When considering biometric systems, you should ensure that they do not cause undue psychological stress for users or raise unwarranted privacy issues.

- **The physical status of the user:** Users who are physically disabled might find eye scanners difficult to reach. Those missing hands or fingers will be unable to use fingerprint readers, palm scanners, or hand geometry systems.

- **Whether the user can use the biometric:** Some users may not be able to use the biometric. For example, some people cannot have their fingerprints read. This may be genetic or based on the job the person does. For example, brick layers and bank tellers typically cannot use fingerprint readers because their fingerprints may be worn off.

A final consideration with biometrics is selection. With so many technologies, it takes a significant amount of effort to choose a system that meets user criteria and is technologically feasible. One tool that can aid in this task is the International Biometric Group’s Zephyr Analysis, which provides a means of evaluating different biometric technologies based on two categories:

- **User criteria:** Effort and intrusiveness

- **Technology criteria:** Cost and accuracy

> **ExamAlert**
> 
> CISSP exam candidates must understand the different ways in which biometric systems can be evaluated. When comparing like devices,
