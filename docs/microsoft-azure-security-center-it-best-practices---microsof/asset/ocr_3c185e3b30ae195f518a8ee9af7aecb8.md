# Common threats

As mentioned, one type of attack is the use of drive-by download sites. These are websites that host one or more exploits that target vulnerabilities in web browsers and browser add-ons. According to the Microsoft Security Intelligence Report, Volume 22, Bing detected 0.17 drive-by download pages for every 1,000 pages in the index in March 2017.

According to the same report, in the first quarter of 2017, trojans were the most commonly encountered type of malicious software (followed by worms and droppers). Trojans always pose as a useful application. For example, take the Win32/Zadupi Trojan, also called WinZipper(%ProgramFiles%\WinZipper) or QkSee(...). In addition to creating a shortcut to itself in the Start menu (see Figure 1-2) that enables users to zip and unzip files, this Trojan also creates a service (qkseeService) that connects to command and control (C2 servers) and periodically checks for instructions using HTTP requests. Often, these instructions silently download new files, which could contain malware that will be executed on the local computer. This is just one example of how threats spread.

![](bbox=[0.151, 0.363, 0.613, 0.769])

Figure 1-2 Typical installation location for QkSee

These days, the user is almost always the target because he or she is the weakest link. With the proliferation of mobile devices, bring-your-own-device (BYOD) models, and cloud-based apps, users are installing more and more apps. All too often, these are merely masquerading as valid apps. Many do something similar to (or even worse than) what QkSee