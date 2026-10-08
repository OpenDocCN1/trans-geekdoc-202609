# 380 BLOCKCHAIN IN HEALTH SCIENCES

Also, it enables sensor nodes to communicate with legitimate fog/cloud nodes. Similarly, users and cloud/fog servers should be mutually authenticated.

+   c) Access Control: In an IoT-based healthcare system, multi-access levels should be established so that all authorized users, such as physicians, hospital managers, paramedical personnel, and patients, do not have access to all information. Instead, each group of users should only have access to the information they need. Through access control, insider attacks can be prevented.

+   d) Data Integrity Verification: Data integrity ensures that data cannot be modified without authorization during storage or transmission. To prevent change, cryptographic primitives such as digital signatures or hash functions are required. Even if a change occurs, it should be quickly detected.

+   e) Secure Device Management: In IoT-based healthcare systems, each device must be managed and monitored properly to prevent the deployment of any malicious devices. For this, each device must be properly registered at the time of deployment. Additionally, all registered devices must be authenticated before the start of the communication. Furthermore, keys of all devices must be managed securely and efficiently.

+   f) Secure Communication Protocols: Since the communication between fog nodes and the sensor nodes occurs over public channels, there should be the use of standard communication protocols like Transport Layer Security (TLS) to provide security and confidentiality. Additionally, the communication protocols should resist eavesdropping attacks.

Even though incorporating security measures into IoT-based health care systems can improve their robustness and reliability, some challenges hinder their in practice. The major challenges faced by such systems are:

+   a) Interoperability: In health care systems, multiple sensor nodes are grouped together to sense the health of patients, environments, or equipment. All sensor nodes may need to communicate with each other to function fully. However, different sensors may be made by different