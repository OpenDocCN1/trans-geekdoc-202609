
## 312 Hacking Multifactor Authentication

(e.g., C:\Users\username\ and if you cd .. and press Enter, you will be in the parent folder (e.g., C:\Users). A single dot represents the current folder. Using combinations of dots and double dots as names with forward slashes (and sometimes backward slashes) would sometimes, if you were lucky, you get to folders that you had been told you did not have access to.

Back to my previous experience where the Foundstone penetration testing team was attacking a box device. In order to access the device, you went to its IP address with 192.168.1.1. That gave you a web-based login prompt. We tried password guessing it and nothing was working. I ran a server identification tool called Nikto (circ.net/nikto2) against the box, because you could not use it to connect to any server that is running a mini-web server of some sort. Nikto will try to identify the server by service version and then run a bunch of attacks against it. Nikto was not successful in finding a vulnerability, but it did identify the server version. It was called Notebook. I had never heard of it, and it was difficult to research, but I found a single Google reference to Digital Research web server called Notebook discontinued over two decades ago. I knew that web servers are all free of directory traversal vulnerabilities. So, I tried the test I listed earlier, and voila! just like that, I was in the device with full administrative control-level of access possible on the box. We were able to completely control the device, steal credit card information, steal paid shows for free, and completely manipulate the code of the device. The next day, we did the XSS attack listed earlier and took over the whole corporate office. So, in two days we had not only completed the device we were paid to hack, but had also taken over the entire corporation. That is one of my best hacking memories to this day, and I am still missing it as this type of thing.

Directory traversal attacks aren't as common these days, but they can still be used to get permission controls on operating systems and (non-web) server programs. People who build web servers know all directory traversal attacks and control them, but it seems that other developers are not as familiar. Preventing directory traversal attacks is usually solved by correct permissions—and leads us to our next topic.

## Overly Permissive Permissions

A very, common vulnerability these days is overly permissive permissions, meaning that who-created a system did not correctly define the permissions for all users—be they admins, regular users, guests, or the infamous “everyone” groups. Whoever defined them inadvertently allows users and visitors who should not be able to read or write protected files the ability to do so. So, a regular user or visitor who normally should only be able to read files or execute code the developer intends up with the ability to maliciously modify or add critical files and download confidential files.

## Chapter 15: Buggy Software

These days the most popular attacked targets due to overly permissive permissions is that of Amazon Web Services (AWS) cloud storage "buckets". An organization buys and uses AWS storage and that often has overly permissive permissions. Here are some examples of real-world attacks:

- www.upguard.com/breaches/cloud-leak-accenture
- www.forbes.com/thomas-brewer/2017/12/19/120m-american-households-exposed-in-massive-consumerview-database-leak-#1667d9e97961
- www.wired.com/story/exactis-database-leak-340-million-records/
- www.znet.com/article/accenture-left-a-hove-of-client-passwords-over-exposed/
- www.hackread.com/personal/data-of-over-50000-honda-connect-appakedaked/

Even before cloud storage became popular, when hired as a penetration tester of one my favorite hacks was to look for overly permissive permissions on shared network log files and local computer files for programs that ran with the ultra-privileged System permissions. Many networks ran a number of shared common executables and scripts on connecting device after people log to the network. I liked to look for those shared files and scripts, and if it allowed regular users to modify these objects, I would modify it to include potentially malicious program or script. If I was hired to pen-test a regular computer, I would look for local programs I could find with elevated privileges. I found a few antivirus programs with overly permissive permissions. I would replace modify one of the files to sneak in my potentially malicious backdoor programs, reboot the computer, and then take it over. I always found ironic that the programs designed to defend an asset were the ones I must abused to successfully attack somewhat.

Defenses against overly permissive permissions is for the developers to ensure that the correct permissions have been set in the beginning and for administrators and developers to run periodic audits to look for overly permissive permissions on potentially dangerously misused files and folders.

## Hard-Coded/Default Credentials

Another vulnerability is for programs to have hard-coded, can't-change log credentials or to have very common, well-known log credentials that the users frequently don't change. Many developers either don't know the risk of hard-coded credentials or use them during early development and forget to remove them. The only way to fix hard-coded credentials is to update the software or programming with updated code that removes the hard-coded credentials. The Commonness Enumeration has a great description and examples of this type of vulnerability: cwe.mitre.org/data/definitions/798.html. Hard-coded credentials can be mitigated by developer education and tools that look for.

## Hacking Multifactor Authentication

Hacking Multifactor Authentication

One of my favorite real-world examples was Stuxnet (en.wikipedia.org/wiki/Stuxnet). Anyone interested in reading more about Stuxnet should see cs.arizona.edu/~collin/446-566/2012/Resources/presentations/2012/topic9-report.pdf and read Kim Zimmer's ebook, Countdown to Zero Day (Broadway Books, 2015).

But, anyway anyone with penetration testing SCADA knows that many industrial control systems have hard-coded passwords, not just Siemens (although many different types of have hard-coded passwords as well). It's rare in the industry and isnt uncommon anywhere. You would think developers understand how risky hard-coded passwords are and never do it. I first had this thought in 1990. I assumed that this particular issue was so well known that no developer would ever be stupid to make this mistake. I was wrong. Security defending is not abundant; it's education and awareness. If the developers and managers involved in a programming project aren't aware of the problems with hard-coded passwords, then they can't minimize them.

During my 30-year penetration testing career, I've found hundreds of hard-coded passwords in programs and systems I've been hired to test. Once, not long ago, I was advising a Fortune 10 company that developed software and services on how to better manage security bugs from their systems. When they ran Qualys vulnerability scanners, the resulting reports often list 50 or more “critical” bugs that were found on each system. The task to fix them all at once over thousands of systems was overwhelming, so they asked me for my advice. I pride myself on figuring what should be fixed first. I even wrote a book about it (A Data-Driven Computer Defense, independently published, 2019).

I told them to ignore the voluminous reports and asked, “What is the vulnerability type that has been successfully used by attackers to exploit your systems in the real world?” I figured there was no better answer than to fix the way the systems had actually executed the most as the first, best step they could take. They had to research the data. And then found out that thousands of publicly exposed systems, only eight had been successfully compromised that they knew about. But of those, when I asked how they were exploited, they answered, “Hard-coded login credentials!”
