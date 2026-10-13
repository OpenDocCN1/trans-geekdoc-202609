
# Recovering from Ransomware and Third-Party Data Breaches

## Ransomware Recovery Decisions

If you have been hit with ransomware and do not have proper backups, however, you may face a difficult decision. Obviously, it is not in the common interest for you to pay a ransom to a criminal in order to get your data back, but in some cases, if your data is important to you, that may be the route that you need to go. In many cases, criminals will not even give you your data back if you do pay the ransom — so, by paying a ransom, you may not only waste money, but still suffer a permanent loss of your data. You will need to decide if you want to take that chance. (Hopefully, the information in the preceding few sentences will serve as a strong motivator for readers to back up proactively as discussed in the chapter on backups, rather than to rely on paying ransoms as a possible method of addressing ransomware attacks.)

![Remember](images/remember.png) The best defense for home users against the impact of ransomware is to back up and keep the backups disconnected from anything else!

![Tip](images/tip.png) Before paying a ransom, consult an information security expert and a lawyer.

### Consult a cybersecurity expert

Speaking with the cybersecurity expert is important, because some ransomware can be removed, and its effects undone, by various security tools. However, unless your security software tells you that it can undo the encryption done by ransomware, do not try to remove ransomware on your own once it has encrypted your data. Some advanced ransomware wipes the data permanently if it detects attempts to decrypt the data. Also, keep in mind that some advanced ransomware does not encrypt data, but rather removes it from the victim's device and only transmits it back if the ransom is paid. Such ransomware may be removable by security software, but security software cannot usually restore the data pilfered by the ransomware.

### Consult a lawyer

Speaking with an attorney familiar with the relevant areas of law is important because, in some cases, paying a ransomware ransom can be a serious crime that could potentially land you in prison. Seriously!

While to date, the United States has not made it a crime to pay ransoms in general — although there are various ongoing efforts being made to influence legislators to enact such legislation — there are cases in which paying a ransom violates other laws.

For example, if criminals operating a particular ransomware system are under sanctions — meaning that it is a federal crime to conduct any financial transactions with them — it can be a felony to pay them a ransom in order to obtain access to your own data. While individuals have not, to date, been prosecuted by the U.S. government under such laws, at the end of the Trump administration's term, the federal government threatened to begin doing so, and regardless of who is in power, such enforcement is likely to become reality at some point in the not-so-distant future. After all, if sanctioned parties can easily become rich by perpetrating cybercrimes, and nobody is prosecuted for participating in the transactions that enrich them, what good are sanctions in the first place?

Likewise, eventually, we may see prosecution of ransom payers under federal statues related to wire fraud and/or money laundering.

![Tip](images/tip.png) While the FBI generally officially recommends against paying ransoms, it is not the party that suffers the consequences of losing data when ransoms are not paid — the ransomware victims are. As such, many parties ignore the FBI's advice. Should the law mandate that ransoms not be paid, the FBI's instructions could potentially change from advice to a legal requirement.

## Learning for the future

It is important to learn from breaches. If you can figure out what went wrong, and how a hacker managed to get into your systems (either directly or by using malware), you can institute de facto policies and procedures for yourself to prevent future such compromises. A cybersecurity professional may be able to help you vis-à-vis doing so.

## Recovering When Your Data Is Compromised at a Third Party

Nearly all Internet users have received notification from a business or government entity (or both) that personal data was potentially compromised. How you address such a scenario depends on many factors, but the following sections tell you the essentials of what you need to know.

### Reason the notice was sent

Multiple types of data breaches lead to organizations sending notifications. Not all of them represent the same level of risk to you, however. Notifications may be sent when a company has

*   Knowledge that an unencrypted database containing personal information was definitely stolen
*   Knowledge that an encrypted database containing personal information was definitely stolen
*   Detected unauthorized activity on a computing device housing your information
*   Detected unauthorized activity on a computing device, but not the one that houses your information (but on one connected to the same or logically connected network)
*   Detected the theft of credit or debit card numbers as can occur with a skimming device or the hacking of a point-of-sale credit card processing device
*   Discovered that there were, or may have been, improperly discarded computers, hard drives, or other storage media or paper-based information
*   Discovered that there was, or may have been, improperly distributed information, such as sensitive information sent to the wrong parties, unencrypted email sent to authorized parties, and so on

In all these cases, action may be warranted. But if a company notifies you that an unencrypted database of passwords including yours was stolen, the need to act is more urgent than if it detects unauthorized activity on a system on the same network as another machine containing only an encrypted version of your password.

### Scams

Criminals see when a breach receives significant attention and often leverage the breach for their own nefarious purposes. One common technique is for crooks to send bogus emails impersonating the breached party. Those emails contain instructions for setting up credit monitoring or filing a claim for monetary compensation for the pain and inconvenience suffered due to the breach. Of course, the links in such messages point to phishing sites, sites that install malware, and other destinations to which you do not want to go.

Criminals also act quickly. In February 2015, for example, Better Business Bureaus across the United States started reporting complaints of emails impersonating Anthem, Inc., less than one day after the health insurance company announced that it had suffered a breach.

### Passwords

One of the types of breaches most commonly reported in the mass media involves the theft of password databases. Modern password authentication systems are designed to provide some protection in case of a breach. Passwords are usually stored in a `hashed format`, meaning that they are stored with one-way encryption. When you enter your password during an attempt to log in, what you type is hashed and then compared with the relevant hash value stored in the password database. As such, your actual password is not stored anywhere and is not present in the password database. If a hacker steals a password database, therefore, the hacker does not immediately obtain your password.

At least that is how things are supposed to work.

In reality, however, not all authentication systems are implemented perfectly; hashed password databases have multiple exploitable weaknesses, some of which can help criminals decipher passwords even when they are hashed. For example, if a criminal looks at the database and sees that the hashed password for many people is the same, it is likely to be a common password (maybe even `password`), which often can be cracked quickly. There are defenses against such attacks, but many authentication systems do not use them.
