
## Human Issues in Cryptography

With sufficiently long keys and a well-tested cipher, symmetric key encryption for confidentiality is impractical to crack from a technical standpoint. However, if the sender or receiver fails to keep the key secret, the eavesdropper may learn the key and read every message.

More broadly, poor communication discipline in general can defeat the strongest cipher and longest key. For example, during World War II, the Japanese Navy often sent messages when there was little need to do so. This gave Allied cryptologists a large base of messages to examine. This made the jobs of cryptanalysts much easier than if the Japanese had used better communication discipline. In addition, as noted earlier in this chapter, Japanese naval reports often began with a standard flowery introduction that was several sentences long. This “known plaintext” situation was invaluable in cracking Japanese codebooks. Also helpful was the fact that transmissions often followed a set format for common types of situations such as reporting a ship’s speed and compass bearing.

Sending encrypted e-mail using HTTPS results in a slightly slower overall connection speed compared to an HTTP (non-encrypted) connection. However, using SSL to encrypt the transfer of e-mail messages would stop man-in-the-middle attacks. HTTPS is now default for all web-based e-mail services.

Communicating partners can even have a false sense of security because they will think that the cracked encryption method is still protecting them. In World War II, the Germans had an encryption machine called Enigma, which was very advanced technically. However, the Polish military captured a copy of the machine and reverse-engineered it to reveal how it worked. After Poland fell to Germany, the Poles passed their results to the English, who continued the work. Eventually, the English could read a large percentage of German messages encrypted with Enigma. The overconfident Germans sent vast amounts of very sensitive traffic thinking that they were completely safe.

The reality of cryptography is that it is not an automatic protection. It only works if companies have and enforce organizational processes that do not compromise the technical strengths of cryptography.

## Test Your Understanding

9. Why is cryptography not an automatic protection?

## In the News

### No More Crypto

In 2019 the newly appointed Secretary of State for the Home Department in the UK, Priti Patel, said she wanted to see backdoor access inserted into all end-to-end encryption systems to make it easier for law enforcement to view user data and communications. This would effectively end end-to-end encryption and diminish privacy within the UK. Patel is quoted as saying, “Where systems are deliberately designed using end-to-end encryption, which prevents any form of access to content, no matter what crimes that may enable, we must act.”

### Encrypted Voting

In 2019 Microsoft demonstrated its new secure voting system named ElectionGuard. The new electronic voting system gives voters the option of voting electronically or having their ballot printed out on paper.^9^ It also gives voters a tracking code that lets them go online and verify that their vote has been counted without revealing their specific ballot choices. Microsoft posted the source code for its ElectionGuard system on GitHub for anyone to review, and Microsoft said it will make the code open source for anyone to use. Consumers regularly use online systems for banking, viewing medical records, paying bills, and buying nearly everything. Secure electronic voting may be next.

### WhatsApp Backdoor

In 2017 it was discovered that a backdoor had been placed in WhatsApp that allows hackers or WhatsApp itself to intercept and view encrypted messages.^10^ In 2016 WhatsApp turned on end-to-end encryption for all 1 billion users by default. This was a great relief to users who were concerned that their private messages were being viewed. However, this new security flaw was seen by some as a “feature” that allowed for a more user-friendly experience. Others saw WhatsApp’s implementation of the end-to-end security protocol as weakening user’s privacy.

### Self-Encrypting SSDs

In 2018 two researchers from the Netherlands, Carlo Meijer and Bernard van Gastel, found vulnerabilities in the firmware of several popular self-encrypting SSD drives that would allow attackers to bypass all cryptographic protections.^11^ Attackers could then gain direct access to user data without knowing the user’s password or encryption key. These vulnerabilities were found in drives made by Samsung and Crucial, but the researchers warn that devices made by other manufacturers could contain similar vulnerabilities. It’s important to know about potential cryptographic vulnerabilities so users aren’t given a false sense of security and lose confidential data.

### The Death of Encryption

In 2019 Facebook announced its plans to push “content moderation” out to users’ devices. This would essentially allow Facebook and its subsidiaries WhatsApp and Instagram to scan user content before it’s even transmitted.^12^ End-to-end encryption would only provide protection between users. But the endpoints, where the messages are created and read, would be continually scanned. The cryptographic protections promised by end-to-end encryption would be defeated by these new on-device content scanning applications. Users can protect themselves by removing Facebook’s apps from their devices. But what happens if hardware manufacturers push out their own “content moderation” applications?

9. Tim Anderson, “Microsoft Demos End-to-End Voting Verification System ElectionGuard, Code Will Be on GitHub,” *The Register*, July 15, 2019. https://www.theregister.co.uk/2019/07/18/microsoft_demos_electionguard_system_will_publish_code_on_github.

10. Mohit Kumar, “WhatsApp Backdoor Allows Hackers to Intercept and Read Your Encrypted Messages,” *The Hacker News*, January 13, 2017. https://thehackernews.com/2017/01/whatsapp-encryption-backdoor.html.

11. Swati Khandelwal, “Flaws in Popular Self-Encrypting SSDs Let Attackers Decrypt Data,” *The Hacker News*, November 6, 2018. https://thehackernews.com/2018/11/self-encrypting-ssd-hacking.html.

12. Kalev Leetaru, “The Encryption Debate Is Over—Dead at the Hands of Facebook,” *Forbes*, July 26, 2019. https://www.forbes.com/sites/kalevleetaru/2019/07/26/the-encryption-debate-is-over-dead-at-the-hands-of-facebook.

## 3.2 Symmetric Key Encryption Ciphers

**3.2** **Describe symmetric key encryption and the importance of key length.**

When using symmetric key encryption, you can choose from a variety of ciphers. They all accomplish the ultimate goal of producing an encrypted message. However, they function very differently and vary in strength, speed, and computing requirements. Communication partners must choose a specific symmetric key encryption cipher if they wish to communicate securely. Only a few common symmetric key encryption ciphers have been well tested, and it is important to select from these few. We will look at the most common well-tested ciphers: RC4, DES, 3DES, and AES. Figure 3-6 compares these ciphers.

### RC4

The weakest cipher in common use today is RC4, which is usually pronounced as “ARK FOUR.” RC4 has two advantages over other popular encryption algorithms.

First, RC4 is extremely fast and uses only a small amount of RAM.¹³ This means that it is ideal for small handheld devices and was viable for even the earliest 802.11 wireless access points. Consequently, RC4 became the basis for the notorious WEP encryption system for wireless LANs, which we will see in Chapter 4.

Second, RC4 can use a broad range of key lengths. For most ciphers, longer key length is better. However, RC4 was widely used primarily because its shortest optional key length is 40 bits. As noted earlier in this chapter, national export restrictions in many countries once limited commercial products to 40-bit encryption. Consequently, 40-bit RC4 became the standard key length for WEP.

Unfortunately, RC4 is a dangerous cipher to use. If it is not implemented correctly, its protection is minimal. Poor RC4 implementation is what made WEP such a weak protection system for wireless LANs.

### Test Your Understanding

10.
  a. What are the two advantages of RC4?
  b. Why is an RC4 key length of 40 bits commonly used?
  c. Is this a strong key?

|  | RC4 | DES | 3DES | AES |
|---|---|---|---|---|
| Key length (bits) | 40 bits or more | 56 | 112 or 168 | 128, 192, or 256 |
| Key strength | Very weak at 40 bits | Weak | Strong | Strong |
| Processing requirements | Low | Moderate | High | Low |
| RAM requirements | Low | Moderate | Moderate | Low |
| Remarks | Can use keys of variable lengths | Created in the 1970s | Applies DES three times with two or three keys | Today’s gold standard, likely to be dominant in the future |

**Figure 3-6** Major Symmetric Key Encryption Ciphers

¹³ One way to see why RC4 is fast is to note that RC4 can be implemented in only about 50 lines of code. By contrast, the gold-standard AES algorithm requires 350 lines of code (*www.informit.com*). More lines of code generally correspond to longer processing time per key.
