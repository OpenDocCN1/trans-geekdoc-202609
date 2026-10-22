
## 29.16 BIOMETRIC AUTHENTICATION

The use of DNA as a biometric identifier has also been investigated, although it has significant weaknesses including the fact that DNA in body tissues (e.g., epithelial cells) can be obtained surreptitiously and transferred easily for nefarious purposes whereas the official methods of collection (e.g., taking blood samples) are relatively intrusive.

Other physiological biometrics that may prove useful in the future include body odor, skin reflectance, and ear shape.

## 29.5 TYPES OF ERRORS AND SYSTEM METRICS.

All types of identification and authentication systems suffer from two types of errors: false accepts and false rejects.

### 29.5.1 False Accept.

Also known as false match, false positive, or type 1 error, false accept is the likelihood, expressed as a percentage, that an imposter will be matched to a valid user's biometric. In some systems, such as those that attempt to secure entry to a weapons facility, a bank vault, or a high-level system administrator account, the false match/false accept rate is the most important metric to watch. In other systems, such as a facial recognition system deployed by a casino in an effort to spot card counters, a high level of false matches may be tolerated.

### 29.5.2 False Reject.

Also known as false nonmatch, false negative, or type 2 error, false reject is the probability that “a user’s template will be incorrectly judged to not match his or her enrollment template.”31 False nonmatches typically result in the user being locked out of the system. These false nonmatches can occur because of changes in a user’s biometric data, changes in how the biometric data is presented, and/or changes in the environment. Biometric systems are generally more susceptible to false rejects than they are to false accepts.

### 29.5.3 Crossover Error Rate.

An important metric in biometric systems is the crossover error rate (CER), also known as the equal error rate (EER). This useful metric is the intersection of the false accept and false reject rates. In general, a lower CER indicates the biometric device is more accurate and reliable than another biometric device with a higher CER. Exhibit 29.2 provides a summary of benchmark test-based accuracy/error rates for the five most prevalent biometric technologies. Each biometric technology is rank-ordered from most accurate to least accurate based on CER.

### EXHIBIT 29.2 Accuracy/Error Rates of Leading Biometric Technologies

| Biometric | False Match Rate | False No-Match Rate |
|---|---|---|
| Iris scan | 0.0001% | 1.1-1.4% |
| Finger scan | 0.02% | 0.6% |
| Hand scan | 0.3% | 3.0% |
| Voice (text independent) | 2-5% | 5-10% |
| Voice (text dependent) | 2.0% | 0.03% |
| Face scan | 0.1% | 1-2.5% |

Source: Based on data contained in Anil K. Jain (2008), “Biometric Authentication,” Scholarpedia, 3(6); 3716.

### 29.5.4 Failure to Enroll.

Another critical metric in biometric systems is FTE. As Ashbourn explains, FTE refers to “a situation whereupon an individual is unable to enroll their biometric in order to create a template of suitable quality for subsequent automated operation.”32 Common reasons for failure to enroll include physical disability and a user whose physiological/behavioral characteristics are less distinctive than average. Nanavati, Thieme, and Nanavati observe that failure to enroll can be a major problem in “internal, employee-facing deployments” in which “high FTE rates are directly linked to increased security risks and increased system costs.”33 A final important metric is the “transaction time.” Transaction time refers to “a theoretical time taken to match the live template against a reference sample.”34

## 29.6 DISADVANTAGES AND PROBLEMS

### 29.6.1 General Considerations.

Despite the many advantages over other commonly used authentication systems, the implementation of biometric authentication controls carries a number of risks and disadvantages. Even the most accurate biometric system is not perfect, and errors will occur. The error rates and the types of errors will vary with specific biometrics deployed and the circumstances of deployment. Certain types of errors, such as false matches, may pose fundamental, critical risks to organizational security. Other types of errors—failure to enroll, false nonmatch—may reduce organizational productivity and efficiency and increase costs. Organizations planning biometrics implementation will need to consider the acceptable error threshold. In any event, organizations deploying biometric authentication systems must not be lulled into a belief that they are invulnerable to errors and/or fraud. Certain biometric systems (e.g., iris scanning) are fairly impervious to fraud, while others (especially behavior-based systems) are much more susceptible to it. Facial scanning systems can be foiled with clothing, makeup, eyeglasses, and/or changes in hairstyle. Even relatively stable physiology-based biometrics like fingerprint scans can be defrauded with the use of rubber or gelatin fingers. Matsumoto outlines a gummy finger approach designed to fool even those countermeasures mentioned in Section 29.4.1.35 The protein used has a similar galvanic response to flesh and, since it is very thin and attached to a live finger, has the correct temperature. In some cases, blowing warm air over the scanner may even raise the latent print of the intruder’s predecessor.

The deployment of commonly used authentication systems (i.e., ID badges, passwords, etc.) requires relatively little training, although one could argue that better training on the development and use of passwords would improve security. This limited need for training is not the case with most of the most commonly used biometric systems. Both systems administrators and users need instruction and training to ensure smooth operation of the system. Some biometric systems are exquisitely sensitive to intra- and inter-user variation in presentation and performance. Their effectiveness becomes substantially compromised and error rates substantially increase in cases of significant variation and/or irregular presentation. A related problem concerns user acceptance of the biometric system. Some users may object to the deployment of biometrics due to concerns over privacy and intrusiveness. In other instances, users may object to the deployment of biometrics and avoid optimal interface with the system because of safety and/or health concerns, general fears, and/or cultural and religious beliefs. For example, some individuals may be concerned that biometric systems that require them to touch a finger pad or hand pad will unnecessarily expose them to germs and place them at risk for illness. Some users may fear that eye scans will damage their eyes. Other users may object to eye scans on the basis that the eyes are the window to the soul. Anderson notes that some persons may object to the use of biometrics due to a personal interpretation of religious doctrine.36 Notwithstanding users’ beliefs and perceptions about the biometric system, in many cases features or elements related to the users and/or the operating environment will influence the successful implementation and effectiveness of the system.

### 29.6.2 Health and Disability Considerations.

Individuals with arthritis and/or certain other disabilities and physical limitations may be unable to enroll in systems and subsequently, to align themselves physically in an optimal position with respect to biometric sensors. For example, users with severe hand arthritis may be unable to place their hand firmly as required on the hand geometry sensor, and users with migraines and associated photophobia may find it physically too uncomfortable to look straight into the light sensor for the iris scan. Some disabled people may have to be excluded from biometric systems altogether. Some relatively minor disabilities, such as a slight tremor, may compromise a legitimate user’s ability to gain access through certain biometric systems. Variations in physical size can also influence system accuracy. An iris scanner positioned for a standard height range may fail to capture images of either very short or very tall individuals, or in some cases an individual’s hands or fingers may be either too large or too small to be read accurately in a hand or finger scanner. Likewise, individuals with neck and back problems may find it difficult to use some biometric devices, depending on the kind of positioning required. Systems that rely on behavioral biometrics such as voice or signature are particularly vulnerable to variations and irregularities in user characteristics. For example, users who speak too softly, too loudly, or too rapidly may cause system errors. Minor changes in users’ health can affect some biometric readings. Excessive skin moisture or lack of skin moisture can impact finger scans.

Although one of the ideal properties of a biometric is its universality, in reality not everyone has the characteristic or has it to the same degree. For example, some people are born without distinct fingerprints. In other cases, users may have lost the distinctiveness of their fingerprints because of years of manual labor, use of certain chemicals, scarring, or the aging process. Anderson notes that “people with dark-colored eyes and large pupils give poorer iris codes.”37 Certain eye diseases and metabolic conditions may also reduce or negate the efficacy of eye scan authentication. Age has a significant impact on the user-biometric-system interface. Definite physiological changes are associated with the aging process and can result in poor template matching with the live biometric. In this case, reenrollment may be needed. Fingerprints are affected by the aging process as the skin becomes drier and more brittle; voice patterns change in tonal quality over time; and facial shape or appearance may shift with age. Overall, the acceptability of a biometric system will be lessened if there is the impression that implementation of the system discriminates against, or has an otherwise adverse impact on, the disabled, the ill, ethnic minorities, the elderly, and other protected or traditionally disadvantaged groups of users. Organizations must ensure compliance with the Americans with Disabilities Act when implementing biometric authentication systems. Compliance may involve providing alternative methods of authentication to those affected.

### 29.6.3 Environmental and Cultural Considerations.

A broad range of factors in the operating environment can also impact the effectiveness and acceptability of biometric systems. User-related cultural, social, and behavioral factors can influence
