
`A locked file cabinet or office safe` -> `一个锁着的文件柜或办公室保险箱`

`A disk secured with full (whole) disk encryption, which can prevent an intruder from accessing the operating system and passwords stored on the system. (Just know that this technique isn’t foolproof, as I outline in [Chapter 11](#c11.xhtml).)` -> `一张使用全盘加密（完整磁盘加密）的磁盘，它可以防止入侵者访问系统上的操作系统和存储的密码。（只需知道，这种技术并非万无一失，如我在 [第11章](#c11.xhtml)中所述。）`

`A secure password management tool such as LastPass ([https://www.lastpass.com](https://www.lastpass.com)) or the open-source program Password Safe ([https://pwsafe.org](https://pwsafe.org))` -> `一个安全的密码管理工具，如 LastPass（https://www.lastpass.com）或开源程序 Password Safe（https://pwsafe.org）。`

`Again, as I mention earlier, applications such as these aren’t impervious to attack, so be careful.` -> `再次提醒，像这些应用程序并非对攻击免疫，所以请小心。`

![warning](images/warning.png)Don’t write passwords on sticky notes! People joke about this practice, but it *still* happens a lot, and it’s not good for business! -> ![warning](images/warning.png)不要把密码写在便签纸上！虽然人们嘲笑这种做法，但它*仍然*经常发生，而且对商业不利！

### Creating password policies

As an IT or security professional, you should show users the importance of securing their passwords. Here are some tips on how to do that:

*   Demonstrate how to create secure passwords. Refer to passwords as *passphrases,* because people tend to take *passwords* literally and use only words, which can be less secure. -> *演示如何创建安全的密码。将密码称为*passphrases*，因为人们倾向于字面理解*passwords*，只使用单词，这可能安全性较低。*

*   Show what can happen when weak passwords are used or passwords are shared. -> *展示使用弱密码或共享密码可能带来的后果。*

*   Diligently build user awareness of social engineering attacks. -> *认真建立用户对社交工程攻击的认识。*

Enforce (or at least encourage the use of) a strong password-creation policy that includes the following criteria:

*   **Use uppercase and lowercase letters, special characters, and numbers.** Never use only numbers. Such passwords can be cracked quickly. -> **使用大写和小写字母、特殊字符和数字。** 切勿只使用数字。这类密码可以被快速破解。

*   **Misspell words or create acronyms from a quote or a sentence.** *ASCII*, for example, is an acronym for *American Standard Code for Information Interchange* that can be used as part of a password. -> **拼写错误单词或从引语或句子中创建缩写。** 例如，*ASCII* 是 *American Standard Code for Information Interchange* 的缩写，可以作为密码的一部分。

*   **Use punctuation characters to separate words or acronyms.** -> **使用标点符号分隔单词或缩写。**

*   **Change passwords every 6 to 12 months or immediately if they’re suspected of being compromised.** Any change more frequent introduces an inconvenience that serves only to create more vulnerabilities. -> **每6到12个月更改一次密码，或在怀疑其被破坏时立即更改。** 更频繁的更改只会带来不便，并增加漏洞。

*   **Use different passwords for each system.** This practice is especially important for network infrastructure hosts, such as servers, firewalls, and routers. It’s okay to use similar passwords; just make them slightly different for each type of system, such as *SummerInTheSouth-Win10* for Windows systems and *Linux*+*SummerInTheSouth* for Linux systems. -> **为每个系统使用不同的密码。** 这对于网络基础设施主机（如服务器、防火墙和路由器）尤其重要。可以使用相似的密码，但要略微调整以适应不同类型的系统，例如 *SummerInTheSouth-Win10* 用于 Windows 系统，*Linux*+*SummerInTheSouth* 用于 Linux 系统。

*   **Use variable-length passwords.** This trick can throw off attackers because they won’t know the required minimum or maximum length of passwords and must try all password-length combinations. -> **使用可变长度密码。** 这种技巧可以让攻击者困惑，因为他们不知道密码的最小或最大长度，必须尝试所有可能的长度组合。

*   **Don’t use common slang words or words that are in a dictionary.** -> **不要使用常见的俚语或词典中的单词。**

*   **Don’t rely completely on similar-looking characters, such as *3* instead of *E, 5* instead of *S,* or *!* instead of *1.*** Password-cracking programs and dictionaries are available to help check for this practice. -> **不要完全依赖外观相似的字符，例如 *3* 代替 *E, 5* 代替 *S,* 或 *!* 代替 *1.*** 密码破解程序和词典可用于检查此类做法。

*   **Don’t reuse the same password within at least four to five password changes.** -> **不要在至少四到五次密码更改内重复使用同一密码。**

*   **Use password-protected screen savers.** Unlocked screens are a great way for systems to be compromised. You could have the strongest passwords and best full disk encryption in the world, but none of that matters if the computer is left unattended with the screen unlocked. -> **使用密码保护的屏幕保护程序。** 未锁定的屏幕是系统被入侵的常见方式。即使你拥有最强的密码和最佳的全盘加密，如果电脑未锁定而离开，这些也都无济于事。

*   **Don’t share passwords.** To each his or her own! -> **不要共享密码。** 各自为政！

*   **Avoid storing user passwords in an unsecured central location, such as an unprotected spreadsheet on a hard drive.** This practice is an invitation to disaster. Use a password manager to store user passwords if you’re willing to do so. (I’m not yet.) -> **避免在不安全的中央位置（如未受保护的硬盘上的电子表格）存储用户密码。** 如果你愿意，可以使用密码管理器来存储用户密码。（我暂时还不做。）

### Taking other countermeasures

Here are some other password hacking countermeasures that I recommend:

*   **Enable security auditing to help monitor and track password attacks.** You can’t possibly manage this part of your security program if you’re not looking out for attacks. -> **启用安全审计，以帮助监控和跟踪密码攻击。** 如果你不主动关注攻击，就无法管理安全程序的这一部分。

*   **Test your applications to make sure they aren’t storing passwords indefinitely in memory or writing them to disk.** A good tool for this is WinHex ([`www.winhex.com/winhex/index-m.html`](http://www.winhex.com/winhex/index-m.html)). I’ve used this tool to search a computer’s memory for keywords such as password, pass=,* login, and so on, and have come up with some passwords that the developers thought were cleared from memory. -> **测试你的应用程序，确保它们没有在内存中无限期存储密码或将其写入磁盘。** WinHex（http://www.winhex.com/winhex/index-m.html）是一个良好的工具。我曾使用该工具在计算机内存中搜索诸如 password、pass=、* login 等关键词，并找到了开发者认为已被清除的密码。

    ![tip](images/tip.png)Some password-cracking Trojan-horse applications are transmitted through worms or simple email attachments. Such malware can be lethal to your password-protection mechanisms if they’re installed on your systems. The best defense is malware protection or whitelisting software from Webroot, McAfee, or Bit9. -> ![tip](images/tip.png)一些密码破解特洛伊木马应用程序通过蠕虫或简单的电子邮件附件传播。如果它们安装在你的系统上，这些恶意软件可能会破坏你的密码保护机制。最佳防御是使用 Webroot、McAfee 或 Bit9 的恶意软件防护或白名单软件。

*   **Keep your systems patched.** Passwords are reset or compromised during buffer overflows or other denial of service (DoS) conditions. -> **保持系统补丁更新。** 在缓冲区溢出或其他拒绝服务（DoS）条件下，密码可能被重置或被破坏。

*   **Know your user IDs.** If an account has never been used, delete or disable the account until it’s needed. You can determine unused accounts by manual inspection or by using a tool such as DumpSec (https://[`www.systemtools.com/somarsoft/?somarsoft.com`](http://www.systemtools.com/somarsoft/?somarsoft.com)), a tool that can enumerate the Windows operating system and gather user IDs and other information. -> **了解你的用户 ID。** 如果账户从未使用，请在需要时删除或禁用该账户。你可以通过手动检查或使用 DumpSec（http://www.systemtools.com/somarsoft/?somarsoft.com）等工具来确定未使用的账户，该工具可以枚举 Windows 操作系统并获取用户 ID 等信息。

As the security manager in your organization, you can enable account lockout to prevent password-cracking attempts. *Account lockout* is the ability to lock user accounts for a certain time after a certain number of failed login attempts has occurred. Most operating systems (and some applications) have this capability. Don’t set it too low (fewer than five failed logins), and don’t set it too high to give a malicious user a greater chance of breaking in. Somewhere between 5 and 50 may work for you. I usually recommend a setting of around 10 or 15. Consider the following when configuring account lockout on your systems:

*   To use account lockout to prevent any possibilities of a user DoS condition, require two different passwords, and don’t set a lockout time for the first one if that feature is available in your operating system. -> 为了使用账户锁定防止用户 DoS 条件的可能性，要求使用两种不同的密码，并且如果操作系统支持，不要为第一次尝试设置锁定时间。

*   If you permit autoreset of the account after a certain period — often referred to as *intruder lockout* — don’t set a short time period. Thirty minutes often works well. -> 如果你允许在一定时间后重置账户（通常称为 *入侵者锁定*），不要设置过短的时间段。30 分钟通常效果良好。

A failed login counter can increase password security and minimize the overall effects of account lockout if the account experiences an automated attack. A login counter can force a password change after a certain number of failed attempts. If the number of failed login attempts is high and has occurred over a short period, the account has likely experienced an automated password attack. -> 失败登录计数器可以提高密码安全性，并减少自动攻击对账户锁定的整体影响。登录计数器可以在达到一定次数的失败尝试后强制更改密码。如果失败登录次数很多且在短时间内发生，账户很可能经历了自动密码攻击。

Other password-protection countermeasures include:

*   **Stronger authentication methods:** Examples are challenge/response, smart cards, tokens, biometrics, and digital certificates. -> **更强的认证方法：** 例如挑战/响应、智能卡、令牌、生物特征和数字证书。

*   **Automated password reset:** This functionality lets users manage most of their password problems without getting others involved. Otherwise, this support issue becomes expensive, especially for larger organizations. -> **自动密码重置：** 此功能让用户无需他人参与即可管理大部分密码问题。否则，此支持问题成本高昂，尤其是对大型组织而言。

*   **Password-protected system BIOS:** This countermeasure is especially important on servers and laptops that are susceptible to physical security threats and vulnerabilities. -> **密码保护的系统 BIOS：** 这一措施在服务器和笔记本电脑上尤其重要，因为这些设备易受物理安全威胁和漏洞的影响。

## Securing Operating Systems

You can implement various operating-system security measures to ensure that passwords are protected.

![remember](images/remember.png)Regularly perform these low-tech and high-tech password-cracking tests to make sure that your systems are as secure as possible — perhaps as part of a monthly, quarterly, or biannual audit of local and domain passwords. -> ![remember](images/remember.png)定期进行这些低技术和高技术密码破解测试，以确保你的系统尽可能安全 —  — 也许作为本地和域密码的月度、季度或半年度审计的一部分。

### Windows

The following countermeasures can help prevent password hacks on Windows systems:

*   Some Windows passwords can be gleaned by reading the clear text or crackable cipher text from the Windows Registry. Secure your registries by doing the following: -> 有些 Windows 密码可以通过读取 Windows 注册表中的明文或可破解的密码文本获取。通过以下方式保护你的注册表：

    *   Allow only administrator access. -> 仅允许管理员访问。