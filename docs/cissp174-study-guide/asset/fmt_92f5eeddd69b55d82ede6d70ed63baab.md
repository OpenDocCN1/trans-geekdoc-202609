
# Least Privilege and Need to Know

*Least privilege* means users should be granted the minimum amount of access (authorization) required to do their jobs, but no more. *Need to know* is more granular than least privilege: the user must need to know that specific piece of information before accessing it.

Sebastian is a nurse who works in a medical facility with multiple practices. His practice has four doctors, and Sebastian could treat patients for any of those four doctors. Least privilege could allow Sebastian to access the records of the four doctors’ patients, but not access records for patients of other doctors in other practices.

Need to know means Sebastian can access a patient’s record only if he has a business need to do so. If there is a patient being treated by Sebastian’s practice, but not by Sebastian himself, least privilege could allow access, but need to know would not.

## Learn by Example

### Real-World Least Privilege

A large healthcare provider had a 60-member IT staff responsible for 4000 systems running Microsoft Windows. The company did not employ least privilege: the entire IT staff was granted Windows Domain Administrator access. Staff with such access included help desk personnel, backup administrators, and many others. All 60 domain administrators had super-user privileges on all 4000 windows systems.

This level of privilege was excessive and led to problems. Operator errors led to violation of CIA. Because so many could do so much, damage to the environment was prevalent. Data was lost; unauthorized changes were made; systems crashed, and it was difficult to pinpoint the causes.

A new security officer was hired, and one of his first tasks was to enforce least privilege. Role-based accounts were created: a help desk role that allowed access to the ticketing system, a backup role that allowed backups and restoration, and so on. The domain administrator list was whittled down to a handful of authorized personnel.

Many former domain administrators complained about loss of super-user authorization, but everyone got enough access to do their job. The improvements were immediate and impressive: unauthorized changes virtually stopped and system crashes became far less common. Operators still made mistakes, but those mistakes were far less costly.

## Subjects and Objects

A *subject* is an active entity on a data system. Most examples of subjects involve people accessing data files. However, computer programs can be subjects as well. A Dynamic Link Library file or a Perl script that updates database files with new information is also a subject.

An *object* is any passive data within the system. Objects can range from documents on physical paper, to database tables to text files. The important thing to remember about objects is that they are passive within the system. They do not manipulate other objects.

There is one tricky example of subjects and objects that is important to understand. For example, if you are running `iexplore.exe` (Internet Explorer browser on a Microsoft Windows system), it is a subject while running in memory. When the browser is not running in memory, the file `iexplore.exe` is an object on the filesystem.

> **Exam Warning**
>
> Keep all examples on the CISSP® exam simple by determining whether they fall into the definition of a subject or an object.

## Defense-in-Depth

*Defense-in-Depth* (also called layered defenses) applies multiple safeguards (also called controls: measures taken to reduce risk) to protect an asset. Any single security control may fail; by deploying multiple controls, you improve the confidentiality, integrity, and availability of your data.

### Learn by Example

#### Defense-in-Depth Malware Protection

A 12,000-employee company received 250,000 Internet emails per day. The vast majority of these emails were malicious, ranging from time- and resource-wasting spam to malware such as worms and viruses. Attackers changed tactics frequently, always trying to evade safeguards designed to keep the spam and malware out.

The company deployed preventive defense-in-depth controls for Internet email-based malware protection. One set of UNIX mail servers filtered the incoming Internet email, each running two different auto-updating antivirus/antimalware solutions by two different major vendors. Mail that scanned clean was then forwarded to an internal Microsoft Exchange mail server, which ran yet another vendor’s antivirus software. Mail that passed that scan could reach a user’s client, which ran a fourth vendor’s antivirus software. The client desktops and laptops were also fully patched.

Despite those safeguards, a small percentage of malware successfully evaded four different antivirus checks and infected the users’ client systems. Fortunately, the company deployed additional defense-in-depth controls, such as *Intrusion Detection Systems* (IDSs), incident handling policies, and a CIRT (*Computer Incident Response Team*) to handle incidents. These defensive measures successfully identified infected client systems, allowing for timely response.

All controls can fail, and sometimes multiple controls will fail. Deploying a range of different defense-in-depth safeguards in your organization lowers the chance that all controls will fail.

## Due Care and Due Diligence

*Due care* is doing what a reasonable person would do. It is sometimes called the “prudent man” rule. The term derives from “duty of care”: parents have a duty to care for their children, for example. *Due diligence* is the management of due care.

Due care and due diligence are often confused; they are related, but different. Due care is informal; due diligence follows a process. Think of due diligence as a step beyond due care. Expecting your staff to keep their systems patched means you expect them to exercise due care. Verifying that your staff has patched their systems is an example of due diligence.

### Gross Negligence

Gross negligence is the opposite of due care. It is a legally important concept. If you suffer loss of PII, but can demonstrate due care in protecting the PII, you are on legally stronger ground, for example. If you cannot demonstrate due care (you were grossly negligent), you are in a much worse legal position.

# Legal and Regulatory Issues

Though general understanding of major legal systems and types of law is important, it is critical that information security professionals understand the concepts described in the next section. With the ubiquity of information systems, data, and applications comes a host of legal issues that require attention. Examples of legal concepts affecting information security include: crimes being committed or aided by computer systems, attacks on intellectual property, privacy concerns, and international issues.

## Compliance With Laws and Regulations

Complying with laws and regulations is a top information security management priority: both in the real world and on the exam. An organization must be in compliance with all laws and regulations that apply to it. Ignorance of the law is never a valid excuse for breaking the law.

> **Exam Warning**
>
> The exam will hold you to a very high standard regarding compliance with laws and regulations. We are not expected to know the law as well as a lawyer, but we are expected to know when to call a lawyer. Confusing the technical details of a security control such as `Kerberos` may or may not cause a significant negative consequence, for example. Breaking search and seizure laws due to confusion over the legality of searching an employee’s personal property, for example, is likely to cause very negative consequences. The most legally correct answer is often the best for the exam.

## Major Legal Systems
