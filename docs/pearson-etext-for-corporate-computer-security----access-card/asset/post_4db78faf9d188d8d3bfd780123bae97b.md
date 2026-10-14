
### Access Cards
- Magnetic stripe cards
- Smart cards
  - Have a microprocessor and RAM
  - Can implement public key encryption for challenge/response authentication
- In selection decision, must consider cost and availability of card readers

### Tokens
- Constantly changing password devices for one-time passwords
- USB plug-in tokens

### Proximity Access Tokens
- Use Radio Frequency ID (RFID) technology
- Supplicant only has to be near a door or computer to be recognized

### Addressing Loss and Theft
- Both are frequent
- Card cancellation
- Requires a wired network for cancellation speed
- Must cancel quickly if risks are considerable

### Two-Factor Authentication Needed Because of Ease of Loss and Theft
- PINs (personal identification numbers) for the second factor
- Short: 4 to 6 digits
  - Can be short because attempts are manual
  - Should not choose obvious combinations (1111, 1234) or important dates
- Other forms of two-factor authentication
  - Store fingerprint template on device; check supplicant with a fingerprint reader

Figure 5-7 Access Cards and Tokens (Study Figure)

### MAGNETIC STRIPE CARDS
The simplest access cards use magnetic stripes like the ones on your credit cards. Magnetic stripes can store authentication data about the individual. If you have traveled recently, you know that **magnetic stripe cards** are often used for hotel room access.

## Figure 5-8 Access Cards and Tokens

![](img/073342643701cc54eb7875c41ab92ef2_255_0.png)

### PHYSICAL DEVICE CANCELLATION
One response to theft and loss is to disable compromised devices. For instance, in hotels, if you lose your room access card, a front desk employee will disable the old card’s access to all locks. The employee will then give you a new card for your room. The new card will have a new access code.

Cancellation requires installing wiring from the security center to individual verification devices. However, access device loss is so common that dealing actively with lost access devices is mandatory. (Access device security usually also requires connections to log access events for auditing purposes.)

How fast must cancellation be? This is a matter for risk analysis that balances the cost of faster cancellation against the cost of break-ins that are likely to occur during the time before cancellation.

### TWO-FACTOR AUTHENTICATION
Two-factor authentication, which we saw briefly earlier in this chapter, requires the use of two different authentication methods. The access device would only be one of these methods. As noted at the beginning of this chapter, two-factor authentication has limitations, but it is still useful in many cases.

### PINs.
Some firms require employees to type **personal identification numbers (PINs)** when they use physical access devices. Typically, these PINs are only four to six digits. Passwords need to be long because attackers can try millions of comparisons per second. However, people must enter PINs manually, so attackers can only enter a PIN every second or two. In addition, someone standing over an access door trying many PIN codes would be highly conspicuous and therefore vulnerable to detection. Still, the company should ban easily guessed PINs such as 1111, 2222, 1234, the last four digits of the user’s social security number, or an important personal date in month/day format, such as the supplicant’s birthday or wedding anniversary.

Companies should aggressively ban the recording of the PIN on the card or in the wallet a person uses to carry the card. Such practices negate the benefits of two-factor authentication.

### Other Forms of Two-Factor Authentication.
There are many other ways to do two-factor authentication. For instance, a smart card can contain the access device owner’s fingerprint. The person using the physical access device would also have to run a finger over a fingerprint scanner to verify that he or she is the legitimate user of the device.

## Test Your Understanding

10.
a. Distinguish between magnetic stripe cards and smart cards.
b. What are one-time-password tokens?
c. What are USB tokens?
d. What is the advantage of USB tokens compared to cards?
e. What is the attraction of proximity tokens?

11.
a. Why is it important to disable lost or stolen access devices?
b. Give an example of two-factor authentication not mentioned in the text.
c. What is a PIN?
d. Why can PINs be short—only four to six digits—while passwords must be much longer?

## 5.5 Biometric Authentication
5.5 Describe biometric authentication, including verification and identification.

## Biometrics
We forget passwords. We lose access cards. Yet despite jokes about leaving our heads at home, we always take our bodies with us. This allows biometric authentication, which is based on biological (bio) measurements (metrics). Biometric authentication is based on something you are (your fingerprint, iris pattern, face, hand geometry, etc.) or something you do (write, type, walk, etc.). The major promise of biometrics is to make reusable passwords obsolete.

> The major promise of biometrics is to make reusable passwords obsolete.

## Test Your Understanding

12. a. What is biometric authentication?
b. On what two things about you is biometric authentication based?
c. What is the major promise of biometrics?

## Biometric Systems
### INITIAL ENROLLMENT
Figure 5-10 shows a biometric authentication system. Each user must first be enrolled in the system. Enrollment has three steps:

- Step 1—The reader scans each person’s biometric data. This enrollment scan creates far too much data to use. In addition, the scan data will be different each time the user is scanned.

**Biometric Authentication**
Authentication based on biological (bio) measurements (metrics)
Biometric authentication is based on something you are (your fingerprint, iris pattern, face, hand geometry, etc.)
Or something you do (write, type, etc.)
A major promise of biometrics is to make reusable passwords obsolete
**Biometric Systems (Figure 5-10)**
Enrollment (enrollment scan, process for key features, store template)
Scan data are variable (scan fingerprint differently each time)
Key features extracted from the scan should be nearly the same
Later access attempts provide access data, which will be turned into key feature data for comparison with the template
Biometric access key features will never be exactly the same as the template
There must be configurable decision criteria for deciding how close a match (match index) to require
Requiring an overly exact match index will cause many false rejections
Requiring too loose a match index will cause more false acceptances

Figure 5-9 Biometric Authentication (Study Figure)

### SUBSEQUENT ACCESS ATTEMPTS
When users later wish to be authenticated, they are scanned again. The reader processes this **supplicant scanning** information to create key features. These key features become the **user access data**. The central system matches the user access data against the person’s template in the database.

### ACCEPTANCE OR REJECTION
When a system receives access data, it computes a **match index**, which is the difference between the scan’s key features and the template. There is never a perfect match because scanning never works exactly the same way twice. If the error is smaller than a value called the **decision criterion**, the supplicant is accepted as a match. If not, the supplicant is rejected as a match.

## Test Your Understanding

13.
a. Describe the three scanner actions in the enrollment process.
b. What are key features?
c. Why are they necessary?
d. What does the server do with the key features created by the enrollment scan?
e. What is a template?
f. What is user access data?
g. What are match indices, and how are they related to decision criteria?

## Biometric Errors
Access control requires high accuracy. Unfortunately, there are many questions about the reliability of various types of biometric authentication. One issue is **error rate**, which refers to accuracy when the supplicant is not trying to deceive the system. The other accuracy issue is the **deception rate**, which is the likelihood that an impostor will be able to deceive the system if he or she tries. For now, we will focus on error rates.

> Caution: The following material is difficult to learn because there are several related concepts that are easy to confuse. Slow down as you study this section, and keep comparing what you are reading with what you have already read.

## Figure 5-12 Subsequent Access—Failure and Success

![](img/073342643701cc54eb7875c41ab92ef2_260_0.png)

**SOURCE:** Transcend Information, Inc.
