
![tip](images/tip.png)A commonly overlooked storage vulnerability is that many storage systems can be accessed from both the demilitarized zone (DMZ) segment and the internal network segment(s). This vulnerability poses risks to both sides of the network. Be sure to check manually to see whether you can reach the DMZ from the internal network, and vice versa.

You can also perform basic file permission and share scans (as outlined in [Chapter 12](#c12.xhtml)) in conjunction with a text search tool to uncover sensitive information that no one on the network should have access to. Digging down further, a quick means for finding open network shares is to use SoftPerfect Network Scanner’s share scanning capabilities, as shown in [Figure 16-3](#c16.xhtml#c16-fig-0003).

![ FIGURE 16-3:  Using SoftPerfect Network Scanner to search for network shares.](images/9781119485476-fg1603.png)

 [FIGURE 16-3:](#c16.xhtml#rc16-fig-0003)  Using SoftPerfect Network Scanner to search for network shares.

As you can see in [Figure 16-3](#c16.xhtml#c16-fig-0003), Network Scanner enables you to perform a security and security permission scan for all devices or simply folders. I recommend selecting Specific Account in the Authentication section and then clicking Manage so that you can enter a domain account for the network that has general user permissions. This technique provides a good level of access to determine which shares are accessible.

When Network Scanner completes its scan, the shares showing Everyone in the Shared Folder Security column are the shares that need attention. I rarely complete a security assessment without coming across such shares open to the Windows Everyone group. Just as common is seeing the directories and files within these shares that are accessible to any logged-in Windows user to open, modify, delete, and do whatever else they please. How’s that for accountability?

### Rooting out sensitive text in network files

When you find open network shares, scan for sensitive information stored in files such as `.pdf`, `.docx`, and `.xlsx` files. The process is as simple as using a text search utility such as FileLocator Pro. Alternatively, you can use Windows Explorer or the `find` command in Linux to scan for sensitive information, but that process is too slow and cumbersome for my liking.

You'll be *amazed* by what you come across stored insecurely on users’ desktops, server shares, and more, such as the following:

*   Employee health records

*   Customer credit card numbers

*   Corporate financial reports

*   Source code

*   Master database files

The sky’s the limit. Such sensitive information should be protected by good business practices, and it’s also governed by state, federal, and international regulations, so make sure that you find it and secure it.

![tip](images/tip.png)Do your searches for sensitive text while you’re logged in to the local system or domain as a regular user — not as an administrator. This practice gives you a better view of regular users who have unauthorized access to sensitive files and shares that you thought were secure. When using a basic text search tool such as FileLocator Pro, look for the following text strings:

*   DOB (for dates of birth)

*   SSN (for Social Security numbers)

*   License (for driver’s-license information)

*   Credit or CCV (for credit-card numbers)

![remember](images/remember.png)Don’t forget about your mobile devices when seeking sensitive, unprotected information. Everything from laptops to USB drives to external hard drives is fair game to the bad guys. A misplaced or stolen system can create a costly data breach. The same can be said for cloud-based file sharing services such as OneDrive and Sharefile.

The possibilities for information exposure are endless. Start with the basics, and peek only into common files that you know may have some juicy info in them. Limiting your search to these files will save you a ton of time:

*    `.txt` 

*    `.doc`  and `.docx`

*    `.rtf` 

*    `.xls`  and `.xlsx`

*    `.pdf` 

[Figure 16-4](#c16.xhtml#c16-fig-0004) shows a basic text search with FileLocator Pro. Notice the files located on different parts of the server.

![ FIGURE 16-4:  Using FileLocator Pro to search for sensitive text on unprotected shares.](images/9781119485476-fg1604.png)

 [FIGURE 16-4:](#c16.xhtml#rc16-fig-0004)  Using FileLocator Pro to search for sensitive text on unprotected shares.

FileLocator Pro can also search for content inside `.pdf` files to uncover sensitive data.

To speed the process, use Spirion's Sensitive Data Manager ([`https://www.spirion.com`](https://www.spirion.com)). This product, formerly known as IdentityFinder and since rolled into the company’s enterprise data discovery platform, is a neat tool designed for scanning storage devices for sensitive, personally identifiable information. It can also search inside binary files such as PDFs.

For a second round of testing, you could perform your searches while logged in as an administrator. You’re likely to find a lot of sensitive information scattered about. It might seem worthless at first, but it can highlight sensitive information stored in places where it shouldn’t be or that network administrators shouldn’t be able to access.

![remember](images/remember.png)Testing is highly dependent on timing, searching for the right keywords, and looking at the right systems on the network. You likely won’t root out every single bit of sensitive information, but this effort shows you where certain problems are, which helps you justify the need for stronger access controls and for better IT and security management processes.

## Following Best Practices for Minimizing Storage Security Risks

Like database security, storage security isn’t brain surgery. Keeping your storage systems secure is simple, too, if you do the following things:

*   Check the underlying operating systems for security vulnerabilities. I cover operating system exploits for Windows and Linux in [chapters 12](#c12.xhtml) and [13](#c13.xhtml).

*   Ensure that your network storage (SAN and NAS systems) falls within the scope of patching and system hardening.

*   Require strong passwords on every storage management interface.

*   Use appropriate file and share permissions to keep prying eyes away.

*   Educate your users on where to store sensitive information and the risks of mishandling it.

*   Deidentify any sensitive production data before it’s used in development or quality assurance, using tools made for this purpose.

*   Use a network access control lists or a firewall, such as those available from Fortinet ([`https://www.fortinet.com`](https://www.fortinet.com)) or WatchGuard Technologies ([`https://www.watchguard.com`](https://www.watchguard.com)) to ensure that only the people and systems with a business need to access your storage environment can do so — and do nothing more.

Part 6

# Security Testing Aftermath

IN THIS PART …

Report your way to success with security testing deliverables that management can understand and appreciate.

Follow-up on your security vulnerabilities so that they’re not exploited.

Implement good security practices into your day-to-day information technology and business operations to help build resilience.

Chapter 17

# Reporting Your Results

IN THIS CHAPTER

![check](images/check.png)**Bringing your test data together**

![check](images/check.png)**Categorizing vulnerabilities you discover**

![check](images/check.png)**Documenting and presenting the results**

