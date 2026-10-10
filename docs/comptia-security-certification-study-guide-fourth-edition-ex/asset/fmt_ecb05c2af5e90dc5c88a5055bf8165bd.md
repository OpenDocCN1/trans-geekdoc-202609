
Not only does the hacker risk being detected with online attacks, but typically the hacker does not have time to perform a full password attack online, so taking a copy of the account passwords offline and trying to crack them offline in the comfort of home is very beneficial to the hacker because there is no time constraint involved.

#### Other Password Attack Terms

When it comes to the world of password attacks, there are a number of terms you should be familiar with for the Security+ certification exam. The following are other password attack terms you should know:

- **Replay** A password replay attack is when the hacker eavesdrops on a conversation and captures the password hash being sent from a client system to the server. Once the hacker has the hash value, they then use that to impersonate the original client and access the server.

- **Weak implementation** Passwords can be encrypted to protect the plaintext value, but sometimes the encryption is not performed in the best way possible. For example, the Windows passwords are hashed in the SAM database, but they are broken into two seven-character hashes. This allows the hacker to determine very easily if someone has a password of fewer than eight characters because the last part of the password hash would be the same for all of those passwords.

#### Preventing Password Attacks

Understanding how to prevent password attacks in your environment is an important skill for any security professional.

To prevent dictionary attacks against your systems, you must implement a strong password policy and require users to use complex passwords. A `complex password` is a password that has a mix of uppercase and lowercase characters, and it uses numbers and symbols. You should also ensure that users are creating passwords that are at least eight characters in length.

Implementing password complexity will not protect your systems from brute-force attacks, so you must implement an account lockout policy to protect your systems from them. If you use an `account lockout policy`, after a certain number of bad logons, the account is locked out and cannot be used until the administrator unlocks it. Most companies implement an account lockout policy that locks an account after the third bad logon attempt. The account lockout policy takes the time away that is required to perform a brute-force attack; after the third bad logon attempt, the account is locked.

![Image](exam.jpg)

**For the Security+ certification exam, know that password complexity is the countermeasure to a dictionary attack, whereas an account lockout policy is a countermeasure to a brute-force attack.**

One thing to understand about your password policy and account lockout policy is that they do not have any effect if the hacker is performing an offline password attack. In an `offline password attack`, the hacker gets physical access to the system, copies the user account database to a flash drive, and takes the database away. The hacker then attacks from their own home, where you have no password policy or account lockout policy in place. After the hacker cracks the passwords, they can then gain access to the systems by using the usernames and passwords that have been discovered.

![Image](exam.jpg)

**An offline password attack is when the hacker copies the user account database from your system to a flash drive and takes it away with them in order to do the password cracking. In this example, the password attack will not be stopped because there is no password policy or account lockout policy at the hacker's location.**

The following are some popular password-auditing and -cracking tools:

- **LC4** A very popular password-auditing tool that can be used to access user passwords on a Microsoft network. It can do dictionary, brute-force, and hybrid attacks against the passwords.

- **Cain & Abel** A very functional password-cracking program. The benefit of Cain & Abel is it is a free download and can capture passwords on the network and crack those passwords with dictionary or brute-force attacks.

- **NAT** The NetBIOS Authentication Tool is a small program that allows you to do a dictionary attack against a Windows system.

- **Brutus** Brutus is unique in the sense that it can encapsulate the password attack through different Internet applications such as HTTP, FTP, POP3, and Telnet, to name a few.

- **John the Ripper** A very popular dictionary and brute-force cracker that runs on Windows or Linux.

### CERTIFICATION SUMMARY

In this chapter you learned about the different types of attacks that occur in computing environments today. Be sure to know these attacks for the Security+ exam. The following list summarizes what you learned about different types of attacks:

- Some different types of attacks include social engineering attacks, network attacks, password attacks, and application attacks.

- Social engineering attacks are attacks through social contact methods like the phone or e-mail, where the hacker tries to trick you into compromising security.

- Network attacks involve the hacker coming across the network and compromising a system. Examples of network attacks are sniffing, DoS, DDoS, and on-path attacks (formerly known as man-in-the-middle attacks).

- Three types of password attacks are a dictionary attack, which uses a word list file for passwords; a brute-force attack, which mathematically calculates all potential passwords; and a hybrid attack, which modifies the entries in the word list file.

- The best ways to protect your environment against social engineering attacks is to educate your users on social engineering and to train them on what to do if they receive such contact.

With a strong understanding of the material presented in this chapter, you will have no problems with any attack-related questions on your exam. Not only is the material presented here important for the exam, but it also will be worth gold in the real world, as it makes you more aware of the different attacks that can occur.

#### ✓ TWO-MINUTE DRILL

##### Understanding Social Engineering

![Image](boxsq.jpg) Social engineering attacks are when the hacker tries to trick you into compromising security through means of personal contact such as a phone call or e-mail message.

![Image](boxsq.jpg) Phishing is when a hacker tries to trick a person into divulging account information by leading them to a fake site that looks like the real one, such as a bank's web site or eBay.

![Image](boxsq.jpg) Dumpster diving is when the hacker goes through the garbage looking for information that can help in an attack.

![Image](boxsq.jpg) Tailgating is when a person walks through a secure area by closely following an authorized person who has unlocked the door using their swipe card or passcode. As a countermeasure to tailgating, your organization should implement a mantrap.

![Image](boxsq.jpg) User awareness and training are the only ways to prevent social engineering attacks.

##### Identifying Network Attacks

![Image](boxsq.jpg) A denial of service (DoS) attack is when the hacker causes a system to be unable to perform its job function by consuming the resources on the system, resulting in the system performing slowly or crashing. A distributed denial of service (DDoS) attack involves the hacker using multiple systems to perform the denial of service.

![Image](boxsq.jpg) Spoofing is when the hacker alters the source address to make the information appear as if it is coming from someone else. Examples of spoofing are IP spoofing, MAC spoofing, and e-mail spoofing.

![Image](boxsq.jpg) A sniffing attack is when the hacker uses a network sniffer to capture traffic to potentially view confidential information. Wireshark is an example of a network sniffer that is a free download from the Internet.
