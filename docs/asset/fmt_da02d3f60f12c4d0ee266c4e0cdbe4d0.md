
**Confidential or Proprietary** `confidential`或`proprietary`标签通常指代组织中最高级别的机密数据。在这种情况下，数据泄露可能导致对组织使命造成异常严重损害。例如，攻击者多次攻击索尼，窃取了超过 100TB 的数据，包括未发布电影的完整版本。这些数据迅速出现在文件共享网站上，安全专家估计人们下载了这些电影多达一百万次。由于盗版电影的可用性，许多人在索尼最终发布时选择跳过观看，这直接影响了其收入。这些电影是专有的，组织可能认为这属于异常严重损害。事后，他们可能会将电影标记为`confidential`或`proprietary`，并使用最严格的访问控制来保护它们。

**Private** `private`标签指数据应在组织内部保持私密，但不符合`confidential`或`proprietary`的定义。在这种情况下，数据泄露可能导致对组织使命造成严重损害。许多组织将 personally identifiable information (PII) 和 protected health information (PHI) 标记为`private`，也常见将内部员工数据和部分财务数据标记为`private`。例如，公司的薪酬部门可以访问薪酬数据，但这些数据不对普通员工开放。

**Sensitive** `Sensitive`数据类似于`confidential`数据。在这种情况下，数据泄露会对组织的使命造成损害。例如，组织的信息技术 (IT) 人员可能拥有关于内部网络的大量数据，包括布局、设备、操作系统、软件、Internet Protocol (`IP`) 地址等。如果攻击者轻松获取这些数据，将极大便利他们发动攻击。管理层可能决定不希望这些信息公开，因此可能将其标记为`sensitive`。

**Public** `Public`数据类似于`unclassified`数据，包括在网站、宣传册或其他公共来源上发布的信息。虽然组织不对公共数据的机密性进行保护，但会采取措施保护其完整性。例如，任何人都可以查看网站上发布的公共数据。但组织不希望攻击者修改这些数据，因此会采取保护措施。

Civilian organizations aren’t required to use any specific classification labels. However, it is important to classify data in some manner and ensure personnel understand the classifications. No matter what labels an organization uses, it still has an obligation to protect sensitive information.

After classifying the data, an organization takes additional steps to manage it based on its classification. Unauthorized access to sensitive information can result in significant losses to an organization. However, basic security practices, such as properly marking, handling, storing, and destroying data and hardware assets based on classifications, helps to prevent losses.

## Defining Asset Classifications

Asset classifications should match the data classifications. In other words, if a computer is processing top secret data, the computer should also be classified as a top secret asset. Similarly, if media such as internal or external drives holds top secret data, the media should also be classified as top secret.

It is common to use clear marking on the hardware assets so that personnel are reminded of data that can be processed or stored on the asset. For example, if a computer is used to process top secret data, the computer and the monitor will have clear and prominent labels reminding users of the classification of data that can be processed on the computer.

## Determining Data Security Controls

After defining data and asset classifications, it’s important to define the security requirements and identify security controls to implement those security requirements. Imagine that an organization has decided on data labels of Confidential/Proprietary, Private, Sensitive, and Public as described previously. Management then decides on a data security policy dictating the use of specific security controls to protect data in these categories. The policy will likely address data stored in files, in databases, on servers including email servers, on user systems, sent via email, and stored in the cloud.

For this example, we’re limiting the type of data to only email. The organization has defined how it wants to protect email in each of the data categories. They decided that any email in the Public category doesn’t need to be encrypted. However, email in all other categories (Confidential/Proprietary, Private, Sensitive, and Public) must be encrypted when being sent (data in transit) and while stored on an email server (data at rest).

Encryption converts cleartext data into scrambled ciphertext and makes it more difficult to read. Using strong encryption methods such as Advanced Encryption Standard with 256-bit cryptography keys (AES 256) makes it almost impossible for unauthorized personnel to read the text.

Table 5.1 shows other security requirements for email that management defined in their data security policy. Notice that data in the highest level of classification category (Confidential/Proprietary) has the most security requirements defined in the security policy.

**TABLE 5.1** **Securing email data**

| Classification || Security requirements for email |

| --- | --- |

| Confidential/Proprietary(highest level of protection for any data) || Email and attachments must be encrypted with AES 256.Email and attachments remain encrypted except when viewed.Email can only be sent to recipients within the organization.Email can only be opened and viewed by recipients (forwarded emails cannot be opened).Attachments can be opened and viewed, but not saved.Email content cannot be copied and pasted into other documents.Email cannot be printed. |

| --- | --- |

| Private(examples include PII and PHI) || Email and attachments must be encrypted with AES 256.Email and attachments remain encrypted except when viewed.Can only be sent to recipients within the organization. |

| Sensitive(lowest level of protection for classified data) || Email and attachments must be encrypted with AES 256. |

| Public || Email and attachments can be sent in cleartext. |

Security administrators use the requirements defined in the security policy to identify security controls. For Table 5.1, the primary security control is strong encryption using AES 256. Administrators would identify methodologies making it easy for employees to meet the requirements.

Although it’s possible to meet all of the requirements in Table 5.1, they require implementing other solutions. For example, software company Boldon James sells several products that organizations can use to automate these tasks. Users apply relevant labels (such as confidential, private, sensitive, and public) to emails before sending them. These emails pass through a data loss prevention (DLP) server that detects the labels, and applies the required protection.

Table 5.1 shows possible requirements that an organization might want to apply to email. However, an organization wouldn’t stop there. Any type of data that an organization wants to protect needs similar security definitions. For example, organizations would define requirements for data stored on assets such as servers, data backups stored onsite and offsite, and proprietary data.

Additionally, identity and access management (IAM) security controls help ensure that only authorized personnel can access resources. Chapter 13, “Managing Identity and Authentication,” and Chapter 14, “Controlling and Monitoring Access,” cover IAM security controls in more depth.

## Understanding Data States

It’s important to protect data in all `data states`, including while it is at rest, in motion, and in use.

**Data at Rest** Data at rest is any data stored on media such as system hard drives, external USB drives, storage area networks (SANs), and backup tapes.

**Data in Transit** Data in transit (sometimes called data in motion) is any data transmitted over a network. This includes data transmitted over an internal network using wired or wireless methods and data transmitted over public networks such as the internet.

**Data in Use** Data in use refers to data in memory or temporary storage buffers, while an application is using it. Because an application can’t process encrypted data, it must decrypt it in memory.

The best way to protect the confidentiality of data is to use strong encryption protocols, discussed later in this chapter. Additionally, strong authentication and authorization controls help prevent unauthorized access.

As an example, consider a web application that retrieves credit card data for quick access and reuse with the user’s permission for an e-commerce transaction. The credit card data is stored on a separate database server and is protected while at rest, while in motion, and while in use.

Database administrators take steps to encrypt sensitive data stored on the database server (data at rest). For example, they would encrypt columns holding sensitive data such as credit card data. Additionally, they would implement strong authentication and authorization controls to prevent unauthorized entities from accessing the database.
