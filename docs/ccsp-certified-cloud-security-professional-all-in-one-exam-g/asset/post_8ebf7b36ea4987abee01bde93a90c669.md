
# CCSP Certified Cloud Security Professional All-in-One Exam Guide
356

token in order to know the regularly changing PIN code that the token has at the time the PIN code needs to be entered. This would satisfy the multifactor requirements because the password would constitute “known” to the user and the RSA token would be something in possession of the user.

C is incorrect because the use of a text message as a secondary factor along with a password would satisfy the requirement for multifactor authentication. To receive the text message with a secondary code, the user would need to be in possession of a preregistered device, which would be something in their possession. Because the device would have to be preregistered with the system to receive the text code, this is also a robust security system because it would negate someone from getting a new device and trying to use it to access the system.

43. Which of the following ISO/IEC standards pertains to eDiscovery processes and best practices?

-   A. ISO/IEC 27050
-   B. ISO/IEC 17789
-   C. ISO/IEC 27001
-   D. ISO/IEC 17788

A. ISO/IEC 27050 is a standard focused on eDiscovery processes and how best to approach an order. The goal of the standard is to establish common terminology, give an overview of the eDiscovery process, and then provide guidance and best practices for conducting the data collection, including discovery, preservation, and analysis.

B is incorrect because ISO/IEC 17789 provides a reference architecture for cloud computing and is focused on general cloud computing design and implementation. While some information contained would be useful in instances of eDiscovery, the standard itself does not address eDiscovery at all or provide any guidance toward it.

C is incorrect because ISO/IEC 27001 is focused on general security principles and best practices, and does not have any specific guidance or focus on eDiscovery processes or anything that is involved with.

D is incorrect because ISO/IEC 17788 provides terminology and definitions for cloud computing in general, but does not have any focus or sections pertaining to eDiscovery at all.

44. Which of the following is NOT one of the cloud computing activities, as outlined in ISO/IEC 17789?

-   A. Cloud service provider
-   B. Cloud service partner
-   C. Cloud service administrator
-   D. Cloud service administrator customer

C. The activity of a cloud service administrator is not one of the defined cloud computing activities in ISO/IEC 17789.

A is incorrect because the cloud service provider is an official role established in ISO/IEC 17789. The cloud service provider is the entity that makes cloud services available to users or customers, regardless of the cloud deployment model or hosting model used.

B is incorrect because the cloud service partner is an official role established in ISO/IEC 17789. The cloud service partner is defined as an entity that assists either the cloud service customer or the cloud service provider in the delivery of cloud services, or both.

D is incorrect because the cloud service customer is an official role established in ISO/IEC 17789. The cloud service customer is defined as any entity that has a business relationship for the use of cloud services.

# Appendix A: Exam Review Questions

45. Which act relates to the use and protection of PII with financial institutions?

-   A. SOX
-   B. GLBA
-   C. HIPAA
-   D. PCI DSS

B. The Gramm–Leach–Bliley Act (GLBA), also known as the Financial Modernization Act of 1999, is specifically focused on the use of PII by financial institutions and the necessary requirements for the protection of it. The Act contains what is known as the Safeguards Rule, which puts the specific requirements and burdens on financial institutions to protect the privacy and personal information of their customers. The Act also requires notification of the privacy practices of financial institutions as well as with whom they share information and for what purposes.

A is incorrect because the Sarbanes–Oxley Act (SOX) is focused on the protection of stakeholders and shareholders from financial irregularities, improper practices, and errors by organizations. The Act also outlines specific requirements for data retention and preservation of financial and system records.

C is incorrect because the Health Insurance Portability and Accountability Act (HIPAA) is focused on privacy and personal information as it relates to healthcare and health records, and has no bearing on financial institutions at all.

D is incorrect because PCI DSS is a financial industry regulation as it pertains to organizations that accept credit card payments from the major credit network providers. It is focused on security requirements and records retention for those types of transactions specifically, and does not apply to personal data or the financial sector in general.

46. Which of the following is NOT one of the cloud service capabilities?

-   A. Infrastructure
-   B. Network
-   C. Platform
-   D. Software

B. Network is not a defined cloud service capability. Network services are a major component of cloud computing in general, and all service capabilities heavily use and depend on network services, but network is not a standalone category.

A is incorrect because infrastructure is one of the three cloud service capabilities. This is why Infrastructure as a Service is one of the three main cloud service categories, where the cloud provider is responsible for the physical environment and making services available, but the cloud customer is responsible for the virtual machines, configurations, storage, and almost all aspects of maintenance.

C is incorrect because platform is one of the three cloud service capabilities. Platform as a Service, being one of the main cloud service categories, where the cloud provider makes available to the cloud customer virtual machines with application frameworks installed and configured, where the cloud customer just needs to load their application code and data. The cloud service provider is responsible for the patching and maintenance of the virtual machines and the associated frameworks running on them.

D is incorrect because software is one of the three cloud service capabilities. Software as a Service is one of the main cloud service categories, and one where the cloud provider is responsible for the infrastructure up to the fully functional application. The cloud customer may have limited configuration or default settings to leverage but otherwise is responsible for importing or loading applicable data and then for user account management.

47. Which of the following would NOT be used to determine the classification of data?

-   A. Metadata
-   B. PII
-   C. Creator
-   D. Future use

D. The future use or intended use of data should have no bearing on the classification of it. The classification of data should be based on the sensitivity of the data, any regulatory requirements, and the potential risks and costs associated with compromise. Applications and services that intend to use data must adapt their security controls and policies to the classification of the data. The data should not be classified based on the demands or needs of specific applications or users.

A is incorrect because metadata is one of the keys for classifying data. Information about the creation of data, the time of creation, who created the data, where and how it is stored, and the specific fields involved play heavily into data classification, and all fall under the concept of metadata.

B is incorrect because any data that contains PII will automatically have legal or regulatory requirements placed on it for data classification. In most regulatory systems, the inclusion of PII will have automatic ramifications on the classification level of the data and the necessary security controls that must be used on it.

C is incorrect because the creator of data can definitely have an impact on the classification level of it. For example, if the creator of data is a doctor’s office, and the nature of the data is healthcare related, the data will automatically assume certain data classification requirements.

48. What is the prevailing factor for determining which regulations apply to data that is housed in a cloud environment?

-   A. PII
-   B. Classification
-   C. Population
-   D. Location

D. The location of the data, and any jurisdictions that the location fall under, will always be the prevailing factor for determining which regulations apply to it, regardless of what type of data it is.
A is incorrect because while PII will have a definite impact on the regulations that apply to data, it is a subset of the overall data classification requirements.
B is incorrect because the classification of the data will always have a major impact on the regulations that apply to it, but the jurisdiction, based on location, is what makes that determination.
C is incorrect because while the population of the data can certainly have an impact on the regulations that apply to it, it is a subset of the overall data classification requirements.

49. Which concept involves applying standardized configurations and settings to ensure compliance with policy or regulatory requirements?

-   A. Images
-   B. Repudiation
-   C. Baselines
-   D. Interoperability
