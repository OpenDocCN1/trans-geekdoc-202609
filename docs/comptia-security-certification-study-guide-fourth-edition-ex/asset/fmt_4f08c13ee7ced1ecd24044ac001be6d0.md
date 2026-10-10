
# Separation of Duties

The concept of separation of duties is used to keep everyone honest and to prevent fraudulent activity within the organization. Be aware that separation of duties will not protect you from `collusion`, which is the term used to describe when parties conspire together to commit a fraudulent act—for example, the person writing the check and the person signing the check decide to start writing checks for their own joint business.

## Rotation of Duties

Another important security principle that relates to personnel and day-to-day business operations is the concept of rotation of duties. `Rotation of duties` is the principle of rotating multiple employees through different job roles. For example, you have a team of network administrators, and this month Bob will take care of account management, but next month Sue will take over that duty, and Bob will take over the job role that Sue had.

![Image](exam.jpg)

**For the exam, be sure to know the difference between separation of duties and rotation of duties.**

Rotation of duties offers multiple benefits. First, it is a way to ensure accountability for employee actions. If Bob has been intentionally or accidentally misusing his privileges, then Sue will notice that the following month and report it. The other benefit of rotation of duties is that the organization does not depend on one person being the only person able to perform a job role. By rotating multiple employees through different roles, the organization has some redundancy in skill sets in case an employee becomes sick, goes on leave, or quits.

## Concept of Need to Know

Later in this book, you will learn more about authentication and access control, but one of the security principles I wanted to introduce in this terminology chapter before you hit those chapters is the concept of `need to know`, which means that you give employees access only to information that they need to know about. For example, instead of giving all managers access to the accounting data, you want to ensure that only the accounting manager gets access to the accounting data. You don’t give the marketing manager access to accounting data because the marketing manager doesn’t need this access.

Another example of implementing the concept of need to know is found in military environments. Just because a commander has been given top secret clearance does not mean they should be able to view all top secret data in the organization. For example, if the commander is not involved with a certain operation, they do not need to know the information being presented to the personnel involved in that operation.

## Layered Security and Diversity of Defense

Two other very important security principles that should be followed to help create a more secure environment are the concepts of taking a layered security approach and diversity of defense. `Layered security` is the concept of not putting all of your eggs in one basket by relying on one type of security solution to create a secure environment. For example, although firewalls are a critical part of the security for any organization, if someone brings a flash drive that is infected with a virus into the office, the firewall is not going to help protect the systems. Taking a layered approach to security means that you will rely on many different types of security controls, such as authentication, virus protection, patching systems, and firewalls. Taking a layered approach to security is also known as “defense in depth”.

`Diversity of defense` is the concept that you should use different products to increase the level of security in your environment. For example, when designing a firewall strategy, you will most likely have multiple layers of firewalls, and it is important to not use the same firewall product at each layer. If the hacker figures out how to hack into the first firewall and you are using the same firewall product elsewhere on the network, the hacker will use the same technique to bypass those firewalls. If you use different products provided by different manufacturers, the method used to hack into the first firewall will not necessarily work on the second firewall. The concept here is that although all products have vulnerabilities, the vulnerabilities are different for each of the different products, and the hacker will have to work extra hard to get through each different product.

Another example of diversity of defense is that when you purchase antivirus software for your anti-spam server, your e-mail server, and your desktop systems, be sure to use antivirus software from different vendors. The purpose of this is that if the virus gets by one of the antivirus products, one of the other antivirus products will catch it, hopefully. I have heard of cases where a zero-day exploit came out that was missed by the external antivirus scanner running on the e-mail server but was caught by the antivirus software running on the client when the attachment arrived on the e-mail client. Instances like this help you justify the cost of running antivirus software at different layers of the network.

## Due Care and Due Diligence

Other important principles of security are the concepts of due care and due diligence, which are intended to ensure that the organization is taking actions to do the right thing to protect its employees and assets. `Due care` is the concept of doing the right thing. When it relates to security, due care is about implementing the correct security controls to ensure the protection of the organization’s assets. Examples include the creation of the security policy, performing regular backups, and performing regular virus scans. The key thing to note with due care is that you are implementing an action. `Due diligence`, on the other hand, is about identifying your risk so that you know what security controls to put in place (due care). Due diligence involves performing regular assessments and analyzing the assessment results to identify security issues in the environment.

## Vulnerability and Exploit

Two very important terms that security professionals toss around quite often are vulnerability and exploit. A `vulnerability` is a weakness in a piece of software or hardware that was created by the manufacturer by accident. Hackers spend quite a bit of time evaluating new software and hardware to try to locate vulnerabilities. Once the hackers find a weakness, they work on a way to `exploit` the weakness and compromise the system security.

### Reasons for Vulnerabilities

The Security+ exam will test your knowledge on vulnerabilities and why they exist. There are a number of reasons why there are so many vulnerabilities today:

- **End-of-life systems** An end-of-life (EOL) system is a system that has reached the end of its usefulness (or profitability) from a vendor’s point of view. EOL systems are typically referred to as legacy systems and may be needed within a company because they run an old piece of software that has yet to be replaced. An EOL system presents a security risk to your company because the vendor of the system stops supporting it when it reaches its EOL date. For example, a vendor will not create patches for any new vulnerabilities found in software that has reached EOL—making the system a huge security risk to the company using it.

- **Embedded systems** An embedded system is a small computer system that contains minimal hardware, such as a processor, circuit board, and memory, and usually a stripped-down version of an OS, and is embedded within a larger device or system to perform specific functions. Because hardware devices run embedded systems with software, they are vulnerable to attack, just like a regular computer system if the running software has vulnerabilities. Embedded systems are often overlooked from a security standpoint, so extra effort should be made to locate embedded systems and evaluate vulnerabilities that might exist.
