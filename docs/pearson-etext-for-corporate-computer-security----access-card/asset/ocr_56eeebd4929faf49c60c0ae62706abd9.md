# 7.3 Vulnerabilities and Patches

7.3 Describe vulnerabilities and patches.

# Vulnerabilities and Exploits

The arms race between operating-system vendors and hackers is an endless battle. Vulnerability finders constantly discover new vulnerabilities, which are security weaknesses that open a program to attack.

> Vulnerabilities are security weaknesses that open a program to attack.

Most vulnerability finders notify software vendors, so that vendors can develop fixes for these vulnerabilities. However, some vulnerability finders sell their vulnerabilities to hackers, who quickly develop exploits—programs that take advantage of the vulnerability.

Software vendors create fixes when vulnerabilities are reported to them. However, hacker attacks occur before these fixes are created. Attacks that come before fixes are released are called zero-day attacks.

> Attacks that come before fixes are released are called zero-day attacks.

Ironically, the most dangerous period usually comes immediately after a fix is released by a vendor. Attackers reverse-engineer the fix to learn about the underlying vulnerability. Reengineering-based exploits typically appear in a day or two, and they sometimes occur within hours. Companies must not delay in applying newly released fixes for critical vulnerabilities.

# Test Your Understanding

+   5. a. What is a vulnerability?
+      b. What is an exploit?
+      c. What is a zero-day attack?
+      d. Why is the quick application of critical fixes important?

# Fixes

When vendors discover that they have vulnerabilities, they create fixes. There are four types of fixes.

# WORK-AROUNDS

The least satisfactory fix is a work-around, which is a series of manual steps the systems administrator must take to ameliorate the problem. No new software is involved. Work-arounds tend to be highly labor-intensive. In addition, it is easy to make a mistake when doing complex manual fixes; this can have disastrous results, even if no attacks occur.

# PATCHES

It is better when vendors create a patch, which is a small program that fixes a particular vulnerability. A systems administrator must download, install, and run the patch. Microsoft typically releases patches on the second Tuesday of each month. This has affectionately come to be known as “patch Tuesday.”5

5 Microsoft Corp., “Microsoft Security Update Guide,” Microsoft.com. September 14, 2019 https://portal.msrc.microsoft.com/en-us/security-guidance.