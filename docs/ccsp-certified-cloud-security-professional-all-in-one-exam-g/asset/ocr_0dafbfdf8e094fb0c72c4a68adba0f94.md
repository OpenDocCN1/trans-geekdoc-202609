Chapter 5: Cloud Application Security

# Threat Modeling

Threat modeling is done on a system or application once it is live, and is used to determine any potential threats that it face. It is a very fluid and constant process because IT security and threats to IT systems are constantly changing. This is due to the rapidly changing technical landscape, new tools and approaches for attacks are evolving and application maintenance and upgrades are ongoing. Each time new code is introduced or configuration changes are made, the potential to impact threat assessments is a reality. Two prominent models recommended by OWASP are STRIDE and DREAD threat models, though both were conceptualized by Microsoft.

# STRIDE

STRIDE is a threat classification scheme in which the acronym STRIDE is a mnemonic for known threats in the following six categories (more information on STRIDE can be found at https://www.owasp.org/index.php/Threat_Risk_Modeling#STRIDE):

+   * Spoofing Identity This is a common risk for any application that uses application-specific access control for the application and database, meaning while users authenticate to the application with their credentials and receive their own particular authorization based on their attributes, the application itself uses a single context to communicate with services and databases, as a "service account" or similar without credential. This configuration, it is important for the application to have proper controls in place to prevent any user from using the identity of another user, to gain access to that user’s information or to leverage their authorization levels to gain data.

+   * Tampering with Data Any data sent to the user faces the potential that the user could manipulate or alter it, whether it resides in cookies, GET or POST commands, or headers. The user could also manipulate clientside validations. If the user receives data from the application, it is crucial that the application validate and verify any data received back from the user. For example, if a user is applying for a loan and a proposed interest rate, package, or terms are sent to the user, it is possible that it could be manipulated (to a lower rate or more attractive terms) and then transmitted back to the application with an “acceptance” by the user. If the data is not verified by the application upon being sent, it could be written into the database in altered form and have downstream effects on processing. Data received back from any user should never be accepted outright; it should be validated to ensure it was the same data sent to the user, or that it matches possibilities within the application.

+   * Repudiation Applications must create and comprehensive logs of all user transactions. Without such logging, any transaction on the system is open to dispute or challenge by a user, who can claim they never performed the type of transaction the system says they did, or challenge the data contained on the system. For example, with a financial system, users can claim they paid certain

173