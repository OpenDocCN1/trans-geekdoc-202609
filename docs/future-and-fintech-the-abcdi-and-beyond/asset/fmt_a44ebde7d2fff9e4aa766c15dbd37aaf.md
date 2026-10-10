
Many dedicated AI chips e.g., Huami, Intellifusion, AnyVision, Syntiant, and Xailient, are developed or are currently under development for this purpose. The Huami Huangshan-2(`MHS002`) is based on RISC-V architecture as an AI-backed cardiac biometrics engine. Syntiant’s solutions of edge AI processors target at a voice-controlled “multimodal” AI processor, while Intellifusion, AnyVision, and Xailient target at super-fast biometric face detection and identification chips.

When AI improves the security of biometrics technology, it is also used for attacks. In fact, AI can beat standard biometrics by deceiving it using synthetic fingerprints, manipulated printed 3-dimensional (3D) face image or mask, etc. Brute force attacks can be orchestrated with such synthetic data, trying every option till none are left. For example, Apple’s Face ID can be tricked by an altered pair of glasses in just 120 seconds. Deepfakes^([7](#chap11.xhtml#rfn7)) is an amusing but also threatening tool for the liveness detection of face biometrics.

### 11.6 Biometrics Applications in Financial Services

In this section, the financial service applications of biometrics are discussed in details.

#### 11.6.1 General Category

Biometrics are essentially used to identify personal characteristics, although they can also be applied for healthcare and personal health insurance. Here, we mainly consider its applications in individual authentication and group differentiation for digital identity and cybersecurity.

##### 11.6.1.1 Mobile and online banking

This is the most common application nowadays with various biometrics, e.g., fingerprint, face, iris, etc. Almost all banks, insurance companies, and trading platforms provide their mobile apps and online portal for business operations, i.e., it becomes a standard component for a modern financial institution.

Several recent advancements could be used to improve MFA methods for better convenience and security, e.g., biometric-based single sign-on (SSO) services, AI-backed hardware security module (HSM), and continuous user authentication.

##### 11.6.1.2 Digital payment

It is generally divided into online and offline categories. Offline devices can be a biometric embedded card (e.g., a credit card), a token device, or a mobile device. For example, the central bank digital currency (CBDC) issued in China supports offline payment. Online device is usually smartphone-based. Many banks support mobile apps with selfie payment and virtual credit card activation via face recognition and fingerprint (e.g., Apple Touch ID).

Based on Juniper’s study,^([8](#chap11.xhtml#rfn8)) by 2023, in-store and remote payments authenticated by mobile biometrics will have a market value of US$2 trillion, and the mobile biometrical-verified commerce transactions will represent a massive 57% of total biometric transactions from 28% in 2018.

##### 11.6.1.3 Seamless digital onboarding, KYC, AML

According to Forbes,^([9](#chap11.xhtml#rfn9)) digital account opening (DAO) is one of the most popular technologies in banking for the third consecutive year since 2018. Nearly 80% of all banks and credit unions were either adding new DAO systems or improving their existing ones in 2020.

Know your customer (KYC) is a mandatory due diligence process to identify and verify customers’ identity upon onboarding, e.g., DAO. It becomes a significant aspect of fighting against financial crime and money laundering. Biometrics-based authentication allows FIs to dramatically expedite their due diligence and eKYC activities to deliver fast and seamless onboarding experiences, from hours to few minutes.

Singaporean banks can enjoy the benefits of Singpass and its mobile apps to authenticate the customers and authorize their access to the customers’ government-certificated personal profile for opening new accounts. NatWest in the UK is one of the first major high street banks to open accounts using a selfie and AI-backed real-time verification. Branch video teller machines (VTMs) and mobile VTMs (e.g., portable-dedicated device or staff tablet) with face recognition and other biometrics sensors, support to open new account, issue debit cards, and provide personal identification numbers (PIN) on the spot or at the customers’ locations.

From the perspective of anti-money laundering and counter-terrorism financing (AML/CTF), the customer onboarding (enrolment) and transaction verification are the two most important steps. With multimodal biometrics system (MBS), potential bad actors, bots, and synthetic or fraudulent identities can be identified during the onboarding phase, while illegal activities, such as account takeover fraud, identity theft, and phishing can be prevented during the authentication phase. Therefore, the AML/CTF process can be enhanced dramatically by reducing the time and cost of onboarding, mitigating financial fraud and crime, improving compliance efficiency, and preventing many criminal events, such as unauthorized account access, fraudulent payments, and money mules.

##### 11.6.1.4 Online fraud detection and cybersecurity

When FIs are going through digitalization and increasing the varieties of digital services, particularly during the COVID-19 pandemic, cyber-attackers have become increasingly sophisticated. Without compromising users’ experiences, intelligent security measurements to detect cybercrime in omnichannel becomes more important. At the same time, online fraud continues to grow dramatically, and fraudsters are incessantly refining their attack bots and agents with new strategies to identify vulnerabilities and penetrate defenses.

[Table 11.1](#chap11.xhtml#tab11-1) and [Figure 11.1](#chap11.xhtml#fig11-1) seen earlier list behavioral biometrics that capture multiple forms of interactive gestures, keystroke, mouse movement, or tapping and typing pattern, to analyze a user’s online physical and cognitive behavior. By differentiating the patterns of digital behavioral traits common to fraudsters and trusted users, behavioral biometrics can be used to identify legitimate human users versus non-human cybercriminal actors like bots, and detect anomaly sessions, etc. This analysis generally works together with AI and Big Data technologies for better accuracy. Many companies provide relative matured solutions, such as ThreatMark, LexisNexis, and BioCatch.

##### 11.6.1.5 Cardless ATM transactions

Cash is still widely used in most countries. The traditional ATM allows customers to withdraw money with only physical cards and a digital PIN, which caused a loss of about 250 million Euros’ in 2018 in Europe due to ATM fraud, e.g., duplicated cards and PIN loss.^([10](#chap11.xhtml#rfn10)) However, as it is generally not easy to trace the wrongful users, anti-fraud detection for ATM is technically difficult. Therefore, some new types of ATMs using biometrics are built to enhance the security:

1.  **Biometric-equipped ATM.** Customers can use their fingerprint, face, palm, iris, etc., to get authenticated. However, this approach has the advantage of easy adoption, but leave the data storage security issue to banks.

2.  **App-enabled ATM.** Users can authenticate themselves via on-device biometrics and initiate transactions using the corresponding bank’s app. An example is the collaboration between Mastercard and Diebold Nixdorf for banking experiences with cardless ATMs.^([11](#chap11.xhtml#rfn11))

A similar idea can be applied to safe-box services in the bank.

##### 11.6.1.6 On-site marketing

In some on-site roadshow and promotion events, the prompters need to identify potential customers immediately when they pass by the venue. Experienced prompters may capture key information from the persons’ appearance, emotions, and movement trajectory, and quickly judge if they have the intention to buy the products or services. AI-based biometrics detection system can achieve the same with properly trained models.

##### 11.6.1.7 Surveillance
