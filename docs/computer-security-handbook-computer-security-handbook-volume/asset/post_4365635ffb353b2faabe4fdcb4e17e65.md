
Similarly, disposable virtual machines48,49 can be used by normal users to separate the normal operating environment from one where there is a perceived increase in risk exposure (e.g., browsing suspect sites; forced installation of ActiveX controls of uncertain provenance or safety).

## 17.4.5 Server Responsibilities.

As noted earlier in this chapter, Web servers represent an attractive vector for attacks. Signing (authentication) methods are a way to control damage potential, provided the mechanisms used for admitting executable code are properly controlled. Failure to control these mechanisms leads to severe side effects.

The concept of minimum necessary privilege applies to mobile code. There is little reason to impose the use of ActiveX for the purposes of changing the color of a banner advertisement. This effect can often be accomplished using Cascading Style Sheets (CSS). JavaScript/ECMAScript is capable of many powerful, display-related operations with a high degree of safety in situations where CSS is not adequate. Using Java to maintain a shopping cart (price, quantities, and contents) is reasonable and does not require the use of a signed applet, with its attendant greater capabilities and risks. At the other end of the scale, it is plausible that a system update function (e.g., the Windows Update function, which automatically downloads and installs changes to the Windows operating system) requires the unbridled power of a signed ActiveX control.

When the power of signed applets or controls is required, good software engineering practice provides excellent examples of how to limit the potential for damage and mischief, as discussed in Chapter 38 in this Handbook.

These problems extend beyond an individual organization’s direct exposure. An increasing trend over the past several years has been to use third-party Web servers as an infection vector, a springboard for infecting Website visitors. If components are downloaded from third-party servers, the integrity of your WWW site may be vulnerable to compromise.

Good software implementation isolates functions and limits the scope of operations that require privileged access or operations. Payroll applications do not directly manipulate printer ports, video display cards, network adapters, or disk drives. Privileged operating system components, such as device drivers and file systems, are responsible for the actual operation. This separation, together with careful parameter checking by the operating system kernel and the privileged components, ensures safety.

The same techniques can be used with applets and controls. Because they require more access, they should be programmed carefully, using the same defensive measures as are used when implementing privileged additions to operating systems. As an example, there is little reason for a Simple Mail Transfer Protocol (SMTP) server to be privileged. An SMTP server requires privileges for a single function, the delivery of an individual email message to a recipient’s mailbox. This can be accomplished in two ways:

- 1. Implement the application in a nonprivileged way, by marking users’ email files and directories with the necessary access permissions for the mail delivery program to create and modify email files and directories. Such a mechanism is fully in conformance with the NCSC Orange Book’s C2-level of security.
- 2. Implement a separate subcomponent whose sole responsibility is the actual message delivery of the message. The subcomponent must be written defensively to check all of its parameters, and does not provide an interface for the execution of arbitrary code. This approach is used by HP’s OpenVMS operating system.

The UNIX sendmail program, by contrast, is a large, multifunctional program that executes with privileges. sendmail has been the subject of numerous security problems for over a decade and has spawned efforts to produce more secure replacements.⁵⁰

## 17.5 SUMMARY.

Mobile code provides many flexible and useful capabilities. The different mechanisms for implementing mobile code range from the innocuous (HTML), to fairly safe (JavaScript/ECMAScript), and with increasing degrees of power and risk through Java and ActiveX.

Ensuring security and integrity with the use of mobile code requires cooperation on the part of both the provider and the client. Clients should not accept random signed code and controls. Providers have a positive responsibility to:

- Follow good software engineering practices
- Grant minimum necessary privileges and access
- Use defensive programming
- Limit privileged access, with no open-ended interfaces
- Ensure the integrity of the signing process and the associated private keys

With appropriate caution, mobile code can be a constructive, powerful part of intranet and Internet applications, both within an organization and in cooperation with its customers and other stakeholders.

## 17.6 FURTHER READING

Carl, Jeremy. “ActiveX Security: Under the Microscope,” Web Week. 2. No. 17. November 4, 1996; www.Webdeveloper.com/activex/activex_security.html

CERT. “NIMDA Worm,” September 11, 2001, www.cert.org/advisories/CA-2001-26.html

CERT. “sadmind/IIS Worm,” May 8, 2001, www.cert.org/advisories/CA-2001-11.html

CERT. “Unauthentic ‘Microsoft Corporation’ Certificates,” March 22, 2001, www.cert.org/advisories/CA-2001-04.html

Dormann, Will, and Jason Rafail. “Securing Your Web Browser.” CERT. January 23, 2006, www.cert.org/tech_tips/securing_browser/index.html on March 19, 2013.

Evers, J. FAQ: JavaScript Insecurities. CNET July 28, 2006 < http://news.cnet.com/2100-7349_3-6100019.html >

Felten, Edward. “Security Tradeoffs: Java vs. ActiveX,” last modified April 28, 1997, www.cs.princeton.edu/sip/faq/java-vs-activex.html

Felten, E., and J. Halderman (2006, February 14). Lessons from the Sony CD DRM Episode, Center for Information Technology Policy, Department of Computer Science, Princeton University, USENIX Security 2006 http://static.usenix.org/events/sec06/tech/full_papers/halderman/halderman.pdf

Felten, E., and G. McGraw. Securing Java: Getting Down to Business with Mobile Code. New York: John Wiley & Sons, 1999. Also free and unlimited Web access from www.securingjava.com

Gehtland, J., B. Galbraith, and D. Almaer. Pragmatic Ajax. Raleigh, NC: Pragmatic Bookshelf, 2006.

Grossman, J., and T. C. Niedzialkowski. “Hacking Intranet Websites from the Outside,” Black Hat (USA), Las Vegas, August 3, 2006. www.blackhat.com/presentations/bh-usa-06/BH-US-06-Grossman.pdf

Hensing, R. “W32/HLLP.Philis.bq, Chinese Gold Farmers and What You Can Do about It,” December 2, 2007, http://blogs.technet.com/robert_hensing/archive/2006/12/04/w32-hllp-philis-bq-chinese-gold-farmers-and-what-you-can-do-about-it.aspx

Holzman, S. Ajax Bible. Hoboken, NJ: John Wiley & Sons, 2007.

Keizer, G. “FBI Planted Spyware on Teen’s PC to Trace Bomb Threats,” PCWorld, July 19, 2007. www.pcworld.com/article/134823/article.html

McGraw, G., and E. W. Felten. Securing Java: Getting Down to Business with Mobile Code, 2nd Edition. John Wiley & Sons, 1999.

McGraw, Gary & Ed Felten. “Java Security Web Site.” www.cigital.com/javasecurity/index.html

Microsoft. “Introduction to Code Signing” (with appendix), 2001, http://msdn.microsoft.com/en-us/library/ms537361%28v=vs.85%29.aspx

Rhoads, C. “Web Scammer Targets Senior U.S. Executives,” Wall Street Journal, November 9, 2007.

Schwartz, J. “iPhone Flaw Lets Hackers Take Over Security Firm Says,” New York Times, July 23, 2007.

VeriSign, “Microsoft Security Bulletin MS01-017: Erroneous VeriSign-Issued Digital Certificates Pose Spoofing Hazard,” March 22, 2001, www.microsoft.com/TechNet/security/bulletin/MS01-017.asp

VeriSign, “VeriSign Security Alert Fraud Detected in Authenticode Code Signing Certificates,” March 22, 2001.

Zakas, N., J. McPeak, and J. Fawcett. Practical Ajax, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2007.

## 17.7 NOTES

- 1. ECMA-262 retrieved from www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-262%205th%20edition%20December%202009.pdf
- 2. Carter Dotson, “Is Apple Losing Its Grip on App Store Security?” Mashable Web site, March 1, 2012. http://mashable.com/2012/03/01/app-store-security-risks
- 3. Scott Thurm and Yukari Iwatani Kane, “Your Apps Are Watching You,” The Wall Street Journal, December 17, 2010, http://online.wsj.com/article/SB10001424052748704694004576020083703574602.html
- 4. J. Schwartz, “iPhone Flaw Lets Hackers Take over, Security Firm says,” The New York Times, July 23, 2007, www.nytimes.com/2007/07/23/technology/23iphone.html
- 5. CBC News (2013, January 28) “WhatsApp breaches privacy laws,” CBC News, January 28 2013. www.cbc.ca/news/technology/story/2013/01/28/technology-whatsapp-privacy.html
- 6. Office of Privacy Commissioner of Canada, “Report of Findings Investigation into the personal information handling practices of WhatsApp Inc.,” January 15, 2013, www.priv.gc.ca/cf-dc/2013/2013_001_0115_e.asp
- 7. Memorandum by Arthur M. Money, Assistant Secretary of Defense for C3I, and CIO to Secretaries of the Military Departments, Chairman of the Joint Chiefs of Staff, Chief Information Officers of the Defense Agencies, et al., “Use of Mobile Code Technologies in DoD Information Systems,” October 23, 2006. www.dtic.mil/whs/directives/corres/pdf/855201p.pdf
