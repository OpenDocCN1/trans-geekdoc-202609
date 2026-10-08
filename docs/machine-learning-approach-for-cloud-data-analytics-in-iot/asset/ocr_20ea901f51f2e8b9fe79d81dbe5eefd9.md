# 5.3.1 Security Challenges Related to Data at Rest

Data at rest refers to the data maintained at persistent storage in cloud. CSPs provide data owners with highly scalable and customizable storage instances where these storages are unreliable and removed in case of non-requirement. Persistent storage gives a reliable storage solution for the long-term storage of data. However, in both the types, the data is stored at a location far removed from users. Location gives rise to the security challenges $[11,13,14]$.

**Data Persistence:** The standard model for cloud computing includes allocation and deallocation of resources as per requirement. This means hosting the data required for that business transaction on the cloud servers itself.

After the work has been done, the resources are then de-allocated from the cluster used by the company. It may happen that data that was used during the business process may persist after the storage has been deallocated and maybe accessible in the network. Such a type of security fault is referred to as *data persistence*.

**Data Duplication:** Data hosted on the cloud is subjective to the hardware provided by the CSP. That includes the network, processors, and storage available. It may have its own set of vulnerabilities. They may be exploited to duplicate the data or the VM (virtual machine itself.

**Access Control:** Data is an asset. It may be required by multiple parties within the same organization. This requires fine grained access control. Access control refers to the right given to any party regarding the ability to read, write, or manipulate the data in any way based on its role. Irregular access control may lead to unauthorized access to the sensitive data which may be corrupted malicious parties.

**Secure Data:** Securing the data itself is necessary. Unencrypted data is easy to read and in case of unauthorized access it may really harm the organization as the data can be utilized immediately. Any counter measures may be too slow to prevent the damage caused.

**CSP Accountability:** Hardware faults may lead to data corruption and loss. Hence, the CSP must have countermeasures in place to avoid such faults. The CSP may utilize facilities like redundant storage, to protect the organization from unwanted data loss. The CSP must establish failsafe strategies in case of failure of the cloud, especially for organizations which store sensitive data on the CSPs cloud with the subscription for it. Another issue with CSP accountability relates to low level trust between the organization and the CSP. One problem related to it is the verification of data manipulation, accidentally or maliciously, by the CSP.