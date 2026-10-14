
## Figure 8-21 Google Cookie

![](img/073342643701cc54eb7875c41ab92ef2_418_0.png)

SOURCE: ©2018 Google LLC, used with permission.

## Test Your Understanding

- 12. a. Why do hackers attack browsers?
- b. What is mobile code?
- c. Why is it called mobile code?
- d. What is a client-side script?
- e. What is a Java applet?
- f. Why is Active-X dangerous?
- g. How do scripting languages compare to full programming languages?
- h. Is JavaScript a scripted form of Java?
- 13. a. Why is it bad to go to a malicious website?
- b. How can social engineering be used to trick a victim to go to a malicious website?
- c. Why do attackers want to get domain names such as microsoft.com?
- d. Why can malware that allows an attacker to execute a single command on a user’s computer not really be limited to executing a single command?
- e. What may happen on a compromised computer if a user mistypes the host name in a URL?
- f. What dangers do cookies create?

## Enhancing Browser Security

### CONFIGURATION
Stopping browser attacks also involves changing browser configuration settings to reduce the likelihood of damage. Unfortunately, different browsers do this differently.

### INTERNET OPTIONS
In Microsoft Internet Explorer (IE), users begin to change their settings by selecting Internet Options under the Tools menu. This opens the Internet Options dialog box, shown in Figure 8-22.

### SECURITY TAB
The dialog box shows its *Security* tab. From this tab, the user can select security settings for general Internet websites, intranet websites, trusted websites, and restricted websites. All websites are initially in the Internet category. However, the user can place them in other categories—intranet for internal company sites, trusted websites for highly trusted websites, and restricted websites for questionable websites.

The defaults in each category generally are good choices for security, but the user can also select the *Custom Level* button to change the settings for the four types of websites to control content more finely.

For instance, in the general Internet zone, signed Active-X controls (Active-X controls with digital signatures) by default execute after a prompt that identifies the creator of the Active-X control. Employees might not have sufficient knowledge to understand the danger of using even signed Active-X controls. In addition, active scripting is enabled by default, including Java scripting. These are at least somewhat risky choices.

### PRIVACY TAB
In addition to the Security tab, there is the *Privacy* tab. The Privacy tab, which is shown in Figure 8-23, allows the user to control what information is released to websites, including how cookies are used. IE has a sliding scale that the user can push up for greater privacy and down for reduced privacy. The default is medium privacy. An *Advanced* button allows more specific control over cookies.

The *Privacy* tab also controls the website’s pop-up blocker, which is on by default. Under the Settings button, the user can set different pop-up defaults for individual websites.

## Figure 8-22 Internet Options Dialog Box in Internet Explorer

![](img/073342643701cc54eb7875c41ab92ef2_419_0.png)

## Test Your Understanding

- 14.
- a. What can users do to enhance browser security?
- b. Under Internet Options in IE, what can the user do on the Security tab?
- c. What are your computer’s settings for the four zones?
- d. In which tab are cookies controlled?

## 8.4 E-Mail Security

### 8.4 Explain the process of securing e-mail.
We have been looking at WWW service/e-commerce security and browser security. Another big application on the Internet is **electronic mail (e-mail).**

## E-mail Content Filtering

Many firms now filter incoming e-mail messages (and sometimes outgoing messages) for dangerous or inappropriate content.

## Figure 8-23 Internet Explorer Privacy Tab

![](img/073342643701cc54eb7875c41ab92ef2_420_0.png)

### MALICIOUS CODE IN ATTACHMENTS AND HTML BODIES
As we saw in Chapter 1, e-mail attachments can contain viruses, worms, and other malicious code. In addition, now that many e-mail systems can show messages with HTML bodies, scripts in the bodies may execute malicious code, as we saw earlier in this chapter.

### SPAM
One of the most annoying aspects of e-mail is that most users are deluged by **spam**⁹—unsolicited commercial e-mail. Today, spam accounts for 60 to 90 percent of all Internet mail traffic on any given day. Spam clogs mailboxes, slows user computers, annoys users, and requires users to spend time deleting the unwanted messages.

In addition, many spammers now use **image spam**, which presents their message as a graphical image. This frustrates most content filtering. It also makes each spam message much larger, consuming even more bandwidth and disk storage space than traditional text spam.

### Filtering Spam
Given the large volume of spam today, most firms filter incoming e-mail to discard spam. However, firms that filter incoming spam sometimes find that they have **overfiltered** arriving e-mail. A growing number of legitimate messages are being rejected as spam, and few spam-filtering systems warn either the sender or the receiver if a message is rejected. Companies that filter spam should quarantine dropped messages to study them later and to address receiver and sender complaints about lost messages.

### Content Filtering
- Malicious code in attachments and HTML bodies (scripts)
- Spam: unsolicited commercial e-mail
- Volume is growing rapidly: slowing PCs and annoying users (porno and fraud)
- Filtering for spam also rejects some legitimate messages

### Inappropriate Content
- Companies often filter for sexually or racially harassing messages
- Could be sued for not doing so

### Extrusion Prevention for Intellectual Property (IP)

### Stopping the Transmission of Sensitive Personally Identifiable Information (PII)

### Where Do We Do E-mail Filtering? (Figure 8-25)
- At the user PC (users often turn off antivirus protection or make it ineffective)
- At corporate e-mail servers
- At e-mail managed service providers

### E-mail Encryption (Figure 8-28)

## Figure 8-24 E-mail Security (Study Figure)

## INAPPROPRIATE CONTENT

In some cases, employees send sexually or racially harassing or abusive e-mail to fellow workers. If the company does nothing to attempt to prevent this, it will be liable for lawsuits. Consequently, a growing number of firms scan all e-mail for indications of sexual, racial, or abusive content. Many have already fired employees for sending inappropriate e-mail.

## EXTRUSION PREVENTION

Filtering can also be done to prevent employees from sending intellectual property out of the corporation. **Extrusion prevention** filtering begins with a simple search through documents looking for words like “confidential.” In practice, it goes far beyond that.

## PERSONALLY IDENTIFIABLE INFORMATION

Another goal is to stop the sending of personally identifiable information (PII), such as private employee information and private customer information. In health care, PII must be protected by law. In general, the transmission of social security numbers and other sensitive personal information is likely to lead to lawsuits if it can potentially lead to credit card number theft or identity theft.

## Test Your Understanding

- 15. a. Why are HTML bodies in e-mail messages dangerous?
- b. What is spam?
- c. What three problems does spam create?
- d. Why is spam filtering dangerous?
- e. For what legal reason should companies filter sexually or racially harassing message content?
- f. What is extrusion prevention?
- g. Why is extrusion prevention needed for intellectual property?
- h. What is PII, and why must it be prevented from leaving the firm?

## Where to Do E-mail Malware and Spam Filtering

One issue that companies face is where to do e-mail malware and spam filtering. Traditionally, this filtering was done on client PCs, as Figure 8-25 shows. Client filtering has several problems. Users often turn off their antivirus and antispam filters. They frequently fail to set up their systems properly for automatic downloading. They may even fail to maintain their subscription for receiving updates. If they do any of these things, they still will have antivirus and antispam software on their systems but no protection against new attacks.

In light of problems with client-based filtering, most companies now use filtering at the corporate e-mail server as the primary line of defense for e-mail (see Figure 8-25). This relegates client filtering to secondary importance as a defense-in-depth measure. E-mail administrators have the discipline and knowledge needed to manage e-mail filtering. In fact, e-mail administrators usually spend most of their time on antivirus filtering, spam filtering, and other security issues.

Due to the labor burdens of e-mail security, some companies are moving filtering entirely out of the firm to e-mail managed service providers. Managed service providers reduce labor costs. They also have expertise in e-mail filtering.

Many companies filter at all three locations to increase defense in depth. At their corporate e-mail server, they may use a different filtering program than their managed service providers use. Different antivirus and antispam programs catch somewhat different threats.
