
# Chapter 1: Phishing Attacks

Phishing is a social engineering attack. In most cases, it is used to access and steal user data such as credit card numbers and login credentials. This kind of attack occurs when an intruder masquerades as a trusted party and deceives the victim into opening a text message, instant message, or email. Next, the victim is duped into clicking a link which allows the attacker to freeze the system or install malware. This kind of attack can be damaging and may lead to identity theft, stealing of funds, and unauthorized purchases. In governmental or corporate networks, phishing grants the intruder a foothold and opens the door for a larger attack like an APT (advanced persistent threat). In an APT, the organization can suffer substantial financial losses among many other damages.

Phishing attack examples can be emails like for example `myuniversity.edu` which may be sent out to faculty members. The email tells the recipient that their user password is going to expire in a short time. Instructions will be included, guiding the user to go to `myuniversity.edu/renewal` so they can renew their password. When the recipient clicks the link, a few things may happen:

*   They may be redirected to a bogus page, `myuniversity.edurenewal.com`, which is very similar to the actual renewal page. The user is asked to enter the old and new password. The attacker monitors the page and gets the original password which will give them access to the university network.
*   The link may redirect the user to the real password renewal page. During the redirection process, the infiltrator activates a malicious script in the background, hijacking the session cookie of the user. The result is a reflected XSS attack that gives the attacker access to privileged information.

Email phishing scams are a numbers game. The fraudulent message is sent to a huge number of recipients, so even if only a small percentage of the recipients fall for this scam, the attacker will still gather a lot of information. Intruders have techniques to give them high success rates. They make sure the phishing message looks a lot like an actual email from the targeted information. They create a sense of urgency to push the recipients into action. The links included in the messages look like the legitimate links.

Spear phishing is not aimed at random people; it targets a specific enterprise or person. It is an advanced version of phishing and special knowledge about the organization is required. When an attacker gets valid login credentials, they may successfully carry out a first stage APT.

To protect an organization from phishing attacks, both the enterprise and users need to take precautionary measures:

*   **Users need to be vigilant.** Any spoofed message has little mistakes that will expose it.
*   **Enterprises should follow several steps to reduce both spear phishing and phishing attacks:**
    *   Establish a two-factor authentication (2FA). This method requires an extra step of verification from users when they are accessing sensitive information.
    *   In addition to 2FA, companies should have strict password management policies. Employees should change their passwords regularly and use different passwords for different applications.
    *   The enterprise should organize educational campaigns.

---

# Chapter 2: Advanced Persistent Threat (APT)

An APT is a broad term. It describes an attack campaign by an intruder, where they establish a malicious, long-term presence on a network with the aim of mining sensitive data. The intruder or team of intruders carefully search and pick their targets, usually government networks or large corporations. These intrusions can cause a lot of damage, including:

*   Theft of intellectual property
*   Compromise of sensitive information
*   Total takeover of sites
*   Sabotaging of critical infrastructure

APT attacks are a little different from traditional web application attacks in that:

*   They are executed manually
*   They are way more complex
*   They are never hit-and-run attacks
*   Their goal is usually to penetrate an entire network

## APT Progression

A successful advanced persistent threat happens in three stages:

1.  **Infiltration:** In most cases, enterprises are infiltrated via the compromising of one of the following: authorized human users, network resources, or web assets. This can be achieved through social engineering attacks such as spear phishing or malicious uploads such as SQL injection. Moreover, intruders can execute a DDoS attack simultaneously against the target. This distracts the network personnel and weakens the security perimeter. As soon as the initial access has been achieved, the infiltrators install a backdoor shell. This malware gives them network access and remote control.
2.  **Expansion:** Once they have established a foothold, they spread their presence. They move up the hierarchy of the organization and compromise staff members by accessing very sensitive data. In this process, they gather the business’ critical information such as financial records, employee data and product line information. They can sell this information to competitors or sabotage the product line and destroy the company.
3.  **Extraction:** During the APT event, the thieves store the stolen data somewhere within the network they are assaulting, in a secure place. After they have collected enough data, they extract it quietly without being noticed. Your security team is distracted using white noises as the information is being extracted.

## Mitigation Strategies

*   The best way to block the extraction of stolen data and prevent the installation of backdoors is monitoring egress and ingress traffic. Make a habit of inspecting traffic in your network perimeter so any unusual behavior does not go unnoticed.
*   Deploy a web application firewall on your network perimeter to help filter the traffic being driven to your web application servers. Network firewalls and other internal traffic monitoring services can also help.
*   Whitelisting controls the domains that are accessible from your network and the applications that users can install. It reduces the attack surfaces that are available to intruders. This security measure is not foolproof. To make it more effective, always have strict updated policies so that your users run updated versions of your applications.
*   Your employees are the largest and the most susceptible soft-spot. There are three categories of targets:
    *   Careless users
    *   Malicious insiders
    *   Compromised users
*   Carefully review all your employees and the information that they have access to.
*   Always patch any OS and software network vulnerabilities as soon as they are uncovered.
*   Encrypt remote connections so that intruders do not use them to access your network.
*   Filter incoming emails. This prevents phishing attacks and spam.
*   Log security events immediately to improve whitelists and any other policies.

---

# Chapter 3: Penetration Testing
