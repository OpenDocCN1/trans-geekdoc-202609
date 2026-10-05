# Chapter 15 Buggy Software 313

These days the most popular attacked targets due to overly permissive permissions is that of Amazon Web Services (AWS) cloud storage "buckets". An organization buys and uses AWS storage and that often has overly permissive permissions. Here are some examples of real-world attacks:

+   * www.upguard.com/breaches/cloud-leak-accenture
* www.forbes.com/thomas-brewer/2017/12/19/120m-american-households-exposed-in-massive-consumerview-database-leak-#1667d9e97961
* www.wired.com/story/exactis-database-leak-340-million-records/
* www.znet.com/article/accenture-left-a-hove-of-client-passwords-over-exposed/
* www.hackread.com/personal/data-of-over-50000-honda-connect-appaked/

Even before cloud storage became popular, when hired as a penetration tester of one my favorite hacks was to look for overly permissive permissions on shared network log files and local computer files for programs that ran with the ultra-privileged System permissions. Many networks ran a number of shared common executables and scripts on connecting device after people log to the network. I liked to look for those shared files and scripts, and if it allowed regular users to modify these objects, I would modify it to include potentially malicious program or script. If I was hired to pen-test a regular computer, I would look for local programs I could find with elevated privileges. I found a few antivirus programs with overly permissive permissions. I would replace modify one of the files to sneak in my potentially malicious backdoor programs, reboot the computer, and then take it over. I always found ironic that the programs designed to defend an asset were the ones I must abused to successfully attack somewhat.

Defenses against overly permissive permissions is for the developers to ensure that the correct permissions have been set in the beginning and for administrators and developers to run periodic audits to look for overly permissive permissions on potentially dangerously misused files and folders.

# Hard-Coded/Default Credentials

Another vulnerability is for programs to have hard-coded, can't-change log credentials or to have very common, well-known log credentials that the users frequently don't change. Many developers either don't know the risk of hard-coded credentials or use them during early development and forget to remove them. The only way to fix hard-coded credentials is to update the software or programming with updated code that removes the hard-coded credentials. The Commonness Enumeration has a great description and examples of this type of vulnerability: cwe.mitre.org/data/definitions/798.html. Hard-coded credentials can be mitigated by developer education and tools that look for and alert on such instances in programming code.