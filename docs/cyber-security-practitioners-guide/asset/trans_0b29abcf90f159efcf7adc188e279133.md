
47. P. S. Foundation. (2012). `Regular Expression Operations` \[Online\]. Available at: https://docs.python.org/3.1/lbrary/re.html. (Accessed: November 2018).

48. Rajpal, M. S. and Kotov, V. (2014). `Understanding Crypto-Ransomware: In-Depth Analysis of the Most Popular Malware Families.` Cupertino, CA, USA: Bromium.

49. Richet, J.-L. (2016). Extortion on the Internet: The Rise of CryptoRansomware. `Harvard Researches`, **2**(1), pp. 2–6.

50. Savage, K., Coogan, P. and Lau, H. (2015, 6 August). The Evolution of Ransomware. Mountain View, CA, USA: Symantec.

51. SC Magazine. (2017). `Malware and the “Other” Platforms: Mac and Android Devices are Increasingly at Risk` \[Online\]. Available at: https://media.scmagazine.com/documents/314/malware\_and\_the\_”other”\_platfo\_78268.pdf (Accessed: 11 October 2018).

52. Securonix Threat Research Team. (2018). `Grandcrab Ransomware Attack.` Addison, Texas, USA: Securonix .

53. Sneed, A. (2016). `The Most Vulnerable Ransomware Targets Are the Institutions We Rely On Most.` New York, NY, USA: Scientific American.

54. Snow, J. (2016, 29 June). `Ransomware on Mobile Devices: Knock-Knock-Block.` Available at: https://www.kaspersky.com/blog/mobile-ransomware2016/12491/(Accessed: 11 October 2018).

55. Soni, V. (2018). `Multifunctional Malware Becoming Extensive in 2018, Finds Kaspersky Lab Report`. Available at: [https://www.dailyhostnews.com/multifunctional-malware-becoming-extensive/](https://www.dailyhostnews.com/multifunctional-malware-becoming-extensive/) (Accessed: 2 October 2018).

56. Stavrou, A., Rhandi, M., Ghosh, A., Jajodia, S. and Andrianakis, C. (2010, 9 April). `USA Patent No. US8935773B2.`

57. Tasril, V., Ginting, M., Mardiana and Siahaan, A. (2017). Threats of Computer System and its Prevention. `IJSRST,` **3**(6), pp. 448–451.

58. Touchette, F. (2016). The Evolution of Malware. `Network Security`, **1**(1), pp. 11–14.

59. Turpin, S. and Harmsworth, S. (2001, July). `Creating an Effective Dissemination Strategy: An Expanded Interactive Workbook for Educational Development Projects` \[Online\]. Available at: https://ajpp-online.org/resources/downloads/06-CreatingAnEffectiveDisseminationStrategy-AnExpandedWorkbook.pdf (Accessed: 12 October 2018).

60. Walker, J. (2018). `Ransomware Remains Biggest Malware Threat in 2018, Says Europol` \[Online\]. Available at: [https://portswigger.net/daily-swig/ransomware-remains-biggest-malware-threat-in-2018-says-europol](https://portswigger.net/daily-swig/ransomware-remains-biggest-malware-threat-in-2018-says-europol) (Accessed: 6 October 2018).

61. Walton, A. G. (2017, 11 December). `Phone Addiction Is Real — And So Are Its Mental Health Risks` \[Online\]. Available at: [https://www.forbes.com/sites/alicegwalton/2017/12/11/phone-addiction-is-real-and-so-are-its-mental-health-risks/#527d531813df](https://www.forbes.com/sites/alicegwalton/2017/12/11/phone-addiction-is-real-and-so-are-its-mental-health-risks/#527d531813df) (Accessed: 11 October 2018).

62. Young, A. L. and Yung, M. (2017). Privacy and Security Cryptovirology: The Birth, Neglect, and Explosion of Ransomware. `Communications of the ACM`, **60**(7), pp. 24–26.

63. Zetter, K. (2016). `Inside The Cunning, Unprecedented Hack of Ukraine’s Power Grid.` London, UK: Wired.

## Chapter 6

## Protecting and Securing Data Through Blockchain Across Industries

Stefan Kendzierskyj\* and Hamid Jahankhani^†

*Northumbria University London, UK*

\*[`stefan.kendzierskyj@northumbria.ac.uk`](mailto:stefan.kendzierskyj@northumbria.ac.uk)

^†[`Hamid.jahankhani@northumbria.ac.uk`](mailto:Hamid.jahankhani@northumbria.ac.uk)

## ABSTRACT

Blockchain is being viewed as a mechanism that can further protect and enhance the security of data due to its properties of immutability, auditability and encryption, whilst providing transparency between parties who may not know each other and who therefore are operating in a trustless environment. It’s true that blockchain has its roots in cryptocurrency applications and is still evolving for that purpose in the financial sector, but many other organisations across different industries are beginning to see the non-crypto use cases in which this mechanism can be used to record data that cannot be changed or reversed or as smart contracts (as a way to time-stamp transactions between parties). Consequently, blockchain is becoming extremely relevant and purposeful. Organisations have various options. They can run blockchain as permissionless (anyone can join), permissioned (invitations are required) or hybrid (like a consortium). They can also choose whether data should be held on-chain or off-chain in data lakes. With industry entering its fourth industrial revolution (Industry 4.0), the addition of blockchain as a complementary technology has its place; there are some industries very suited to the significant impact it may bring. Also, the advances made in areas such as Internet of Things and Machine Learning and Artificial Intelligence may have considerable impact on the amount of data we collect for analysis and the ways in which we store, manage and analyse it. They may also increase the likelihood of cyber attacks and the ripple effects they cause. This has also become complicated, as cyber attacks have become much more sophisticated in recent years. Cyber attacks come in different configurations, and various industry sectors have suffered from a range of these different attack vectors, resulting in some devastating outcomes. These cyber attacks have manifested in the shape of ransomware, malware, manipulation methods, phishing and spear-phishing. Whilst data breaches are a serious incident, there is a growing concern in most organisations regarding attacks that are designed to have a more destructive effect, such as the Ukraine cyber attack in 2015 that resulted in a shutdown of the power grid, or the WannaCry ransomware attack in 2017 that caused widespread chaos with healthcare institutions unable to carry out any tasks since access to data/systems was unavailable.

*Keywords*: `blockchain`, `Industry 4.0`, `smart contracts`, `cyber attacks`, `IoT`, `AI`, `ML`, `WannaCry`, `immutability`, `auditability`

### 6.1. Introduction

With the fast-growing development of cloud-based architecture, smart technology such as Internet of Things (IoT) and many other new developments of Artificial Intelligence (AI) and Machine Learning (ML) have caused a large increase in data volumes and more complexities to arise during the process of finding a more secure and efficient way to handle and manage the data. This is heightened by the increasing cyber attacks and the wide range of attack vectors. Cyber attacks have become a lucrative and more organised criminal behaviour with the availability of ransomwareas-a-service, as an example. It’s becoming apparent that even with attention to the various business structures and methods to mitigate cyber security risks, such as continual review of policies/compliance, training, patching, deploying Intrusion Detection and Prevention Systems (IDPS), etc., the cyber security breach effect has not been lessened. In fact, more diverse types of cyber attacks are increasing and growing year on year at a faster and faster rate, particularly in the healthcare industry. Attacks on the healthcare industry account for more than 50% of all cyber attacks. From an organisational perspective, there are of course many advantages to having access to modern software and system developments, and to living in a ‘data on demand’ culture. Organisations will benefit in many ways, particularly with the more recent developments in Artificial Intelligence and Machine Learning. However, there is a feeling that data usage and access to data are not very strictly controlled. There are also concerns over the possible impact this may have. For instance, it may lead to criminal activity such as identity theft and victimisation.
