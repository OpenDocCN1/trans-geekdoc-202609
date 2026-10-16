
-   [是否需要锁定笔记本电脑包？关于开机密码呢？加密可以解决很多与物理安全相关的弱点。](https://wiki.example.org/feynmans_learning_method)

-   有人可以多么轻松地连接到无线接入点信号或接入点本身以加入网络？还需要考虑恶意接入点。我在[第10章](#c10.xhtml)中详细介绍了无线网络。

-   网络防火墙、路由器、交换机和集线器（基本上，任何有以太网或控制台连接的设备）是否容易被访问，从而让攻击者轻松插入网络？

-   所有的电缆是否都通过在布线橱柜的配线板上连接，使得所有的网络插口都处于活动状态（如前面提到的未受监控的大堂区域）？

![warning](images/warning.png)这套配置虽然常见，但却是个坏主意，因为它允许任何人随时插入网络并获得访问权限，同时也能传播恶意软件。

#### Countermeasures

网络和计算机安全防护措施虽然实施简单，但难以执行，因为它们涉及日常行为。下面是这些防护措施的清单：

- 让用户了解需要注意的事项，从而拥有额外的“眼睛和耳朵”帮助你发现问题。
- 要求用户在离开电脑时锁定屏幕——只需几次点击或键盘操作即可完成。更进一步，可在 Active Directory 或本地计算机策略中设置组策略对象（GPO）强制设置超时。
- 确保使用强密码。（我在[第8章](#c08.xhtml)中介绍了该主题。）
- 要求笔记本电脑用户使用锁定电缆将系统固定在书桌上——这对远程工作者、旅行者以及大型公司的员工以及经常在人流密集的场所工作的人来说尤为重要。
- 要求所有笔记本电脑使用全盘加密技术。例如 Windows 的 BitLocker（最好配合 Microsoft BitLocker Administration and Monitoring 管理软件，网址为[`https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/mbam-v25/`](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/mbam-v25/)），另一个选项是 WinMagic SecureDoc Full Disk Encryption（网址为[`https://www.winmagic.com/products/full-disk-encryption-for-windows`](https://www.winmagic.com/products/full-disk-encryption-for-windows)）。macOS 内置的 FileVault 也是适用于日益增长的此类计算机的方案。同时，还应考虑对可移动介质进行加密，因为敏感信息必然会在那里。

- 保持服务器机房和布线橱柜上锁，并监控这些区域的任何不当行为。
- 保持组织内硬件和软件的当前清单，以便轻松发现额外设备的出现或丢失——尤其是在计算机室中非常重要。
- 用更现代的访问控制系统取代传统的门锁和钥匙。
- 在存储和运输过程中妥善保护计算媒体。
- 扫描并关闭恶意无线接入点。
- 使用线缆陷阱和锁具，防止入侵者从配线板或计算机上拔掉网络线并利用该连接接入其他设备。
- 对磁介质使用大容量擦除工具，并在销毁前将其粉碎。

Chapter 8

# Passwords

IN THIS CHAPTER

![check](images/check.png)`Identifying password vulnerabilities`

![check](images/check.png)`Examining password-hacking tools and techniques`

![check](images/check.png)`Hacking operating system passwords`

![check](images/check.png)`Hacking password-protected files`

![check](images/check.png)`Protecting your systems from password hacking`

Password hacking is one of the easiest and most common ways that attackers obtain unauthorized network, computer, or application access. You often hear about it in the headlines, and study after study, such as the `Verizon Data Breach Investigations Report`, reaffirms that weak passwords are at the root of many security problems. I have trouble wrapping my head around the fact that I’m `still` talking about (and businesses are suffering from) weak passwords, but that fact is a reality. As an information security testing professional, you can certainly do your part to minimize the risks.

Although strong passwords — ideally, longer, stronger passphrases, which are difficult to crack (or guess) — are easy to create and maintain, network administrators and users often neglect this aspect of password management. Therefore, passwords are among the weakest links in the information security chain. Passwords rely on secrecy. After a password is compromised, its original owner isn’t the only person who can access the system with it. That’s when accountability goes out the window and bad things start happening.

External attackers and malicious insiders have many ways to obtain passwords. They can glean passwords simply by asking for them or by looking over the shoulders of users *(shoulder surfing)* while they type their passwords. Hackers can also obtain passwords from local computers by using password-cracking software. To obtain passwords from across a network, attackers can use remote cracking utilities, keyloggers, or network analyzers.

This chapter demonstrates how easily the bad guys can gather password information from your network and computer systems. I outline common password vulnerabilities and describe countermeasures that help prevent these vulnerabilities from being exploited on your systems. If you perform the tests and implement the countermeasures outlined in this chapter, you’ll be well on your way to securing your systems’ passwords.

## Understanding Password Vulnerabilities

When you balance the cost of security and the value of the protected information, the combination of a user id and a secret password is usually adequate. Passwords create a false sense of security, however, as the bad guys know, and they attempt to crack passwords as a step toward breaking into computer systems.

One big problem with relying solely on passwords for security is that more than one person can know them. Sometimes, multiple people knowing a password is intentional; often, it’s not. The tough part is that there’s no way of knowing who, besides the password’s owner, knows a password.

![remember](images/remember.png)Knowing a password doesn’t make someone an authorized user.

Here are the two general types of password vulnerabilities:

- **Organizational or user vulnerabilities:** Include lack of password policies that are enforced within the organization and lack of security awareness on the part of users
- **Technical vulnerabilities:** Include weak encryption methods and unsecure storage of passwords on computer systems

I explore these classifications in more detail in the following sections.

Before computer networks and the Internet, the user’s physical environment was an additional layer of password security that worked pretty well. Now that most computers have network connectivity, that protection is gone. [Chapter 7](#c07.xhtml) provides details on managing physical security in this age of networked computers and mobile devices.

### Organizational password vulnerabilities
