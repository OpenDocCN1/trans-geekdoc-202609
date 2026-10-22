
### 28.11 NOTES

- 1. "No Token Resistance: Citi rolls out Digipass authentication devices to biz clients," Bank Systems & Technology, May 25, 2006, www.banktech.com/features/showArticle.jhtml?articleID=188103117
- 2. J.-J. Quisquater, L. Guillou, and T. Berson, "How to Explain Zero-Knowledge Protocols to Your Children," Proceedings of CRYPTO '89, Advances in Cryptology, vol. 435 (1989) pp. 628–631. www.cs.wisc.edu/~mkowalcz/628.pdf
- 3. R. Wright, "Secret Communication Using a Deck of Cards." Abstract of presentation from DIMACS Research and Education Institute Cryptography and Network Security. July 28–August 15, 1997 (Abstracts of Talks Presented); ftp://dimacs.rutgers.edu/pub/dimacs/TechnicalReports/TechReports/1997/97-80.ps.gz
- 4. M. E. Kabay, "SiteKey Tries to Counter Phishing," Network World Security Strategies, April 3, 2007. www.networkworld.com/newsletters/sec/2007/0402sec1.html
- 5. M. E. Kabay, "Password Management: Facing the Problem," Network World Security Strategies, October 11, 2007. www.networkworld.com/newsletters/sec/2007/1008sec2.html
- 6. This section (28.4.1) was originally part of Chapter 23 on "Protecting the Physical Information Infrastructure," by Franklin Platt, from the 5th edition of this Handbook.
- 7. This section (28.4.2) was originally part of Chapter 23 on "Protecting the Physical Information Infrastructure," by Franklin Platt, from the 5th edition of this Handbook.
- 8. FIPS 201-1, "Personal Identity Verification (PIV) of Federal Employees and Contractors." Gaithersburg, MD: NIST. 2006, p. iv, http://csrc.nist.gov/publications/fips/fips201-1/FIPS-201-1-chng1.pdf
- 9. Shibboleth, http://shibboleth.net
- 10. InCommon, www.incommonfederation.org
- 11. UK Access Management Federation for Education and Research, http://ukfederation.org/
- 12. RSA Data Security, "Are Passwords Really Free? A Closer Look at the Hidden Costs of Password Security," 2006. www.rsa.com/go/wpt/wpindex.asp?WPID=3384
- 13. M. E. Kabay. "Airport Safety," 2005. www.mekabay.com/opinion/airport_safety.pdf

## BIOMETRIC AUTHENTICATION

Eric Salveggio, Steven Lovaas, David R. Lease, and Robert Guess

| Section | Title | Page |
|---------|-------|------|
| 29.1 | INTRODUCTION | 29-2 |
| 29.2 | IMPORTANCE OF IDENTIFICATION AND VERIFICATION | 29-2 |
| 29.3 | FUNDAMENTALS AND APPLICATIONS | 29-2 |
| 29.3.1 | Overview and History | 29-2 |
| 29.3.2 | Properties of Biometrics | 29-4 |
| 29.3.3 | Identification, Verification, and Authentication | 29-5 |
| 29.3.4 | Application Areas | 29-7 |
| 29.3.5 | Data Acquisition and Presentation | 29-8 |
| 29.4 | TYPES OF BIOMETRIC TECHNOLOGIES | 29-9 |
| 29.4.1 | Finger Scan | 29-9 |
| 29.4.2 | Facial Scan/Recognition | 29-11 |
| 29.4.3 | Hand Geometry Scan | 29-12 |
| 29.4.4 | Iris Scan | 29-13 |
| 29.4.5 | Voice Recognition | 29-14 |
| 29.4.6 | Other Biometric Technologies | 29-15 |
| 29.5 | TYPES OF ERRORS AND SYSTEM METRICS | 29-16 |
| 29.5.1 | False Accept | 29-16 |
| 29.5.2 | False Reject | 29-16 |
| 29.5.3 | Crossover Error Rate | 29-16 |
| 29.5.4 | Failure to Enroll | 29-17 |
| 29.6 | DISADVANTAGES AND PROBLEMS | 29-17 |
| 29.6.1 | General Considerations | 29-17 |
| 29.6.2 | Health and Disability Considerations | 29-18 |
| 29.6.3 | Environmental and Cultural Considerations | 29-18 |
| 29.6.4 | Cost Considerations | 29-19 |
| 29.6.5 | Attacks on Biometric Systems | 29-19 |
| 29.6.6 | Privacy Concerns | 29-20 |
| 29.6.7 | Legal Issues | 29-22 |
| 29.7 | RECENT TRENDS IN BIOMETRIC AUTHENTICATION | 29-22 |
| 29.7.1 | Government Advances in Biometric Authentication | 29-22 |
| 29.7.2 | Face Scanning at Airports and Casinos | 29-22 |
| 29.7.3 | Increased Deployment in the Financial Industry | 29-23 |
| 29.7.4 | Biometrics in the Healthcare Industry | 29-23 |
| 29.7.5 | Increased Deployment of Time and Attendance Systems | 29-24 |
| 29.8 | SUMMARY AND RECOMMENDATIONS | 29-24 |
| 29.9 | FURTHER READING | 29-26 |
| 29.10 | NOTES | 29-26 |

is considered reliable to this day. This methodology underlies fully automated modern biometrics, including the Integrated Automated Fingerprint Identification Systems (IAFIS) used by law enforcement agencies. Commercial biometric systems (typically relying on hand geometry) designed for use in physical access to buildings emerged in the 1960s and 1970s.

Biometric methods of identification and identity verification, including automatic fingerprint analysis and facial recognition technologies, have been available and used by some government/public agencies (e.g., law enforcement, intelligence, and national security) and a few private industries (e.g., facial recognition scans in casinos) since the 1960s and 1970s. Notwithstanding the potential benefits and advantages over other authentication methods, biometrics have not been widely applied, particularly in the corporate world. Analysts cite high costs of equipment and implementation, technological problems, vulnerabilities of specific biometrics, lack of standards, and user resistance (notably, concerns over privacy) as reasons for the lack of implementation.

However, beginning in the 1990s, significant improvements in biometric technologies, a movement toward standardization, regulatory changes requiring organizations to adopt stringent security and privacy controls, and significantly reduced costs have encouraged wider adoption. A number of U.S. Government agencies (e.g., Department of Homeland Security, Department of Transportation, Department of Defense, Customs and Border Protection, Department of Justice, National Library of Medicine) and businesses in certain industries (e.g., health care and finance) have significantly increased their use of biometrics during the past few years—a factor that is likely to encourage other organizations to adopt biometrics as well. HP and Lenovo offer fingerprint scanners on their notebook computers, enabling users to increase security by requiring a finger swipe and a password (or just a finger swipe) to access files. Other computer manufacturers and peripheral vendors have added fingerprint scanning to computer keyboards and/or developed standalone fingerprint scanners that connect to computers via a Universal Serial Bus (USB) port.

Some analysts see the 2001 attacks on the World Trade Center and the Pentagon also as a key impetus behind the increased usage of biometrics for authentication and identification. The terrorist attacks have been critical in encouraging adoption not only because they have heightened the security concerns of companies and agencies but also because the impact and implications of the terrorists' attacks seem to have lowered users' resistance to the use of biometrics by employers and government. In other words, in the same way that the threat of global terrorism reduced public objections to possible infringements on civil liberties as a result of implementation of the USA PATRIOT Act and other security-focused measures, these attacks also appear to have rendered many people less sensitive to the potential privacy-invading implications of biometrics. Boroshok reported in 2007 that a survey sponsored by AuthenTec found that 71 percent of U.S. consumers would pay more for biometric security options in their cell phones and 63 percent of consumers would pay an additional cost for these options to be added to their personal computers.¹

The changing security environment has prompted forecasts of rapid growth in biometrics. In 2004, the International Biometric Group (IBG) had predicted rapid growth for the biometrics industry over the next several years from revenues totaling under $50 million in 2004 to revenues of almost $200 million in 2008.² In late 2003, analysts at the San Jose, California–based market research firm Frost and Sullivan predicted that biometric applications from commercial applications (not including the Federal Bureau of Investigation's IAFIS) would jump from $93.4 million in 2001 to $2.05 billion by 2006—up from the $700 million (in 2006) that these analysts predicted prior to the September 11, 2001, attacks. In January 2009, IBG released their most recent projections of market growth for the biometrics industry. They estimated that biometric industry revenues will grow from $3.01 billion in 2007 to over $7.4 billion by 2012.³ This is a far cry from their initial projected growth rate published in 2004, and may be attributed to a lack of standards, regulatory issues, and privacy groups that decried the invasion of their privacy by these devices (IBG hasn't publicly released a more recent report so we can't tell if these projections were met).

Despite rosy projections from industry analysts, adoption of biometric authentication systems continues to lag. Some firms continue to cite cost issues (though this is dwindling) and privacy concerns, while others point to problems surrounding biometric implementation in airports and among government agencies. Overall, surveys of companies indicate that forecasts of dramatic and rapid growth in biometrics implementation may be overstated.

This has been proven to be true by the recent 2013 Spending Priorities Survey put out by InformationWeek. Of the 513 businesses that responded to the survey, 13 percent had budget decreases from their 2012 budgets, with 43 percent having no change in their budgets—for many, it's a "do what you can with what you have" mentality. However, in spite of this, 58 percent of those surveyed wanted to improve their security overall.⁴ In another 2013 survey, however, the InformationWeek survey "Strategic Security Survey" revealed 52 percent of the more than 1,000 respondents wanted to increase their identity and password management practices.⁵ The seeming disconnect may be attributed to management wanting to keep costs down, and the ever-changing world of regulations—many are waiting to see what the landscape will look like when the dust settles.

A 2003 Forrester Research survey found that only 1 percent of companies had implemented biometric systems, just 3 percent had a biometric system rollout in progress, only 15 percent were testing biometrics, and 58 percent of those surveyed had no plans to try biometrics. Ten years later, we still have yet to see any substantial adoption of biometric authentication.

### 29.3.2 Properties of Biometrics

The contemporary meaning of biometrics emphasizes its automated aspects, which allow for deployment on a large scale. The most widely cited definition of biometrics is some variation of "the automatic identification of a person based on his or her physiological or behavioral characteristics."⁶ The term "biometrics" generally is used as a noun to refer to the automatic recognition of persons based on their physical or behavioral characteristics. The term "biometric" can be used as a noun in reference to a single technology or measure (e.g., finger scan is a commonly used biometric) or as an adjective, as in "a biometric system uses integrated hardware and software to conduct identification or verification."⁷

Biometrics have long been touted as a possible solution to the problems and vulnerabilities of other commonly used methods of authentication and identification. They represent sophisticated versions of the traditional means of identification, such as a guard allowing access to a user whom the guard recognizes by sight. Biometrics commonly are defined as automated methods of recognition/verification/identification of individuals based on some measurable physiological or behavioral characteristics, such as fingerprints, hand geometry, facial shape, iris pattern, voice, signature, and the like.

Whereas identification (ID) badges and keys authenticate the user based on something the user possesses, and passwords/personal identification numbers (PINs) authenticate the user based on what the user knows, biometrics allows authentication and identity verification based on who the user is. Because biometric methodologies of authentication actually base identification on physiological or behavioral "pieces" of the
