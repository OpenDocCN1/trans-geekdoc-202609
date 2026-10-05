
## Chapter 1 Logon Problems 21

across the Internet. Lots of people have the same weird hobby. After you do it a few times, you're going to get very bored because the most popular passwords from three decades ago are still the most popular passwords today. They are passwords containing the word password, easy key combinations on the keyboard, and common names of people. Most organizations have employees with passwords from a list of the most common passwords.

## Malware Password Guessing

Many malware programs contain password-guessing routines, when they encounter an authentication login—say to a website, remote login service (e.g., RDP, SSH), or network drive share—will try many common passwords. Several malware programs will try a hundred or more passwords and will be successful in guessing the password.

> NOTE Automated guessing malware programs are also notorious for locking up blocks of user accounts because the company network they are attacking has account lockout feature enabled. The password guessing malware program is coded to guess a hundred or more different passwords, but they end up locking out the user account after three to five guesses. Times, the first sign of a password guessing malware program running on a network is nearly everyone's account being locked out at the same time unexpectedly. Luckily, at Windows computers a true Administrator account cannot be locked out, so it can be used to get back into the network, eradicate the malware program, and unlock everyone's account. Unfortunately, because it cannot be locked out, it is also a favorite target of password guessing malware programs and hackers.

## Password Spray Attacks

"Password spray" (or "credential stuffing") attacks are very, very popular these days. A typical automated password guessing attack will try to guess a thousand or ten thousand passwords against one known identity account. If a company enables account lockout or monitors failed logins, they might be alerted to a traditional password guessing attack. A password spray attack tries a thousand or ten thousand guesses, one at a time, slowly, never fast enough to make the account lockout protection feature kick in, against every identity they can find. So instead of trying to password guess against one account or ten thousand identities, they guess a handful of times against a thousand or ten thousand identity accounts.

Password spray attacks have been highly successful. Both Google and Microsoft consider them one of the biggest threats against authentication systems. In September 2019, Akami reported that they saw 61 billion password spray attacks in just 18 months on the servers and services they monitor (www.cbronline.com/news/credential-stuffing-attempts-akami). Within these were plenty of successful attacks.

## Hacking Multifactor Authentication

Performing a password spray attack involves the following steps:

1. The attacker decides on a target.
2. The attacker uses OSINT tools to collect as many login names as they can find and places them into a single file.
3. The attacker finds an accessible online victim login portal (e.g., Outlook for Web Access, Gmail, Remote Desktop Protocol, Cisco VPN, Microsoft Active Directory Federated Services) that they can access.
4. The attacker determines the victim's account lockout policy.
5. The attacker downloads a password spray dictionary.
6. The attacker downloads a password spray attack tool.
7. The attacker loads the target's login portal location in the tool, loads the password dictionary, loads the identity list, and executes the tool.
8. The password spray tool starts the credential stuffing attack and notifies hacker of any successful logins.

There are many password spray tools available for free on the Internet. Figure 1.6 shows one of those, spray, in action, with its command-line inputs shown:

```
spray.sh <targetIP> <username> <passwordList> <AttemptsPerLockoutPeriod> <LockoutPeriodInMinutes> <DOMAIN>
```

![](img/c78b0f79db62998ee317a35df5629d85_49_0.png)

**Figure 1.6:** Spray password guessing tool

In addition to password guessing hackers and hacking tools, there is a myriad of automated malware that spends its time guessing and stealing passwords. For decades they have been worms that included the ability to guess at user passwords. They break into one node on a network and spread them by guessing at login prompts, often having up to one hundred passwords in their repertoire.

These days password guessing against Microsoft's Remote Desktop Protocol (RDP) implementations is popular. RDP is often enabled on Microsoft Windows computers and servers, and attackers using remote password guessing attack tools are common. In one study (nakedsecurity.sophos.com/2019/07/17/rdp-exposed-the-wolves-already-at-your-door), the researchers set up 10 RDP "honeypot" computers to study how long it would take for them to be discovered and guessed and how many password guesses would be taken. The first honeypot was discovered in less than 2 minutes; they averaged over 110,000 guesses a day and had more than 4 million guesses taken in a month. Wow! The team of rampant guessing happens against Linux-Secure Shell (SSH) remote login portals.

## Password Hash Cracking

Password hashes are nearly as valuable as the plaintext passwords they represent. Hackers can often use in future authentication attacks that take advantage of processes and applications that will accept the hashes as valid or otherwise typed-in plaintext password, or they can "crack" the password hash back to its plaintext equivalent. The former types of attacks, where the obtained hash is used in further attacks, are often known as pass-the-hash (PtH) attacks. They’ve been around for decades and are most popular on Microsoft Windows systems. However, the actual plaintext password is even better, because it can be used directly to log on authentication portals that accept only plaintext passwords. Many attackers, if they gain access to only the password, will convert many of them as possible to their plaintext equivalents. Password attacks still rule!

Obtaining the password hash in the first places can take another first-order root cause exploit. The attacker not only must break in a computer’s normal defenses but must usually obtain privileges if they are to be successful in getting the hashes. Sometimes the initial root exploit gets the attack elevated access from the start, and other times they must initiate a second privilege escalation exploit. The harder part is obtaining the initial access. Once inside an exploited computer, gaining privileged access, if not obtained immediately, is easier to accomplish.

If an attacker can gain local administrator access on a Microsoft Windows computer, they can use one of a dozen or more free hackers to obtain available hashes. These tools include Pdump, Mimikatz, Metasploit, and the Empire PowerShell Toolkit, in increasing order of popularity. These tools require at least admin access on the Windows computer; the attacker then has to install a second door or software that operates at the system level (which is higher than admin) to get the hashes. Getting hashes from a Microsoft Directory domain controller—where all the hashes of all networked user and computer accounts are stored—requires a domain account to accomplish. Apparently, gaining this level of access is not too hard because the Windows password hashes is among the most common successful attack outcomes there is in the computer world for corporate hackers.

## Network Eavesdropping

If an attacker can insert themselves and eavesdrop on a network authentication session, they can usually capture any typed-in plaintext passwords, hashes, or challenge-response sessions. If sides and transactions of a challenge-response session can be viewed, they usually can be converted back to the involved password hash and eventually to the underlying plaintext password.

## 24 Hacking Multifactor Authentication

A challenge-response session makes it harder for an attacker, because they can't "sniff" the network and get a plaintext response right away. With a complete challenge-response session, the only unknown variable between the challenge and response is the password hash. So, if an attacker can get both sides, the involved password hash can be easily computed.

## Email Hash Theft Trick

It's also possible to steal passwords remotely one at a time in some uncommon edge cases. For example, one very interesting method involves sending a phishing attack to an intended victim. The email contains an embedded Universal Name Convention (UNC) file moniker, file://URL. Emails usually connect to Uniform Resource Locator (URL) links. The fact that the email contains a file moniker, which is normally associated with NetBIOS connections, confuses many email clients, and they can be tricked into connecting to any remote (often malicious) server and resource.

The email or browser client, if it supports Windows Authentication (Windows, Mac and Linux clients do), will automatically, unbek to most users, authenticate with the server. The client will participate in a challenge-response NTLM authentication session, and from that a rogue server can drive the user's password hash. Here is a great discussion on the overall technique: securify.in/blog/SFY20180501/living-off-the-land-stealing-netntl-hashes.html.

To summarize, an attacker can send an email that the victim simply opens, or most clicks on the embedded link, and the remote attacker gets the victim's password hash, which they then convert to a plaintext response. Infamous hacker, boss, and my friend, Kevin Mitnick, has a YouTube video demonstrating this attack method: blog.knowbe4.com/kevin-mitnick-demos-password-hack-no-link-click-or-attachments-memory.

> NOTE Kevin's video he demonstrates "previewing" the email is to kick off the connection to the embedded UNC/URL link resource, but most of the time users will be tricked into clicking the embedded link (i.e., the connection doesn't initiate automatically).

Without converting the hash to its plaintext equivalent, there is lot a hacker can do. The attacker can create additional logon sessions, log on remotely to access RDS sessions, manipulate group memberships, connect to network drives and resources, and even create brand-new, temporary, rogue domain controllers (look up "golden ticket" attacks—they are vicious). In most operating
