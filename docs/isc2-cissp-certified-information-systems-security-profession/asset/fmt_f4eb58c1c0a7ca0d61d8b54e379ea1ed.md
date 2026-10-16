
Security baselines provide a set of security controls that an organization can implement as a secure starting point. Some publications (such as NIST SP 800-53) identify security control baselines. However, these baselines don’t apply equally to all organizations. Instead, organizations use scoping and tailoring techniques to identify the security controls to implement in their baselines. Additionally, organizations ensure that they implement security controls mandated by external standards that apply to their organization.

## Exam Essentials

**Understand the importance of data and asset classifications.** Data owners are responsible for defining data and asset classifications and ensuring that data and systems are properly marked. Additionally, data owners define requirements to protect data at different classifications, such as encrypting sensitive data at rest and in transit. Data classifications are typically defined within security policies or data policies.

**Know about PII and PHI.** Personally identifiable information (PII) is any information that can identify an individual. Protected health information (PHI) is any health-related information that can be related to a specific person. Many laws and regulations mandate the protection of PII and PHI.

**Know how to manage sensitive information.** Sensitive information is any type of classified information, and proper management helps prevent unauthorized disclosure resulting in a loss of confidentiality. Proper management includes marking, handling, storing, and destroying sensitive information. The two areas where organizations often miss the mark are adequately protecting backup media holding sensitive information and sanitizing media or equipment when it is at the end of its lifecycle.

**Understand record retention.** Record retention policies ensure that data is kept in a usable state while it is needed and destroyed when it is no longer needed. Many laws and regulations mandate keeping data for a specific amount of time, but in the absence of formal regulations, organizations specify the retention period within a policy. Audit trail data needs to be kept long enough to reconstruct past incidents, but the organization must identify how far back they want to investigate. A current trend with many organizations is to reduce legal liabilities by implementing short retention policies with email.

**Know the difference between different roles.** The data owner is the person responsible for classifying, labeling, and protecting data. System owners are responsible for the systems that process the data. Business and mission owners own the processes and ensure that the systems provide value to the organization. Data processors are often the third-party entities that process data for an organization. Administrators grant access to data based on guidelines provided by the data owners. A user accesses data while performing work tasks. A custodian has day-to-day responsibilities for protecting and storing data.

**Understand the GDPR security controls.** The EU General Data Protection Regulation (GDPR) mandates protection of privacy data. Two key security controls mentioned in the GDPR are encryption and pseudonymization. Pseudonymization is the process of replacing some data elements with pseudonyms. This makes it more difficult to identify individuals.

**Know about security control baselines.** Security control baselines provide a listing of controls that an organization can apply as a baseline. Not all baselines apply to all organizations. However, an organization can apply scoping and tailoring techniques to adapt a baseline to its needs.

## Written Lab

1.  Describe PII and PHI.

2.  Describe the best method to sanitize SSDs.

3.  Describe pseudonymization.

4.  Describe the difference between scoping and tailoring.

## Review Questions

1.  Which one of the following identifies the primary purpose of information classification processes?

    1.  Define the requirements for protecting sensitive data.

    2.  Define the requirements for backing up data.

    3.  Define the requirements for storing data.

    4.  Define the requirements for transmitting data.

2.  When determining the classification of data, which one of the following is the most important consideration?

    1.  Processing system

    2.  Value

    3.  Storage media

    4.  Accessibility

3.  Which of the following answers would *not* be included as sensitive data?

    1.  Personally identifiable information (PII)

    2.  Protected health information (PHI)

    3.  Proprietary data

    4.  Data posted on a website

4.  What is the most important aspect of marking media?

    1.  Date labeling

    2.  Content description

    3.  Electronic labeling

    4.  Classification

5.  Which would an administrator do to classified media before reusing it in a less secure environment?

    1.  Erasing

    2.  Clearing

    3.  Purging

    4.  Overwriting

6.  Which of the following statements correctly identifies a problem with sanitization methods?

    1.  Methods are not available to remove data ensuring that unauthorized personnel cannot retrieve data.

    2.  Even fully incinerated media can offer extractable data.

    3.  Personnel can perform sanitization steps improperly.

    4.  Stored data is physically etched into the media.

7.  Which of the following choices is the most reliable method of destroying data on a solid state drive (SSD)?

    1.  Erasing

    2.  Degaussing

    3.  Deleting

    4.  Purging

8.  Which of the following is the most secure method of deleting data on a DVD?

    1.  Formatting

    2.  Deleting

    3.  Destruction

    4.  Degaussing

9.  Which of the following does not erase data?

    1.  Clearing

    2.  Purging

    3.  Overwriting

    4.  Remanence

10.  Which one of the following is based on Blowfish and helps protect against rainbow table attacks?

     1.  3DES

     2.  AES

     3.  Bcrypt

     4.  SCP

11.  Which one of the following would administrators use to connect to a remote server securely for administration?

     1.  Telnet

     2.  Secure File Transfer Protocol (SFTP)

     3.  Secure Copy (SCP)

     4.  Secure Shell (SSH)

12.  Which of the following tasks would a custodian most likely perform?

     1.  Access the data

     2.  Classify the data

     3.  Assign permissions to the data

     4.  Back up data

13.  Which of the following data roles is most likely to assign permissions to grant users access to data?

     1.  Administrator

     2.  Custodian

     3.  Owner

     4.  User

14.  Which of the following best defines “rules of behavior” established by a data owner?

     1.  Ensuring that users are granted access to only what they need

     2.  Determining who has access to a system

     3.  Identifying appropriate use and protection of data

     4.  Applying security controls to a system

15.  Within the context of the EU GDPR, what is a data processor?

     1.  The entity that processes personal data on behalf of the data controller

     2.  The entity that controls processing of data

     3.  The computing system that processes data

     4.  The network that processes data

16.  Your organization has a large database of customer data. To comply with the EU GDPR, administrators plan to use pseudonymization. Which of the following *best* describes pseudonymization?

     1.  The process of replacing some data with another identifier

     2.  The process of removing all personal data

     3.  The process of encrypting data

     4.  The process of storing data

17.  An organization is implementing a preselected baseline of security controls, but finds that some of the controls aren’t relevant to their needs. What should they do?

     1.  Implement all the controls anyway.

     2.  Identify another baseline.

     3.  Re-create a baseline.

     4.  Tailor the baseline to their needs.
