
### Classification
As you learned earlier in the chapter, data is assigned a security label, and in order for someone to access that information, they must have that security clearance level. Be sure to review the data classifications presented earlier in the chapter when you prepare for the Security+ exam.

### Governance
To help minimize security incidents with data, a company should have data governance policies that determine who has control over the data, as well as how data is handled within the organization.

### Retention
Companies should have retention policies that determine how long data should be retained. Different types of data may have different retention requirements—for example, financial records are typically retained for seven years.

### Credential Policies
Another type of policy that should exist is credential policies. Credential policies determine the credentials, or usernames, used by different entities within the business. The following are some common considerations for credentials:

#### Personnel
Each employee within the company should have their own credentials for accessing the network and computer systems. Employees should be taught security best practices with credentials, such as not sharing credentials with other employees.

#### Third party
Third-party entities such as business partners or contractors should also have credentials to access systems that are needed. It is important to follow best practices with these credentials, such as ensuring that account expiration options are set on contractors’ credentials.

#### Devices
You may need to manage credentials for devices in a few different ways. First, you would set passwords on devices so that only authorized persons can access those devices. You should also set the idle timeout on each device so that the device automatically locks after a short idle time.

#### Service accounts
Software that runs on a system also needs to run as “someone,” so you should create what is known as a service account for the software. After creating the account, you then configure the software to use that account to authenticate to the system. This becomes the security identity of the software as it accesses resources on the network.

#### Administrator/root accounts
You should also manage the credentials of administrator accounts on systems (also known as root accounts). It is important to ensure that the administrator account on each system is using a different password so that if the password is compromised on one system, the same password cannot be used on the other systems.

![Image](exam.jpg)

**For the Security+ certification exam, be familiar with security best practices in regard to credential policies such as configuring software to use service accounts and ensuring the administrator account on each system is configured with a different password.**

### Privacy and Sensitive Data Concepts
Understanding the security risk to the company and its data is an important skill for security professionals. In this section you will learn about the consequences to a company if it has a security breach, the types of data we want to protect, and the tools used to protect that data.

#### Organizational Consequences of Privacy and Data Breaches
A company may face a number of consequences if it finds it has a privacy and data breach. The following are key consequences to remember for the Security+ exam:

##### Reputation damage
One of the biggest consequences to a company is reputation damage. If customers learn that your business is not safeguarding sensitive data, they may decide to no longer do business with your company. This impacts the financial status of the company and could cause the company to close.

##### Identity theft
If unauthorized access to sensitive data occurs, you or your customers may experience identity theft.

##### Fines
You could be susceptible to fines for not safeguarding sensitive data properly. These fines could put financial stress on your company.

##### IP theft
If you have a data breach that results in unauthorized access to sensitive company data, it could result in the attacker stealing intellectual property.

#### Notifications of Breaches
If a data breach occurs within your business, you will need to notify the appropriate persons. Who you notify will depend on the type of business you have and the type of security incident that occurred. The two different forms of notifications are as follows:

##### Escalation
After discovering that a security incident has occurred, you may need to report the incident to the incident response team. After investigating the incident, the incident response team may need to escalate to another party, depending on the incident. For example, if it is a cloud incident, they may need to escalate to the cloud service provider.

##### Public notifications and disclosures
Depending on the regulations and laws governing your organization, you may need to make a public statement about any security incidents and disclose the details of the type of information that has been breached. The law may require that the company individually notify affected users and customers.

#### Data Types
When creating security policies, your goal is to protect privacy and sensitive data within the organization. Understanding the types of data that exist within the organization will help you understand the type of security controls needed. For example, knowing the different `classifications` of information discussed earlier in the chapter, such as private and public data, is important to securing that data. Other types of data found within businesses that need safeguarding are listed here:

##### Personally identifiable information (PII)
PII is any information that can uniquely identify a person. For example, a driver’s license number is considered PII data. You will learn more about PII information in the next section.

##### Health information
Health information typically contains confidential medical information about a person that should only be accessed by authorized individuals, such as a patient’s doctor.

##### Financial information
Financial information such as credit card numbers and bank account information should be kept confidential, with steps taken to ensure the data is not stored in plain text within information systems.

##### Government data
Information that could present a security risk to the government if breached should be heavily protected so that only authorized individuals have access to the information.

##### Customer data
Sensitive customer data should be protected at all times, such as contact details, address information, and any financial data related to the customer.

#### Privacy-Enhancing Technologies
You can use a number of different technologies to help protect different types of sensitive information, such as credit card numbers and health information. For the Security+ exam, you should remember the following key techniques for maintaining privacy:

##### Data minimization
The first step to securing sensitive data is to minimize the amount of information you collect. Data minimization is the term used to describe the process of only collecting information that is necessary.

##### Data masking
Data masking is a technique used to protect confidential or private data, which involves replacing characters in the data with nonrelevant characters. An example where data masking may be used is if you have a consultant working on a database, you supply them a masked version of the database so that sensitive information found in the data is not available to the consultant.
