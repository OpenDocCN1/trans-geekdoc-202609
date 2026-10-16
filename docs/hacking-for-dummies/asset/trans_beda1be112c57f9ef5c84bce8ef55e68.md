
5. **点击“Launch”图标以启动彩虹破解过程。**

如果您看到密码哈希仅在“NT Hash”列中（如[图 11-3](#c11.xhtml#c11-fig-0003)所示），请确保您已从[`http://ophcrack.sourceforge.net/tables.php`](http://ophcrack.sourceforge.net/tables.php)或其他位置下载了正确的哈希表。一个适合开始使用的哈希表是Vista 特别版（8.0GB）。要加载新表，请点击 ophcrack 窗口顶部的“Tables”图标，如[图 11-4](#c11.xhtml#c11-fig-0004)所示。

![ FIGURE 11-2:  Loading password hashes from a remote SAM database in ophcrack.](images/9781119485476-fg1102.png)

[FIGURE 11-2:](#c11.xhtml#rc11-fig-0002)  Loading password hashes from a remote SAM database in ophcrack.

![ FIGURE 11-3:  Usernames and hashes extracted via ophcrack.](images/9781119485476-fg1103.png)

[FIGURE 11-3:](#c11.xhtml#rc11-fig-0003)  Usernames and hashes extracted via ophcrack.

![ FIGURE 11-4:  Loading the required hash tables in ophcrack.](images/9781119485476-fg1104.png)

[FIGURE 11-4:](#c11.xhtml#rc11-fig-0004)  Loading the required hash tables in ophcrack.

如果需要，可在步骤 5 中重新启动彩虹破解过程。该过程可能需要几秒钟到几天（或更长），具体取决于您的计算机速度和正在破解的哈希复杂度。

可在[`http://ophcrack.sourceforge.net/download.php?type=livecd`](http://ophcrack.sourceforge.net/download.php?type=livecd)处下载的基于 Linux 的可启动 ophcrack 版本，让您无需登录或安装任何软件即可启动系统并开始破解密码。

![tip](images/tip.png)I *highly* recommend that you use ophcrack’s LiveCD on a sample laptop computer or two to demonstrate how simple it is to recover passwords and, subsequently, sensitive information from laptops that don’t have encrypted hard drives. This tool is amazingly simple, yet many people still refuse to invest money in full-disk encryption software, even the free and enterprise-ready Microsoft BitLocker. ElcomSoft System Recovery is another great tool for this exercise.

### Applying countermeasures

The best safeguard against a hacker using a password reset program against your systems is encrypted hard drives. You can use BitLocker in Windows, WinMagic SecureDoc ([`https://www.winmagic.com/products`](https://www.winmagic.com/products)), or another preferred endpoint security product for the platform your systems are running on.

Power-on passwords set in the BIOS can be helpful as well, but they’re often mere bumps in the road. All a criminal has to do is reset the BIOS password or, better, remove the hard drive from your lost system and access it from another machine. You also need to ensure that people can’t gain unauthorized physical access to your computers. When a hacker has physical access and your drives aren’t encrypted, all bets are off. That said, full-disk encryption isn’t foolproof; see the nearby sidebar “[The fallacy of full-disk encryption](#c11.xhtml#c11-fea-0001).” The good news is that more recent computers with Unified Extensible Firmware Interface (UEFI) are more resilient to these types of attacks.

## Cracking Phones and Tablets

I don’t envy IT administrators and information security managers for many reasons, but especially when it comes to the *bring your own device* (BYOD) movement taking place in business today. With BYOD, you have to trust that your users are making good decisions about security, and you have to figure out how to manage every device, platform, and app. This management task is arguably the greatest challenge that IT professionals have faced to this point. Further complicating matters, criminal hackers, thieves, and other hooligans are doing their best to exploit this complexity, creating serious business risks. The reality is that few businesses — and individuals — have their phones and tablets properly secured.

Plenty of vendors claim that their mobile device management (MDM), enterprise mobility management (EMM), or unified endpoint management (UEM) solutions are the answer to mobile device woes. They’re right … to an extent. These systems have controls that separate personal information from business information and ensure that the proper security controls are enabled at all times, which is a big leap toward locking down the mobile enterprise.

One of the best things you can do to protect phones and tablets from unauthorized use is implement this nifty security control that dates back to the beginning of computers: *passwords*. Yep, your phone and tablet users should employ good old-fashioned passwords (technically, passphrases) that are easy to remember but hard to guess. Passwords are among the best controls you can have, yet there are plenty of mobile devices with no passwords or passwords that are easily cracked.

Starting with iOS 9, iOS devices have come with a six-character passcode default. Android Lollipop originally defaulted to encrypting the entire device, although that setting was reversed after complaints about performance degradation.

In the following section, I demonstrate accessing mobile devices with a commercial forensics tool. Keep in mind that such tools are typically restricted to law enforcement personnel and security professionals, but they could certainly end up in the hands of the bad guys. Using such tools for your own information security testing can be a great way to demonstrate the business risk and make the case for better mobile controls.

![remember](images/remember.png)Mobile apps can introduce a slew of security vulnerabilities into your environment, especially certain apps available for Android via Google Play that aren’t properly vetted. In recent source-code analysis with Checkmarx’s CxSuite (see [Chapter 15](#c15.xhtml)), I’ve found these apps to have the same flaws as traditional software, such as SQL injection, hard-coded encryption keys, and buffer overflows that can put sensitive information at risk. The threat of malware is there as well. Mobile apps are yet another reason to get your mobile environment under control by using, at minimum, a proven MDM system such as MaaS360 ([`www.maas360.com`](http://www.maas360.com)) or AirWatch ([`www.air-watch.com`](http://www.air-watch.com)).

### Cracking iOS passwords

I venture to guess that many phone and tablet passwords (really, just four-digit PINs or passcodes) can be guessed outright. When a mobile device gets lost or stolen, all that the person who recovers it has to do is try basic number combinations such as 1234, 1212, or 0000. Soon, *voilà!* — the system is unlocked.

Many phones and tablets running iOS and Android are configured to wipe the device if the incorrect password is entered a certain number of times (often 10 failed attempts). This security control is reasonable indeed. But what else can you do? Some commercial tools can be used to crack simple passwords or PINs and recover information from lost or stolen devices or devices undergoing a forensics investigation.

ElcomSoft’s iOS Forensic Toolkit ([`https://www.elcomsoft.com/eift.html`](https://www.elcomsoft.com/eift.html)) provides a way to demonstrate how easily passwords and PINs on iOS-based phones and tablets can be cracked through iOS version 7. Here’s how:

1.  **Plug the iOS device (iPhone, iPod, or iPad) into your test computer, and place it in Device Firmware Upgrade (DFU) mode.**

    To enter DFU mode, power the device off, hold down the Home button (bottom center) and sleep button (often, the top-right corner) at the same time for 10 seconds, and continue holding down the Home button for another 10 seconds. The device’s screen goes blank.

2.  **Load the iOS Forensic Toolkit by inserting your USB license dongle into your test computer and running `Tookit.cmd`.**

    You see the screen shown in [Figure 11-5](#c11.xhtml#c11-fig-0005).
