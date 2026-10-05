
# Hacking Multifactor Authentication

# Summary

In this chapter, we covered brute-force attacks against MFA solutions. You learned about common brute-force methods and saw multiple examples of real-world brute-forcing examples found by whitehat hackers. We concluded with a look at seven developer controls and one user control designed to help mitigate brute-force attacks.

- Chapter 15, “Buggy Software” will cover MFA solution vulnerabilities.

## 15 Buggy Software

This chapter will cover vulnerabilities in MFA solutions, discussing common types of vulnerabilities, potential exploitation outcomes, real-world examples, and defenses.

## Introduction

There is no such thing as perfect, flawless computer programming, at least not yet—in the real world—even by the very programmers who tried their hardest to prove it was possible. Today, it’s quite the opposite situation. Software, firmware, and chip vulnerabilities are everywhere. As Figure 4.1 showed in Chapter 4, “Usability vs. Security,” we had 12,174 publicly announced vulnerabilities in 2019. We had 16,356 the year before and 14,714 the year before that. So far humans have been poor at making flawless code. Some argue that artificial intelligence (AI) will one day make flawless code, but flawed like everything else we have ever done, and somehow I’m supposed to believe that the flawed AI would be capable of making flawless code? I don’t buy it.

As Figure 5.1 from Chapter 5, “Hacking MFA in General” showed, every MFA solution has a lot of components. We have to assume that every component and dependency in an authentication solution has one or more vulnerabilities and can be a potential attack vector. And there have been hundreds to thousands of security vulnerabilities on all sorts of authentication software. If you want to see if your authentication solution has any publicly known vulnerabilities, you can check a CVE (Mean www.cvetails.com/google-search-results.php). An example search on the vendor RSA, who has been around and doing cryptography and MFA longer than anyone, turns up at least 79 different published vulnerabilities (see Figure 15.1).

Publicly announced vulnerability sites only list the publicly announced vulnerabilities. Most vendors do not announce vulnerabilities internally or those found in preproduction. Days, some of the world’s best vendors keep their publicly released software in “beta” for years and feel that doing so somehow reduces their responsibility to have report security bugs to public databases.

## CVE Vulnerabilities database

The ultimate security vulnerabilities

## RSA Vulnerabilities

| # | ID | # Exploits | Publish | Update | Score | Access | Remote | Authenticity | Conf. | Intrag. | Align |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| CVE-2019-23758 | 2 | 0 | 2019-09-19 | - | 7.5 | High | None | Required | Partial | Partial | Partial |
| CVE-2019-23759 | 0 | 0 | 2019-09-19 | - | 8.3 | High | Remote | Medium | Required | None | None |
| CVE-2019-23760 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23761 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23762 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23763 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23764 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23765 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23766 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23767 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23768 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23769 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23770 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23771 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23772 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23773 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23774 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23775 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23776 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23777 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23778 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23779 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |
| CVE-2019-23780 | 0 | 0 | 2019-09-19 | - | 7.5 | High | Remote | Medium | Required | None | None |

## Common Types of Vulnerabilities

Programming vulnerabilities occur with any program, not just software. Vulnerabilities are frequently found in firmware and hardware devices, including CPU chips. Programming is the way all computers and electronic devices work, although most of the time that programming is hard-coded it is much harder to fix. One of my favorite sayings, is firmware are are harder-to-patch software

So, what are practices developers make to prevent security vulnerabilities? There are many types of threats that any programmer can make, although
