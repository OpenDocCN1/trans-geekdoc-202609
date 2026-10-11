
# Network Traffic Analysis (NTA)

Network traffic analysis (NTA) is important for networks because sophisticated attackers frequently go undetected in a victim's network for an extended period. Attackers can blend their traffic with legitimate traffic that only skilled network analysts know how to detect. A skilled cybersecurity professional should know how to identify malicious network activity as well as network protocols, network architecture, intrusion detection systems, network traffic capture, and traffic analysis. Network tools commonly used to analyze captured network traffic include `Wireshark` and the command-line versions `Tshark` or `TCPdump`.

## Network Traffic Decryption/Deep Packet Inspection

`Wireshark` can also be used for some packet inspection, but there are tools that go deeper. Deep packet inspection (DPI) is a form of packet filtering that is able to inspect the information as well as the contents of the packet itself. `Wireshark` can tell that HTTP is being used but cannot view the contents of an encrypted packet. DPI has the ability to do something about traffic that fits a profile, such as dropping the whole packet or limiting bandwidth. Tools like `nDPI` are open-source tools, while Cisco's Network Based Application Recognition (NBAR) is on many Cisco devices.

## Data Classification, Labeling, and Tagging

Information classification strengthens the organization in many ways. Labeling information `secret` or `strictly confidential` helps employees see the value of the information and give it a higher standard of care. Information classification also specifies how employees are to handle specific information. For example, a company policy might state, “All sensitive documents must be removed from the employee's desk when leaving work. We support a clean desk policy.” Tagging and marking a piece of data based on its category helps make it searchable, trackable, and protected in the most efficient way.

There are two widely used information classification systems that have been adopted. Each is focused on a different portion of the CIA security triad. These two approaches are as follows:

*   **Government Classification System**: This system focuses on confidentiality.
*   **Commercial Classification System**: This system focuses on integrity.

### Governmental Information Classification System

The governmental information classification system is divided into the following categories:

*   **Top Secret**: Its disclosure would cause grave damage to national security. This information requires the highest level of control.
*   **Secret**: Its disclosure would be expected to cause serious damage to national security and may divulge significant scientific, technological, operational, and logistical secrets, as well as many other developments.
*   **Confidential**: Its disclosure could cause damage to national security and should be safeguarded against disclosure.
*   **Unclassified**: Information is not sensitive and need not be protected unless For Official Use Only (FOUO) is appended to the classification. Unclassified information would not normally cause damage, but over time Unclassified FOUO information could be compiled to deduce information of a higher classification.

### Commercial Information Classification System

The commercial information classification system is focused not just on confidentiality but also on the integrity of information; therefore, it is divided into the following categories:

*   **Confidential**: This is the most sensitive rating. This is the information that keeps a company competitive. Not only is this information for internal use only, but its release or alteration could seriously affect or damage a corporation.
*   **Private**: This category of restricted information is considered personal in nature and might include medical records or human resource information.
*   **Sensitive**: This information requires controls to prevent its release to unauthorized parties. Damage could result from its loss of confidentiality or its loss of integrity.
*   **Public**: This is similar to unclassified information in that its disclosure or release would cause no damage to the corporation.

Depending on the industry in which the business operates and its specific needs, one of these options will typically fit better than the other. Regardless of the classification system chosen, security professionals play a key role in categorizing information and helping to determine classification guidelines. Once an organization starts the classification process, it's forced to ask what would happen if specific information was released and how its release would damage or affect the organization.

### Metadata/Attributes

Metadata generated as a regular part of operations, communications, and other activities can also be used for incident response. Metadata is information about other data. In the case of systems and services, metadata is created as part of files and embedded documents, is used to define structured data, and is included in transactions and network communications amongst many other places you can find it. Metadata attributes express qualifications on content and can be used to modify how the content is processed or filtered. Another use is to flag content based on values or status. Metadata attributes can provide a list of one or more qualifications such as `administrator programmer`. This means the content applies to both administrators and programmers.

The following are common types of metadata to understand:

*   **Email**: This includes headers and other information found in an email. Email headers provide specifics about the sender, the recipient, the date, and time the message was sent, and if the email had an attachment.
*   **Mobile**: Data is collected by phones and other mobile devices including call logs, SMS and other message data, data usage, GPS location tracking, and cellular tower information. Mobile metadata is incredibly powerful because of the amount of geospatial information that is recorded about where the phone has traveled.
*   **Web**: This is embedded into a website as part of the code of the website but is invisible to average users and includes meta tags, headers, cookies, and other information that may help with search engine optimization, website functionality, advertising, and tracking.
*   **File**: This is a powerful tool when reviewing when a file was created, how it was created, if and when it was modified, and who modified it. Metadata is commonly used for forensics and other investigations, and most forensic tools have built-in metadata viewing capabilities.

## Obfuscation

**Obfuscation** means being evasive, unclear, or confusing. Encryption is a way to obfuscate data, rendering it extremely difficult to use. Other ways to obfuscate data in an enterprise are to use the following techniques:

*   **Tokenization**: Replace sensitive data with a unique nonsensitive identification element, called a token, that has no exploitable value.
*   **Scrubbing**: Sometimes called cleansing; fixing incorrect or duplicate data in a data set.
*   **Masking**: Hiding or filtering data so only the data you want is shown.

## Anonymization

**Anonymization** of data is removing anything in a data set that could identify an individual. By removing sensitive or private information such as names, Social Security numbers, or phone numbers, the data itself remains, but it cannot be attributed to a single individual, preserving a data subject's privacy. When data becomes anonymized, it can be used for the greater good while ensuring the rights of the individual.

## Encrypted vs. Unencrypted
