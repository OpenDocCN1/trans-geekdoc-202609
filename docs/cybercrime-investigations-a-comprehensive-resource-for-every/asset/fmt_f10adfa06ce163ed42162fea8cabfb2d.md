
## 4.2.1 Information Security Objectives: The CIA Triad

Information security centers around three basic objectives for protecting information assets: confidentiality, integrity, and availability. Configuring information systems often requires compromises among these three objectives. When investigating a cybercrime, or defending against a cyberattack, distinguishing which objective is implicated can be a useful place to start.

*Confidentiality* means ensuring the secrecy of information that is meant to remain private, and ensuring that only authorized individuals can access it. A cybercriminal who breaches a company’s network and steals data has violated the confidentiality that it was supposed to have. Similarly, an individual who steals a victim’s password and accesses her email has violated the confidentiality of her account.

*Integrity* means ensuring that information cannot be altered or tampered with by unauthorized parties. An employee who changes the company’s financial data to give himself a bonus or hide a theft has violated the integrity of the data. Integrity compromises also might include a cyber intruder breaching a website and defacing it, or breaching an email system and sending emails as if he were the rightful account owner.

*Availability* means ensuring that systems and information are available for use by those who need them and are authorized to use them, such as employees, customers, and account holders. Long before cybercrime, businesses worked to anticipate the effects of floods and fires to ensure they would not shut down information systems for too long or cause paper records to be destroyed. With cybercrime, malicious actors might impair the availability of information by attacking websites to render them inaccessible for users, or by using ransomware to encrypt a victim’s data.

### 4.2.2 Controls to Protect Information Systems

In order to ensure these three objectives, various control measures need to be applied to systems, data, and people. These controls usually are broken into three different types: administrative, technical, and physical. In a cyberattack, investigators might consider which controls were circumvented, or should have been in place but were not.

An *administrative control* is a management tool, such as a policy, procedure, governance structure, or training. For example, a company may require employees to attend trainings on securing their devices and accounts, or may have a written policy that states only select employees can access sensitive data. If a cybercrime occurs, the investigation may review governance documents setting forth these controls to determine whether they are reasonable, and whether the company ensured compliance with them. Organizations of larger sizes require a more mature security posture, including greater documentation. Inaccurate or inadequate documentation by the organization can play a role in determining root causes of a successful cyberattack and who is liable for any damage.

A *technical control* is a rule in software or hardware that works to protect information and prevent unauthorized access. For example, there may be a technical control that requires passwords to be at least ten characters long, and of sufficient complexity, and will not allow a user to create a simpler or shorter password. Firewalls (software or hardware barriers that monitor and regulate contact with the Internet and other networks), intrusion detection systems, encryption, and access control software are also examples of technical controls.

*Physical controls* protect the physical locations where information and systems are accessible. Such controls include doors, locks, fencing, lighting, security alarms, and security guards. Physical security is essential for information security. If you lose or damage your laptop or smartphone, you create opportunities for unauthorized access to your data and information systems. If an attacker gains physical access to a computing device, router, switch, or cabling, the attacker may be able to obtain data contained within or passing through these forms of hardware.

Administrative, technical, and physical controls can protect one or more of the “CIA” objectives.

### 4.2.3 Authentication to Guard Access (*Who Are You Anyway?*)

Authentication is a technical control that enforces administrative rules about access to data. It is one of the most widely used information security methods and a familiar one to most users. An authentication process verifies that a user of a computer system is who she purports to be, and is authorized to access certain resources. Every time we log into a computer system, or into our email or other cloud accounts, we go through an authentication process.

There are three main “factors” used to authenticate users of information systems:

*   Something you *know*, such as a password
*   Something you *have*, such as a smartphone, key fob, or other token
*   Something you *are*, such as a fingerprint pattern, retinal pattern, or facial features.

Some information security systems rely on just one of these factors, while others use a combination of factors for authentication.

Passwords, although the most common authentication factor, have many vulnerabilities, and can be compromised through a number of techniques. Where information systems are available through the Internet – to anyone with an Internet connection – a password alone may be inadequate to provide reasonable security. A second factor of authentication may be required. When a system requires two or more factors of authentication to authenticate a user, this method is called two-factor authentication or multi-factor authentication (2FA, MFA as depicted in [Figure 4.2](#chapter04.xhtml#fig4_2)). Of course, no security measure is impenetrable and cybercrime techniques continually evolve to beat enhanced authentication security.

![Figure 4.2 Prove Who You Are: Multi-Factor Authentication.](images/fig4_2.jpg)

**Figure 4.2** Prove Who You Are: Multi-Factor Authentication.

#### Two-Factor Authentication Lawsuit

Two-factor authentication is not foolproof. Consider the example of Michael Terpin, a cryptocurrency enthusiast who secured his virtual currency account using two-factor authentication (a password plus a SMS text message to his cellular phone). His cellular service was supplied by AT&T.

Cybercriminals targeted Terpin, learned his cell phone number, and – with the help of a low-level AT&T employee – gained control of his cellphone account. The criminals then were able to take over Terpin’s cryptocurrency account by changing its password. When the cryptocurrency sought to verify the change by sending a text to Terpin’s cellphone, the criminals were able to confirm the change as if they were Terpin. Within a short time, they stole nearly $24 million in cryptocurrency funds from the account.

Terpin sued AT&T in the U.S. District Court for the District of California in Los Angeles for $224 million, a figure representing his lost funds plus $200 million in punitive damages for failing to safeguard his cellphone account.^()

### 4.2.4 Principle of Least Privilege (*You Don’t Need to Know That or Do That, So I’m Not Letting You*)

The principle of “least privilege” is an information security principle along the lines of “need to know”. If you do not need access to information or systems, then you should not have it. If you do not need the ability to perform certain functions, you should not have it, as depicted in [Figure 4.3](#chapter04.xhtml#fig4_3).

![Figure 4.3 Principle of Least Privilege.](images/fig4_3.jpg)

**Figure 4.3** Principle of Least Privilege.
