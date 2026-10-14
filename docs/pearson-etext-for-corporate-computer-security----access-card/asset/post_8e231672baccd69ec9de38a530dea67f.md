
## KEY ESCROW

If you forget your password, it is a mere inconvenience. The help desk staff simply resets the password and tells you the new password.

Key loss in encryption is far more serious. If encryption is done so that attackers cannot get the information without the key, then people with legitimate access needs will also be equally locked out if the key is lost. If encryption is done well, then the answer to the question “How can I find my key?” will be “You can’t.” If you can get the key back, so could an attacker.

In fact, some organizations forbid encryption in most circumstances, fearing that the risk of key loss is far more serious than the risk of attackers reading unencrypted information.

The solution to the key loss problem is key escrow, which automatically saves the key so that it can be stored off the computer. If a problem occurs, the escrowed key can be retrieved and used to decrypt the information. The escrowed key should be locked away securely, and access to the key should be restricted.

Key escrow should never be left to individual users. First, individual users are not likely to comply with key escrow policies. Second, if only individual users know their encryption keys, they can blackmail the company by refusing to decrypt critical data. The use of an automatic central key escrow server to manage encryption keys is better.

In a larger corporate environment, it may be necessary to purchase a separate hardware device called a hardware security module (HSM) that can create and store cryptographic keys. They can come in the form of a USB drive, an internal PCI card, or even a network appliance.

In addition to key management, HSMs can provide additional functionality such as encryption, decryption, hashing, and producing digital signatures. They are often used to help reduce the processing load for companies with many concurrent SSL connections such as banks or credit card processors. Certificate authorities also use HSMs to securely manage cryptographic key pairs.

## FILE/DIRECTORY ENCRYPTION VERSUS WHOLE-DISK ENCRYPTION

When encrypting information on a disk, there are two general options—file/directory encryption and whole-disk encryption. The names are self-explanatory. File/directory encryption only encrypts the specific files and directories you tell it to encrypt, while whole-disk encryption encrypts an entire disk drive. If a user knows the directories containing sensitive data, he or she can use file/directory encryption confidently. However, whole-disk encryption ensures that sensitive data are protected even if a user overlooks an important directory.

## PROTECTING ACCESS TO THE COMPUTER

Encryption usually is fully transparent to the PC user. As long as you know the password for your computer, you can work with encrypted directories and files exactly as you do with unencrypted directories and files. In fact, you usually do not even know if information is encrypted. Of course, anyone knowing the password for your computer gets the same easy access. Consequently, encryption typically is only as strong as your login password, and login password practices tend to be poor.

## DIFFICULTIES IN FILE SHARING

Although encryption is very desirable, it makes sharing more difficult. Files usually have to be decrypted if they are moved to another computer. Using third-party encryption software (like AxCrypt or VeraCrypt) to encrypt files is more effort, but makes sending and sharing encrypted files much easier.

### Test Your Understanding

- 18.
  - a. Why is encryption usually attractive for sensitive data from a legal standpoint?
  - b. How long must an encryption key be to be considered strong today?
  - c. What happens if the encryption key is lost?
  - d. How do companies address this risk?
  - e. Why is entrusting users to do key escrow risky?
  - f. In what sense is encryption usually transparent to the user?
  - g. Why is this attractive?
  - h. Why is this dangerous?
  - i. What must users do to address this danger?
  - j. How does encryption make file sharing more difficult?

## 9.6 Data Loss Prevention

**9.6** **Describe how to prevent data loss, and how to securely delete data.**

Losing data is both damaging and embarrassing. For corporations, data loss can lead to lawsuits, a reduced customer base, lost intellectual property, and a direct loss of revenues. For these reasons, corporations are hesitant to admit that they have lost data. They often downplay the importance of the data or simply deny it was lost in the first place.

Data loss can be intentional (theft) or unintentional (carelessness). Internal employees and external attackers can both leak sensitive data. **Data loss prevention (DLP)** is a set of policies, procedures, and systems designed to prevent sensitive data from being released to unauthorized persons. Planning for DLP takes place as part of the overall corporate strategic planning process.

### Data Collection

Most corporations collect more data than they can adequately protect. Management and marketing types are interested in collecting as much data as they can. They believe it will help them make better decisions. Sometimes it does. However, gathering certain types of data, or too much data, can actually harm the corporation.

For example, a car dealership may ask you for your Social Security number (SSN) when applying for a car loan. They use your SSN to correctly identify your credit history. This is a reasonable use of your SSN. The question then becomes, Should the car dealer store your SSN? Whether it’s stored electronically or on paper, the car dealer can be held liable if the data is lost.

Will the stored data, the SSNs, lead to greater financial benefits? Or will the data loss lead to irate customers, loss of reputation, and a costly legal battle? Managers need to carefully weigh the costs and benefits of collecting certain types of data.

**PERSONALLY IDENTIFIABLE INFORMATION** One type of data that deserves special attention is **personally identifiable information (PII)**. This could include private employee information and private customer information that can be used to uniquely identify a person. In health care, PII must be protected by law. In general, the loss of PII can lead to credit card and identity theft. As a result, corporations with “deep pockets” are targets of lawsuits.

The National Institute of Standards and Technology (NIST) lists the following as PII.⁹

- *Name*, such as full name, maiden name, mother’s maiden name, or alias.
- *Personal identification number*, such as Social Security number (SSN), passport number, driver’s license number, taxpayer identification number, or financial account or credit card number.
- *Address information*, such as street address or e-mail address.
- *Personal characteristics*, including photographic image (especially of face or other identifying characteristic), fingerprints, handwriting, or other biometric data (e.g., retina scan, voice signature, or facial geometry).
- *Linking information*, information about an individual that is linked or linkable to one of the above (e.g., date of birth, place of birth, race, religion, weight, activities, geographical indicators, employment information, medical information, education information, or financial information).

### DATA MASKING

If possible, it’s better to not collect PII at all. It’s better to assign customers unique Customer IDs, rather than identifying them by SSN or other PII. If PII must be kept, there are alternative ways of storing PII. **Data masking** obscures data such that it cannot identify a specific person but remains practically useful.

### Test Your Understanding

- 19.
  - a. What is data loss prevention (DLP)?
  - b. Are there some types of data that are too risky to collect?
  - c. In your judgment, do most organizations adequately protect their data? Why?
  - d. What is PII? Please give a couple examples of PII.
  - e. What is data masking?

### Information Triangulation

Some of the PII categories listed earlier may seem harmless. It may be difficult to see how knowing a customer’s ZIP code could be harmful. Figure 9-33 shows how it is possible to combine two different data sets to gather more information about a person.

Professor Latanya Sweeney at Carnegie Mellon University combined data from a public voter list with seemingly anonymous medical data.¹⁰ She found that it was possible to correctly **re-identify** 87 percent of individuals using ZIP code, birth date, and sex. In other words, a person’s name from a public voter list could be associated with medical data through **linking attributes**.

Combining two pieces of information and then accurately inferring the value of the third is probably something you’ve done before in a geometry class. Figure 9-34 shows that the third angle (X°) in a triangle can be inferred from the other two angles (60°), as well as the name of the triangle.

⁹ Erika McCallister, Tim Grance, and Karen Scarfone, “Guide to Protecting the Confidentiality of Personally Identifiable Information (PII).” Special Publication 800-122, National Institute of Standards and Technology, U.S. Department of Commerce. April 2010. http://csrc.nist.gov/publications/nistpubs/800-122/sp800-122.pdf.

¹⁰ Latanya Sweeney, “k-anonymity: A Model for Protecting Privacy,” International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems, 10(5), 2002, pp. 557–570.
