
## Test Your Understanding

- 19.
  - a. Distinguish between error rates and deception in biometrics.
  - b. Why can fingerprint scanning, which is often deceived, be acceptable for entry into a supply cabinet?
  - c. When may it not be sufficient?

## Biometric Methods

### FINGERPRINT RECOGNITION
Thanks to crime movies, almost everyone is familiar with fingerprint recognition. **Fingerprint recognition** technology is well developed and inexpensive. Fingerprint scanners are cheap enough to be added to computers and even small handheld devices. Due to their low cost, fingerprint scanners account for most of the total biometrics market.

![](img/073342643701cc54eb7875c41ab92ef2_265_0.png)

**Figure 5-14** Biometric Errors and Deception (Study Figure)

Unfortunately, fingerprint recognition technology often is easy to deceive. In one study researchers were able to defeat 80 percent of fingerprint recognition systems by creating a gelatin finger from a latent print (i.e., an invisible print left on a glass or other object).¹⁶ Fingerprint readers that can better detect deception use measures such as measuring skin capacitance and even pulse rates. However, these types of fingerprint readers are expensive and so are less widely used.

Given that fingerprint scanners can be deceived, we have noted that they should only be used in applications for which there is little danger of serious deception. An example would be logging into a personal computer that does not hold sensitive information.

### IRIS RECOGNITION

The iris is the colored part of your eye. Irises are far more complex and individual than fingerprints. In fact, iris recognition is the most precise form of biometric authentication, with very low FARs. In general, iris scanning is the gold standard in biometric authentication today. Unfortunately, like gold, it is expensive.

- **Fingerprint Recognition**
  - Simple, inexpensive, well proven
  - Most biometrics today is fingerprint recognition
  - Often can be defeated with latent fingerprints on glasses copied to gelatin fingers
  - However, fingerprint recognition can take the place of reusable passwords for low-risk applications
- **Iris Recognition**
  - Pattern in colored part of eye
  - Uses a camera (no light is shined into eye, as in Hollywood movies)
  - Very low FARs
  - Very expensive
- **Face Recognition**
  - Surreptitious (without the person's knowledge) identification is possible (in airports, etc.)
  - High error rates, even without deception
- **Hand Geometry for Door Access**
  - Shape of hand
  - Reader is very large, so usually used for door access
- **Voice Recognition**
  - High error rates
  - Easily deceived by recordings
- **Other Forms of Biometric Authentication**
  - Veins in the hand
  - Keystroke recognition (pace in typing password)
  - Signature recognition (hand-written signature)
  - Gait (way the person walks) recognition

Figure 5-15 Biometric Methods (Study Figure)

¹⁶ “Doubt Cast on Fingerprint Security,” BBC News, May 17, 2002. http://news.bbc.co.uk/2/hi/science/nature/1991517.stm.

## Figure 5-16 HIIDE™ Eye Scan

![](img/073342643701cc54eb7875c41ab92ef2_267_0.png)

**SOURCE:** PJF Military Collection/Alamy Stock Photo

Iris scanners can read iris patterns from several centimeters to a few meters or so away.¹⁷ In movies, iris scanning typically is shown as a red laser beam shining into the supplicant’s eye. This is complete nonsense. With iris scanners, people simply look into ordinary cameras. There is typically a small TV monitor to help the supplicant ensure that he or she is looking directly into the camera.

### FACE RECOGNITION
Facial features can be read from several meters away. This makes **face recognition** useful for door access control. However, face recognition is highly sensitive to lighting differences between the scanned image stored on the computer and the situation in which the scan is taken. It also is moderately sensitive to changes in facial features such as facial hair, and it is often very sensitive to deception by people turning their faces away from the camera.

The only major benefit of face recognition is that it can be used **surreptitiously**, that is, without the subject’s knowledge. This makes it seem to be good for surveillance cameras searching for criminals and terrorists. However, its high error rates and the ease with which it can be deceived make its use for criminal and terrorist watch lists highly suspect.

### HAND GEOMETRY
Human **hand geometry**, including finger length, finger width, palm width, and other characteristics, is fairly easy to measure and is used mostly in door access control because of the size of hand geometry scanners. The user simply places his or her hand on a scanner that is the size of a textbook.

### VOICE RECOGNITION
Fingerprint, iris, face, hand geometry, and vein recognition are examples of something you are. **Voice recognition**, by contrast, is based on something you do, namely speak. Unfortunately, voice recognition is easily deceived by recordings. In addition, high false rejection rates make voice recognition frustrating to users.

¹⁷ By contrast, retinal scanning, which is based on patterns in the retina at the back of the eyeball, requires users to press their eye sockets against a reader; many users will not do this. Although movies frequently mention retinal scanning, it is rare in practice.

## OTHER FORMS OF BIOMETRIC AUTHENTICATION

There are many other forms of biometric authentication—the recognition of *veins in the hand*, *keystroke recognition* (typing pace between keystrokes), written *signature* recognition, and the recognition of *gait* (way of walking), to name just a few. However, fingerprint, iris, face, and hand geometry are the most widely used types of biometric authentication today, and fingerprint recognition is dominant.

## Test Your Understanding

- 20. a. What is the advantage of fingerprint recognition?
  b. What are the disadvantages?
  c. For what type of use is fingerprint recognition sufficient?
  d. What is the advantage of iris recognition?
  e. What are the disadvantages?
  f. Does iris scanning shoot light into your eye?
- 21. a. What is the advantage of face recognition?
  b. What does *surreptitious* mean?
  c. Where is hand geometry recognition used?
  d. What are the disadvantages of voiceprint recognition?
  e. What are the most widely used forms of biometric authentication?
  f. What is the most widely used form of biometrics?

## 5.6 Cryptographic Authentication

5.6 Explain how PKI provides cryptographic authentication.

## Key Points from Chapter 3

In Chapter 3, we looked at cryptographic authentication in the context of cryptographic systems. Cryptographic authentication is the gold standard in authentication. It is the most secure form of authentication if implemented properly. Like gold, it also is the most expensive form of authentication. Chapter 3 made several key points:

- In cryptographic systems, there are two forms of authentication—*initial authentication* at the beginning of the dialogues and *message-by-message* authentication with electronic signatures for all messages in the dialogue.
- We looked at MS-CHAP for initial authentication using passwords.
- We then looked at two forms of electronic signatures. Key-hashed message authentication codes (HMACs) are fast and inexpensive, but they lack nonrepudiation.
- Digital signatures use public key encryption and digital certificates to give extremely strong but slow authentication.
- Although Chapter 3 did not discuss it, public key authentication with digital certificates is also useful for initial authentication.¹⁸

¹⁸ More precisely, this was left to a thought question.

## Public Key Infrastructures

Using public key authentication with digital certificates requires the organization to establish a **public key infrastructure** (PKI) to create and manage public key–private key pairs and digital certificates. Figure 5-18 illustrates the functions of a PKI.

### THE FIRM AS A CERTIFICATE AUTHORITY
As Chapter 3 noted, certificate authorities (CAs) manage digital certificates. The chapter also noted that CAs are not regulated, and this creates questions of trust. However, if firms act as their own CAs, they have control of trust in their entire public key infrastructure. On the negative side, being a certificate authority is quite expensive because of the labor involved.

### CREATING PUBLIC KEY–PRIVATE KEY PAIRS
First, a PKI needs a way to generate public key–private key pairs for non-PKI servers and clients. This is typically done by the client or non-PKI server rather than by the PKI server. The client or server generates a private key–public key pair,¹⁹ and then sends the public key to the CA. This transmission can be done in the clear because public keys are not secret. The private key, which is secret, is not transmitted at all.

### DISTRIBUTING DIGITAL CERTIFICATES
Obviously, the PKI infrastructure must be able to distribute public keys in digital certificates.

- **Key Points from Chapter 3**
  - Cryptographic systems have initial and message-by-message authentication
  - MS-CHAP uses passwords for initial authentication
  - Electronic signatures provide message-by-message authentication
    - Key-hashed message authentication codes (HMACs) are fast and inexpensive
    - Digital signatures with digital certificates are extremely strong but slow
  - Chapter 3 did not mention that digital certificates are also good for initial authentication
- **Public Key Infrastructures** (Figure 5-18)
  - Firms can be their own certificate authorities (CAs)
  - But this requires a great deal of labor
  - Provisioning
    - Giving the user access credentials
    - Human registration is often the weakest link
      - If an impostor can deceive the provisioning authority, the system breaks down
      - Controlling the giving of access credentials is the prime authentication problem
      - If an impostor is given credentials, no technology access controls will work
      - Limit who can submit names for registration
      - Limit who can authorize registration
      - Have rules for exceptions
  - Must have effective terminating procedures
  - Supervisors and human resources department must assist

![](img/073342643701cc54eb7875c41ab92ef2_269_0.png)

¹⁹ It is easy to create public key–private key pairs. However, computing a private key if you know a public key is almost impossible.
