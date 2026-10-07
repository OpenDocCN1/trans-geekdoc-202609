# Appendix A: Exam Review Questions
351

**A** is incorrect because obfuscation involves replacing sensitive or protected data fields with random information, typically for generating data sets for testing in nonproduction systems or other purposes similar in nature. The difference between tokenization and obfuscation is that, with obfuscation, the original mappings to the protected data are not maintained, nor are they important. Although this will be more secure than tokenization because the original mappings are not preserved anywhere, it also means that the data cannot be used in any meaningful way beyond testing or development purposes.

**B** is incorrect because anonymization involves replacing data so that it cannot be successfully mapped back to an individual.

**D** is incorrect because it is built on the concept of direct and indirect identifiers. Indirect identifiers are those attributes that by themselves cannot map to a single individual, but a combination of many indirect identifiers could lead to the identification of a specific individual. Anonymization is often used in conjunction with the obfuscation or tokenization of sensitive fields as a way of removing the indirect identifiers to ensure the data sets cannot be mapped back successfully through any means.

36. Which of the following is *NOT* one of the security domains presented within the Cloud Controls Matrix?

+   A. Financial security

+   B. Mobile security

+   C. Data center security

+   D. Interface security

**A.** Financial security is not one of the specific security domains presented as part of the Cloud Controls Matrix (CCM). While many other domains will play into the protection of financial information, there is not a domain that is specifically related to it. This also includes the inclusion of costs as a factor in security, because only security controls and policies are part of the CCM.

**B** is incorrect because mobile security is one of the specific domains outlined in the Cloud Controls Matrix.

**C** is incorrect because data center security is one of the specific domains outlined in the Cloud Controls Matrix.

**D** is incorrect because interface security is one of the specific domains outlined in the Cloud Controls Matrix, specifically labeled as application and interface security.