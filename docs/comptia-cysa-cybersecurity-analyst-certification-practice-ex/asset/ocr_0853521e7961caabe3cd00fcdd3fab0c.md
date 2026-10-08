because PCI DSS is a set of requirements for businesses that deal with credit card data. C is incorrect because Nessus is a vulnerability scanner that rates its findings based on CVSS score.

+   34. Soon after completing a vulnerability scan, you review the most critical findings on your Nginx web server. From the following list, which is the likely false positive?

+   A. CVE-2016-1247 Nginx Root Privilege Escalation

+   B. CVE-2017-0278 Windows SMB Remote Code Execution

+   C. CVE-2017-7529 Nginx Remote Integer Overflow

+   D. CVE-2018-7584 PHP Stack Buffer Overflow

+   E. CVE-2017-14176 Bazaar with Subprocess SSH, allows Remote Execution

+   * B is correct. This is lone Windows vulnerability and therefore the likely false positive.

+   * A, C, D, and E are incorrect. These are all Nginx or Linux vulnerabilities. Because the odd one is a Windows vulnerability, it's safe to assume the Windows finding is the false positive.

+   35. A vulnerability scan reports a web service running on a server. However, you only know of an application developed in-house running on that server. Additionally, the server is not external facing, and you're fairly confident there is no web service running. What is the likely port of that internally developed application?

+   A. 445

+   B. 69

+   C. 110

+   D. 80

+   * D is correct. If a scanner reports a web service running, it might have only detected port 80 as open and listening.

+   * A, B, and C are incorrect. Ports 445, 69, and 110 are not associated with HTTP traffic.

+   36. A vulnerability scan reports a web service running on a server, but you were unaware of any web service or anything running on port 80. What might be the next step?

+   A. Scan the server with a port scanner to see if port 80 is listening.

+   B. Write a policy that web services must be approved before an installation.